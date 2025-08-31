---
layout: default
title: WEEK6
permalink: /week6/
---

# **Industrial remote control and image processing** :camera:

* **CCTV AND NETWORK**

# Mission  
[1. Switch and Lamp](#1-switch-and-lamp)  
[2. CCTV and IP Camera](#2-cctv-and-ip-camera)  
[3. Zerotier](#3-zerotier)

## 1. Switch and Lamp

![](/assets/week6/Screenshot%202025-08-31%20153250.png)

### Self Holding Circuit  
> วงจรนี้เป็นวงจรรีเลย์พื้นฐานที่เรียกว่าวงจร "สตาร์ท-สต็อป" หรือ "วงจรล็อคตัวเอง (Latching Circuit)" ซึ่งมักใช้ในการควบคุมการเปิด-ปิดอุปกรณ์ไฟฟ้าต่างๆ ด้วยปุ่มกดเพียงครั้งเดียว

![](/assets/week6/Screenshot%202025-08-31%20162304.png)  
• กด ON: หลอดไฟติดค้าง  
• กด OFF: หลอดไฟดับ

> **วงจรที่ได้** :rotating_light:  
![](/assets/week6/4e5957f2-3fd3-4ffc-8f3d-72de9ea40c35.jpg)

> **ผลลัพธ์ที่ได้** :sunflower:  
[YouTube](https://youtu.be/HYyC-zmJW1k) :tv:  
![](/assets/week6/e5c2ea08-72e0-4e63-8335-055c2b8edd72.jpg)
![](/assets/week6/faf13c82-51c4-40b3-ae09-4adba4a471d5.jpg)

### Interlocking circuit

> วงจรประเภทนี้เรียกว่า วงจรอินเตอร์ล็อก (Interlocking Circuit) หรือ วงจรสตาร์ทมอเตอร์แบบกลับทิศทาง (Reversing Motor Control Circuit)
> หลักการทำงานเบื้องต้นของวงจรนี้:
 •	วงจรนี้ใช้หลักการ "อินเตอร์ล็อก" เพื่อป้องกันไม่ให้อุปกรณ์สองตัวทำงานพร้อมกัน ซึ่งเป็นสิ่งสำคัญในงานควบคุมที่ต้องการความปลอดภัยสูง (เช่น การหมุนมอเตอร์ไปข้างหน้าและถอยหลัง)
•	เมื่อกดปุ่ม S2 วงจรจะล็อคให้ K1 ทำงาน และจะไม่มีทางที่ S3 จะสั่งให้ K2 ทำงานได้
•	เมื่อกดปุ่ม S3 วงจรจะล็อคให้ K2 ทำงาน และจะไม่มีทางที่ S2 จะสั่งให้ K1 ทำงานได้
•	หากต้องการสลับการทำงานจาก K1 ไป K2 จะต้องตัดวงจรการล็อคตัวเองของ K1 ก่อน โดยการกดปุ่ม S1 เพื่อหยุดการทำงาน แล้วจึงจะสามารถสั่งให้ K2 ทำงานได้
•	หลอดไฟ L1 และ L2 ใช้แสดงสถานะการทำงานของ K1 และ K2 ตามลำดับ


> **วงจรที่ได้** :rotating_light:  
![](/assets/week6/4e5957f2-3fd3-4ffc-8f3d-72de9ea40c35.jpg)

> **ผลลัพธ์ที่ได้** :sunflower:  
[YouTube](https://youtu.be/emaeK4DWwGo) :tv:  
![](/assets/week6/501b7a81-6e90-41da-b3fb-846b2fda8f1b.jpg)  
![](/assets/week6/bcde53bd-f412-4a90-8d21-f25cc1acc481.jpg)


## 2. CCTV and IP Camera

> Setup and Config
>1. ต่อวงจร
• ต่อ WAN เข้ากับ PoE Switch (TSW100:Teltonika Unmanaged PoE+ Ethernet
Switch)
• ต่อ IP Camera HKVision เข้ากับ PoE Switch
• ต่อ Remote PC เข้ากับ PoE Switch

![](/assets/week6/Screenshot%202025-08-31%20170330.png)

### Capture จาก Web URL

>รันโปรแกรม Advance IP Scan

![](/assets/week6/Screenshot%202025-08-31%20171535.png)

>ตรวจสอบ MAC Address ของอุปกรณ์ และรีโมตเข้าเพื่อตั้งค่า ใช้งานผ่าน browser

![](/assets/week6/Screenshot%202025-08-31%20171710.png)

>Take a snapshot via HTTP URL
###### http://username:password@address:httpport/ISAPI/Streaming/Channels/channel/picture

> **วงจรที่ได้** :rotating_light:

![](/assets/week6/1f7c09b4-a271-43bb-836f-e4aa9ed5bb24.jpg)
> **ผลลัพธ์ที่ได้** :sunflower:
![](/assets/week6/3d4fa047-6de0-4fb5-88b7-e2267d2c711d.jpg)

### Capture จาก VLC Program
>Live View with VLC
> * Live with rtsp on VLC Program
    Open Media >> rtsp://admin:admin@192.168.1.64:554/Streaming/Channels/102/
![](/assets/week6/Screenshot%202025-08-31%20191210.png)


> **ผลลัพธ์ที่ได้** :sunflower:
![](/assets/week6/Screenshot%202025-08-31%20191547.png)

### Capture จาก Python Code

![](/assets/week6/4a2f6cbe-316c-492f-8c64-1670f81f4da0.jpg)

> Code :computer:
![](/assets/week6/Screenshot%202025-08-31%20192001.png)

> **ผลลัพธ์ที่ได้** :sunflower:
![](/assets/week6/5d62708b-afd8-46bd-a3c1-c451ce66288b.jpg)



## 3. Zerotier

![](/assets/week6/Screenshot%202025-08-31%20193628.png)

### Setup Device
![](/assets/week6/Screenshot%202025-08-31%20194734.png)

> * Download firmware @20250424 = RUT9M_R_00.07.13.4_WEBUI.bin >> https://wiki.teltonika-networks.com/view/RUT956_Firmware_Downloads
> * Fix Notebook IP = 192.168.1.23, run browser ไปที่ ip 192.168.1.1
> * ทํา Factory Reset ให้ RUT_956 ด้วยการ 
> (1)กด Reset ค้างไว้ 
> (2)จ่ายไฟเข้า RUT_956
(3)รอประมาณ 12-20 วินาที
(4)ปล่อย Reset
>* ทําการ Update firmware
>
![](/assets/week6/Screenshot%202025-08-31%20194244.png)

> * แล้วรีโมทเข้าตั้งค่าผ่าน LAN1 Port โดยหลังทํา Factory Reset RUT_956
> * login: admin, pass: ดูได้ที่ใต้อุปกรณ์
> * ตั้งค่าให้ RUT_956 รับสัญญาณอินเทอร์เน็ตทาง WAN Port และทํางานเป็น DHCP Server กําหนดให้จ่าย IP = 192.168.2.1/24

![](/assets/week6/Screenshot%202025-08-31%20194528.png)

### Remote On/Off Control in LAN Group 

> **วงจรที่ได้** :rotating_light:
![](/assets/week6/Screenshot%202025-08-31%20201851.png)


> **ผลลัพธ์ที่ได้** :sunflower:
![](/assets/week6/Screenshot%202025-08-31%20202043.png)
------------------------------------------------------

> * สมัครและตั้งค่า ZeroTier
> * สมัครใช้งาน Zerotier One >> https://www.zerotier.com/
> * กําหนดให้ใช้ IPV4 = 192.168.191.*
![](/assets/week6/Screenshot%202025-08-31%20200008.png)

> * ติดตั้ง Zerotier One บนอุปกรณ์รีโมท
https://www.zerotier.com/download/
> * Join ZeroTier Network
![alt text](image-28.png)
> * ZeroTier Web ทําการ Authorized อุปกรณ์ที่ Join เข้ามา
![alt text](image-29.png)

------------------------------------------
### ติดตั้ง ZeroTier บน RUT-956
> 
![alt text](/assets/week6/Screenshot%202025-08-31%20201605.png)


> * เพิ่ม ZT Package
> ![](/assets/week6/Screenshot%202025-08-31%20200832.png)
> * เพิ่ม Network ID
> ![](/assets/week6/Screenshot%202025-08-31%20201123.png)
> * ตรวจสอบด้วย CLI (Command Line Interface) : ifconfig
>
> * ทําการ Managed Routes
จาก IP ที่ RUT-956 จ่าย (192.168.2.0/24) >> ให้มาที่ ZT Port (192.168.191.*)
![](/assets/week6/Screenshot%202025-08-31%20201505.png)

### Remote On/Off Control in WAN Group 

> **วงจรที่ได้** :rotating_light:
![](/assets/week6/Screenshot%202025-08-31%20202257.png)

> **ผลลัพธ์ที่ได้** :sunflower:
![](/assets/week6/Screenshot%202025-08-31%20202458.png)

--------------------------------------------------------
### Remote Access IP Camera in WAN Group

![](/assets/week6/Screenshot%202025-08-31%20202726.png)

> * ตรวจสอบ IP กล้อง (ตัวอย่าง: 192.168.2.64)
> * ตัวอย่าง RTSP Path สำหรับ TP-Link VIGI: rtsp://username:password@192.168.2.64:554/stream1
> * เปิด VLC → Media → Open Network Stream → วาง URL

> **ผลลัพธ์ที่ได้** :sunflower:
> ![](/assets/week6/ec8b647a-d45f-4025-a148-5583c9b9a32c.jpg)