# Wireless Head Tracker flashing instructions #

### Flashing background information ###

The WHT consists of two separate devices: the first device is the tracker which contains the movement sensor (MPU-6050 or MPU-9150) and a microcontroller (just fancy word for a low power computer) with a 2.4GHz radio transmitter and receiver. The second device is a dongle with a USB plug, another microcontroller and a 2.4GHz radio. This USB dongle receives the movement sensor information from the tracker, then processes it and sends it over USB to the PC.

![http://wireless-head-tracker.googlecode.com/svn/wiki/images/wht_dongle_and_tracker.jpg](http://wireless-head-tracker.googlecode.com/svn/wiki/images/wht_dongle_and_tracker.jpg)

As I've mentioned, the microcontrollers on these two devices are essentially small computers and they contain a little bit of flash memory (16KB each). This flash memory stores the software these small computers are running. Software running on microcontrollers is often called firmware but in essence it is not much different from software running on your PC or smartphone. And just like any software, the firmware on the tracker and the dongle can be updated to fix bugs or add new features. This update process is called firmware flashing.

In order to flash the two devices, you need to have another device called a flash programmer. It connects to the PC though a USB cable, and to the tracker through another cable, or to the dongle by directly plugging it into the programmer. The programmer receives commands and data from the PC, then sends these commands to the microcontroller on the tracker or dongle which overwrites the program contained in their flash memory.

The programmer with tracker flashing cable: ![http://wireless-head-tracker.googlecode.com/svn/wiki/images/programmer_and_tracker_cable.jpg](http://wireless-head-tracker.googlecode.com/svn/wiki/images/programmer_and_tracker_cable.jpg)

The flash programmer doesn't need drivers, but you will need to wait a few minutes after plugging in the programmer for the first time for Windows to figure that out.

During the flashing process, the tracker and the dongle need to be powered and they receive this power from the programmer. It is very important to remember that the tracker and dongle require different voltages to run correctly. The dongle needs 5V and the tracker needs 3.3V. The output voltage level of the programmer is selected with the red jumper. Powering the tracker with 5V will probably damage it beyond repair, so be careful and follow the instruction below to the letter.

### The necessary software ###

The PC software needed to communicate with the flash programmer, the flash images for the dongle and tracker and the WHT configuration program are all contained in the WHT software package which you can download from this link:

https://docs.google.com/uc?authuser=0&id=0B5QsMM8GX6NEV01oVFdwOVRJS3M&export=download

Unzip this file into a new folder. The ZIP contains two folders: **flash** and **config**.

folder: **flash\**
  * **nrfburn.exe** - the software which communicates with the programmer
  * **flash\_dongle.bat** - the windows batch file which calls **nrfburn.exe** with the required arguments to flash the dongle
  * **flash\_tracker.bat** - the windows batch file which calls **nrfburn.exe** with the required arguments to flash the tracker
  * **tracker.hex** - the tracker flash image
  * **whtdngl.hex** - the dongle flash image

folder: **config\**
  * **WHTConfig.exe** - the WHT configuration program (not needed for this guide)
  * **WHTConfig.ini** - the WHT configuration settings (not needed for this guide)

We will deal with the flash folder in this tutorial.

### Tracker flashing details ###

  1. Make sure you have downloaded and unzipped the WHT software package
  1. If the tracker or the dongle is connected to the programmer remove them
  1. Remove the battery from the tracker
  1. Remove the flash programmer from USB
  1. Put the jumper labelled TGT\_PWR to the 3.3V position like shown on the picture below ![http://wireless-head-tracker.googlecode.com/svn/wiki/images/3v3_pos.jpg](http://wireless-head-tracker.googlecode.com/svn/wiki/images/3v3_pos.jpg)
  1. Connect the flat end of the programming cable to the pin header on the flash programmer labelled "LU1+ SPARKFUN". Make sure you match the label on the programmer cable with the labels on the flash programmer pin header. See picture:![http://wireless-head-tracker.googlecode.com/svn/wiki/images/tracker_prog_cable.jpg](http://wireless-head-tracker.googlecode.com/svn/wiki/images/tracker_prog_cable.jpg)
  1. Connect the other end of the programming cable to the tracker. ![http://wireless-head-tracker.googlecode.com/svn/wiki/images/tracker_with_cable.jpg](http://wireless-head-tracker.googlecode.com/svn/wiki/images/tracker_with_cable.jpg)
  1. Just in case, double check that the TGT\_PWR jumper is in the 3.3V position
  1. Plug the programmer with the tracker attached into USB. If this is the first time you plugged in the programmer into your PCs USB port, wait a minute or two for Windows to recognize the programmer. You will get a "This device is now ready" message from Windows.
  1. Go to the folder where you unpacked the WHT software package and run the flash\_tracker batch file. The flashing process should take about 6 seconds.
  1. If the flashing is successful you will see this message in the window: ![http://wireless-head-tracker.googlecode.com/svn/wiki/images/tracker_flashing_success.png](http://wireless-head-tracker.googlecode.com/svn/wiki/images/tracker_flashing_success.png)
  1. Remove the programming cable from the programmer and the tracker.
  1. Put the battery back into the tracker
  1. You're done!

### Dongle flashing details ###

  1. Make sure you have downloaded and unzipped the WHT software package
  1. Remove the flash programmer from USB
  1. Remove the tracker or the dongle from the programmer if either is connected to it
  1. Place the red jumper labelled TGT\_PWR to the 5V position like shown on the picture below: ![http://wireless-head-tracker.googlecode.com/svn/wiki/images/5v_pos.jpg](http://wireless-head-tracker.googlecode.com/svn/wiki/images/5v_pos.jpg)
  1. Plug the dongle directly into the programmer's row of pins labelled "LU1+ generic". Make sure that every pin in the programmer is connected to every slot in the dongle. ![http://wireless-head-tracker.googlecode.com/svn/wiki/images/prog_dongle.jpg](http://wireless-head-tracker.googlecode.com/svn/wiki/images/prog_dongle.jpg)
  1. Just in case, double check that the TGT\_PWR jumper is in the 5V position
  1. Plug the programmer with the dongle attached into USB. If this is the first time you plugged in the programmer into your PCs USB port, wait a minute or two for Windows to recognize the programmer. You will get a "This device is now ready" message from Windows.
  1. Go to the folder where you unpacked the WHT software package and run the flash\_dongle batch file. The flashing process should take about 6 seconds.
  1. If the flashing is successful you will see this message in the window: ![http://wireless-head-tracker.googlecode.com/svn/wiki/images/dongle_flashing_success.png](http://wireless-head-tracker.googlecode.com/svn/wiki/images/dongle_flashing_success.png)
  1. Remove the programmer with the dongle from USB
  1. Remove the USB dongle from the programmer
  1. You're done!

After the dongle and tracker have been flashed you will need to recalibrate and reconfigure the devices with the WHTConfig.exe program.

Calibration and configuration instructions:
http://youtu.be/GKqRHQjisI0