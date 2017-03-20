# Anosmic Alert :nose::warning:
![Anosmic Alert](https://github.com/linaangel/PhComp_repo/blob/master/midterm/Anosmic-Alert/anosmicalert.jpg)

Using the Arduino UNO kit and some extra components I created an Anosmic Alert :nose::warning:

As you already know, there are blind people, depth people, but there's also Anosmic people, like me! This means I can't smell at all... Yes, anything! It's ok when you never had that sense, as David Eaglemen says in his TED talk is all about your "umwelt" [Here is the TEDTalk](https://www.ted.com/talks/david_eagleman_can_we_create_new_senses_for_humans) in case you want to understand what I'm talking about!

To create a electronic "Nose" you first need to understand the sense of smell, here is a pdf with useful info: [The Smell Report by Kate Fox](https://github.com/linaangel/PhComp_repo/blob/master/midterm/smell.pdf). Also, here is a link to smell disorders: [Smell Disorders](https://www.nidcd.nih.gov/health/smell-disorders)

As an Anosmic, I thought it was very useful to have an "Anosmic Alert", I know there are some e-noses and other projects similar, but nothing with those main odors that you need to smell to be alerted and avoid danger. Here is what I've learn from the experience, I really found important to know:

* When there's an scape of gas (In Colombia some people uses natural gas for the stove and to heat the water in the shower)
* When something is burning
* When your niece is a baby, and you're supposed to babysitt her, and you can't smell the diapers to know if she Pee or Poop:poop:.
* When the food is rotten 

Anosmic Alert activates a sound alarm, turns On different colors LEDs when some of these things happends. 

## Code Plan
* Green LED = Poo Smell
* Yellow LED = Pee Smell
* Red LED = Smoke Smell
* Blue LED = Gas Smell

## Components:
* 3D Printed Nose
* 4 Potentiometers (Simulation Chemical Sensors)
* 4 LEDs: 1 Red, 1 Blue, 1 Green and 1 Yellow
* 1 Piezo buzzer
* 4 Resistors 220 Omhs

![Dog Nose 3D Printing](https://github.com/linaangel/PhComp_repo/blob/master/midterm/Anosmic-Alert/3dnose.png)
 
### Sound Alert: 
* Piezo beeps if any of the 4 sensors value x > certain value (Presence of the smell - chemical)
* Green LED On: Frequency 15000
* Yellow LED On: Frequency  25000
* Red LED On: Frequency 45000
* Blue LED On: Frequency 65535

### Light Alert:
Light is proportional to the value. Minor presence of chemical, less light. Mayor presence of chemical, more light.
* Blue LED On: Natural Gas/Methane smell is present. 
* Red LED On: Smoke/Burning smell is present
* Yellow LED On: Pee smell is present
* Green LED On:  Poo smell is present

## Arduino Code
```
// Green smells like Poo
#define ledGreen 12
// Yellow smells like Pee
#define ledYellow 11
// Red smells like Smoke
#define ledRed 10
// Blue smells like Gas
#define ledBlue 9

void setup() {
  // put your setup code here, to run once:
  Serial.begin(9600);
  pinMode (ledGreen, OUTPUT);
  pinMode (ledYellow, OUTPUT);
  pinMode (ledRed, OUTPUT);
  pinMode (ledBlue, OUTPUT);
}

void loop() {
// put your main code here, to run repeatedly:
// Green smells like Poo
  int potGreenRead = analogRead(A0);
// Yellow smells like Pee
  int potYellowRead = analogRead(A1);
// Red smells like Smoke
  int potRedRead = analogRead(A4);
// Blue smells like Gas
  int potBlueRead = analogRead(A5);

// Green LED ON = smells like Poo
if(potGreenRead == 0 && potYellowRead == 0 && potRedRead == 0 && potBlueRead == 0) {
    digitalWrite(ledGreen, LOW);
    digitalWrite(ledYellow, LOW);
    digitalWrite(ledRed, LOW);
    digitalWrite(ledBlue, LOW);
    noTone(13);
  }
  if(potGreenRead == 1023) {
    digitalWrite(ledGreen, HIGH);
    digitalWrite(ledYellow, LOW);
    digitalWrite(ledRed, LOW);
    digitalWrite(ledBlue, LOW);
    tone(13,15000);
  }

// Yellow LED ON = smells like Pee
  if(potYellowRead == 1023) {
    digitalWrite(ledGreen, LOW);
    digitalWrite(ledYellow, HIGH);
    digitalWrite(ledRed, LOW);
    digitalWrite(ledBlue, LOW);
    tone(13,25000);
  }

// Red LED ON = smells like Smoke
  if(potRedRead == 1023) {
    digitalWrite(ledGreen, LOW);
    digitalWrite(ledYellow, LOW);
    digitalWrite(ledRed, HIGH);
    digitalWrite(ledBlue, LOW);
    tone(13,35000);
  }
// Blue LED ON = smells like Gas
  if(potBlueRead == 1023) {
    digitalWrite(ledGreen, LOW);
    digitalWrite(ledYellow, LOW);
    digitalWrite(ledRed, LOW);
    digitalWrite(ledBlue, HIGH);
    tone(13,65000);
  }
}
```

![Anosmic Alert Img 2](https://github.com/linaangel/PhComp_repo/blob/master/midterm/Anosmic-Alert/R2D2.jpg)
![Anosmic Alert Img 1](https://github.com/linaangel/PhComp_repo/blob/master/midterm/Anosmic-Alert/anosmicalert-dognose.jpg)
![Anosmic Alert Img 2](https://github.com/linaangel/PhComp_repo/blob/master/midterm/Anosmic-Alert/3DNose.jpg)
![Anosmic Alert Img 2](https://github.com/linaangel/PhComp_repo/blob/master/midterm/Anosmic-Alert/ArduinoNose.jpg)

Anosmic Alert Video [Click Here](https://github.com/linaangel/PhComp_repo/blob/master/midterm/Anosmic-Alert/more/IMG_3292.MOV) or [Here](https://www.youtube.com/watch?v=34q1Hhweqo8&feature=youtu.be)

[More](https://github.com/linaangel/PhComp_repo/tree/master/midterm/Anosmic-Alert/more)
