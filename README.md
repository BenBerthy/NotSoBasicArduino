# NotSoBasicArduino
 The follwing files are my second foray into Arduino
 
 
## Table of Contents
* [Table of Contents](#TableOfContents)
* [LED_Fade](#LED_Fade)
* [HelloFunctions](#HelloFunctions)
* [NewPing](#NewPing)
---


## LED Blink Revisited

### Description & Code
This code is as simple as it gets, its just a LED blinking.

```C++
void setup() {
  // initialize digital pin LED_BUILTIN as an output.
  pinMode(LED_BUILTIN, OUTPUT);
}

// the loop function runs over and over again forever
void loop() {
  digitalWrite(LED_BUILTIN, HIGH);   // turn the LED on (HIGH is the voltage level)
  delay(1000);                       // wait for a second
  digitalWrite(LED_BUILTIN, LOW);    // turn the LED off by making the voltage LOW
  delay(1000);                       // wait for a second
}
```

### Evidence
[Evidence](https://create.arduino.cc/editor/Ben_Berthy123/7d987f93-11e8-482f-a7b8-852e78559434)
### Images
![Screenshot 2021-01-30 at 12 45 39 AM](https://user-images.githubusercontent.com/71345176/106348468-7dc9ef80-6294-11eb-83b1-606679f40811.png)
### Reflection
This was the easiest part of this entire day. I would say that I learned what both void Setup and void loop do.


## Finite LED Blinker

### Description & Code
This is practically the same as the previous assignment, but this time it only blinks 5 times.
```C++

void loop()
{


  //
}

void blinkyBlinky(int repeats, int time)
{
  for (int i = 0; i < repeats; i++)
  {
    digitalWrite(Counter, HIGH);
    delay(time);
    digitalWrite(Counter, LOW);
    delay(time);
  }
}
```
The way this works is by making the arduino boad count up to a specific number.

### Evidence
[Evidence](https://create.arduino.cc/editor/Ben_Berthy123/5d1992cf-db73-47a7-a438-b912e7e48087)
### Images
![Screenshot 2021-01-30 at 12 43 24 AM](https://user-images.githubusercontent.com/71345176/106348420-2d529200-6294-11eb-834c-b7d1e7011184.png)

### Reflection
I learnt about using proper variables for my code lines. I also found out how Conditional Operaters function.
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
![Screenshot 2021-01-30 at 12 46 55 AM](https://user-images.githubusercontent.com/71345176/106348500-b4a00580-6294-11eb-96e8-175c73f023b9.png)
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
![Screenshot 2021-01-30 at 12 40 46 AM](https://user-images.githubusercontent.com/71345176/106348381-d8168080-6293-11eb-9d4c-242904ca4c1e.png)
### Reflection
This code was particularly challenging for me, I needed a lot fo help from the internat, and I had to remake it a couple times to get it correct. What i learned was that sometimes you have to keep trying to succeed.


## Photoresistors

### Description & Code
Using a photo resistor, I was able to make a light turn on when things got dark. So basically if I swipe my hand over the Photoresistor, the light would flicker.

```C++

const int sensorPin = 0;
const int ledPin = 9;

// We'll also set up some global variables for the light level a calibration value and
//and a raw light value
int lightCal;
int lightVal;


void setup()
{
  // We'll set up the LED pin to be an output.
  pinMode(ledPin, OUTPUT);
  lightCal = analogRead(sensorPin);
  //we will take a single reading from the light sensor and store it in the lightCal
  //variable. This will give us a prelinary value to compare against in the loop
}


void loop()
{
  //Take a reading using analogRead() on sensor pin and store it in lightVal
  lightVal = analogRead(sensorPin);


  //if lightVal is less than our initial reading (lightCal) minus 50 it is dark and
  //turn pin 9 HIGH. The (-50) part of the statement sets the sensitivity. The smaller
  //the number the more sensitive the circuit will be to variances in light.
  if (lightVal < lightCal - 50)
  {
    digitalWrite(9, HIGH);
  }

  //else, it is bright, turn pin 9 LOW
  else
  {
    digitalWrite(9, LOW);
  }
  {
```

So this thing works, by the photoresistor recording a specific lightness/darkness, and if it passes that specific limit, then the light flickers.
### Evidence
[Evidence}(https://create.arduino.cc/editor/Ben_Berthy123/2d8eb21d-1829-4dda-91be-9dffe4100d68)

### Images
![Screenshot 2021-01-30 at 12 34 02 AM](https://user-images.githubusercontent.com/71345176/106348267-f0d26680-6292-11eb-8a7d-e2e6758e1415.png)

### Reflection
I learned about finding and recording light Value. As complicated as it may seem, it was not as difficult as I expected.
