## Problem Statement
Attach a servo motor at pin 11 and rotate it by using custom input values from the serial monitor

### Circuit:

![diagram](https://github.com/Sarthak-22/Intro_to_Arduino_Workshop/blob/main/images/Rotate%20a%20servo.png)

### Code:
```
#include <Servo.h>  //Including the Servo library 
int servopin=11;
int input=0;
int servodelay=25;

Servo mypointer; //Create an object for the Servo library 

void setup() 
{
  Serial.begin(9600);
  mypointer.attach(servopin);//Instructing the Arduino that the Servo object should operate at servopin=11
  mypointer.write(input);
}

void loop() 
{
 Serial.print("Enter an input(0-180) - ");
  while(Serial.available()==0)
  {}
  input=Serial.parseFloat();
  Serial.println(input);
  mypointer.write(input);
  delay(servodelay);
}
```

### TinkerCad circuit link:
[Rotating servo motor by custom input values](https://www.tinkercad.com/things/dOe1qM7TP2e)
