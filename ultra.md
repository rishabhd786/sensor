# SENSORS
## 1. HC-SR04 ULTRASONIC SENSOR
**Introduction**

In this tutorial we will learn how to use a HC-SR04 Ultrasonic Sensor.
The HC-SR04 ultrasonic sensor uses sonar to determine distance to an object like
bats do. It offers excellent non-contact range detection with high accuracy and stable
readings in an easy-to-use package. From 2 cm to 400 cm or 1” to 13 feet. It comes
complete with ultrasonic transmitter and receiver module.

![image](/ultra1.jpg)

Some features of this sensor are:

 Power Supply :+5V DC
 Quiescent Current : <2mA
 Working Current: 15mA
 Effectual Angle: <15°
 Ranging Distance : 2cm – 400 cm/1′′ – 13ft
 Resolution : 0.3 cm
 Measuring Angle: 30 degree
 Trigger Input Pulse width: 10uS
 Dimensions: 45mm x 20mm x 15mm

**Components**
- 1 * Arduino Uno board
- 1 * USB cable
- 1 * HC-SR04 Ultrasonic Sensor
- Jumper wires(Female to Male)

**Principles**

**Experimental Procedures**

**Step 1:**  Connect circuit as shown in the following photo:

![image](/ultra2.jpg)

Make the connections as follows:

![image](/ultra3.jpg)

**Step 2:**  Press Ctrl+Shift+I to go to the manage libraries section in your Arduino IDE.Then search for **NewPing** in the searchbox.
Install the **NewPing Library** along with all the dependecies from there:

![image](/ultra4.jpg)

**Step 3:**   Now paste the following code in your Arduino IDE:

**Code:-**

```

/*
* Posted on http://randomnerdtutorials.com
* created by http://playground.arduino.cc/Code/NewPing
*/
#include <NewPing.h>
#define TRIGGER_PIN 12
#define ECHO_PIN 11
#define MAX_DISTANCE 200
NewPing sonar(TRIGGER_PIN, ECHO_PIN, MAX_DISTANCE); // NewPing setup of pins and
maximum distance.
void setup() {
Serial.begin(9600);
}
void loop() {
delay(50);
unsigned int uS = sonar.ping_cm();
Serial.print(uS);
Serial.println(‘‘cm’’);
}

```

You can also use the following code if you don't want to use the library:

**Code:-**

```
int trigPin = 11;
int echoPin = 12;
long duration, cm, inches;
void setup() {
//Serial Port begin
Serial.begin (9600);
//Define inputs and outputs
pinMode(trigPin, OUTPUT);
pinMode(echoPin, INPUT);
}
void loop()
{
// The sensor is triggered by a HIGH pulse of 10 or more microseconds.
// Give a short LOW pulse beforehand to ensure a clean HIGH pulse:
digitalWrite(trigPin, LOW);
delayMicroseconds(5);
digitalWrite(trigPin, HIGH);
delayMicroseconds(10);
digitalWrite(trigPin, LOW);
// Read the signal from the sensor: a HIGH pulse whose
// duration is the time (in microseconds) from the sending
// of the ping to the reception of its echo off of an object.
pinMode(echoPin, INPUT);
duration = pulseIn(echoPin, HIGH);
// convert the time into a distance
cm = (duration/2) / 29.1;
inches = (duration/2) / 74;
Serial.print(inches);
Serial.print("in, ");
Serial.print(cm);
Serial.print("cm");
Serial.println();
delay(250);
}

```

**Step 4:**  Now compile the program by clicking on the **Verify** button or by pressing **Ctrl+R**.

**Step 5:**  Now upload the program on you Arduino Board by clicking on the **Upload** button or by pressing **Ctrl+U**.

![image](/dhtsave.jpg)

**Step 6:**  Open the **tools-->Serial Monitor**, then you can see the distance readings.

![image](/ultra5.jpg)
