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

(int ledArray[] = {5,6,9};) defines the colour sensor LED pins
(boolean balanceSet = false;) boolean to check if the balance has been set, basically we want to confirm calibration status
(int red = 0;
int green = 0;
int blue = 0;)  here we want to create and place 'holders' for any colour that has been detected

(float colourArray[] = {0,0,0};
float whiteArray[] = {0,0,0};
float blackArray[] = {0,0,0};) I have decared float arrays to hold and contain the colour arrays
(int avgRead;) placed a holder for average reading of the observation to help make the closest to correct observation

In the 'setup' function:
(  pinMode(2,OUTPUT);
  pinMode(3,OUTPUT);
  pinMode(4,OUTPUT);) Here, the outputs for the colour sensor are being set up
  
  ( Serial.begin(9600);) here, the serial communication begins
  
In the loop:

In the 'checkbalance' function in the loop, we iterate if the balance has been set, and if it hasn't, then we send the instruction to set it

In the 'setbalance' function:
 delay for five seconds is created, this gives us time to get a white sample in front of our sensor
 scan the white sample.
 go through each light, get a reading, set the base reading for each colour red, green, and blue to the white array.
 
 the white is scanned, then the LED will produce a blue pulse to indicate that now the black colour sample may be placed
 then another delay for 5 seconds is carried out to allow the effective scanning of the black to complete the calibration process.
 
 The 'Checkcolour' function requires extensive explanation, hence almost each line will be explained:
 
   (  digitalWrite(ledArray[i],HIGH);)  turn or the LED, red, green or blue depending which iteration
     (delay(100);        )              delay to allow CdS to stabalize, they are slow
     (getReading(5);      )            take a reading however many times
     (colourArray[i] = avgRead; )       set the current colour in the array to the average reading
     (float greyDiff = whiteArray[i] - blackArray[i];  ) the highest possible return minus the lowest returns the area for values in between
     (colourArray[i] = (colourArray[i] - blackArray[i])/(greyDiff)*255; ) the reading returned minus the lowest value divided by the possible range multiplied by 255 will give us a value roughly between 0-255 representing the value for the current reflectivity(for the colour it is exposed to) of what is being scanned
    ( digitalWrite(ledArray[i],LOW); )   turn off the current LED
    
    In the 'getreading' function we take in how many ever readings were requested and then add them up.
    
    We then calculate the average and set it up.
    
    after this, the R, G and B componenets of the colour of the object in front of the sensor will be printed on the screen. Each time, a delay of 2 seconds is placed.
    
    
