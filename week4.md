---
layout: default
title: WEEK4
permalink: /week4/
---
# **Schinder.PLC M221**

# Basic Ladder Programing in PLC 

## Basic I/O 
> Start New Project 
 Switch to RUN Mode 
ต่อวงจร กำหนด PC IP และ M221 IP 

![alt text](image-13.png)

* ตัวแปร %I คือ ตัวแปรที่รับค่ามาจาก port input จาก ตัว PLC 
* ตัวแปะ %Q คือ ตัวแปรที่ส่งค่าไปออกที่ port output ที่ตัว PLC 
* ตัวแปร %M คือ ตัวแปร memory ภายใน เพื่อส่งค่าไปให้ ตัวแปรภายใน

> Model >> TM221CE16R 

![alt text](image-14.png)
>เลือก board แล้ว login

![alt text](image-27.png)

## Output Same Input 

> เงื่อนไขการทดลอง 
  ทำวงจรที่สามารถทำงานได้ตามรายละเอียดต่อไปนี้
>1. กด SW1  LAMP1 แสดงการทำงาน 
>2. กด SW2  LAMP2 แสดงการทำงาน 
>3. กด SW3  LAMP3 แสดงการทำงาน 

![alt text](image-15.png)

> **วงจรที่ได้** :rotating_light:

![alt text](/assets/week4/d7449563-d598-4653-a501-7a0309465d83.jpg)

> **ผลลัพธ์ที่ได้** :sunflower:

![](/assets/week3/8db61560-2ff4-41a8-b78c-007d974b6202.jpg)

## Invert Output 

> เงื่อนไขการทดลอง 
ทำวงจรที่สามารถทำงานได้ตามรายละเอียดต่อไปนี้
>1. กด SW1  LAMP1 หยุดทำงาน 
>2. กด SW2  LAMP2 หยุดทำงาน 
>3. กด SW3  LAMP3 หยุดทำงาน 

![alt text](image-16.png)

> **วงจรที่ได้** :rotating_light:

![alt text](/assets/week4/40acdc0c-94b6-4aa1-ba8f-a1463dcad5b8.jpg)

> **ผลลัพธ์ที่ได้** :sunflower:

![](/assets/week4/5560af5e-b156-4474-af3b-9359c31727b1.jpg)
![](/assets/week4/749b20e7-a6e3-4b7d-ac56-baae367ec769.jpg)


## Self-Holding 
>เงื่อนไขการทดลอง 
>1. กด SW1  LAMP1 แสดงการทำงานค้างตลอดเวลา 
>2. กด SW2  LAMP1 หยุดทำงาน 

![alt text](image-17.png)

> **วงจรที่ได้** :rotating_light:

![alt text](/assets/week4/0ed34ef6-6a43-4b48-9374-a4d1b857719d.jpg)

> **ผลลัพธ์ที่ได้** :sunflower:

![](/assets/week4/f34a575e-38d8-41da-81e3-4584eeee549b.jpg)
![](/assets/week4/6247cf9c-ee2d-465a-95bb-def867173897.jpg)

## Set/Reset 

>เงื่อนไขการทดลอง 
>1. กด SW1  LAMP1 แสดงการทำงานค้างตลอดเวลา 
>2. กด SW2  LAMP1 หยุดทำงาน

![alt text](image-18.png)

> **วงจรที่ได้** :rotating_light:

![alt text](/assets/week4/f6f901e3-192f-4e03-8a10-1a9c9faf80ad.jpg)

> **ผลลัพธ์ที่ได้** :sunflower:

![alt text](/assets/week4/e37a423c-4242-49a7-8852-942c7137caca.jpg) 
![alt text](/assets/week4/ac212089-395b-4aa3-a7df-b502c0d4ae68.jpg)

