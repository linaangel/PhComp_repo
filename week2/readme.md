#LED On/Off :bulb:
##Project: LEDs On!

Here you can see pictures and a video of the Arduino and Breadboard connections to make 3 LEDs blink or stop in different ways!
LEDs On Video: [Click Here to watch it] (https://github.com/linaangel/PhComp_repo/blob/master/week2/LEDs.mov) or [Here] (http://www.youtube.com/watch?v=ppI1XlDYKcY&feature=youtu.be)

Code used to independently control each led with different behaviors:

```
void setup() {
  // initialize digital pin LED_BUILTIN as an output.
  pinMode(13, OUTPUT);
  pinMode(12, OUTPUT);
  pinMode(11, OUTPUT);
}

void loop() {
  digitalWrite(13, HIGH);   // LED connected to Digital Pin 13 stopped
  digitalWrite(12, HIGH);   // LED connected to Digital Pin 12 blinks every 300 milliseconds
  delay(300);                 
  digitalWrite(12, LOW);    
  delay(300);                 
  digitalWrite(11, HIGH);   // LED connected to Digital Pin 11 blinks every 500 milliseconds
  delay(500);                 
  digitalWrite(11, LOW);    
  delay(500);                 
}
```
![LEDs On Img 1] (https://github.com/linaangel/PhComp_repo/blob/master/week2/LEDs-1.jpg)
![LEDs On Img 1] (https://github.com/linaangel/PhComp_repo/blob/master/week2/LEDs-2.jpg)
LEDs On Video [Click Here] (https://github.com/linaangel/PhComp_repo/blob/master/week2/LEDs.mov) or [Here] (http://www.youtube.com/watch?v=ppI1XlDYKcY&feature=youtu.be)
