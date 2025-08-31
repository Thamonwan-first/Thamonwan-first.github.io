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