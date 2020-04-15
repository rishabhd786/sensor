# SENSORS
## 1. MQ2 SMOKE SENSOR
**Introduction**

This guide shows how to build a smoke detector that beeps when it detects
flammable gas or smoke. The MQ-2 smoke sensor is shown in the following figure:

![image](/smoke1.jpg)

The MQ-2 smoke sensor is sensitive to smoke and to the following flammable gases:
LPG, butane, propane, methane, alcohol and hydrogen. The resistance across the
sensor is different depending on the type of the gas. The smoke sensor has a built-
in potentiometer that allows you to adjust the sensor digital output (D0) threshold.
This threshold sets the value above which the digital pin will output a HIGH signal.

![image](/smoke2.jpg)


**Components**
- 1 * Arduino Uno board
- 1 * USB cable
- 1 * MQ2 Smoke Sensor
- 2 * LED
- 1 * Piezo Buzzer
- 3 * 220 Kilo Ohm Resistor
- Jumper wires(Female to Male)

**Principles**

**Experimental Procedures**

**Step 1:**  Connect circuit as shown in the following photo:

![image](/smoke3.jpg)

**Step 2:** Now paste the following code in your Arduino IDE:

**Code**:-
```
int redLed = 12;
int greenLed = 11;
int buzzer = 10;
int smokeA0 = A5;
// Your threshold value
int sensorThres = 400;
void setup() {
pinMode(redLed, OUTPUT);
pinMode(greenLed, OUTPUT);
pinMode(buzzer, OUTPUT);
pinMode(smokeA0, INPUT);
Serial.begin(9600);
}
void loop() {
int analogSensor = analogRead(smokeA0);
Serial.print("Pin A0: ");
Serial.println(analogSensor);
// Checks if it has reached the threshold value
if (analogSensor > sensorThres)
{
digitalWrite(redLed, HIGH);
digitalWrite(greenLed, LOW);
tone(buzzer, 1000, 200);
}
else
{
digitalWrite(redLed, LOW);
digitalWrite(greenLed, HIGH);
noTone(buzzer);
}
delay(100);
}
```


**Step 4:**  Now compile the program by clicking on the **Verify** button or by pressing **Ctrl+R**.

**Step 5:**  Now upload the program on you Arduino Board by clicking on the **Upload** button or by pressing **Ctrl+U**.

![image](/dhtsave.jpg)

When you press a lighter next to the sensor, the red LED lights up and the buzzer
beeps. You can also see at the serial monitor, the values changing and surpassing
the threshold value.

**Step 6:**  Open the **tools-->Serial Monitor**, then you can see the sensor readings.

![image](/smoke4.jpg)
