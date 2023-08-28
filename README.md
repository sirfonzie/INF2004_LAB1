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

Programming an embedded system requires a deep-level understanding of the embedded processor architecture, the development environment tool, and the hardware interfaced with the embedded system. In this laboratory session, you will be introduced to the basic tools and how it can be used to aid your understanding of software development, and more importantly to help you build your software. Programming for an embedded system differs greatly from programming on a desktop computer. The main differences are the limited resource constraints in terms of the program code and RAM and the overall computation performance of an embedded system. For instance, our RP2040 microcontroller only provides 256KB of SRAM memory space. A 16MB Flash memory is added to the board and externally connected to the RP2040. Moreover, the various software components discussed in the lecture will be observed in  this session. At this point, you should  be familiar with  the fundamentals of C programming. You are encouraged to brush up on it if you still need to. Do revise ALL the fundamentals of C programming covered in the following [site](https://www.cprogramming.com/tutorial/c-tutorial.html). This will prepare you for the subsequent lab sessions and make this subject more enjoyable. In addition, please brush up on the following:
- “Numeral Systems” (e.g. binary, decimal, hexadecimal, etc)
- “Ordering Consideration” (e.g. endianness, MSB, LSB, etc)

## **RASPBERRY PI PICO** 

In this lab session, we learned about the development platform Raspberry Pico and the Pico C/C++ SDK used throughout all lab sessions. We will also familiarise you with concepts like direct register access, polling, and serial communication. The following introduction should give a broad overview of the working environment, but it is optional to understand all the details to complete this laboratory. 

The Raspberry Pi Pico is an affordable microcontroller board developed by the Raspberry Pi Foundation, ideal for electronics projects. It features a dual-core ARM Cortex-M0+ processor, 26 GPIO pins, and supports multiple programming languages. However, it lacks built-in wireless connectivity. The Raspberry Pi Pico Wireless (Pico W) is an enhanced version of the Pico, with built-in Wi-Fi and Bluetooth. This makes it suitable for IoT and wireless communication projects while maintaining compatibility with Pico's programming languages and GPIO pins.

The Raspberry Pi Pico family currently consists of four boards: Raspberry Pi Pico, Pico H, Pico W, and Pico WH.

The following is the pin out for the Raspberry Pi Pico
![Screenshot of a Raspberry Pi Pico](https://www.raspberrypi.com/documentation/microcontrollers/images/pico-pinout.svg)

The following is the pin out for the Raspberry Pi Pico W
![Screenshot of a Raspberry Pi Pico W](https://www.raspberrypi.com/documentation/microcontrollers/images/picow-pinout.svg)

The most important documents of an embedded system are, among others, datasheets, user guides, technical reference manuals, application notes, errata or schematics. Therefore, every embedded system comes with many documentation files. All the necessary files for this lab and subsequent labs can be found on the Raspberry Foundation site and supplementary documents will be provided on the course xsite website. It is essential to have access to all parts of the documentation to use the functionality of an embedded system to its fullest extent. Details of the hardware can be found [here](https://www.raspberrypi.com/documentation/microcontrollers/rp2040.html).

## **SETTING UP PICO SDK**

There are various [methods](https://datasheets.raspberrypi.com/pico/getting-started-with-pico.pdf) (see chapters 2 and 9) to setup the development environment for the pico in C using the Pico SDK, depending on what OS you are using on your PC/laptop. However, if you are using Windows OS, the easiest way is to download and install [this](https://github.com/raspberrypi/pico-setup-windows/releases/latest/download/pico-setup-windows-x64-standalone.exe) tool.

Visual Studio Code will ask if you want to configure the pico-examples project when it is first opened; click *Yes* on that prompt to proceed. You will then be prompted to select a kit -- select the *Pico ARM GCC - Pico SDK Toolchain with GCC arm-none-eabi* entry. 

## **BUILDING AN EXAMPLE**

Ensure you selected the right application when starting the Visual Studio Code, as two variations might be installed on your laptop. The icon should look as follows:

![Screenshot of Pico - Visual Studio Code](/img/pico_vsc.png)

Once "Pico - Visual Studio Code" (VSCode) is started, click the [CMake](/img/cmake.png) icon and select the sample code you want to work on. In this example, we will use the [Hello World](https://github.com/raspberrypi/pico-examples/tree/master/hello_world/usb) example. The following [video](https://www.youtube.com/watch?v=NPwoflT_bB0) demonstrates how you get started with VSCode. Note that we are using the hello_usb version of the code. This allows the USB connection between the pico and the PC/laptop to become a virtual UART connection, which can be used together with printf (for debugging purposes).

Now, try to compile and run the [blink](https://github.com/raspberrypi/pico-examples/tree/master/blink) example.

If you are using the Pico W boards, you must make a small amendment to the CMakeLists.txt file. Include "set(PICO_BOARD pico_w)" to line #11. The following [video](https://www.youtube.com/watch?v=sTNtLkoHN58) demonstrates how to make the changes and build a [blink](https://github.com/raspberrypi/pico-examples/tree/master/pico_w/wifi/blink) example for the Pico W. 

![Screenshot of Pico - Visual Studio Code](/img/picow_support.png)

> [NOTE]
> The normal blink example will only work on a standard Pico (without wireless). This is because the Pico W LED is connected to the WiFi SoC and not directly to the RP2040.

## **DOWNLOADING FIRMWARE INTO THE PICO**

Depending on your preferences and requirements, several methods exist to upload firmware onto a Raspberry Pi Pico microcontroller board. Here is a brief overview of two of the most common methods:

1. **Drag and Drop (Mass Storage Device):**
   - The Raspberry Pi Pico has a built-in feature that makes it appear as a mass storage device when connected to a computer via USB.
   - To get the board in bootloader mode ready for the firmware update, hold down the BOOTSEL button while plugging the board into USB. You can only release the button once you connect the pico to the PC/laptop properly.
   - Drag and drop a UF2 file onto Pico's virtual drive to upload firmware using this method.
   - This is a beginner-friendly method and doesn't require any additional software.

3. **Using JTAG/SWD (For Advanced Users):**
   - Advanced users and developers may opt for JTAG/SWD debugging and programming tools to upload firmware.
   - This method offers greater control and debugging capabilities but requires additional hardware and expertise.
   - You may configure another pico as a SWD Debugger called PicoProbe. See [Appendix A](https://datasheets.raspberrypi.com/pico/getting-started-with-pico.pdf).
   - Here is a video of someone configuring and using the [PicoProbe](https://www.youtube.com/watch?v=0i2gLeBal9Y).

**In this lab, we will use method #1 (Drag and Drop).**

## **TASK**

In this [basic code](basic.c) example, we embark on a journey to understand various types of operators in the C programming language. By executing this code, we gain insights into arithmetic, relational, logical, and bitwise operators, each playing a distinct role in manipulating and evaluating data.


## **EXERCISE**

This [blinky code](blinky.c) is supposed to blink an LED connected to the GPIO pin. The LED blinks at a rate determined by the "a" variable, which starts at 1 ms and __doubles__ with each iteration of the loop. When variable "a" reaches 2048ms, it resets to 1, creating an odd repeating LED blink pattern. The LED blink pattern must turn on and off with the same delay at __each loop iteration__. Could you identify where the errors are and make the necessary changes so that the code works as intended?

> [!IMPORTANT]
> Include a printf statement to monitor the variable "a". You might need to modify the CMake file to allow printf to work on the blink example.

