# SENSORS
## 1. PIR MOTION SENSOR
**Introduction**

In this tutorial we will learn how to use a PIR Motion Sensor.
The PIR motion sensor is ideal to detect movement. PIR stand for “Passive
Infrared”. Basically, the PIR motion sensor measures infrared light from objects in its
field of view. So, it can detect motion based on changes in infrared light in the
environment. It is ideal to detect if a human has moved in or out of the sensor range.

![image](/pir1.jpg)

The sensor in the figure above has two built-in potentiometers to adjust the delay
time (the potentiometer at the left) and the sensitivity (the potentiometer at the right).

**Components**
- 1 * Arduino Uno board
- 1 * USB cable
- 1 * PIR motion sensor
- 2 * LED
- Jumper wires(Female to Male)

**Principles**

**Experimental Procedures**

**Step 1:**  Connect circuit as shown in the following photo:

![image](/pir2.jpg)

**Step 2:** Now paste the following code in your Arduino IDE:

**Code**:-

/*  
    Arduino with PIR motion sensor
    For complete project details, visit: http://RandomNerdTutorials.com/pirsensor
    Modified by Rui Santos based on PIR sensor by Limor Fried
*/
 
int led = 13;                // the pin that the LED is atteched to
int sensor = 2;              // the pin that the sensor is atteched to
int state = LOW;             // by default, no motion detected
int val = 0;                 // variable to store the sensor status (value)

void setup() {
  pinMode(led, OUTPUT);      // initalize LED as an output
  pinMode(sensor, INPUT);    // initialize sensor as an input
  Serial.begin(9600);        // initialize serial
}

void loop(){
  val = digitalRead(sensor);   // read sensor value
  if (val == HIGH) {           // check if the sensor is HIGH
    digitalWrite(led, HIGH);   // turn LED ON
    delay(100);                // delay 100 milliseconds 
    
    if (state == LOW) {
      Serial.println("Motion detected!"); 
      state = HIGH;       // update variable state to HIGH
    }
  } 
  else {
      digitalWrite(led, LOW); // turn LED OFF
      delay(200);             // delay 200 milliseconds 
      
      if (state == HIGH){
        Serial.println("Motion stopped!");
        state = LOW;       // update variable state to LOW
    }
  }
}



**Step 4:**  Now compile the program by clicking on the **Verify** button or by pressing **Ctrl+R**.

**Step 5:**  Now upload the program on you Arduino Board by clicking on the **Upload** button or by pressing **Ctrl+U**.

![image](/dhtsave.jpg)

**Step 6:**  Open the **tools-->Serial Monitor**, then you can see the sensor readings.

![image](/pir3.jpg)
