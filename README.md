# NotSoBasicArduino
 The follwing files are my second foray into Arduino
 
 
## Table of Contents
* [Table of Contents](#TableOfContents)
* [LED_Fade](#LED_Fade)
* [HelloFunctions](#HelloFunctions)
* [NewPing](#NewPing)
---

## LED_Fade

### Description & Code
My objective was to make a LED light fade in and out.

```C++
  analogWrite(led, brightness);

  // change the brightness for next time through the loop:
  brightness = brightness + fadeAmount;

  // reverse the direction of the fading at the ends of the fade:
  if (brightness <= 0 || brightness >= 255) {
    fadeAmount = -fadeAmount;
  }
```
The 

### Evidence
[Evidence](https://create.arduino.cc/editor/Ben_Berthy123/9c4aa851-88aa-4b7c-bbfa-2604bda92def)

### Images
<img src=
### Reflection

## LED Blink Revisited

### Description & Code

### Evidence

### Images

### Reflection

## Finite LED Blinker

### Description & Code

### Evidence

### Images

### Reflection

## Arduino Review Assignment

### Description & Code
(I was never givena button in my pack so I skipped that part of the assignment.)

This code allowed the LED to start flickering faster over time, until eventually it stops.

```C++
int LedPin = 8;
int delayVar = 1000;

void setup() {
  pinMode(LedPin,OUTPUT);
  Serial.begin(9600);
}

void loop() {
  Serial.println(delayVar);
  
  digitalWrite(LedPin, HIGH);
  delay(delayVar);
  digitalWrite(LedPin, LOW);
  delay(delayVar);
  
  delayVar = delayVar - 100;
  ```
  This works, by after each blip/flicker, you take off 100 milliseconds of the wait time, until it gets super fast.
### Evidence
[Evidence](https://create.arduino.cc/editor/Ben_Berthy123/d6f6e6de-eb6f-4ea5-aec8-49dcc091f1f7)
### Images

### Reflection
This was a practically effortless code, you gave me the code in the beggining, and all I had to do was figure it out on the Bread Board. I learned that a lot of the time, its ok to use others code (If you cite them), because I guess that normal in Engineering.

## HelloFunctions

### Description & Code
So this code connects a motion sensor with a tiny motor, so that whenever the motion sensor sense motion, the little motor will move a wheel.

```C++
include <LiquidCrystal.h> //Load Liquid Crystal Library
LiquidCrystal LCD(7, 8, 9, 10, 11, 12); //Create Liquid Crystal Object called LCD
int trigPin=2; //Sensor Trip pin connected to Arduino pin 2
int echoPin=3; //Sensor Echo pin connected to Arduino pin 3
int myCounter=0; //declare your variable myCounter and set to 0
float pingTime; //time for ping to travel from sensor to target and return
float targetDistance; //Distance to Target in inches
float speedOfSound=776.5; //Speed of sound in miles per hour when temp is 77 degrees.
void setup() {

Serial.begin(9600);
pinMode(trigPin, OUTPUT);
pinMode(echoPin, INPUT);
LCD.begin(16,2); //Tell Arduino to start your 16 column 2 row LCD
LCD.setCursor(0,0); //Set LCD cursor to upper left corner, column 0, row 0
LCD.print("Target Distance:"); //Print Message on First Row
}
void loop() {

 digitalWrite(trigPin, LOW); //Set trigger pin low
 delayMicroseconds(2000); //Let signal settle
 digitalWrite(trigPin, HIGH); //Set trigPin high
 delayMicroseconds(15); //Delay in high state
 digitalWrite(trigPin, LOW); //ping has now been sent
 delayMicroseconds(10); //Delay in high state

 pingTime = pulseIn(echoPin, HIGH); //pingTime is presented in microceconds
 pingTime=pingTime/1000000; //convert pingTime to seconds by dividing by 1000000 (microseconds in a second)
 pingTime=pingTime/3600; //convert pingtime to hourse by dividing by 3600 (seconds in an hour)
 targetDistance= speedOfSound * pingTime; //This will be in miles, since speed of sound was miles per hour
 targetDistance=targetDistance/2; //Remember ping travels to target and back from target, so you must divide by
 targetDistance= targetDistance*63360; //Convert miles to inches by multipling by 63360 (inches per mile)

 LCD.setCursor(0,1); //Set cursor to first column of second row
 LCD.print(" "); //Print blanks to clear the row
 LCD.setCursor(0,1); //Set Cursor again to first column of second row
 LCD.print(targetDistance); //Print measured distance
 LCD.print(" inches"); //Print your units.
 delay(250); //pause to let things settle

```
The way this Little doohichey works, is that when the motion sensor senses something, It will start to move the wheel, that specific distance that the object is.
Its pretty cool!

### Evidence
[Evidence](https://create.arduino.cc/editor/Ben_Berthy123/878b9368-c8a6-42b4-8ae0-eeb4f6d408a1)

### Images
draw it yourself, take a picture, make a fritzing, whatever you want to EFFECTIVELY communicate how its put together.
DO THIS
### Reflection
This code was particularly challenging for me, I needed a lot fo help from the internat, and I had to remake it a couple times to get it correct. What i learned was that sometimes you have to keep trying to succeed.

## NewPing

### Description & Code
Description goes here

Here's how you make code look like code:

```C++
Code goes here
```
Talk about how the code works, here....

### Evidence
link goes here

### Images
draw it yourself, take a picture, make a fritzing, whatever you want to EFFECTIVELY communicate how its put together.

### Reflection

