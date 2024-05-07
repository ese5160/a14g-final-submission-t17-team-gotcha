[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-24ddc0f5d75046c5622901739e7c5dd533143b0c8e959d652212380cedb1ea36.svg)](https://classroom.github.com/a/kzkUPShx)
# a14g-final-submission

    * Team Number: 17
    * Team Name: Team Gotcha
    * Team Members: Michael Shao & Gabriel Bennett
    * Github Repository URL: https://github.com/ese5160/a14g-final-submission-t17-team-gotcha
    * Description of test hardware: SAMW25, Distance Sensors, UCAMIII, Servos, PCAC9685 Adafruit Motor Driver Board 

See the deployed website ![here](https://ese5160.github.io/a14g-final-submission-t17-team-gotcha/)
    
# 1. Video Presentation
<video src='FinalIoTDesign%20(1).mp4' width=480 > </video>


Right click to see the playing options on the github pages.
![Download the video!](https://github.com/ese5160/a14g-final-submission-t17-team-gotcha/blob/main/FinalIoTDesign%20(1).mp4)
# 2. Project Summary

## Device Description
Our Device solves the problem all traps have, live and otherwise. You must check the traps daily to see if they caught anything.
Our trap allows the user to know when the trap goes off, what animal they caught, and if its the wrong animal, a full resest of the trap.
The user learns this information by a message sent over the internet, and the message to reset the trap is sent over the internet as well.

## Inspiration
Veterinarian and Animal Shelters run Catch & Release Programs for Spaying & Neutering Animals. They trap stray cats and vaccinate and treat them before releasing them into the wild. We thought our design could help assist their limited workforce and resources by making the whole process more time efficient. 

## Device Functionality
The device is designed to accomplish 4 things. First, detect when the trap has been activated. Second, show the user what is in the trap. Third, reset the trap remotely. Fourth, scare any unwanted animal out of the trap.

We accomplish the first task by using a distance sensor. This detects when the door has been opened and shut, and it broadcasts this info to the server.

We accomplish the second task by using a UCAM-III Camera. This camera takes a picture on remote request of the user, and sends this info to the server.

We accompish the third task by using three motors, a motor driver board, and information provided by the distance sensor. The motors work in a 6 step process:
1. Retract the trigger hook
2. Pull back the spring that locks the door shut
3. Pull up base of door to open it
4. Drop trigger hook
5. Gently Lower base of door
6. Release tension on door spring

We accompish the forth task by activating the CMI-1295-85T Buzzer when the trap is opened in order to scare out the unwanted animal.

![MEAM519 drawio(1) drawio (2)](https://github.com/ese5160/a14g-final-submission-t17-team-gotcha/assets/148781333/0d2dfb8d-2982-4a46-8a08-b87153ee9ecb)

Our device has a single cell 3.7V LiPo battery connected into a BQ24075RGTR chip which is responsible for allowing the battery to be recharged via a usb connector. This chip is also routed into a 3.3V buck regulator and a 5V boost regulator we configured ourselves so that each peripheral, as well as the microcontroller, is powered at the appropriate voltage level. We used the SAMW25 microcontroller which utilizes a SAMD21 chip as well as a WINC 1500 Wifi Module. Our peripherals are a Buzzer which recieves input via GPIO adjusted by an Op Amp, a Camera which operates using UART, a Distance Sensor running off I2C, a Motor Driver board operating off I2C, and three motors operating on PWM.

### Our sensors are as follows:

The UCAM-III - [Camera](https://www.digikey.com/en/products/detail/4d-systems-pty-ltd/UCAM-III/6623663?utm_adgroup=General&utm_source=google&utm_medium=cpc&utm_campaign=PMax%20Shopping_Product_Zombie%20SKUs&utm_term=&utm_content=General&utm_id=go_cmp-17815035045_adg-_ad-__dev-c_ext-_prd-6623663_sig-Cj0KCQiAzoeuBhDqARIsAMdH14F6TkdvV--Y6dbAXKAQEQVftdMaF9692gcQwgdwuc1FlIvNWcrb_eUaAlEKEALw_wcB&gad_source=1&gclid=Cj0KCQiAzoeuBhDqARIsAMdH14F6TkdvV--Y6dbAXKAQEQVftdMaF9692gcQwgdwuc1FlIvNWcrb_eUaAlEKEALw_wcB)

This allowed our user to see what animal was caught in the trap. The image is transmitted to the server.

The GP2Y0E02B - [Distance Sensor](https://www.digikey.com/en/products/detail/sharp-socle-technology/GP2Y0E02B/4103879)

This allows our system to detect when the door is open or shut. The door state gets transmitted to the server.

### Our actuators are as follows:

The CMI-1295-85T - [Buzzer](https://www.mouser.com/ProductDetail/CUI-Devices/CMI-1295-85T?qs=HoCaDK9Nz5fq6CSX%252BkVNEw%3D%3D)

This alarm sounds when the trap is reset to scare out any animal.

The CN0193 - [20 Kg Servo Motor](https://www.digikey.com/en/products/detail/sunfounder/CN0193/18668609?utm_adgroup=&utm_source=google&utm_medium=cpc&utm_campaign=PMax%20Shopping_Product_Low%20ROAS%20Categories&utm_term=&utm_content=&utm_id=go_cmp-20243063506_adg-_ad-__dev-c_ext-_prd-18668609_sig-CjwKCAiA_OetBhAtEiwAPTeQZxkS_JAFfAI4e2e_Li05ejYRHuHmWZ6jmmmuD82UOQySNqG8KaFG3xoCJJ4QAvD_BwE&gad_source=1&gclid=CjwKCAiA_OetBhAtEiwAPTeQZxkS_JAFfAI4e2e_Li05ejYRHuHmWZ6jmmmuD82UOQySNqG8KaFG3xoCJJ4QAvD_BwE)

This motor pulls back the spring of the cage door.

The SG90 - [Micro Servo Motor](https://www.digikey.com/en/products/detail/dfrobot/SER0006/7597224)

This motor handles the trigger hook of the trap.

The ANNIMOS - [20 Kg Servo Motor](https://www.amazon.com/ANNIMOS-Digital-Waterproof-DS3218MG-Control/dp/B076CNKQX4)

This motor handle pulling the whole door open.

### Our other critical components are:

The Adafruit 16-Channel 12-bit PWM/Servo Driver - I2C interface - [PCA9685](https://www.adafruit.com/product/815) 

This board allowed us to take an I2C signal from our circuit board and translate it into three individual PWM signals for our motors.

## Challenges
We faced a couple of unique and unexpected challenges, most of which we were able to overcome.

1. One motor was not enough to open/reset the trap. This was hard because our board was only designed to handle one motor. In order to overcome this we got a motor driver board and split our I2C comm channel which was communicating to our distance sensor so that our board could also communicate to the motor driver. We hijacked the camera 5V output pin to help power the motor driver as well. In this way we were able to power three motors instead of one. It required careful current monitoring and testing of each one with an Arduino in order to ensure it would not fry our board.
2. I2C refused to work on Sercom 3 for the longest time. All code worked with Sercom 0, and on separate test instances where we solely tested for sercom 3, all functionality for Sercom 3 worked, but for some reason the full code stack on our board would not work. We realized after nights that after we fully soldered one of the wires on, the code suddenly worked. The connection could have been just not secured well enough.
3. Our bootloader wouldn't load in correctly - freezing at the SD configuration check. After 4 hours of testing we realized that the SD card had somehow failed.
4. Our motors could not open the doors initially. We had to go through and do weight testing and some physics calculations in order to determine the weight and torque we would need from each motor. From this we were able to determine the minimum and maximum radii that we could use for our motor spools. We then also had to go through a few servos test to see if any worked, and we also had to deal with some of the servos being limited to 180 or 270 degrees of rotation. Fortunately we sourced two, and ordered a third, which allowed the system to function properly.
5. The camera had many issue for our system. The key one surrounded the amount of data that a single image required of us. Most other drivers availible assume that the host device has much more processing power and memory requiring us to write our own firmware. Then, we realized that the amount of data being sent would require us to chunk the data either forcing us to slowly write it all to the SD card or attempt to immediately send the data chunks to the server. These packages would end up being in the number of hundreds of packets. This also lended to issues into stack overflow error since the amount of data in a since chunk could still be quite large. Of all our challenges, this was the greatest issue since even when we got individual system working in thei data pipeline, we needed further optimizations to make it compatible with the remain memory space in the over all system.

## Prototype Learnings
We learned that this device requires three motors, not one, to be fully opened. We only designed our board for one motor, and in order to handle multiple we needed to add a Motor Driver board. Because of this addition, we needed to split our I2C line between our distance sensor and our motor driver. We also had to share a 5V line of the motor driver with our camera, which hindered its operation. For the next iteration of our prototype we would add in another I2C connector for our motor driver and add a dedicated output pin for power and ground solely for this motors on that board.

For the next iteration of our prototype we would explore using a multi celled battery. Our system was having power problems at the end due to the several motors and camera all trying to be powered. This drained our battery rather quickly. 

Lastly, our mounts were okay for testing whether our overall system works in concept (largely consisting of zipties and a few screw mounts), but we should design a hard mount (either custom printed or screws using lock nuts) that would be secure for multiple uses for all components.

## Next Steps
Resolving the camera issues. We are unsure if the camera can be fully powered while all three of our motors are plugged in, and even so the microcontrollers ability to fully process the image and transmit it to the server was much more difficult to fully implement than we had expected. We believe with more time we could possibly optimize the data pipeline for memory and speed efficiency.

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
[Node-RED instance](http://20.36.130.119:1880/) Server link doesn't work due to our Azure VM account being banned.

[A12G Code Repository](https://github.com/ese5160/a12g-firmware-drivers-t17-team-gotcha)

[PCBA Share Link](https://upenn-eselabs.365.altium.com/designs/FF235DAA-4BB0-4413-B5CD-DB408AEACE1F#design)

# 3. Hardware & Software Requirements
So, how did we do at meeting our hardware and software specifications?
## Hardware Requirements Specification, Then & Now
Our Original Hardware Specification Overview was worded as follows:

*"From a hardware stand point, the system shall be made up of a standard animal live trap and an electronic suite that will sense the state of the trap and mechanically reset the trap on demand. The electronic suite shall be made up of a microcontroller to operate the control logic, a wifi module to communicate the trap state to the user and accept reset commands, various sensors to monitor the interior of the trap and the trap mechanism, motors to reset the trap mechanism, and lights and a noisemaker to drive away non-target subjects."*

Our prototype was indeed a standard animal live trap that can sense the state of the trap based on the input of a distance sensor. We were able to use motors to reset the trap remotely. It was made of a microcontroller with a wifi module linked to a server, a camera sensor to monitor the inside of the trap and a distance sensor to monitor door state, three motors to reset the trap, and a buzzer to scare away any unwanted creatures. We decided against the strobelight. In effect, our end product has the basic elements all listed in our requirement and works as a proof of concept though we do wish to add more features to improve the ease of use.

### Functionality
The Hardware functionality list was as follows with our updated look:

*HRS 01 - Project shall be based on the SAM W25 microcontroller for the state control.*

We did indeed use this microcontroller. Please reference our board images for proof.

*HRS 02 – Distance type sensor shall be used for obstacle detection.  The sensor shall detect obstacles at a maximum distance of at least 10 cm.*

We used the GP2Y0E02B distance sensor which according to the datasheet operates up to 50 cm. The following two images show the results of testing the device which exceeded our expectations and allowed us to measure what we needed. Near vs far.


![18cm](https://github.com/ese5160/a14g-final-submission-t17-team-gotcha/assets/148781333/08b06876-573a-47bd-bcc1-48ef6486e034)
![63cm](https://github.com/ese5160/a14g-final-submission-t17-team-gotcha/assets/148781333/28b724bb-c4d8-452e-aad6-bc266bbba8bc)


*HRS 03 - Camera sensor shall be used for image capture of the trap interior. The resolution shall be at least 480p.*

We did implement a Camera in our system that operated off of UART. We had a pinout on our board for the UCAM-III which can support a resolution of VGA 640x480 pixels. However, we had issues running the camera along with the rest of the system - particularly with memory and wiring which forced us to run the final system without it dispite having the drivers mostly written.

*HRS 04 - There shall be a noisemaker inside the trap with a strenth of at least 55 dB that will.*

The buzzer we used was the CMI-1295-85T which has a max rating of 85 dB accourding to the datasheet. We were satified with the restuls in testing.

*HRS 05 - A electronic motor shall be used to reset the trap remotely and have a torque of 40 Nm in order to reset the trap mechanism.*

We wildly over estimated our initial torque estimates. We actually only needed 20 Kg-cm of torque (around 5% of our initial measurement). However, we also needed three motors rather than one which resulted in us needing to find an appropriate motor driver board to manage the communications. We also needed to do Torque Calculations to figure out what size radii disks we would need without burning out our motors which should have been it's own requirement (though we did not have a cage to test the practical implications of the system at the time).

![20240506_164433nnnn](https://github.com/ese5160/a14g-final-submission-t17-team-gotcha/assets/148781333/fbbc7efb-3a09-45ad-b4ad-a3fb82df396a)



## Software Requirements Specification, Then & Now
Our Original Software Specification Overview was worded as follows:

*"Our system shall have a monitoring system, data transfer system, and control system. The monitoring system shall detect when the trap door mechanism is activated and upon request, send an image of the interior of the trap. The data transfer system will connect the device to a cloud-based system that the user can access. The control system will allow the user to reset the trap mechanism and repel unwanted subjects from the trap interior with the use of a noisemaker."*

Our prototype did indeed monitor, transfer data, and control. We were able to detect when the trap door was opened and closed, though we were unable to send an image of the interior of the trap. The data transfer system leverage the SAMW25 wifi chip to send messages over WIFI using an MQTT system. The data was transfered to a Azure VM server hosting the MQTT broker and processed by a Node-RED Backend which presented to a frontend UI. The data we transfered was the door state and user commands however because we were unable to transfer the images. The control system was the user resetting the trap which at the end of the trap reset cycle the buzzer would sound potentially repelling any unwanted subjects.

### Functionality
The Software functionality list was as follows with our updated look:

*SRS MS 01 – The distance sensor shall operate and report values at least every .5 second.*

This was accomplished, though in practice relax this requirement to 1 second in testing as the refresh rate for the check seemed overkill for nominal use.

*SRS MS 02 - Upon non-nominal distance detected (i.e. the trap mechanism has changed at least 10 cm from nominal range), the system shall be able to detect the change and alert the user in a timely manner (within 5 seconds).*

This was accomplished. The UI would be updated of state changes within a second.

*SRS MS 03 - Upon a request from the user, the system shall get an image from the internal cameral and upload to the image to the user system within 10s.*

This was not accomplished due to both hardware and software issues with the camera. See our notes about the camera hardware requirement.

#### DTS and the User System
*SRS DTS 01 - The user system shall report the status of all connected traps*

Since we only had one trap designed, we have yet to test if the user can sense additional traps. The potential is there, and we have no restriction on adding more to the network.

The trap does get constant updates of the door state telling the user whether the trap is open or closed.

*SRS DTS 02 - The user system shall be able to request any connected trap to be reset*

Since we only had one trap designed, we have yet to test if the user can sense additional traps. The potential is there, and we have no restriction on adding more to the network.

The trap does have the ability to be reset and was demonstrated in the video.

*SRS DTS 03 - The DTS shall use the WINC 1500 wifi module to connect to the user system and send/recieve data*

We did indeed use this module. See image of board for proof.

#### CS
*SRS CS 01 - Upon a request from the user, the motor shall activate and retract the trap mechanism.*

This was accomplished and recorded in the video.

*SRS CS 02 - Upon a request from the user, the noisemaker shall activate for 2 seconds.*

The noisemaker was changed to an automatic result of the trap retraction process as it made more sense for overall design.

# 4. Project Photos & Screenshots

<img src="https://github.com/ese5160/a14g-final-submission-t17-team-gotcha/assets/148781333/6968748e-0084-46ed-b791-7e4b5ebd2a59" width="23%"> <img src="https://github.com/ese5160/a14g-final-submission-t17-team-gotcha/assets/148781333/71a17238-b8aa-4f20-9095-a98a4b90133e" width="23%"> <img src="https://github.com/ese5160/a14g-final-submission-t17-team-gotcha/assets/148781333/6ca1b223-cece-4e03-9119-33ebc11e17bd" width="23%"> <img src="https://github.com/ese5160/a14g-final-submission-t17-team-gotcha/assets/148781333/0e656da0-cc79-4f7b-96dc-44465da74e36" width="23%"> <img src="https://github.com/ese5160/a14g-final-submission-t17-team-gotcha/assets/148781333/7d0ef5bb-12a4-4818-8656-0cd91a6066d1" width="23%"> <img src="https://github.com/ese5160/a14g-final-submission-t17-team-gotcha/assets/148781333/4dcdd188-9a2d-4f06-ab1e-a902e394c9de" width="23%"> <img src="https://github.com/ese5160/a14g-final-submission-t17-team-gotcha/assets/148781333/5b9d1efb-1bd4-4c47-bee3-f1af6a148ed9" width="23%"> <img src="https://github.com/ese5160/a14g-final-submission-t17-team-gotcha/assets/148781333/7524ab6c-3bac-473e-8cbe-d56a0727274b" width="23%"> <img src="https://github.com/ese5160/a14g-final-submission-t17-team-gotcha/assets/148781333/413e2d94-1611-4e26-9509-5dd5203a6ca4" width="23%"> <img src="https://github.com/ese5160/a14g-final-submission-t17-team-gotcha/assets/148781333/aacbe642-56cd-470f-90b7-a63059d7a9c5" width="23%"> <img src="https://github.com/ese5160/a14g-final-submission-t17-team-gotcha/assets/148781333/8bf24f4e-cff3-48e2-8895-262b4b88aec4" width="23%"> <img src="https://github.com/ese5160/a14g-final-submission-t17-team-gotcha/assets/148781333/0d2dfb8d-2982-4a46-8a08-b87153ee9ecb" width="23%">
