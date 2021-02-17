## Problem Statement
Use a photoresistor at analog pin A0 to control the brightness of LED at pin 6

### Circuit:

![diagram](https://github.com/Sarthak-22/Intro_to_Arduino_Workshop/blob/main/images/Photoresistor%20to%20control%20the%20brightness%20of%20LED.png)

### Code:
```
int ledpin=6; //For AnalogWrite
int ldrpin=A0; //For AnalogRead
float readvalue;
float ledvalue;	
void setup()
{
  Serial.begin(9600);
  pinMode(ledpin,OUTPUT);
  pinMode(ldrpin,INPUT);
}

void loop()
{
  readvalue=analogRead(ldrpin);
  Serial.println(readvalue);//For the given arrangement, the resistance of ldr ranges from 54-974
  ledvalue=(255.0/(974.0-54.0))*(readvalue-54.0);// in this step, we map the range of values of photoresistor from 54-974 to 0-255.
  analogWrite(ledpin,ledvalue);//Depending on the the value of photoresitor, the corresponding mapped value b/w 0-255 is given as the input to the led
}
```

### TinkerCad circuit link:
[Use a photoresistor to control the brightness of LED](https://www.tinkercad.com/things/0CITZmFLQnr)
