## Problem Statemnent
Use a pushbutton at pin 12 to switch ON/OFF the LED at pin 13.

### Circuit:

![diagram](https://github.com/Sarthak-22/Intro_to_Arduino_Workshop/blob/main/images/Pushbutton%20to%20control%20the%20LED.png)

### Code:
```
int led = 13;
int button = 12;
int change = 1;
  

void setup()
{
  pinMode(led, OUTPUT);
  pinMode(button, INPUT_PULLUP);
}

void loop()
{
  change = digitalRead(button);
  digitalWrite(led, abs(change-1)); //abs is used for keeping the LED off initially
}
```

### TinkerCad Circuit link:
[Use a pushbutton to switch ON/OFF an LED](https://www.tinkercad.com/things/8sb5exAUvBH)
