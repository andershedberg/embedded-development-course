# Start
First get some kind of Arudino kit which contains the Arduino UNO microkontroller ( the very basic original one ), like this - https://store.arduino.cc/genuino-starter-kit or this ( if you live in Sweden https://www.kjell.com/se/produkter/el-verktyg/arduino/arduino-kit/playknowlogy-startpaket-experiment-arduino-p88211 ) 
( It seems the Arduino folks sometimes call their stuff Genuino due to a split among the original founders, here we just call it Arduino )

Later we will move on to more advanced CPUs but just get the basic Arduino UNO as it is very robust against errors when you connect hardware to it, even minor shortcircuits which will burn most other microcontrollers is usually not fatal.

Just follow the guides there and build the exercises. Blinking lights, sounds, buttons etc. This will give you a basic understanding on what is possible and what can be done. 


# The more advanced stuff
Basic stuff is usually covered in the above type of excersices, but as we aim to really make you into an embedded developer there are some more topics than is good to discover and learn about on the Arduino before moving on to more advanced chips.

* EEPROM 
The Atmel 328p microcontroller contains EEPROM where you can store configuration bytes that survives a power-cycle. This type of memory is often used for storing encryption keys and other settings that needs to be changed sometimes, but not very often. 
Therefore it is vital to have an understanding of how to read and write to this type of memory. https://www.arduino.cc/en/Reference/EEPROM 
Write something to this memory, then power the chip of and then on again and read it back.

* Timer interrupts
All microconrollers has some hardware timers that can be programmed to interrupt the ordinary program and do something completely different. 
This is a simple exammple that blinks a LED https://www.arduino.cc/reference/en/libraries/watchdog/ 
( When we do real-time operating systems we will re-use this kind of timers to create what is usually called a "tick" when the operating system will run for a while. )

* Watchdog timer reset
The 328p and all microcontrollers has a watch-dog functionality that resets the chip if you your program hangs. 
https://create.arduino.cc/projecthub/rafitc/what-is-watchdog-timer-fffe20

## External sensors and their databuses.
* I2C
https://www.arduino.cc/en/Reference/Wire
Many sensors connect through the i2c bus. Some start-kits contains such sensors, otherwise you just need to get one. 
Get a simple sensor that is well documented and has libraries for the Arduino as it is very difficult to start from scratch with a new kind of sensor. 
Learn how to read and write to the sensors registers over the i2c bus. 

* One-wire
A company called Dallas invented a databus that only required a common data and clock-line, instead of the i2c which use separate clock and data lines. It saves pins on the microcontroller. 
It is still used for temperature sensorers, like the DS18B20. 
https://playground.arduino.cc/Learning/OneWire/

* SPI buses
A faster databus with more lines, commonly used with memory cards ( SD cards ). You will need some SD shields if you wish to try this, but they are not commonly available for the Arduino. 
Sparkfun has a special logger with an Arduino 328p chip that can be reprogrammed - https://www.sparkfun.com/products/13712

## Data-sheets and documentaion
So far we have used libraries, but once in a while you will need to dig deeper into the microcontrollers to solve hard problems, such as coding errors in the libraries that makes them hang in edge-cases now an then.
This is the data-sheet for the ATMega 328p that is used in the Arduino. It is only 442 pages. Newer more advanced controllers contain thousand of pages describing all their built in building blocks. They also tend to divide the documents into several parts such as "Datasheet" ( from short summaries on two to sixty pages), "Programmers technical reference", "Hardware design guide", etc. 
Browse this document and then read these parts a little more careful. It is not necessary to understand it all, but these are common documents that an embedded software engineer needs to read from time to time so it is good to know what can be expected to find in such a document. 

https://web.mit.edu/6.111/volume2/www/f2019/handouts/ATmega328P.pdf
* 1 Introduction
* 4 Block diagram. 
* 5 Pin descriptions. (short version, more is in the document )
* 11 The CPU core and it's status registers. 
* 12 Memories inside the chip. Sort of special for this microcontroller, but look at the EEPROM registers as well, as it is quite strang to reach a memory through registers. It is not a memory mapped memory ;-)
* 13 Clocks. Selection of different clock-sources for low-power consumption and the pros and cons of the different clocks. Pre-scalers that can be programmed is a very important concept. I.e you have counters that can be programmed that will divide your fast clock into a tick every milli-second as an example. 
* 14 Sleep modes. To preserve battery power we can remove the clock and change it's frequency from some parts of chip. This disables a lot of transistors that turn on and off with the clock and saves power.
* 15 Resets. How to reset the chip if the power is going down just a bit so the microcontroller always has a stable known state. 
* 16 Interrupts. The jumpvector that the program counter is set to depending on the type of interrupt. Interrupt masks so not all interrupts are enabled. 
* 18 IO-pins. From basic IO pin to alternate functions and how to set it use power-up resistors, so you don't need external resistors for your buttons. 
* 24 Serial ports. A lot of registers to set up the correct clocks and parameters. 
* 30,31 Boot and fuse bits for copy protection. There is some kind of program running on all microcontroller at starts to let us program them. The Atmega is sort of special, ARM has ordinary ARM-code running at boot.
* 32 Electrical specification. Max voltage! Also 32.1 which is very special for this chip as it actually shows that higher voltage means you can clock the chip faster.
* 38 Errata. There are always errors in the documentation... Check if you have the latest documentation and that you are not affected by known errors of the chip. The older the chip, the more errors are known. Can be very hard to resolve problems with new chips.


Look at the documents on https://www.microchip.com/wwwproducts/en/ATMEGA328 
* Erratas. Known errors in different silicon versions of the chip itself.
* Application notes. Check them out. The chip-vendor usually has guides on hardware as well as software application development. This is a very used chip so the application notes are many!
* AVR instruction set manual. All the machine/assembler instructions for this CPU. This is usually not published for ARM microcontrollers as it is published by other sources and in books.
* White papers. Another name for Application notes ;-)

## Whats saved for other platforms
* Wireless communication
The memory of the Adrduino is very limited and these protocol stacks that handle communication tends to eat too much memory to be fun to work with on the Arduino.

* MQTT (Message Queuing Telemetry Transport) 
This is a protocol that has been adopted widely for doing IoT stuff between embedded systems and servers. As stated above, it can be done on the Arduino, but you would need an ethernet or wifi-card for the Arduino and then the memory is sort of used up already.

* Realy time Operating system

* OTA ( Over the Air programming ) 
The 328p chip is a chip-design from the 1990's and has separated ( Flash ) and data ( RAM ) memories. This is called a "Harward architecture". It is not possible to execute code from RAM at all, even though it is possible to copy "data" from flash to ram.
Newer ARM chips usually have the same architecture, but they combine the adress and databuses from the CPU-core to make it possible to run code from all kind of memories and due to this they can also change their own programs in the field.
This also makes the AVR/Arduino unsuitable for IoT-sensors that needs software updates in the field. 

More trivia about the microcontroller itself - 
https://en.wikipedia.org/wiki/AVR_microcontrollers

