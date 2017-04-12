# Anosmic Alert :nose::warning:
![Anosmic Alert](https://github.com/linaangel/PhComp_repo/blob/master/AnosmicAlert/anosmicalert.jpg)
![Anosmic Alert](https://github.com/linaangel/PhComp_repo/blob/master/AnosmicAlert/components.png)

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
* Arduino Nano
* MQ4 Methane Sensor
* MQ2 Smoke Sensor
* Gas Breakout
* Soil Moisture Sensor
* Jumper Wires 
* 4 LEDs: 1 Red, 1 Blue, 1 Green and 1 Yellow
* 1 Piezo buzzer
* Switches
* Resistors

### Arduino Nano
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
* Green LED On: Frequency 15000
* Yellow LED On: Frequency  25000
* Red LED On: Frequency 45000
* Blue LED On: Frequency 65000

### Light Alert:
Light fades according to the presence of the smell, is proportional to the value. Minor presence of chemical, less light. Mayor presence of chemical, more light.
* Blue LED On: Natural Gas/Methane smell is present. 
* Red LED On: Smoke/Burning smell is present
* Yellow LED On: Pee smell is present
* Green LED On:  Poo smell is present

### Switches
Turn off a sound when you’re controlling it
