[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-24ddc0f5d75046c5622901739e7c5dd533143b0c8e959d652212380cedb1ea36.svg)](https://classroom.github.com/a/kzkUPShx)
# a14g-final-submission

    * Team Number: 
    * Team Name: 
    * Team Members: 
    * Github Repository URL: 
    * Description of test hardware: (development boards, sensors, actuators, laptop + OS, etc) 

# 1. Video Presentation

# 2. Project Summary

## Device Description
Our Device solves the problem all traps have, live and otherwise. You must check the traps daily to see if they caught anything.
Our trap allows the user to know when the trap goes off, what animal they caught, and if its the wrong animal, a full resest of the trap.
The user learns this information by a message sent over the internet, and the message to reset the trap is sent over the internet as well.

## Inspiration
Veterinarian and Animal Shelters run Catch & Release Programs for Spaying & Neutering Animals. They trap stray cats and vaccinate and treat them before releasing them into the wild. We thought our design could help assist their limited workforce and resources by making the whole process more time efficient. 

## Device Functionality
The device is designed to accomplish 4 things. First, when has the trap been set. Second, what is in the trap. Third, resetting the trap remotely. Fourth, scare any unwanted animal out of the trap.

We accomplish the first task by using a distance sensor. This detects when the door has been opened and shut, and it broadcasts this info to the server.

We accomplish the second task by using a UCAM-III Camera. This camera takes a picture once the door state has been changed from open to closed, and send this info to the server.

We accompish the third task by using three motors, a motor driver board, and information provided by the distance sensor. The motors work in a 6 step process:
1. Retract the trigger hook
2. Pull back front part of door
3. Pull up base of door
4. Drop trigger hook
5. Gently Lower base of door
6. Release tension on front part of door

We accompish the forth task by activating the CMI-1295-85T Buzzer when the trap is opened in order to scare out the unwanted animal.

[Insert Flow chart]

### Our sensors are as follows:

The UCAM-III - [Camera](https://www.digikey.com/en/products/detail/4d-systems-pty-ltd/UCAM-III/6623663?utm_adgroup=General&utm_source=google&utm_medium=cpc&utm_campaign=PMax%20Shopping_Product_Zombie%20SKUs&utm_term=&utm_content=General&utm_id=go_cmp-17815035045_adg-_ad-__dev-c_ext-_prd-6623663_sig-Cj0KCQiAzoeuBhDqARIsAMdH14F6TkdvV--Y6dbAXKAQEQVftdMaF9692gcQwgdwuc1FlIvNWcrb_eUaAlEKEALw_wcB&gad_source=1&gclid=Cj0KCQiAzoeuBhDqARIsAMdH14F6TkdvV--Y6dbAXKAQEQVftdMaF9692gcQwgdwuc1FlIvNWcrb_eUaAlEKEALw_wcB)

This allowed our user to see what animal was caught in the trap. The image is transmitted to the server.

The GP2Y0E02B - [Distance Sensor](https://www.digikey.com/en/products/detail/sharp-socle-technology/GP2Y0E02B/4103879)

This allows our system to detect when the door is open or shut. The door state gets transmitted to the server.

### Our actuators are as follows:

The CMI-1295-85T - [Buzzer](https://www.mouser.com/ProductDetail/CUI-Devices/CMI-1295-85T?qs=HoCaDK9Nz5fq6CSX%252BkVNEw%3D%3D)

This alarm sounds when the trap is reset to scare out any animal.

The CN0193 - [20 Kg Servo Motor](https://www.digikey.com/en/products/detail/sunfounder/CN0193/18668609?utm_adgroup=&utm_source=google&utm_medium=cpc&utm_campaign=PMax%20Shopping_Product_Low%20ROAS%20Categories&utm_term=&utm_content=&utm_id=go_cmp-20243063506_adg-_ad-__dev-c_ext-_prd-18668609_sig-CjwKCAiA_OetBhAtEiwAPTeQZxkS_JAFfAI4e2e_Li05ejYRHuHmWZ6jmmmuD82UOQySNqG8KaFG3xoCJJ4QAvD_BwE&gad_source=1&gclid=CjwKCAiA_OetBhAtEiwAPTeQZxkS_JAFfAI4e2e_Li05ejYRHuHmWZ6jmmmuD82UOQySNqG8KaFG3xoCJJ4QAvD_BwE)

This motor pulls back the first part of the cage door.

The SG90 - [Micro Servo Motor](https://www.digikey.com/en/products/detail/dfrobot/SER0006/7597224)

This motor handles the trigger hook of the trap.

The Blank - 20 Kg Servo Motor

This motor handle pulling the whole door open.

### Our other critical components are:

The Adafruit 16-Channel 12-bit PWM/Servo Driver - I2C interface - [PCA9685](https://www.adafruit.com/product/815) 

This board allowed us to take an I2C signal from our circuit board and translate it into three individual PWM motors.

# 3. Hardware & Software Requirements

# 4. Project Photos & Screenshots
