# Wireless communication

Watch at least the first part of this video to see some wireless tools and also a very simple amplitude modulated signal, that is used to open a garage door and how the signal encodes the on and off switches in the remote.
https://www.youtube.com/watch?v=1RipwqJG50c


Watch the error correction videos here. The previous talk showed a custom protocol using simple on-off pulsing. A bit more advanced wireless systems might send data as Non-Return-To Zero data, even though I have not seen it done on wires as in this video. He also builds something that resembles an I2C protocol with a data and a clock-line, which is often used by chips in embedded systems. Parity is always set in serial communications like RS232, but the hardware he builds is inside the microcontrollers and configured by writing to registers. CRC checksums are very common in wireless communication systems, so view these as well, even though the computation is often done for you by either hardware or software libraries. 
https://www.youtube.com/playlist?list=PLowKtXNTBypFWff2QjXCWuSfJDWcvE0Vm

Watch the wired ethernet communication series, as it walks you through Manchester encodings, through bits to frames, preambles etc. All this is common in wireless communication protocols as well. Preamles are sometimes constructed by your software or programmed into registers in the radio-chips to generate them automatically. Frames are most likely programmed by you or software libraries you use for a certain protocol stack before they are transfered to the radio chip. https://www.youtube.com/watch?v=XaGXPObx2Gs&list=PLowKtXNTBypH19whXTVoG3oKSuOcw_XeW


Continue with Micro:bit lessons https://microbit.org/ and continue with https://docs.pycom.io/gettingstarted/ 
