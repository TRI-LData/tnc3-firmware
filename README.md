# TNC3L
# !!! THIS RESPOSITORY IS WORK INPROGRESS !!!
##Current Status: Repository work and TNC3L prep for FCC testing

TNC3L was developed as an enhanced hardware version of Mobilinkd’s open-sourced TNC3.  
The goal was to make TNC3L easier to use and maintain from a hardware perspective and 
not to change/rewrite firmware developed for TNC3.  This would ensure application compatibility, 
including TNC3 firmware updates.  TNC3L is open-sourced and licensed under GPL-3.0.  This 
repository is a fork of 

 [Mobilinkd TNC3 Repository](https://github.com/mobilinkd/tnc3-firmware)

 TNC3L hardware specific files are in the TNC3L repository directory.  PCB files,
 schematics, BOM, and 3D printer STL files are included.

## TNC3L and TNC3 Differences

TNC3L firmware is almost identical to TNC3 firmware as posted on GitHub.  Minor firmware
changes have been made to accommodate hardware changes.  Functionally all applications 
compatible with the TNC3 should work with the TNC3L.  This repository is for TNC3 firmware
ported to TNC3L hardware.  The code changes are enabled with a define statement
in main.h, #define TNC3L.

Source code with modifications:
main.h
util.h (new)
LEDIndicator.cpp
IOEventTask.cpp



TNC3L was designed to be attached to an HT by simply plugging it in.  There are no 
cables or need to attach the device to the HT with rubber bands or Velcro.   Simply plug 
it in or out of the HT’s speaker and mic jacks.  This configuration allows the HT 
to be comfortably handheld, used with a belt clip, or inserted in the charging 
cradle without detaching the TNC3L from the HT.  Power button and status indicators
are visible and accessible from the front of the HT.

![TNC3L attached to HT](/assets/images/TNC3L_Radio.jpg)
![TNC3L Top](/assets/images/TNC3L_Top.jpg)
![TNC3L Bottom](/assets/images/TNC3L_Bottom.jpg)

### Rechargeable/Replaceable Battery
TNC3L uses a standard 14500 lithium Ion 3.7V battery.  Battery protection and
charging are provided on the circuit board.  Discharged batteries can be replaced without tools or 
charged via the USB port.  The TNC3L circuit board can accommodate other batteries 
size with higher capacities.   However, the standard enclosure is designed for 
14500 batteries only.

### Power button
The push button located on the base of the TNC3L is used to power on and off the device.  
In the off position it disconnects the battery from other circuitry.  The MCU, Bluetooth module, 
LEDs, etc. do not consume any power in the off position.  It is a latching push button switch.  
The on or off position is clearly visible.  Powering the device directly with a push button 
eliminated the need for the MCU to be “on” to control power to other devices and to detect 
button presses to turn itself on or off.  This approach maximizes battery life.  
However, minor firmware modifications were needed.

### USB Type C Connector
A type C USB connector is used instead of a micro-USB.  It has the same connectivity as TNC3
and can be used for charging or programming.  Power is always on when the USB is plugged in
irrespective of the push button.

### Status Indicators (LEDs)
Two status indicators are on the TNC3L.  One is the same as TNC3 for radio, Bluetooth status 
and processor status.  The other is for battery charging.  TNC3L has three charging 
states; green for charging complete; red for charging; off if no USB or off if the USB 
is plugged in and there is a charging error.



### DFU MODE PINS
TNC3L uses a two-pin IDC header to place it into DFU mode for programming.  It does not have 
separate reset or DFU buttons.   
1) Power button in the off position
2) Short the IDC header (jumper wire)
3) Attach USB
4) Remove jumper

### Radio to TNC3L Interface
A TRRS 3.5mm jack and a 4 pin IDC header are available to interface the TNC3L to a radio.  
The 3.5mm TRRS jack has the same signals as the TNC3.  Cables compatible with TNC3 should also be 
compatible with TNC3L.  A second MIC/speaker interface was added to the TNC3L using 
a 4-pin IDC connector.  This port can be used for connecting the TNC3L to radios without
using a 3.5mm plug.  TNC3L K1 style docking adapter is an example.  It connects the TNC3L to the HT without a cable.

![TNC3L DOCK3](/assets/images/TNC3L_Dock3.jpg)

### 3D Printed Enclosure
The TNC3L enclosure and docking adapter are made from 3D printed parts.  FCC testing was
also performed using TNC3L as shown here.  TNC3L is not limited to the a specific enclosure.  Users are welcome to 
design custom enclosures to adopt various battery sizes and device orientation.  

# Firmware 
Please refer to Mobilinkd's TNC3 GitHub repository for building and installing firmware.  Do not use frimware
directly from their repository, use the firmware source provided in this repository.

 [Mobilinkd TNC3 Repository](https://github.com/mobilinkd/tnc3-firmware)    
