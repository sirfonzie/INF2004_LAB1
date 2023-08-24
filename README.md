# LAB 1: Microcontroller and its Development Environment


**OBJECTIVES**
- To setup and get you familiarised with the development environment for Raspberry Pi Pico.
- To get you familiarised with the Raspberry Pi Pico development board.


**EQUIPMENT** 
1.	A laptop that has the Pico C/C++ SDK installed
2.	Raspberry Pico or the wireless variant
3.	Micro-USB Cable 


> [NOTE]
> Only students wearing fully covered shoes are allowed in the lab due to safety. 


## **INTRODUCTION** 

Programming an embedded system requires a deep-level understanding of the embedded processor architecture, the development environment tool, and the hardware that is interfaced with the embedded system. In this laboratory session, you will be introduced to the basic tools and how it can be used to aid your understanding of the software development, and more importantly to help you built your software. Programming for an embedded system is very different from programming on a desktop computer. The main differences are the limited resource constraints in terms of the program code and RAM and the overall computation performance of an embedded system. For instance, our RP2040 microcontroller only provides 256KB of SRAM memory space. A 16MB Flash memory is added to the board and externally connected to the RP2040. Moreover, the various software components discussed in the lecture will be observed in  this session. At this point, you should  be familiar with  the fundamentals of C programming. If not, you are encouraged to brush up on it. Do revise ALL the fundamentals of C programming covered in the following [site](https://www.cprogramming.com/tutorial/c-tutorial.html). This will prepare you for the subsequent lab sessions and make this subject more enjoyable. In addition, please brush up on the following:
- “Numeral Systems” (e.g. binary, decimal, hexadecimal, etc)
- “Ordering Consideration” (e.g. endianness, MSB, LSB, etc)

## **RASPBERRY PI PICO** 

In this lab session, we learned about the development platform Raspberry Pico and the Pico C/C++ SDK used throughout all lab sessions. We will also familiarise you with concepts like direct register access, polling, and serial communication. The following introduction should give a broad overview of the working environment, but it isn't necessary to understand all the details to complete this laboratory. 

The Raspberry Pi Pico is an affordable microcontroller board developed by the Raspberry Pi Foundation, ideal for electronics projects. It features a dual-core ARM Cortex-M0+ processor, 26 GPIO pins, and supports multiple programming languages. However, it lacks built-in wireless connectivity. The Raspberry Pi Pico Wireless (Pico W) is an enhanced version of the Pico, with built-in Wi-Fi and Bluetooth. This makes it suitable for IoT and wireless communication projects while maintaining compatibility with Pico's programming languages and GPIO pins.

The most important documents of an embedded system are, among others, datasheets, user guides, technical reference manuals, application notes, errata or schematics. Therefore, every embedded system comes with many documentation files. For this lab and subsequent labs, all the necessary files can be found on the Raspberry Foundation site and supplementary documents will be provided on the course xsite website. It is essential to have access to all parts of the documentation to use the functionality of an embedded system to its fullest extent. Details of the hardware can be found [here](https://www.raspberrypi.com/documentation/microcontrollers/rp2040.html).

## **SETTING UP PICO SDK**

There are various [methods]() (see chapter 2 and 9) to setup the development environment for the pico in C using the Pico SDK, depending on what OS you are using on your PC/laptop. However, if you are using Windows OS, the easiest way is to download and install [this] tool(https://github.com/raspberrypi/pico-setup-windows/releases/latest/download/pico-setup-windows-x64-standalone.exe). 

Visual Studio Code will ask if you want to configure the pico-examples project when it is first opened; click *Yes* on that prompt to proceed. You will then be prompted to select a kit -- select the *Pico ARM GCC - Pico SDK Toolchain with GCC arm-none-eabi* entry. 

## **BUILDING AN EXAMPLE**

Once Visual Studio Code (VSCode) is started, click on the CMake icon and select the sample code you would like to work on. In this example, we will be using the hello_world example. The following [video](https://www.youtube.com/watch?v=NPwoflT_bB0) demonstrates how you get started with VSCode. Note that we are using the hello_usb version of the code. This allow the USB connection between the pico and the PC/laptop to become a virtual uart connection which can be used together with printf (for debugging purposes).

Now try to compile and run the blink example.

If you are using the Pico W boards, then you will need to make a small ammendment to the CMakeLists.txt file. Include "set(PICO_BOARD pico_w)" to line #11. The following [video](https://www.youtube.com/watch?v=NPwoflT_bB0) demonstrates how to make the changes and build a blink example for the Pico w. 

> [NOTE]
> The normal blink example will only work on a standard Pico (without wireless). This because the led on the Pico W is connected to the WiFi SoC and not to the Rp2040.


## **EXERCISE**

This [code]() is supposed to blink an LED connected to the GPIO pin. The LED blinks at a rate determined by the "a" variable, which starts at 0ms and increments with each iteration of the loop. When variable "a" reaches 250ms, it resets to 0, creating a repeating LED blink pattern. The LED blink pattern should turn on and off with the same delay at each loop-iteration. Identify where the errors are and make the necessary changes so that the code works as intended. [Suggestion] Include a printf statement so that you can monitor the variable "a".
