# Anosmic Alert :nose::warning:
![Anosmic Alert](https://github.com/linaangel/PhComp_repo/blob/master/AnosmicAlert/anosmicalert.jpg)
![Anosmic Alert](https://github.com/linaangel/PhComp_repo/blob/master/AnosmicAlert/components.png)
[Watch the Video](https://youtu.be/47clf0O71S8)
[More Videos of the process](https://www.youtube.com/playlist?list=PLgJFES56l4U2Ey4vrSF77-NlKw0PBJkjE)

As you already know, there are blind people, depth people, but there's also Anosmic people, like me! This means I can't smell at all... Yes, anything! It's good when you never had that sense, as David Eaglemen says in his TED talk is all about your "umwelt" ([Here is the TEDTalk](https://www.ted.com/talks/david_eagleman_can_we_create_new_senses_for_humans) in case you want to understand what I'm talking about!)

To create a electronic "Nose" you first need to understand the sense of smell, here is a pdf with useful info: [The Smell Report by Kate Fox](https://github.com/linaangel/PhComp_repo/blob/master/midterm/smell.pdf). Also, here is a link to smell disorders: [Smell Disorders](https://www.nidcd.nih.gov/health/smell-disorders)

I thought it was very useful to have an "Anosmic Alert", I know there are some e-noses and other projects similar, but nothing with those main odors that you need to smell to be alerted and avoid danger. Here is what I've learn from the experience, I really found important to know:

* When there's an scape of Natural gas (Methane)
* When something is burning (Smoke)
* When your niece is a baby or you have one, and you're supposed to change the diapers before it’s too late and you can't smell to know if she/he Pee or Poop:poop:.

Anosmic Alert is a device that activates a sound alarm, turns On different colors LEDs when some of these things happen. 

## Visual Cues
* Green LED = Poo
* Yellow LED = Pee
* Red LED = Smoke
* Blue LED = Natural Gas

## Components
* Arduino UNO and Nano
* MQ4 Methane Sensor
* MQ2 Smoke Sensor
* Gas Breakout
* Soil Moisture Sensor
* Jumper Wires 
* 4 LEDs: 1 Red, 1 Blue, 1 Green and 1 Yellow
* 1 Piezo buzzer
* 1 Potentiometer
* 1 Liquid Cristal Display
* Switches
* Resistors 220Ω and 10kΩ

#### Arduino Nano
![Arduino Nano](https://github.com/linaangel/PhComp_repo/blob/master/AnosmicAlert/nano.jpg) 
[Here is the link](https://www.amazon.com/gp/product/B00Q9YBO88/ref=oh_aui_detailpage_o06_s00?ie=UTF8&psc=1)

### Gas or Poop :poop:
#### Gas Breakout 
![Gas Breakout](https://github.com/linaangel/PhComp_repo/blob/master/AnosmicAlert/gasbreakout.jpg) 
[Here is the link](https://www.sparkfun.com/products/8891)

#### Methane Sensor
![Methane Sensor](https://github.com/linaangel/PhComp_repo/blob/master/AnosmicAlert/methanesensor.jpg) 
[Here is the link](https://www.sparkfun.com/products/9404)

### Something is Burning
#### Smoke Sensor 
![Smoke Sensor](https://github.com/linaangel/PhComp_repo/blob/master/AnosmicAlert/smoke.jpg) 
[Here is the link](https://www.amazon.com/gp/product/B01F2X3VY6/ref=oh_aui_detailpage_o02_s00?ie=UTF8&psc=1)

### Pee
#### Soil Moisture Sensor
![Soil Moisture Sensor](https://github.com/linaangel/PhComp_repo/blob/master/AnosmicAlert/humiditysensor.jpg) 
[Here is the link](https://www.sparkfun.com/products/13322)

### Other
![Jumper Wire](https://github.com/linaangel/PhComp_repo/blob/master/AnosmicAlert/jumperwire.jpg) 
[Here is the link](https://www.amazon.com/gp/product/B01LZF1ZSZ/ref=oh_aui_detailpage_o00_s00?ie=UTF8&psc=1)

## Code Plan
### Sound Alert: 
* Piezo beeps if any sensors detects pee, poo, smoke or methane in the air.
(Critical Presence of the smell - chemical)
* Green LED On: Threshold 50
* Yellow LED On: Threshold 5
* Red LED On: Threshold 300
* Blue LED On: Threshold 100

### Light Alert:
Light tunrs ON/OFF if the smell is present.
* Blue LED On: Natural Gas/Methane smell is present
* Red LED On: Smoke/Burning smell is present
* Yellow LED On: Pee smell is present
* Green LED On:  Poo smell is present

### Visual Alert:
Liquid Cristal Display with messages:
"Smells like: ....."
* Gas: Methane is present
* Smoke: Something is burning
* Pee: Humidity sensor detects something liquid
* Poo: Methane is present


### Switches
Turn off a sound when you’re controlling it

## Code
```
// include LCD library code:
#include <LiquidCrystal.h>

// Turn off LED/Piezo Alert
#define switch0 1

int buzzer = 13;

// Blue smells like Gas
#define ledBlue 6
// Red smells like Smoke
#define ledRed 7
// Yellow smells like Pee
#define ledYellow 8
// Green smells like Poo
#define ledGreen 9

// set up Smoke Sensor
int sensorPin = A5;
// set up Pee Sensor
int sensorPeePin = A0;

// LCD initialize numbers of the interface pins
LiquidCrystal lcd(12, 11, 5, 4, 3, 2);

// a variable to choose which alert from the Anosmic Alert
int sensorThres = 300;
int sensorPeeThres = 5;

void setup() {
// set up serial port
Serial.begin(9600);

// Buzzer
  pinMode (buzzer, OUTPUT);

// Switch
  pinMode (switch0, INPUT);

// LEDs Mode
  pinMode (ledGreen, OUTPUT);
  pinMode (ledYellow, OUTPUT);
  pinMode (ledRed, OUTPUT);
  pinMode (ledBlue, OUTPUT);
  
// set up the sensor Smoke pin as an input
  pinMode(sensorPin, INPUT);
// set up the sensor Pee pin as an input
  pinMode(sensorPeePin, INPUT);

// set up the number of columns and rows on the LCD
  lcd.begin(16, 2);
  lcd.setCursor(0, 0);
  lcd.print("Smells like:");
}

void loop() {
// Yellow Pee
  int sensorPeePinValue = analogRead(sensorPeePin);
  Serial.print("sensorPeePin Read: ");
  Serial.println(sensorPeePinValue);
// Red Smoke
  int sensorPinValue = analogRead(sensorPin);
  Serial.print("sensorPin Read: ");
  Serial.println(sensorPinValue);
 
// LEDs & Alert
if(sensorPinValue < sensorThres || sensorPeePinValue < sensorPeeThres) {
    lcd.setCursor(0, 1);
    lcd.print(".....");
    digitalWrite(ledGreen, LOW);
    digitalWrite(ledYellow, LOW);
    digitalWrite(ledRed, LOW);
    digitalWrite(ledBlue, LOW);
    noTone(buzzer);
  }

//Red LED ON = Something is burning
  if(sensorPinValue > sensorThres) {
    lcd.setCursor(0, 1);
    lcd.print("Smoke");
    digitalWrite(ledGreen, LOW);
    digitalWrite(ledYellow, LOW);
    digitalWrite(ledRed, HIGH);
    digitalWrite(ledBlue, LOW);
    tone(buzzer, 65000);
  }
// Yellow LED ON = smells like Pee
  if(sensorPeePinValue > sensorPeeThres) {
    lcd.setCursor(0, 1);
    lcd.print("Pee");
    digitalWrite(ledGreen, LOW);
    digitalWrite(ledYellow, HIGH);
    digitalWrite(ledRed, LOW);
    digitalWrite(ledBlue, LOW);
    tone(buzzer, 65000);
  }

// read the state of the switch:
    int switchState = digitalRead(switch0);
  
// Turn Off Alert Switch
// check if the pushbutton is pressed.
// if it is, the buttonState is HIGH:
if (switchState == HIGH) {  
    lcd.setCursor(0, 1);
    lcd.print(".....");
    noTone(buzzer);
    digitalWrite (ledGreen, LOW);
    digitalWrite (ledRed, LOW);
    digitalWrite (ledBlue, LOW);
    digitalWrite (ledYellow, LOW);
  }
}
```

## References
[Arduino MQ Gas Sensors](http://playground.arduino.cc/Main/MQGasSensors)

[Electronic Nose](https://en.wikipedia.org/wiki/Electronic_nose)

[Arduino Project - Electronic Nose](http://www.maskau.dk/projects/electronic-nose)

[Smell Disorder](https://www.nidcd.nih.gov/health/smell-disorders)

[Smoke Detection](http://www.explainthatstuff.com/smokedetector.html)

[Gas Sensors](http://playground.arduino.cc/Main/MQGasSensors)

[Arduino Step By Step](https://create.arduino.cc/projecthub/Aritro/smoke-detection-using-mq-2-gas-sensor-79c54a)

[More](https://github.com/linaangel/PhComp_repo/tree/master/AnosmicAlert/References)
