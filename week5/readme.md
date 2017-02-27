#Six Seconds Digital Hourglass (based on Arduino UNO digital hourglass :hourglass:):watch:

Based on the Arduino UNO project number 8: Digital Hour Glass, I edited the code and 6 leds indicates each second until it reaches 6 seconds and starts again.

Here you can see pictures and videos of the process first with the original code from the book, and then adding some lines to make the LEDs restart without moving the tilt sensor. Uses Six LEDs, Six 220 Ohms resistors, 10 kOhms resistor and a Tilt sensor. The code is based in Millis() the variable to track time in milliseconds!

This was the code used based on the book with some variations for Serial Port reading and Printing:

```
const int tiltSwitch = 8;
unsigned long previousTime = 0;
int tiltState = 0;
int prevTiltState = 0;
int led = 2;
long onesec = 1000;

void setup() {
  // put your setup code here, to run once:
  Serial.begin(9600);
  for(int x = 2;x<8;x++){
    pinMode(x,OUTPUT);
    }

  pinMode(tiltSwitch, INPUT);
}

void loop() {
  // put your main code here, to run repeatedly:
  unsigned long currentTime = millis();

  if(currentTime - previousTime > onesec){
    previousTime = currentTime;
    Serial.print("Current Time: ");
    Serial.println(currentTime);
    digitalWrite(led, HIGH);
    led++;
    if(led == 9){
      prevTiltState = 0;
      }
    }

  tiltState = digitalRead(tiltSwitch);
  if(tiltState != prevTiltState){
    for(int x = 2;x<8;x++){
    digitalWrite(x, LOW);
    }
    led = 2;
    previousTime = currentTime;
    }
    prevTiltState = tiltState;
}
```
After getting it to work, I restart the LEDs with this 3 lines of code:
```
if(led == 9){
prevTiltState = 0;
      }
```

![Six Seconds Digital Hourglass Img 1] (https://github.com/linaangel/PhComp_repo/blob/master/week5/six1.jpg)
![Six Seconds Digital Hourglass Img 2] (https://github.com/linaangel/PhComp_repo/blob/master/week5/six2.jpg)
![Six Seconds Digital Hourglass Img 3] (https://github.com/linaangel/PhComp_repo/blob/master/week5/six3.jpg)

Six Seconds Digital Hourglass Video [Click Here] (https://github.com/linaangel/PhComp_repo/blob/master/week5/six1.MOV) or [Here] (https://www.youtube.com/watch?v=uGtutbs9LJE&feature=youtu.be)

Restarting LEDs without sensor - Six Seconds Digital Hourglass Video [Click Here] (https://github.com/linaangel/PhComp_repo/blob/master/week5/six2.MOV) or [Here] (https://www.youtube.com/watch?v=LZcFEmbMYnE&feature=youtu.be)

[More] (https://github.com/linaangel/PhComp_repo/blob/master/week5/more/)
