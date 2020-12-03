# embedded-development-course
An embedded development course from Arduino blinking to hard core optimizing of battery life on ARM cores.

Follow this flow - 
1. Basics. The Arduino is a well documented education platform that is used in many schools. Learn the basics of connecting hardware and doing software for IO with blinking lights, i2c libraries and simple timer interrupts. See [Arduino excersises.md](Arduino-excersises.md)

2. Wireless IoT communication. Learn how to send data with the most common protocols using wifi, lora and GSM networks to your computer with a dashboard.  https://docs.pycom.io/gettingstarted/ 

3. Real Time operating systems. Between the Arduino ( one-task endless loop programming ) and the Raspberry Pi´s full blown linux systems, there is a need for combining communication protocol stacks with high responsiveness to sensors and IO devices like accelerometers and motor-controllers and put the microcontroller to sleep. This is the domain of RTOS'es. One common one is FreeRTOS, now bought by Amazon for IoT usage.  https://aws.amazon.com/freertos/

4. Power. Go one step deeper to really optimize battery power consumption to reach 10 years lifetime on a coin-cell. What state should IO-pins be set in during deep sleep? Can your application work on 16 bytes of battery backed up RTC registers and no RAM? What really happens when you wake up from deep-sleep/re-boot?
