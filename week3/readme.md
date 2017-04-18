# Two LEDs On/Off with Switches :bulb:
## ColorPath

Here you can see pictures and videos of the process of making the LEDs turn On/Off with switches. Also, the Arduino and Breadboard connections. ColorPath is a prototype of an application of the two LEDs/Switches in a game:
Click the red switch to turn left, the green to turn right. The beetle moves straight until it finds arrows for you to decide the path.

This was the code used to independently control each led with different behaviors:

```
#define led 12
#define led2 13
#define switch0 2
#define switch1 3

int switchState = 0;
int switchState2 = 0;


void setup() {
  // put your setup code here, to run once:
 Serial.begin(9600);
 
 pinMode (led, OUTPUT);
 pinMode (switch0, INPUT);
 pinMode (led2, OUTPUT);
 pinMode (switch1, INPUT);
}

void loop() {
  // put your main code here, to run repeatedly:
 digitalWrite (led, switchState);
 digitalWrite (led2, switchState2);

 switchState = digitalRead(switch0);
 Serial.print("switchState: ");
 Serial.println(switchState);
 switchState2 = digitalRead(switch1);
 Serial.print("switchState2: ");
 Serial.println(switchState2);
}

```
![LEDs-Swtich On/Off Img 1](https://github.com/linaangel/PhComp_repo/blob/master/week3/2Led-Switches.jpg)
![Prototype 1](https://github.com/linaangel/PhComp_repo/blob/master/week3/Prototype1.jpg)
![Prototype 1](https://github.com/linaangel/PhComp_repo/blob/master/week3/Prototype2.jpg)
Switches-LEDs Video [Click Here](https://github.com/linaangel/PhComp_repo/blob/master/week3/2Leds-Switches.MOV)
Color Path Video [Click Here](https://github.com/linaangel/PhComp_repo/blob/master/week3/colorpath.mov) or [Here](http://www.youtube.com/watch?v=GkINUBpN9Ww&feature=youtu.be)
