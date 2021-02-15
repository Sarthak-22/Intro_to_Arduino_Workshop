## Problem Statement
Attach a potentiometer at Arduino pin **A0** and get input values from it

### Circuit:

![diagram](https://github.com/Sarthak-22/Intro_to_Arduino_Workshop/blob/main/images/Get%20Input%20values%20from%20a%20potentiometer%20.png)

### Code:
```
int potpin=A0;
float readvalue;
float potvoltage;

void setup()
{
  Serial.begin(9600);
  pinMode(potpin,INPUT);
}

void loop()
{
  readvalue=analogRead(potpin);
  potvoltage=readvalue*5.0/1024.0;
  Serial.print("The potentiometer reading is - ");
  Serial.println(potvoltage);
  delay(250);
}
```

### Tinkercad Circuit link:
[Get input values from potentiometer](https://www.tinkercad.com/things/93cYnUubKCX)
