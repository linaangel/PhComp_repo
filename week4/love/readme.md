#L:heart:ve-O-Meter

Here you can see pictures and videos of the process of playing with the Arduino ONE project the Love-O-meter :heart: and Analog Readings. Uses a temperature sensor and 3 leds!

This was the code used to represent the sensors measurements in the LEDs:

```
const int meter = A0;
const float baselineTemp = 17;

void setup() {
  // put your setup code here, to run once:
  Serial.begin(9600);
  for (int pinNumber = 2; pinNumber<5; pinNumber++) {
    pinMode(pinNumber,OUTPUT);
    digitalWrite(pinNumber,LOW);
    }
}

void loop() {
  // put your main code here, to run repeatedly:
  int meterVal = analogRead(meter);
  Serial.print("Meter Value: ");
  Serial.print(meterVal);

  float voltage = (meterVal/1024.0) * 5.0;
  Serial.print(" , Volts: ");
  Serial.print(voltage);

  Serial.print(" , degrees C: ");
  float temperature = (voltage - 0.5) * 100;
  Serial.println(temperature);

  if(temperature<baselineTemp){
    digitalWrite(2, LOW);
    digitalWrite(3, LOW);
    digitalWrite(4, LOW);
    }else if(temperature >= baselineTemp+2 && temperature < baselineTemp+4){
    digitalWrite(2, HIGH);
    digitalWrite(3, LOW);
    digitalWrite(4, LOW);
    }else if(temperature >= baselineTemp+4 && temperature < baselineTemp+6){
    digitalWrite(2, HIGH);
    digitalWrite(3, HIGH);
    digitalWrite(4, LOW);}
    else if(temperature >= baselineTemp+6){
    digitalWrite(2, HIGH);
    digitalWrite(3, HIGH);
    digitalWrite(4, HIGH);
    }
    delay(1);
}
```
![Love-O-Meter Img 1] (https://github.com/linaangel/PhComp_repo/blob/master/week4/love/love1.jpg)
![Love-O-Meter Img 2] (https://github.com/linaangel/PhComp_repo/blob/master/week4/love/love2.png)
![Love-O-Meter Img 3] (https://github.com/linaangel/PhComp_repo/blob/master/week4/love/love3.jpg)
Love-O-Meter Video [Click Here] (https://github.com/linaangel/PhComp_repo/blob/master/week4/love.mp4) or [Here] (http://www.youtube.com/watch?v=FX7ud8F0Ick&feature=youtu.be)

[More Images & Videos] (https://github.com/linaangel/PhComp_repo/blob/master/week4/love/more/)
