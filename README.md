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

## Challenges
We faced a couple of unique and unexpected challenges, most of which we were able to overcome.

1. One motor was not enough to open/reset the trap. This was hard because our board was only designed to handle one motor. In order to overcome this we got a motor driver board and split our I2C comm channel which was communicating to our distance sensor so that our board could also communicate to the motor driver. We hijacked the camera 5V output pin to help power the motor driver as well. In this way we were able to power three motors instead of one. It required careful current monitoring and testing of each one with an Arduino in order to ensure it would not fry our board.
2. I2C refused to work on Sercom 3 for the longest time. All code worked with Sercom 0, and on the test devboard all code for Sercom 3 worked, but for some reason the same code on our board would not work. We realized after nights that after we fully soldered one of the wires on, the code suddenly worked. The connection could have been just not secured well enough.
3. Our bootloader wouldn't load. After 4 hours of testing we realized that the SD card had somehow failed.
4. Our motors could not open the doors initially. We had to go through and do weight testing and some physics math in order to determine the weight, and therefore the torque, we would need from each motor. From this we were able to determine the minimum and maximum radii that we could use for our motor spools. We then also had to go through many servos to see if any worked, and we also had to deal with some of the servos being limited to 180 or 270 degrees of rotation. Fortunately we sourced two, and ordered a third, which allowed the system to function properly.
5. 

## Prototype Learnings
We learned that this device requires three motors, not one, to be fully opened. We only designed our board for one motor, and in order to handle multiple we needed to add a Motor Driver board. Because of this addition, we needed to split our I2C line between our distance sensor and our motor driver. We also had to share a 5V line of the motor driver with our camera, which hindered its operation. For the next iteration of our prototype we would either A) add in another I2C line for our motor driver and add an output pin for power and ground solely for this board or B) add in two more motor ports on our main board operating off of PWM so that we could cut out the motor driver all together.

For the next iteration of our prototype we would explore using a multi celled battery. Our system was having power problems at the end due to the several motors and camera all trying to be powered. This drained our battery rather quickly. 

We would also explore using a microcontroller with a larger memory capacity, or a lower quality camera. Because our microcontroller was not able to store the picture in its entirety we ran into memory mismatch issues. 

## Next Steps
Resolving the camera issues. We are unsure if the camera can be fully powered while all three of our motors are plugged in, and even so the microcontrollers ability to fully process the image and transmit it to the server was much more difficult to fully implement than we had expected.

## Takeaways from ESE5160
1. We learned how to design a bootloader as well as why we would need a bootloader in an IoT device.
2. We learned how to design, route, and prepare a circuit board for manufacturing.
3. We learned how to test a circuit board that had been manufactured to determine if it functioned the way the designers intended.
4. We learned how to write the drivers for our periphereal devices for a specificly selected microcontroller.
5. We learned how to integrate our device with the internet via a sever, and send messages to and from our device and server.
6. We learned how to consider system security and integrety for a hardware device.
7. We learned how to build an initial prototype from scratch starting with an idea and working all the way to a (mostly) functioning model.
8. How to use GitHub to collaborate on a project with other Engineers.

## Project Links
[Node-RED instance](http://20.36.130.119:1880/)

[A12G Code Repository](https://github.com/ese5160/a12g-firmware-drivers-t17-team-gotcha)

[PCBA Share Link](https://upenn-eselabs.365.altium.com/designs/FF235DAA-4BB0-4413-B5CD-DB408AEACE1F#design)

# 3. Hardware & Software Requirements

# 4. Project Photos & Screenshots
