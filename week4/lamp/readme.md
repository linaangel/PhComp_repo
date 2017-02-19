#Color Mixing Lamp :bulb: :red_circle: :tennis: :large_blue_circle:

Here you can see pictures and videos of the process of playing with the Arduino ONE project the Color Mixing Lamp and Analog Readings. Uses a Cathode RGB LED, Photosensors with Red, Green and Blue Gels!

This was the code used to read the Photosensors Values and represent them in the color of the RGB LED:

```
const int green = 9;
const int blue = 10;
const int red = 11;

const int redMeter = A0;
const int greenMeter = A1;
const int blueMeter = A2;

int redValue = 0;
int greenValue = 0;
int blueValue = 0;

int redMeterValue = 0;
int greenMeterValue = 0;
int blueMeterValue = 0;

void setup() {
  // put your setup code here, to run once:
 Serial.begin(9600);

 pinMode(green, OUTPUT);
 pinMode(blue, OUTPUT);
 pinMode(red, OUTPUT);
}

void loop() {
  // put your main code here, to run repeatedly:
  redMeterValue = analogRead(redMeter);
  delay(5);
  blueMeterValue = analogRead(blueMeter);
  delay(5);
  greenMeterValue = analogRead(greenMeter);

  Serial.print("Raw Sensor Values \t Red: ");
  Serial.print(redMeterValue);
  Serial.print("\t Green: ");
  Serial.print(greenMeterValue);
  Serial.print("\t Blue: ");
  Serial.println(blueMeterValue);

  redValue = redMeterValue/4;
  greenValue = greenMeterValue/4;
  blueValue = blueMeterValue/4;

  Serial.print("Mapped Sensor Values \t Red: ");
  Serial.print(redValue);
  Serial.print("\t Green: ");
  Serial.print(greenValue);
  Serial.print("\t Blue: ");
  Serial.println(blueValue);

  analogWrite(red, redValue);
  analogWrite(blue, blueValue);
  analogWrite(green, greenValue);
}
```
![Color Mixing Lamp Img 1] (https://github.com/linaangel/PhComp_repo/blob/master/week4/lamp/lamp1.jpg)
![Color Mixing Lamp Img 2] (https://github.com/linaangel/PhComp_repo/blob/master/week4/lamp/lamp2.jpg)
![Color Mixing Lamp Img 3] (https://github.com/linaangel/PhComp_repo/blob/master/week4/lamp/lamp3.jpg)
Color Mixing Lamp Video [Click Here] (https://github.com/linaangel/PhComp_repo/blob/master/week4/lamp/lamp.MOV) or [Here] (http://www.youtube.com/watch?v=)

[More] (https://github.com/linaangel/PhComp_repo/tree/master/week4/lamp/more)
