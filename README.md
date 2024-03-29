# Introduction
I started writing this during the Covid-19 pandemic to teach new skills to employees and interns that has not programmed embedded software before.

Turns out there are a ton of very good information on the internet already, so why redo that? These pages has thus turned into a collection of good introductions. 
Like Miro Samek who has an excellent video tutorial here https://www.state-machine.com/video-course 
Below are my collection of other sources. 

# embedded-development-course
An embedded development course from Arduino blinking to hard core optimizing of battery life on ARM cores.

Follow this flow - 
1. Basics. The Arduino is a well documented education platform that is used in many schools. Learn the basics of connecting hardware and doing software for IO with blinking lights, i2c libraries and simple timer interrupts. See [Arduino excersises.md](Arduino-excersises.md)

2. Power. Go one step deeper to really optimize battery power consumption to reach 10 years lifetime on a coin-cell. What state should IO-pins be set in during deep sleep? Can your application work on 16 bytes of battery backed up RTC registers and no RAM? What really happens when you wake up from deep-sleep/re-boot?
. Get some bare-bones Arduino microcontrollers and follow the [low-power.md](low-power.md).

3. Wireless IoT communication. Learn how to send data with the most common protocols using wifi, lora and GSM networks to your computer with a dashboard. Start with [Wireless-iot.md](Wireless-iot.md) 

4. Programming and microcontroller architechture. 
Embedded systems are usually programmed in the C-programming language as you have experienced with the Arduino tutorials. Arduino hides a lot of the hard stuff.
Advanced C-programming can be learnt by following [C-programming.md](C-programming.md).
To really understand the C-compiler, linkers and their files, read chapter 10 of [The Definite Guide to the Cortex-M3]( https://www.eecs.umich.edu/courses/eecs373/labs/refs/M3%20Guide.pdf) The book is the best guide to the ARM instruction set and what you can expect to find in a SOC ( System On a Chip ) regarding the core CPU and the control of it. Most microcontrollers are built in similar ways. The chapters of Systicks and interrupts are good to understand before moving on to RTOS'es. 

5. Real Time operating systems. Between the Arduino ( one-task endless loop programming ) and the Raspberry Pi´s full blown linux systems, there is a need for combining communication protocol stacks with high responsiveness to sensors and IO devices like accelerometers and motor-controllers and put the microcontroller to sleep. This is the domain of RTOS'es. One common one is [FreeRTOS](https://aws.amazon.com/freertos/), now bought by Amazon for IoT usage.  If you wish to go real deep and academic about semaphores, execution priorities, browse through the later parts of this book - https://ptolemy.berkeley.edu/books/leeseshia/

6. Production test.
Here is a good video introduction on how to build and program a tester that can be used in factory production. Not that complicated nor fancy, but gets the job done! https://www.youtube.com/watch?v=hrNsdTKUbfY Adafruit has some introductions on how to do hardware for jigs with pogo-pins, were you basicly can hold down a PCB-board with one hand and run the computer test steps with the other - https://learn.adafruit.com/how-to-build-a-testing-fixture

