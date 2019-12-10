# L-wingSolarPanelInteractiveDisplay
junedacaya.github.io/L-wingSolarPanelInteractiveDisplay



## Table of Contents
1. [Build Instructions](#PLC-Components-Build-Instructions)
2. [System Diagram](#System-Diagram)
3. [Bill of Materials/Budget](#Bill-of-Material-and-Budget)
4. [Time Commitment](#Time-Commitment)
5. [Mechanical Assembly](#Mechanical-Assembly)
6. [PCB Design and Soldering and Enclosure](#PCB-Design-and-Soldering-and-Enclosure)
7. [Power Up](#Power-Up)
8. [Unit Testing](#Unit-Testing)

## PLC Components Build Instruction
For this build instruction, we will be assembling the Nucleo Wifi PLC using their components shown in the System Diagram which are developed and created by STMicroelectronics. There are three primary hardware components that a developer needs to build their own wireless PLC:
* A CPU/MCU
* Input/output signal conditioning/ PLC functions
* A Wi-Fi module/connection
<img src="https://github.com/junedacaya/L-wingSolarPanelInteractiveDisplay/blob/master/Documentation/Assembled%20Wifi%20PLC%20with%20baseholder.jpg?raw=true">

## System Diagram
<img src="https://github.com/junedacaya/L-wingSolarPanelInteractiveDisplay/blob/master/Documentation/system%20diagram.png?raw=true">

## Bill of Material and Budget

The billing below are just the 4 major components of the PLC as shown above. Apart from the major components, you need to buy a mini-USB($7 cad) connector to connect the components into the PC in order for you to code the flatform. All purchase I've made were free from delivery fees because DigiKey offers free deliveries more than $100 and I also have a amazon prime where I ordered my mini-USB connector. All in all, I would suggest that you order the parts at one go so that you will be able to avail the free one day delivery offered by DigiKey. A total of under $150 cad would be sufficient for the whole project.
<img src="https://github.com/junedacaya/L-wingSolarPanelInteractiveDisplay/blob/master/documentation/proof%20of%20purchase.PNG?raw=true">

## Time Commitment

This project doesn't need a lot of time to build because it doesn't require designing your own PCB and soldering. It will probably take you a weeks to read and understand the materials and what it does. 

## Mechanical Assembly

After you ordered the material, it will probably only takes 1 or 2 days for it to arrive. When you have the material, you just need to do to assemble them is to stack them accordingly as show in the [System Diagram](#System-Diagram). After you stack it correctly, we then move on and try to run a code into it using a mini-USB connection into the PC.
Stack arrangement by [digikey manual](https://www.digikey.ca/en/articles/techzone/2018/jun/creating-a-custom-wireless-programmable-logic-controller)
<img src="https://github.com/junedacaya/L-wingSolarPanelInteractiveDisplay/blob/master/Documentation/StackArrangement.JPG?raw=true">

## PCB Design and Soldering and Enclosure

For this particular project, we dont need to design a new PCB as well as solder anything. We might want to find and create a casing for the components. I found a basic enclosure for the STM32F401RE only. [Nucleo base enclosure](https://github.com/junedacaya/L-wingSolarPanelInteractiveDisplay/blob/master/Electronics/NucleoBox_V1.1.stl)

## Power Up

By plugging it into the PC using the mini-USB connector we provide power into the whole system. In the winter semester, I will input more power into the PLC. But as of this current project, it will have enough power provided by the PC when we try the unit testing.
<img src="https://github.com/junedacaya/L-wingSolarPanelInteractiveDisplay/blob/master/Documentation/Assembled%20Wifi%20PLC%20with%20baseholder.jpg?raw=true">

## Unit Tesing

For my unit testing, I only run a simple blinky program into the PLC comment to show a connection with all the components stacked. 
1. To start, you must download [STM32CubeIDE](https://www.st.com/en/development-tools/stm32cubeide.html) provided by STMicroelectronics. It is an all in one STM32 development tool.
<img src="https://github.com/junedacaya/L-wingSolarPanelInteractiveDisplay/blob/master/Documentation/stm32pic.jpg?raw=true">

2. Plugin your Wifi PLC into a PC using a mini-USB sowe can flash a code into it.

3. Open a the STM32 and click Launch.And, allow the firewall access for the IDE.
<img src="https://github.com/junedacaya/L-wingSolarPanelInteractiveDisplay/blob/master/Documentation/launchscreen.PNG?raw=true">

4. Start a new STM32 Project.
<img src="https://github.com/junedacaya/L-wingSolarPanelInteractiveDisplay/blob/master/Documentation/startStm32Project.PNG?raw=true">

5. Find and select NUCLEO-F401RE in the Board Selector and click Next. Name your project as BlinkyF401RE and hit Finish accept the default settings.
<img src="https://github.com/junedacaya/L-wingSolarPanelInteractiveDisplay/blob/master/Documentation/findf401re.PNG?raw=true" height="550" width="750">
<img src="https://github.com/junedacaya/L-wingSolarPanelInteractiveDisplay/blob/master/Documentation/nameProject.PNG?raw=true">

Wait for the Software Pakcages Download to finish and hit OK.

<img src="https://github.com/junedacaya/L-wingSolarPanelInteractiveDisplay/blob/master/Documentation/softwarepackagedownload.PNG?raw=true">

6. Select the generate code option and press OK. After the code is generated, you will be able to add the code that will control the LED to blink.

7. In the main.c, Add the following code to control the LED to blink.

7. 
