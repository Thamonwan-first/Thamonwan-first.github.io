---
layout: default
title: WEEK3
permalink: /week3/
---

# **PLC - Siemens LOGO!**

# Mission 

[1.	LOGO8_t01_InputOutput](#LOGO8_t01_InputOutput)   
[2.LOGO8_t02a_pressOnpressOff_Ladder = Toggle with Ladder ](#LOGO8_t02a_pressOnpressOff_Ladder=Toggle_with_Ladder)  
[3. LOGO8_t02b_pressOnpressOff = Toggle with FBD](#LOGO8_t02b_pressOnpressOff=Toggle_with_FBD)  
[4. LOGO8_t03_pressOn_HoldOff ](#LOGO8_t03_pressOn_HoldOff)  
[5.  LOGO8_t04_Using_Cursor ](#LOGO8_t04_Using_Cursor)  
[6.  LOGO8_t05a_Count_Show](#LOGO8_t05a_Count_Show)  
[7. LOGO8_t05b_Count_SpeedUp](#LOGO8_t05b_Count_SpeedUp)
[8. LOGO8_t10_Modbus_TCP ](#LOGO8_t10_Modbus_TCP)
[9. LOGO8_t10_Samkoon_LOGO8 ](#LOGO8_t10_Samkoon_LOGO8)
[10. LOGO8_t90_Traffic_Light ](#LOGO8_t90_Traffic_Light)

## **LOGO8_t01_InputOutput**
![](/assets/week3/Screenshot%202025-07-21%20214105.png)

>3.1 Add Device: Network View → Add New Device >> Select = LOGO! 8_3_1, IP, SN, GW  
3.2 Edit FBD and save to “LOGO8_t01_InputOutput”   
3.3 Load: Tools → Transfer → PC to LOGO8, Fill LOGO! IP, Ok   
3.4 RUN: Change to Run Mode  

![](/assets/week3/Screenshot%202025-08-24%20012538.png)

> **ผลลัพธ์ที่ได้** :sunflower:

![](/assets/week3/933b1c7f-2c72-45f1-9c1c-2289d630782b.jpg)

![](/assets/week3/edffbc0d-79d0-41cd-8a08-ad66372a9a0d.jpg)

## **LOGO8_t02a_pressOnpressOff_Ladder=Toggle_with_Ladder**
>Contacts → Make Contact   
>Special Function → Micelenos → And Edge    
>Contacts → Relay Coil   
>Contacts → Break Contact   

![](/assets/week3/Screenshot%202025-07-21%20214120.png)

> RUN

![](/assets/week3/Screenshot%202025-08-24%20012538.png)

> **ผลลัพธ์ที่ได้** :sunflower:

![](/assets/week3/edffbc0d-79d0-41cd-8a08-ad66372a9a0d.jpg)
![](/assets/week3/41ec9464-b734-4c12-9ee9-4e5977a00793.jpg)

## **LOGO8_t02b_pressOnpressOff=Toggle_with_FBD**
>.Input, AND (Edge), Flag, XOR, Output  
.Input, NOT, AND (Edge), Flag, XOR, Output 

![](/assets/week3/Screenshot%202025-07-21%20214137.png)

> **ผลลัพธ์ที่ได้** :sunflower:

![](/assets/week3/8b8fc7d1-756e-4862-8cfa-ac48f2ec3b55.jpg)

![](/assets/week3/11a7e2a1-0b7e-486a-833f-ab8704761467.jpg)

## **LOGO8_t03_pressOn_HoldOff**

>6.1 Edit FBD for I1 and I2  
6.2 Edit FBD for “Hold(2Sec)On_Hold(4Sec)Off” 

![](/assets/week3/Screenshot%202025-07-21%20214152.png)

> **ผลลัพธ์ที่ได้** :sunflower:

![](/assets/week3/8b8fc7d1-756e-4862-8cfa-ac48f2ec3b55.jpg)

![](/assets/week3/11a7e2a1-0b7e-486a-833f-ab8704761467.jpg)


## **LOGO8_t04_Using_Cursor**
>7.1 Press (ESC + Cursor Key) for Input   
7.2 Double Click B002 for Text Edit and display All Member Name on Screen   
7.3 Edit FBD for “Up/Dw = On/Off Q0” and “LF/RG = On/Off Q1”  

![](/assets/week3/Screenshot%202025-07-21%20214048.png)
![](/assets/week3/Screenshot%202025-08-25%20013042.png)

> **ผลลัพธ์ที่ได้** :sunflower:  
>ESC + Cursor = การนำทางเมนู

![](/assets/week3/8b373aa5-c2b8-4095-b798-253d703834af.jpg)

## **LOGO8_t05a_Count_Show**
>8.1 More Data  [Youtube](https://www.youtube.com/watch?v=aOQxynpRd1o)  :book:  
8.2 Counter increase/decrease and show 

![](/assets/week3/Screenshot%202025-07-21%20222609.png)

> **ผลลัพธ์ที่ได้** :sunflower: 
>![](/assets/week3/e5110c97-1bfc-4acd-8b2a-d55f58e8512b.jpg)

## **LOGO8_t05b_Count_SpeedUp**
>9.1 More Data [Youtube](https://www.youtube.com/watch?v=aOQxynpRd1o) :book:    
9.2 Counter increase/decrease with speed up and show 

![](/assets/week3/Screenshot%202025-07-21%20231845.png)

> **ผลลัพธ์ที่ได้** :sunflower: 

![](/assets/week3/c528676b-21fc-4be3-9f75-ae61d674047e.jpg)
![](/assets/week3/0aad4f08-d5fa-4454-87e5-1a0b60afeafd.jpg)

## **LOGO8_t10_Modbus_TCP**
* 10.1 LOGOSoft Code  
   * Right Click → Add Server Connection → Modbus Communication   
  * Modbus TCP at IP and Port = 502  

![](/assets/week3/Screenshot%202025-08-25%20015333.png)
![](/assets/week3/Screenshot%202025-08-25%20015345.png)
![](/assets/week3/modbus.png)
![](/assets/week3/Screenshot%202025-07-22%20003949.png)

* 10.2 Test with ModbusPool 
  * 10.2.1 Install Modbus Poll 64 Bit V 9.5.0 
  * 10.2.2 Remote from “Modbus Poll”   
    * Connection → Connect → Modbus TCP/IP   
    * Modbus TCP == IP:502 
  
![](/assets/week3/Screenshot%202025-08-25%20020513.png)

 * * 10.2.3 Setup → Read/Write Definition

![](/assets/week3/Screenshot%202025-08-25%20020851.png)

 * * 10.2.4  Display in Binara Word 

![](/assets/week3/Screenshot%202025-08-25%20021011.png)

> **ผลลัพธ์ที่ได้** :sunflower: 

![](/assets/week3/b849d3c4-6d68-4021-bf85-dde65c2ee728.jpg)
![](/assets/week3/bb262d2a-67ba-4d89-9810-57b4aecbf214.jpg)

## **LOGO8_t10_Samkoon_LOGO8**
* 10.5Test with Samkoon HMI 
  * 10.5.1 Install Samkoon Software “SKTOOLV7.0.0.35_setup(20191220)”
  * 10.5.2 Open SKTOOL7.0 → New Project → Model=SK-070HS

![](/assets/week3/Screenshot%202025-08-25%20193936.png)

* * Create Link-1
* * Create Screen

![](/assets/week3/Screenshot%202025-08-25%20194500.png)

* Communication Port
  *  General Tab

![](image.png)

* * Parameter Tab
* * PLC IP:502

![](image-1.png)

* Modbus Poll
  * Function 03 Read Holding(4x)

![](image-2.png)

* Samkooon
  * Click Numeric Display
  
![](image-3.png)

* * Edit
* * Data Type = 16 Unsigned
* * Display Type = 16 Binary
* * Monitor Address = Link1, 4x0

![](image-4.png)

* * And Copy
* * Change Monitor Address for Link1 4x0, Link1 4X1

![](image-5.png)

* Download → Online
* Simulation
  * Link1 Tab → Run

![](image-6.png)

* Click Bit Lamp

![](image-7.png)

  * * Edit
      * Shape = 21
      * State 1 = Red, Black, Red
      * State 0 = Green, Black, Green
      * Data Type = Word Bit
      * Monitor Address = Link1, 4x0
      * Bit Number = 8

![](image-8.png)

* * Place Bit Lamp
* *  And Copy
* *  Change Monitor 
Address for Link1 
4x0, Link1 4x1, Link1 
4x2, Link1 4x3

![](image-10.png)

* Download → Online
* Simulation
  * Link1 Tab → Run

![](image-9.png)


Modbus Poll
* Write Single Register
* ID = 1
* Function = 6
* Address = 0x003
* Value = 0x0100

| ![](/assets/week3/Screenshot%202025-08-25%20211540.png)  |
|---|
| Frame = 00 98 00 00 00 06 01 06 00 03 01 00 
 ID = 01
  Function = 06 
 Address = 00 03 
 Value = 01 00    |

Select Bit Switch 

![alt text](image-11.png)

| ![](/assets/week3/Screenshot%202025-08-31%20000144.png)  |
|---|
| Edit 
• Shape 
• Border = Gold 
• FG = Black 
• BG = Gold 
• Function = Set ON 
• Mode = Press Execute 
• Write Address = LB0 
• Appearance, Text = Set On  |
| Place Bit Switch Copy 4 Bit Switch and Edit 
• Set ON, LB0 
• Set ON, LB1 
• Set ON, LB2 
• Set ON, LB3 |

11.1 Download to SAMKOON Device 
* Connect 
   * 24VDC 
   * USB Cable 
   * Ethernet 
* Download
![alt text](image-12.png)

> **ผลลัพธ์ที่ได้** :sunflower: 
![](/assets/week3/a69fd1dd-af25-4093-8179-52a9e19a8434.jpg)

## **LOGO8_t90_Traffic_Light**

ให้เขียน FBD ควบคุมไฟจราจร  
>![](/assets/week3/66342955-6554-4778-b9a7-144f152cda50.jpg)
* ควบคุมไฟจราจรชุดเดียว ที่มี ไฟแดง ไฟเหลือง ไฟเขียว 
* สวิตซ์ควบคุม 2 ตัว สีแดงเลือกโหมดการทำงาน สีเขียวเลือกจังหวะการทำงาน 
* การทำงานมี 3 โหมด คือ ทำงานอัตโนมัติ เหลืองกระพริบ และควบคุมด้วยมือ 
* สามารถควบคุมระยะไกลผ่าน Modbus-TCP 
* โหมดทำงานอัตโนมัติ 
  * ไฟเขียว 4 วินาที 
  * ไฟเหลือง 1 วินาที, ไฟแดง 5 วินาที 
>![](/assets/week3/d42f704a-42f7-485b-87a9-6466633a1e5b.jpg)
![](/assets/week3/c477bf14-a6c5-4dbd-850b-299bd0f5f92a.jpg)
![](/assets/week3/a4c7216d-ff04-46f2-bdb6-0a75824a70c4.jpg)
* โหมดเหลืองกระพริบ 
  * ไฟเหลืองติด 1 วินาที 
  * ไฟเหลืองดับ 1 วินาที 
>![](/assets/week3/3da0f8b9-a129-4bbf-8e33-3f22ea054082.jpg)
![](/assets/week3/7630afbb-252a-477c-b115-c13b374de06c.jpg)


* โหมดควบคุมด้วยมือ 
  * ไฟเขียว → รอกดสวิตซ์สีเขียวเพื่อเปลี่ยนจังหวะการทำงาน 
  * ไฟเหลือง 1 วินาที, ไฟแดง →รอกดสวิตซ์สีเขียวเพื่อเปลี่ยนจังหวะการทำงาน
>![](/assets/week3/701a8f1d-04cc-4ffe-b3da-7b891fd46dd1.jpg)
![](/assets/week3/eaa9769d-db48-4e90-9fcf-cc42b01ff61f.jpg)
![](/assets/week3/83be9c00-ffcd-4eb8-a92a-e9e24793b9e6.jpg)