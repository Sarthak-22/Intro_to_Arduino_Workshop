## Problem Statement
Using 2 IR sensors/distance sensors to detect when a person is coming into/ going out of the range and use a LCD display to greet the person with a warm message. 

### Circuit:

![diagram](https://github.com/Sarthak-22/Intro_to_Arduino_Workshop/blob/main/images/Distance%20sensor%20with%20LCD.png)

### Code:
```
//LCD Pin   LCD PIN NAME  Arduino Pin
//1             VSS          GND
//2             VDD          5V
//3             V0           Pot Center Pin
//4             RS           10
//5             RW           GND
//6             E            9
//7             DB0          NOT CONNECTED
//8             DB1          NOT CONNECTED
//9             DB2          NOT CONNECTED
//10            DB3          NOT CONNECTED
//11            DB4          Pin 5
//12            DB5          Pin 4
//13            DB6          Pin 3
//14            DB7          Pin 2
//15            Backlight LED +V       5V
//16            Backlight LED GND      GND

#include <LiquidCrystal.h>
LiquidCrystal LCD(10,9,5,4,3,2); //Creating a LiquidCrystal object and denoting the position of pins 10,9,5,4,3,2
int trigpin=6;
int echopin=7;
float pingtime;
float distance;
float speedofsound=343; // in m/s

void setup() {
  LCD.begin(16,2); //Indicating the number of columns(16) and number of rows(2)
  //LCD.setCursor(0,0);
  //LCD.print("The distance is: ");
  pinMode(trigpin,OUTPUT);
  pinMode(echopin,INPUT);
}

void loop() 
{
  digitalWrite(trigpin,LOW);
  delay(2);
  digitalWrite(trigpin,HIGH);
  delayMicroseconds(15);
  digitalWrite(trigpin,LOW);

  pingtime=pulseIn(echopin,HIGH); // In microseconds
  distance=speedofsound*pingtime/10000.0;
  distance=distance/2.0;
  
  if(distance>=100)
  {
  LCD.setCursor(0,0);
  LCD.print("Goodbye");
  LCD.setCursor(0,1);
  LCD.print(distance);
  LCD.print(" cm");
  }
  
  if(distance<100)
  {
  LCD.setCursor(0,0);
  LCD.print("Welcome");
  LCD.setCursor(0,1);
  LCD.print(distance);
  LCD.print(" cm");
  } 
 delay(250);
}
```

### TinkerCad circuit link:
[Person greeter with Distance sensor and LCD](https://www.tinkercad.com/things/3XXEYwhCxr0)
