# L-wingSolarPanelInteractiveDisplay
junedacaya.github.io/L-wingSolarPanelInteractiveDisplay




## Table of Contents
1. [System Diagram](#System-Diagram)
2. [Build Instructions](#PLC-Components-Build-Instructions)
3. [Bill of Materials/Budget](#Bill-of-Material-and-Budget)
4. [Time Commitment](#Time-Commitment)
5. [Mechanical Assembly](#Mechanical-Assembly)
6. [PCB Design and Soldering and Enclosure](#PCB-Design-and-Soldering-and-Enclosure)
7. [Power Up](#Power-Up)
8. [Unit Testing](#Unit-Testing)
9. [Production Testing](#Production-Testing)
10. [Reproducing](#Reproducing)

## System Diagram
<img src="https://github.com/junedacaya/L-wingSolarPanelInteractiveDisplay/blob/master/Documentation/system%20diagram.png?raw=true">

## PLC Components Build Instruction
For this build instruction, we will be assembling the Nucleo Wifi PLC using the STMicroelectronics components shown in the System Diagram which are developed and created by STMicroelectronics. There are three primary hardware components that a developer needs to build their own wireless PLC:
* A CPU/MCU
* Input/output signal conditioning/ PLC functions
* A Wi-Fi module/connection
<img src="https://github.com/junedacaya/L-wingSolarPanelInteractiveDisplay/blob/master/Documentation/Assembled%20Wifi%20PLC%20with%20baseholder.jpg?raw=true">

## Bill of Material and Budget

The billing below are just the 4 major components of the PLC as shown above. Apart from the major components, you need to buy a mini-USB($7 cad) connector to connect the components into the PC in order for you to code the flatform. All purchase I've made were free from delivery fees because DigiKey offers free deliveries more than $100 and I also have a amazon prime where I ordered my mini-USB connector. All in all, I would suggest that you order the parts at one go so that you will be able to avail the free one day delivery offered by DigiKey. We would also want to create an eclosure for the project that will cover which will probably cost you less than $50. A total of under $180 cad would be sufficient for the whole project.

<img src="https://github.com/junedacaya/L-wingSolarPanelInteractiveDisplay/blob/master/documentation/proof%20of%20purchase.PNG?raw=true">

## Time Commitment

This project doesn't need a lot of time to build because it doesn't require designing your own PCB and soldering. It will probably take you a weeks to read and understand the materials and what it does. You will either want to print your own enclosure or make it created by a 3D printing shop which will cost you around couple of hours.

## Mechanical Assembly

After you ordered the material, it will probably only takes 1 or 2 days for it to arrive. When you have the material, you just need to do to assemble them is to stack them accordingly as show in the [System Diagram](#System-Diagram). After you stack it correctly, we then move on and try to run a code into it using a mini-USB connection into the PC.
Stack arrangement by [digikey manual](https://www.digikey.ca/en/articles/techzone/2018/jun/creating-a-custom-wireless-programmable-logic-controller)
<img src="https://github.com/junedacaya/L-wingSolarPanelInteractiveDisplay/blob/master/Documentation/StackArrangement.JPG?raw=true">

Here is the assembled parts.

<img src="https://raw.githubusercontent.com/junedacaya/L-wingSolarPanelInteractiveDisplay/master/Documentation/Assembled%20parts%201.jpeg?raw=true" height="360" width="420">

## PCB Design and Soldering and Enclosure

For this particular project, we dont need to design a new PCB as well as solder anything. We might want to find and create a casing for the components. I found a basic enclosure for the STM32F401RE only. Here is the file you need to 3D printed.[Nucleo base enclosure.](https://github.com/junedacaya/L-wingSolarPanelInteractiveDisplay/blob/master/Electronics/NucleoBox_V1.1.stl)

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

6. Under your project go to Core > Src > main.c. Add the code between  /* USER CODE BEGIN */ and /* USER CODE END */. 
Add this code to enable clock for port A. Also to configure pin as output.
```
/* USER CODE BEGIN 1 */
 __HAL_RCC_GPIOA_CLK_ENABLE();
 GPIO_InitTypeDef Init_LED;
 /* USER CODE END 1 */
```

After the initialization, we need to turn the LED on/off with a time delay. Add the following code.
```
/* USER CODE BEGIN 3 */
 HAL_GPIO_TogglePin(GPIOA, GPIO_PIN_5);
 HAL_Delay(1000); 
 }
 /* USER CODE END 3 */
 ```
 
7. After the codes are added, we need to build the project. Click the build button. We should have no problems for this build.
<img src="https://github.com/junedacaya/L-wingSolarPanelInteractiveDisplay/blob/master/Documentation/buildproject2.PNG?raw=true">

8. If you have your component Plug into the PC, we can now run the Blinky401RE into the device. Click Run > Debug As > STM32 Cortex-M C/C++ Application.
<img src="https://github.com/junedacaya/L-wingSolarPanelInteractiveDisplay/blob/master/Documentation/debugas.png?raw=true">

Your program should be running into your device. You need to press the Reset Button of the Nucleo-F401RE to see the LED blink with interval.

<img src="https://github.com/junedacaya/L-wingSolarPanelInteractiveDisplay/blob/master/Documentation/401RE.jpg?raw=true" height="460" width="320">

## Production Testing

Here is an image of my unit. A great addition for my unit would be a full enclosure that will cover all the sides and top but the input/output sockets at the back of the PLC01A1 and OUT01A1 will be available.

<img src="https://github.com/junedacaya/L-wingSolarPanelInteractiveDisplay/blob/master/Documentation/Assembled%20Wifi%20PLC%20with%20baseholder.jpg?raw=true">

## Reproducing
Reproducing this project by following my instructions would be very possible. The project is easier because we dont have to make or create the PCB. All we need for the project are the components for PLC, WIFI, and extra OUTPUT functions and a development flatform and tool to program the device.
