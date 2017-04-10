# Serial Port

Working with Arduino and p5js:

## STEPS:
1. Upload Arduino Code and check if it works
2. Close Serial Port
3. Open p5.serialcontrol
4. Brackets Run Code

### Arduino:
```
String inputString = "";         // a string to hold incoming data
boolean stringComplete = false;  // whether the string is complete

#define ledPin1 12
#define ledPin 13

void setup() {
  // initialize serial:
  Serial.begin(9600);
  // reserve 200 bytes for the inputString:
  inputString.reserve(200);
  pinMode(ledPin, OUTPUT);
  pinMode(ledPin1, OUTPUT);
}

void loop() {
  // print the string when a newline arrives:
  if (stringComplete) {
    //Serial.println(inputString);
    ledState(inputString);
    // clear the string:
    inputString = "";
    stringComplete = false;
  }
}

/*
  SerialEvent occurs whenever a new data comes in the
 hardware serial RX.  This routine is run between each
 time loop() runs, so using delay inside loop can delay
 response.  Multiple bytes of data may be available.
 */
void serialEvent() {
  while (Serial.available()) {
    // get the new byte:
    char inChar = (char)Serial.read();
    // add it to the inputString:
    //inputString += inChar;


    if (inChar != '\n') {
      inputString += inChar;
    }

    // if the incoming character is a newline, set a flag
    // so the main loop can do something about it:
    if (inChar == '\n') {
      stringComplete = true;
    }
  }
  Serial.println(inputString);
}

void ledState(String inputData) {
  //Serial.print(inputData);
  if (inputData.equals("high")) {
    digitalWrite(ledPin, HIGH);
    digitalWrite(ledPin1, LOW);
  }

  if (inputData.equals("low")) {
    digitalWrite(ledPin, LOW);
    digitalWrite(ledPin1, HIGH);
  }
}
```

### HTML
```
<html>
<head>
  <meta charset="UTF-8">
  <script language="javascript" type="text/javascript" src="libraries/p5.js"></script>
  <!-- uncomment lines below to include extra p5 libraries -->
  <!--<script language="javascript" src="libraries/p5.dom.js"></script>-->
  <!--<script language="javascript" src="libraries/p5.sound.js"></script>-->
     <script language="javascript" src="libraries/p5.serialport.js"></script>
  <script language="javascript" type="text/javascript" src="sketch.js"></script>
  <!-- this line removes any default padding and style. you might only need one of these values set. -->
  <style> body {padding: 0; margin: 0;} </style>
</head>

<body>
</body>
</html>
```

### P5js
```
/*
Serial write example
Sends a byte to a webSocket server which sends the same byte
out through a serial port.
You can use this with the included Arduino example called PhysicalPixel.
Works with P5 editor as the socket/serial server, version 0.5.5 or later.
written 2 Oct 2015
by Tom Igoe
*/

// Declare a "SerialPort" object
var serial;
// fill in the name of your serial port here:
var portName = "/dev/cu.usbmodemFA131";
// this is the message that will be sent to the Arduino:
var outMessage = 'high\n';

function setup() {
    createCanvas(windowWidth, windowHeight);

    // make an instance of the SerialPort object
    serial = new p5.SerialPort();

    // Get a list the ports available
    // You should have a callback defined to see the results. See gotList, below:
    serial.list();

    // Assuming our Arduino is connected,  open the connection to it
    serial.open(portName);

    // When you get a list of serial ports that are available
    serial.on('list', gotList);

    // When you some data from the serial port
    serial.on('data', gotData);
}


// Got the list of ports
function gotList(thelist) {
    console.log("List of Serial Ports:");
    // theList is an array of their names
    for (var i = 0; i < thelist.length; i++) {
        // Display in the console
        console.log(i + " " + thelist[i]);
    }
}

// Called when there is data available from the serial port
function gotData() {
    var currentString = serial.readLine();
    console.log(currentString);
}

function draw() {
    background(255, 255, 255);
    fill(0, 0, 0);
    text("click to change the LED", 10, 10);
}
// When you click on the screen, the server sends H or L out the serial port
function mouseReleased() {
    serial.write(outMessage);
    if (outMessage == 'high\n') {
        outMessage = 'low\n';
    } else {
        outMessage = 'high\n';
    }
}
```

![Serial Port Inline](https://github.com/linaangel/PhComp_repo/blob/master/week11/serialport.png)
![Serial Control](https://github.com/linaangel/PhComp_repo/blob/master/week11/p5serialcontrol.png)
![Serial Port Video](https://github.com/linaangel/PhComp_repo/blob/master/week11/serial-LEDs.MOV)
