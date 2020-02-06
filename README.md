Minor Project-IoT-Batch 12: Dec'19-Jan'20-Arjun Sharma

This file contains the description of my project that is the LDR based colour sensor. The design will be described, and the source code will be explained.

Components used:
Arduino Uno microcontroller
RGB LED
Light Dependent Resistor
Resistor of 100 ohm value x3
Resistor of 10k ohm value
Jumper wires
Solderless Breadboard

Wiring the RGB LED:
This will be the emitter part of the circuit emitting different colours which will bounce off of objects, which will be detected by the LDR

Connected pin 2 to the GND pin on the Arduino Uno.
Connect pin 1, the red coloured LED of the RGB LED to pin 5 on the Arduino Uno.
Connect pin 3, the green coloured LED of the RGB LED to pin 6 on the Arduino Uno.
Connect pin 4, the bleu coloured LED of the RGB LED to pin 9 on the Arduino Uno.

The reflected light from the emitter (RGB) LED bouncing back off of any objects will be read by the LDR which will used calibrated values to find the individual R-G-B colour values of a particular colour.

Now wiring the LDR:
Connect pin 1 of the LDR to the GND pin on the Arduino
Connect pin 2 of the LDR to the 3.3V pin on the Arduino.
Connect pin 2 of the LDR to the A0 pin on the Arduino.

 last two wirings are all parallel. This is because we are making a voltage divider to get the changing voltage reading as the reflected light changes in intensity.
 
 First i have prepared a black and white piece of paper before testing the colour

During the first 5 seconds of the program running the RGB LED will emit a variety of colours. I placed a black paper over the LED and LDR for the first 5 seconds. Then I switched the paper to the white piece of paper for the next 5 seconds.


The code is written so that these first 10 seconds are the calibration period. In the video i have already done the calibration, to save time in the video because it was taking too much space in recording, hence I have done the calibration off screen, and had simply placed a red paper aboce the LED and LDR to directly show the working of the project. 

CODE WORKING:
