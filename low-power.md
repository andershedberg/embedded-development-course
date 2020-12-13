# Low power design - how to get 10+ year of battery life

Kevin Darrah has a [site](https://www.kevindarrah.com/) and a passion for low power IoT stuff. On youtube he has a lot of good stuff. For low power design he has a playlist that should be looked through for about 3 hours. https://www.youtube.com/playlist?list=PL0JWuCHXfJ2zjHiHtHUO2AjGQ1pP4Bzab

There are two especially interesting videos to watch and repeat yourself as they must be understood, as these concepts applies to all kind of microcontrollers running on batteries. Your will need an arduino ( Atmel 328p ) stripped of all extras to test this and power-supplies with either build in power measurements or an external ampere meter. If possible, get an [Otii](https://www.qoitech.com/) 

*Obs! an ordinary ampere meter might need to be switch from milli-amp to nano amps during these tests. There is usually an internal resistor in these kind of instruments so if you suddenly pulse 2 Amps with a GSM modem, the voltage drop over the amp-meter might prevent the GSM module from working. Hint - short circuiting the inputs of the ampere meter during these events if they are know to happen at boot usually works.*


The must understand and try videos are:

[Low Power Arduino! Deep Sleep Tutorial](https://youtu.be/urLSDi7SD8M ) Here he walks through and shows actual measurements on the important things when you enable the low-power deep sleep modes of microcontrollers. 
- Turn all unconnected inputs to outputs. An undriven input pin will float with a voltage between GND and +VCC. In the unknown state between a zero and a 1, the input design of the chip draws "a lot" of current ( u-amps ).
- Turn off blocks of analog parts, in this case the A/D converters and the BOD. Due to safety issues I might not turn off the Brown Out Detector, as it detect voltage removal and then resets the chip to a known state. 
- Voltage. The arduino can run at higher speeds if you use a higher voltage, but this consumes more energy. Remember that power consumption in watts is voltage * ampere, so we see an even better effect preserving power with this technique than is obvious from the videos ampere reading. 

[Low Power Arduino! Lower the Voltage and Frequency](https://youtu.be/8dyZvkvqD1Y)
- Programming the internal watchdog timer to wake up at intervals. These kind of internal clocks are not that accurate, but they do not need to drive an external crystal and are usually more power-efficient. 
- As a side-note, the Atmel 328p designs can be cost-optimised to only run on this internal clock. 
- Programming of pre-scalers to get the frequency down to the needs of your application and wake-up times. 

Whats not shown:
- Turn off clocks to part of the chip that is not used. This is not obvious from the videos or Atmel datasheets, but is most likely what actually happens when an internal peripheral is turned on or off through the power registers.
- Debug interfaces. ARM based chips usually has a separate block connected to the CPU core and special pins for debuggers (JTAG/SWD pins). Very nice to use for debugging both at home and in the fields. Usually draws a lot of current though, and must sometimes be clocked while the internal cpu is not clocked.
- Debug connectors. A debug cable can power the chip from the debugger, or pull more current from the chip. Thus they must be disconnected while doing power measurements. The input I/O pins for the debugger must also be turned into an output. See first video. 
- Crystal driver settings. Some chips can drive an external crystal with different powers. We once had a random problem in the field with a crystal not working dure to too low drive. 
