#LED On/Off
##LEDS On project!

Here you can see pictures of the Arduino and Breadboard connections and also some videos of the LEDs!

This was the code used to independently control each led with different behaviors:

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