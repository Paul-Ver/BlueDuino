# BlueDuino
Bluetooth programmable, controllable and debugable Arduino

The aim of this project is to create a small Arduino board that replaces the USB connection.
This allows to debug/control a robot or [LED Table](https://github.com/Paul-Ver/LedTable) withouth having to connect your PC over USB.

In the case of the robot, this is usefull as it's a moving object and in the case of the LED table, you can have the PC completely isolated from the LED power supply (the LED's draw a lot of current, which your USB port cannot provide).
Also, it adds to the ease of use.

This project has auto-reset (for programming) and proper level shifting. Which is (usually) not the case on a lot of projects you may find online. It's also very compact and relatively cheap (PCB is very small and a few quite cheap parts are required).

![Preview image](https://github.com/Paul-Ver/BlueDuino/blob/master/images/assembled.jpg)

## Hardware

* Arduino Pro Mini (5V, 16Mhz, Atmega328P)
* Bluetooth Module
* Logic level shifter
* AMS1117 power supply 5V to 3.3V
* (PCB)[https://oshpark.com/shared_projects/2RTuiq8N]

Please note you could use an 3.3V Arduino with the 3.3V bluetooth module.

![Parts](https://github.com/Paul-Ver/BlueDuino/blob/master/images/parts.jpg)

## Software

Notable is that the Serial Baudrate of your Bluetooth module, has to be set to the upload/communication speed of your Arduino!
When using USB, the IDE will take care of this when selecting a board, but THIS IS NOT THE CASE WHEN USING BLUETOOTH.
You can check the boards.txt file or [external resources](https://42bots.com/resources/arduino-program-sketch-upload-speeds/) for the correct baudrate.
Arduino Micro/Mini's may differ! Some have Atmega328P and some Atmega168 and the baudrate for these differ!

AT+NAME=BlueDuino                   //Set the name of the module (this is how it's visible under bluetooth devices)
AT+POLAR = 1,0                      //Set the polarity of the state pin (which is used as a reset line, automatically resets on connection)
AT+UART=<<INSERT_YOUR_BAUDRATE>>    //Set the UART baudrate (nano 57600, uno 115200) check your boards.txt file
AT+PSWD=<<INSERT_YOUR_PASSWORD>>    //Set passcode for the bluetooth module, to avoid others playing around with it

For me, under windows (clean install) I was able to connect to the bluetooth module directly (would show up as COM port) and it would work directly as if it's an USB/Serial cable.

## TODO/Notes

* I've lost the original board schematics for this project, but the board files are uploaded to this Git as well.

TODO:
* Recreate original board files
* Test and improve above instructions
* Create 3D printable enclosure
* Potentially add build video/instruction
* Add FAQ for common problems.