## Inter Lock Output 
>เงื่อนไขการทดลอง 
>1.  กด SW1 ค้างไว้ LAMP1 จะแสดงการทำงาน, แต่ในขณะที่กด SW2 ต่อจาก SW1, LAMP2 จะแสดงการทำงานแทน LAMP 1 
>2.  กด SW2 ค้างไว้ LAMP2 จะแสดงการทำงาน, แต่ในขณะที่กด SW1 ต่อจาก SW2, LAMP1 จะแสดงการทำงานแทน LAMP 2 

![alt text](image-19.png)

> **วงจรที่ได้** :rotating_light:

![alt text](/assets/week4/70bab810-ad61-4e84-a521-03c3c8c2259e.jpg)

> **ผลลัพธ์ที่ได้** :sunflower:
![alt text](/assets/week4/2b15f7ba-9cbc-4d98-8d7e-21851b440232.jpg) 
![alt text](/assets/week4/ac915194-3ee4-46a0-913f-8500894cdb5f.jpg)

## Inter Lock Input 

>เงื่อนไขการทดลอง 
>1. กด SW1 LAMP1 แสดงการทำงาน, กด SW1 ค้าง จะไม่สามารถกด SW2 เพื่อแสดงการทำงานของ LAMP2 ได้ 
>2. กด SW2 LAMP2 แสดงการทำงาน, กด SW2 ค้าง จะไม่สามารถกด SW1 เพื่อแสดงการทำงานของ LAMP1 ได้ 

![alt text](image-20.png)

> **วงจรที่ได้** :rotating_light:

![alt text](/assets/week4/035c3f8f-1f91-4d43-8115-51d89cae9758.jpg)

> **ผลลัพธ์ที่ได้** :sunflower:
![alt text](/assets/week4/36b510ed-005d-476f-9207-3be71c27722d.jpg) 
![alt text](/assets/week4/489a3112-16ba-4d49-a608-87e47d74fab6.jpg)

## Pulse Input 
>เงื่อนไขการทดลอง 
>1. กด SW1 LAMP2 จะกะพริบ, ปล่อย SW1 LAMP1 จะกะพริบ

![alt text](image-21.png)

> **วงจรที่ได้** :rotating_light:

![alt text](/assets/week4/91803763-2284-4b3b-8abd-531ff60f2af5.jpg)

> **ผลลัพธ์ที่ได้** :sunflower:
![alt text](/assets/week4/7af7af64-1a70-47a2-b3b5-3807cbedebba.jpg) 
![alt text](/assets/week4/e81becfe-6a43-4562-a648-d03ee4c34ecb.jpg)

## Internal Relay 
>เงื่อนไขการทดลอง 
>1. ในขณะที่ไม่มีการกดสวิตช์ LAMP2 จะแสดงการทำงาน, แต่เมื่อกด SW1 LAMP2 จะหยุดการทำงาน แต่ LAMP1 จะทำงานแทน 

![alt text](image-22.png)

> **วงจรที่ได้** :rotating_light:

> **ผลลัพธ์ที่ได้** :sunflower:
![alt text](/assets/week4/5c2ce9e5-a28e-4d23-9db0-41d1e62059fc.jpg)
![alt text](/assets/week4/145a7963-953a-436e-8b36-a714fa376b06.jpg)

## Timer 
>เงื่อนไขการทดลอง 
>1. กด SW1  LAMP1 จะแสดงการทำงาน 3 วินาที หลังจากทำงานครบ 3 วินาที LAMP1 จะดับ 

![alt text](image-23.png)

> **วงจรที่ได้** :rotating_light:

![alt text](/assets/week4/17626b4e-31c9-4268-a624-c9db98eaf8f9.jpg)

> **ผลลัพธ์ที่ได้** :sunflower:
![alt text](/assets/week4/f5abbe9f-3cc2-4336-9cda-d7d2457087f3.jpg)
![alt text](/assets/week4/5a73f057-0251-40ea-a719-e84284f5f453.jpg) 

## Lamp Rotation

