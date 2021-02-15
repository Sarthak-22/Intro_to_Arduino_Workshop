## Problem Statement
Blink an external LED at pin 12 in Arduino with a blinking rate of 1s 

### Circuit: 




### Code:
```
int ledpin=12;

void setup()
{
  pinMode(ledpin, OUTPUT);
}

void loop()
{
  digitalWrite(ledpin, HIGH);
  delay(1000); 
  digitalWrite(ledpin, LOW);
  delay(1000); 
}
```

### Tinkercad Circuit link:
 [Blink an external LED](https://www.tinkercad.com/things/fwv6FJvuFcV)
