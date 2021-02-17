## Problem Statement
Design a Gas sensor circuit using a Gas sensor at analog pin A0 to detect Gas leakage by using an alarm buzzer at pin 

### Circuit:

![diagram](https://github.com/Sarthak-22/Intro_to_Arduino_Workshop/blob/main/images/Gas%20Detector%20Circuit.png)

### Code:
```
int LEDpin=4;
int buzzerpin=6;
int sensorpin=A0;
int readvalue;
int sensorThresh = 150;

void setup()
{
  Serial.begin(9600);
  pinMode(LEDpin,OUTPUT);
  pinMode(sensorpin,INPUT);
  pinMode(buzzerpin,OUTPUT);
}

void loop()
{
  readvalue=analogRead(sensorpin);
  Serial.println(readvalue);
  if (readvalue>sensorThresh)
  {
    tone(buzzerpin,1000);
    digitalWrite(LEDpin,HIGH);
    delay(500); 
    digitalWrite(LEDpin,LOW);
    delay(500);
  }
  else
  {
    noTone(buzzerpin);
    digitalWrite(LEDpin,LOW);
  }
}
```

### TinkerCad Circuit link:
[Gas detector circuit](https://www.tinkercad.com/things/5zEUhuXfwQY)
