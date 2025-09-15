---
layout: default
title: WEEK8
permalink: /week8/
---
# **IRIV Pi Control**

![](/assets/week8/Screenshot%202025-08-31%20204746.png)

###### IRIV Pi Control เป็น Industrial Revolution 4.0 controller ที่พัฒนาโดย Cytron
Technologies โดยใช้ Raspberry Pi Compute Module 4 (CM4) เป็นหัวใจหลัก ออกแบบมา สําหรับงานอุตสาหกรรมที่ต้องการความทนทาน เสถียรภาพ และความสามารถในการเชื่อมต่อที่หลากหลาย

# Setup Device
**[How to Flash OS Into IRIV PiControl](https://th.cytron.io/tutorial/how-to-flash-os-into-iriv-picontrol?r=1)**

> * **Step - Install Image 1/3 - Open IRIV PiControl Case:**
> ![](/assets/week8/Screenshot%202025-08-31%20205837.png)

> * **Step - Install Image 2/3 - Switch on the Boot Mode:**
> ![](/assets/week8/Screenshot%202025-08-31%20210304.png)
> * Connect a USB-C (data) cable from your laptop/PC to IRIV PiControl.

>* **Step - Install Image 3/3 - Flashing OS into Raspberry Pi CM4 eMMC:**
> * On your computer, **install and run rpiboot.exe** to make CM4 eMMC a mass storage device for
Windows.
![alt text](image-31.png)
> * Disconnect the USB cable and set the BOOT switch to its original position. Close the casing. Done!


> * **เปิดใช้งาน (Power On)**
> * ต่อไฟเลี้ยง DC 10–30V (0.3A) → Terminal Block
หรือใช้ USB-C (5V, ≥1.5A)
> * รอให้จอ OLED แสดงผลข้อมูลระบบ (IP, CPU Load, Temp ฯลฯ)
> * IRIV จะเข้าสู่โหมด Access Point Mode โดยอัตโนมัติ
> ![](/assets/week8/36456604-1441-4da7-ac49-5370f3ddd99a.jpg)

> * เข้าใช้งานแบบ Remote ที่หน้า GUI Dashboard >> 192.168.162.21:1800/ui
> ![alt text](image-32.png)

> * สามารถเข้าดู Node-RED flow ได้ >> 192168.162.21:1880
> ![alt text](image-33.png)

## ทดสอบ GPIO ด้วย Thony Python 

> * ใช้โปรแกรม Putty เพื่อรีโมตเปิดใช้งาน VNC Server บน IRIV Pi Control
> • Putty >> IP >> 192.168.162.***
• Login: pi
• Pass: ***
![](/assets/week8/Screenshot%202025-08-31%20211728.png)

> **ผลลัพธ์ที่ได้** :sunflower: 
![alt text](image-34.png)

## Remote Desktop over ZeroTier

> * ต่อ IRIV PiControl ผ่าน ZeroTier Network
![alt text](image-35.png)
> * ตรวจสอบ LAN IP ที่ RUT9556 จ่าย โดยไปที่ Status ➔ Network ➔ LAN
> ![alt text](image-36.png)
> * เข้าใช้งาน Remote I/O ได้ IP
> ![alt text](image-37.png)

## M2M Communication

> **1.Modbus RTU with NodeRED >> XY-MD02**
> * Add Node ➔ Manage Palate
> ![alt text](image-38.png)
> * Test XY-MD02 with Node-RED on IRIV Pi
> ![alt text](image-39.png)
> * Place Node
> ![alt text](image-40.png)

![alt text](image-41.png)
>* * Slave ID = 1
>* * Function = 4
>* * Start Addr = 1
>* * Quantity = 2 Byte
>* * Dev/ttyACM0:9600

![alt text](image-42.png)

>* * Modbus RTU
>* * Serial
>* * /dev/ttyACM0
>* * RTU
>* * 9600
>* * Master ID = 0
>* * Timeout = 1000

> **วงจรที่ได้** :rotating_light: 
![alt text](image-43.png)

> **ผลลัพธ์ที่ได้** :sunflower: 
> ![alt text](image-44.png)

> **2.Modbus TCP with NodeRED**
> ![alt text](image-45.png)
> * PC: Modbus Poll  → ESP32(Server)
```cpp
#include <Modbus.h>
#include <ModbusIP_ESP32.h>
#define mySSID "IoT-Test"
#define myPass "212224236248"
//Modbus Registers Offsets (0-9999)
const int LED_COIL = 100;
//Used Pins
const int ledPin = 2; // LED Test
//ModbusIP object
ModbusIP mb;
void setup() {
Serial.begin(115200);
Serial.print("\nConnecting to ");
Serial.println(mySSID);
mb.config(mySSID, myPass);
while (WiFi.status() != WL_CONNECTED) {
delay(500);
Serial.print(".");
}
Serial.println("");
Serial.println("WiFi connected");
Serial.println("IP address: ");
Serial.println(WiFi.localIP());
pinMode(ledPin, OUTPUT);
mb.addCoil(LED_COIL);
}
void loop() {
//Call once inside loop() - all magic here
mb.task();
//Attach ledPin to LED_COIL register
digitalWrite(ledPin, mb.Coil(LED_COIL));
}
```

> ![alt text](image-46.png)
> * Modbus Poll – Connection
Setup
> ![alt text](image-47.png)
> * Modbus TCP/IP
> * IP Server = xx.xx.xx.xx
> * Server Port = 502
> * Timeout = 3000
> * IP Mode = IPv4

> * **Read/Write Definition** 
> * Slave ID = 1
> * Func = 01 Read Coils
> * Address Mode = Dec
> * Address = 100
> * Quantity = 10
> * Scan Rate = 1000
> * View Row = 10


> * **Read/Write Coil with Node-Red from IRIV Pi**
> ![alt text](image-48.png)
> * Inject
Boolean = True
Boolean = False
> ![alt text](image-49.png)
> * **Set Server**
> * Type = TCP
> * Host Server IP = xx.xx.xx.xx
> * Port = 502
> ![alt text](image-50.png)
> *  **Read Modbus**
> * FC1 – Read Single Coil
> * Address = 100
> * Quantity = 1
> * Poll Rate = 1 Sec.
> * Server = modbus-
> * tcp@xx.xx.xx.xx:502
> * **Write Modbus**
> * FC5 – Write Single Coil
> * Address = 100
> * Server = modbus-
> * tcp@xx.xx.xx.xx:502

> **ผลลัพธ์ที่ได้** :sunflower: 
![alt text](image-51.png)

> * **3.RS485 IIoT Gateway** 
> ![alt text](image-53.png)
> * Test Read SDM120M to MQTT Broker / Control from Broker
> * Set Broker >> https://testclient-cloud.mqtt.cool/
> ![alt text](image-54.png)
> * Subscribe topic: myIRIV_Test1248
Publish to topic: myIRIV_Test1248
> * 6.2 Read SDM120M and Send to Broker
> * * Modbus Read < last topic >
Function < last topic >
> ![alt text](image-55.png)
> * * Add Server
Name = myTest
Server = broker.mqtt.cool
Port = 1883
> ![alt text](image-56.png)
> * * Server = myTest
Topic = myIRIV_Test1248
> ![alt text](image-57.png)

> **ผลลัพธ์ที่ได้** :sunflower: 

> ![alt text](image-58.png)


## **Machine Vision**
>
> * Install OpenCV
> * * sudo apt update && sudo apt upgrade -y
> * * pip3 install opencv-contrib-python

> **Copy OpenCV_File.zip to /home/pi**
> Copy OpenCV_File.zip to /home/pi ไปไว้ใน pi 

> ##### Note วิธีย้ายไฟล์จากคอมเราไปใน pi ผ่าน cmd
> scp -r "D:\Embedded\Week0800 -- IRIV Pi Control-20250819T064259Z-1-001\Week0800 -- IRIV Pi Control\01_Image_Software\OpenCV_File.zip" pi@xxx.xxx.xxx.xxx:/home/pi

```cpp
import cv2
image_path = '/home/pi/OpenCV_File/image/lena30.jpg'
img = cv2.imread(image_path)
cv2.imshow("Lena Image", img)
cv2.waitKey(0)
cv2.destroyAllWindows()
```
> **ผลลัพธ์ที่ได้** 
> ![](/assets/week8/e04c29bb-7ea6-49ce-8e28-9abe31da6319.jpg)


> * **Open USB Camera – with ffplay**
> * * sudo apt-get update && sudo apt-get upgrade -y
v4l2-ctl --list-devices
> * * sudo apt install ffmpeg
ffplay /dev/video0
> ![](/assets/week8/2e26d0b5-bde3-450a-94ff-8c22ffb2c4c4.jpg)

> * **Open USB Camera – with vlc**
> ![alt text](image-52.png) 

> **ผลลัพธ์ที่ได้** 
> ![](/assets/week8/4884fc11-c847-4cd9-9e63-f2385d9cd994.jpg)
>
> * TP-Link 1920x1080 >> rtsp://admin:adminZ01@192.168.1.3:554/stream1
> 
> ![alt text](image-62.png)
> **ผลลัพธ์ที่ได้** 
> ![](/assets/week8/a0d41a8d-c373-40d6-aae4-f860b63ddb7e.jpg)

> * **Open USB Camera – with python Code**
> ![alt text](image-61.png)
> 
> **ผลลัพธ์ที่ได้** 
> ![](/assets/week8/d6426987-9760-4cf6-8c59-42356ddce8e4.jpg)

##### Circle Detect
> * **Pipe Count**
> 
> ![alt text](image-63.png)
```cpp
image_path = '/home/pi/OpenCV_File/image/XX.jpg'
import cv2
import numpy as np
Cimg = cv2.imread(image_path)
Gimg = cv2.imread(image_path,0)
cv2.imshow ('Original Image', Cimg)
imgBlur = cv2.medianBlur(Gimg,7)
imgEdges = cv2.Canny (imgBlur, 50, 100, apertureSize=5, L2gradient=True)
circles = cv2. HoughCircles(imgEdges, cv2.HOUGH_GRADIENT,1,35, param1=25, param2=30, minRadius=15, maxRadius=30)
Count = 0
if circles is not None:
circles = np.uint16(np.around(circles))
for i in circles[0,:]:
cv2.circle(Cimg, (i[0],i[1]),i[2],(0,255,0),2)
cv2.circle(Cimg, (i[0],i[1]),2 ,(0,0,255),3)
Count = Count + 1
else:
print('circle not found')
TEXT_FACE = cv2.FONT_HERSHEY_DUPLEX
TEXT_SCALE = 1.5
TEXT_THICKNESS = 2
Text = 'nCounter = ' + str(Count)
cv2.putText(Cimg, Text, (10,50), TEXT_FACE, TEXT_SCALE, (0,0,0), TEXT_THICKNESS, cv2.LINE_AA)
print(Text)
cv2.imshow ('Detected circles',Cimg)
cv2.waitKey (0)
cv2.destroyAllWindows()
```

> **ผลลัพธ์ที่ได้** 
> ![](/assets/week8/bd6cfaee-5415-4de8-897a-0fa33bd2dc27.jpg)

##### Face Detection with Haar Cascade Model

```cpp
import cv2
import math
import argparse
myName = 'Gender and Age Detection'
imageC = cv2.imread("/home/pi/OpenCV_File/image/GenAge/test01.jpg")
def highlightFace(net, frame, conf_threshold=0.7):
frameOpencvDnn=frame.copy()
frameHeight=frameOpencvDnn.shape[0]
frameWidth=frameOpencvDnn.shape[1]
blob=cv2.dnn.blobFromImage(frameOpencvDnn, 1.0, (300, 300), [104, 117, 123], True, False)
net.setInput(blob)
detections=net.forward()
faceBoxes=[]
for i in range(detections.shape[2]):
confidence=detections[0,0,i,2]
if confidence>conf_threshold:
x1=int(detections[0,0,i,3]*frameWidth)
y1=int(detections[0,0,i,4]*frameHeight)
x2=int(detections[0,0,i,5]*frameWidth)
y2=int(detections[0,0,i,6]*frameHeight)
faceBoxes.append([x1,y1,x2,y2])
cv2.rectangle(frameOpencvDnn, (x1,y1), (x2,y2), (0,255,0), int(round(frameHeight/150)), 8)
return frameOpencvDnn,faceBoxes
faceProto = "/home/pi/OpenCV_File/data/opencv_face_detector.pbtxt"
faceModel = "/home/pi/OpenCV_File/data/opencv_face_detector_uint8.pb"
ageProto = "/home/pi/OpenCV_File/data/age_deploy.prototxt"
ageModel = "/home/pi/OpenCV_File/data/age_net.caffemodel"
genderProto = "/home/pi/OpenCV_File/data/gender_deploy.prototxt"
genderModel = "/home/pi/OpenCV_File/data/gender_net.caffemodel"
MODEL_MEAN_VALUES = (78.4263377603, 87.7689143744, 114.895847746)
ageList = ['(0-2)', '(4-6)', '(8-12)', '(15-20)', '(25-32)', '(38-43)', '(48-53)', '(60-100)']
genderList = ['Male','Female']
faceNet = cv2.dnn.readNet(faceModel,faceProto)
ageNet = cv2.dnn.readNet(ageModel,ageProto)
genderNet = cv2.dnn.readNet(genderModel,genderProto)
padding=20
frame = imageC.copy()
resultImg,faceBoxes=highlightFace(faceNet,frame)
if not faceBoxes:
print("No face detected")
for faceBox in faceBoxes:
face=frame[max(0,faceBox[1]-padding):min(faceBox[3]+padding, frame.shape[0]-1),
max(0,faceBox[0]-padding):min(faceBox[2]+padding, frame.shape[1]-1)]
blob=cv2.dnn.blobFromImage(face, 1.0, (227,227), MODEL_MEAN_VALUES, swapRB=False)
genderNet.setInput(blob)
genderPreds=genderNet.forward()
gender=genderList[genderPreds[0].argmax()]
print(f'Gender: {gender}')
ageNet.setInput(blob)
agePreds=ageNet.forward()
age=ageList[agePreds[0].argmax()]
print(f'Age: {age[1:-1]} years')
print()
cv2.putText(resultImg, f'{gender}, {age}', (faceBox[0], faceBox[1]-10),
cv2.FONT_HERSHEY_SIMPLEX, 0.7, (0,255,255), 2, cv2.LINE_AA)
cv2.imshow(myName + " >> Detecting age and gender", resultImg)
cv2.waitKey(0)
cv2.destroyAllWindows()
```
> **ผลลัพธ์ที่ได้** 
> ![](/assets/week8/33d6260b-e016-4323-9d39-a506690f9109.jpg)

##### Yolo8
> * ติดตั้ง Ultralytics
pip install ultralytics
![alt text](image-64.png)