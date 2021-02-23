## Problem Statement
Use one master Arduino to control the blinking LED of the other slave Arduino using I2C communication protocol between the two.

### Circuit:

![diagram](https://github.com/Sarthak-22/Intro_to_Arduino_Workshop/blob/main/images/I2C%20Communication%20-%202%20Arduinos.png)

### Code:
* Master
  
```                                      
#include <Wire.h> // Include Arduino Wire library for I2C

#define SLAVE_ADDR 9 // Define Slave I2C Address
int analogPin = 0; // Analog pin for potentiometer
int val = 0; // Integer to hold potentiometer value
 
void setup() {
  Wire.begin(); // Initialize I2C communications as Master
}
 
void loop() {
  delay(50);   
  val = map(analogRead(analogPin), 0, 1023, 255, 1); // Read pot value & Map to range of 1-255 for flash rate                                            
  Wire.beginTransmission(SLAVE_ADDR); // Write a character to the Slave
  Wire.write(val);
  Wire.endTransmission();
 }
```
* Slave
```
#include <Wire.h>

#define SLAVE_ADDR 9 // Define Slave I2C Address
int LED = 13; // Define LED Pin
int rd; // Variable for received data
int br; // Variable for blink rate
 
void setup() {
  Serial.begin(9600);
  pinMode(LED, OUTPUT); 
  Wire.begin(9); // Initialize I2C communications as Slave
  Wire.onReceive(receiveEvent); // Function to run when data received from master
  Serial.println("I2C Slave Demonstration");
 }
  
void receiveEvent(int x) {
  rd = Wire.read();  // read one character from the I2C
  Serial.println(rd); // Print value of incoming data
  }

void loop() {
  delay(50);
  br = map(rd, 1, 255, 100, 2000);
  Serial.println(br);
  
  digitalWrite(LED, HIGH); // Blink the LED
  delay(br);
  digitalWrite(LED, LOW);
  delay(br);
 }
```

### TinkerCad circuit link:
[I2C communication between Arduinos](https://www.tinkercad.com/things/6JHjcf41PAh)