>เงื่อนไขการทดลอง
>1. กด SW1 LAMP1 แสดงการทำงาน 3 วินาที หลังจากทำงานครบ 3 วินาที LAMP1 จะดับ และ LAMP2 จะแสดงการทำงาน 3 วินาที  หลังจากทำงานครบ 3 วินาที LAMP2 จะดับ และ LAMP3 จะแสดงการทำงาน 3 วินาที หลังจากทำงานครบ 3 วินาที LAMP3 จะดับทำงานแบบนี้วนซ้ำไปเรื่อย ๆ 
>2. กด SW2 จะหยุดการทำงานของ LAMP ทั้ง 3 หลอด 

![alt text](image-24.png)

> **วงจรที่ได้** :rotating_light:

> **ผลลัพธ์ที่ได้** :sunflower:
> ![alt text](/assets/week4/e9cf4cde-2b6b-45f2-b311-12c8884ddc63.jpg)
> ![alt text](/assets/week4/e37a423c-4242-49a7-8852-942c7137caca.jpg) 
![alt text](/assets/week4/ac212089-395b-4aa3-a7df-b502c0d4ae68.jpg)

## Flash LED (LED Flicker) 

>เงื่อนไขการทดลอง 
>1. กด SW1 LAMP1 แสดงการทำงาน 1 วินาที หยุดทำงาน 1 วินาที และเริ่มทำงานใหม่แบบต่อเนื่อง 
>2. กด SW2 LAMP1 หยุดการทำงาน 

![alt text](image-25.png)

> **วงจรที่ได้** :rotating_light:

> **ผลลัพธ์ที่ได้** :sunflower:
> ![alt text](/assets/week4/a39766ec-f0cc-4901-a4b2-1181e8b5d71f.jpg)
> ![alt text](/assets/week4/cfb262f1-a4fa-48ff-86ed-18895dab85dd.jpg)

## Counter 

>เงื่อนไขการทดลอง 
>1. กด SW3 Counter UP ครบ 5  ครั้ง  LAMP1 ทำงาน 
>2. กด SW1 เพื่อ RESET Counter นับ 0 LAMP1 หยุดทำงาน 
>3. กด SW2 เพื่อ SET Counter นับ 5 LAMP1 หยุดทำงาน 
>4. กด SW4 Counter  Countdown นับ 4,3,2,1 ตามลำดับ LAMP1 หยุดทำงาน 

![alt text](image-26.png)

> **วงจรที่ได้** :rotating_light:

> **ผลลัพธ์ที่ได้** :sunflower:
>![alt text](/assets/week4/56e2ae81-8014-402b-9dcd-6e41d10e40ad.jpg) 
![alt text](/assets/week4/fab78348-bf0f-472c-a36b-6782cd40808c.jpg) 
![alt text](/assets/week4/be803e27-6302-4104-a309-7adbfdf2b898.jpg)

##  Traffic Light Control 

> **วงจรที่ได้** :rotating_light:
>input
![alt text](/assets/week4/a067964b-5892-4e34-91b9-ff0b8047f990.jpg) 
>mode select
![alt text](/assets/week4/c0e5824d-c2e9-4dce-8c32-c93670bab3d5.jpg) 
>mode
![alt text](/assets/week4/bcc770da-6b50-4cbb-a46c-a393d384e616.jpg) 
![alt text](/assets/week4/cb9eb177-2493-42df-b911-e7faf81a864a.jpg) 
![alt text](/assets/week4/b4b72e1d-a8d5-40f4-bd96-1ded9cd109da.jpg)

> **ผลลัพธ์ที่ได้** :sunflower:
> ![alt text](/assets/week4/0c7e6a54-a048-4d11-976a-ba9b1d99bc21.jpg) 
> ![alt text](/assets/week4/ec3102b4-2c97-4913-b3e0-34e399c56bbb.jpg) 
> ![alt text](/assets/week4/011ec008-392b-406d-8fe6-a80475572ee2.jpg)