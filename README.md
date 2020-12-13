# embedded-development-course
An embedded development course from Arduino blinking to hard core optimizing of battery life on ARM cores.

Follow this flow - 
1. Basics. The Arduino is a well documented education platform that is used in many schools. Learn the basics of connecting hardware and doing software for IO with blinking lights, i2c libraries and simple timer interrupts. See [Arduino excersises.md](Arduino-excersises.md)

2. Power. Go one step deeper to really optimize battery power consumption to reach 10 years lifetime on a coin-cell. What state should IO-pins be set in during deep sleep? Can your application work on 16 bytes of battery backed up RTC registers and no RAM? What really happens when you wake up from deep-sleep/re-boot?
. Get some bare-bones Arduino microcontrollers and follow the [low-power.md](low-power.md).

2. Wireless IoT communication. Learn how to send data with the most common protocols using wifi, lora and GSM networks to your computer with a dashboard. Start with [Wireless-iot.md](Wireless-iot.md) 

3. Programming and microcontroller architechture. 
Embedded systems are usually programmed in the C-programming language as you have experienced with the Arduino tutorials. Arduino hides a lot of the hard stuff.
Advanced C-programming can be learnt by following [C-programming.md](C-programming.md).
To really understand the C-compiler, linkers and their files, read chapter 10 of [The Definite Guide to the Cortex-M3]( https://www.eecs.umich.edu/courses/eecs373/labs/refs/M3%20Guide.pdf) The book is the best guide to the ARM instruction set and what you can expect to find in a SOC ( System On a Chip ) regarding the core CPU and the control of it. Most microcontrollers are built in similar ways. The chapters of Systicks and interrupts are good to understand before moving on to RTOS'es. 

4. Real Time operating systems. Between the Arduino ( one-task endless loop programming ) and the Raspberry Pi´s full blown linux systems, there is a need for combining communication protocol stacks with high responsiveness to sensors and IO devices like accelerometers and motor-controllers and put the microcontroller to sleep. This is the domain of RTOS'es. One common one is [FreeRTOS](https://aws.amazon.com/freertos/), now bought by Amazon for IoT usage.  If you wish to go real deep and academic about semaphores, execution priorities, browse through the later parts of this book - https://ptolemy.berkeley.edu/books/leeseshia/
