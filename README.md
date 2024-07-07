# Tools will be used to complete this task
####  Servo SG90 motor
####  TinkerCAD
- Breadboard
- Arduino

# Servo SG90 motor

The SG90 is a popular micro servo motor commonly used in robotics, electronics, and hobbyist projects.

<img src= "https://github.com/Layan002/Electrical-and-Electronics-Task1-Servo-motor-simulation/assets/107956591/3c55d9c9-6a00-4ec4-ba89-c57440088702" alt= "Servo" width= 200><br>

 Here are some key features and specifications of the SG90 servo motor:<br>

### Features: 
- Compact Size: The SG90 is small and lightweight, making it ideal for projects with space constraints.<br>
- Analog Control: It uses Pulse Width Modulation (PWM) to control its position.<br>
- Torque: It can provide sufficient torque for small-scale applications, typically around 1.8 kg·cm (at 4.8V).<br>
- Rotation Angle: It can rotate approximately 180 degrees (±90 degrees from the neutral position).<br>
- Plastic Gears: The gears are made of plastic, which makes it less durable than metal gear servos but also more affordable.<br>

### Specifications:
- Operating Voltage: 4.8V to 6V <br>
- Stall Torque: ~1.8 kg·cm (at 4.8V) <br>
- Operating Speed: ~0.1 sec/60 degrees (at 4.8V) <br>
- Dimensions: 22.2mm x 11.8mm x 31mm <br>
- Weight: ~9 grams <br>

### Applications: 
- Robotics: Used for controlling small robot arms, grippers, or pan-tilt mechanisms.<br>
- RC Models: Common in radio-controlled (RC) cars, boats, and airplanes for controlling steering, throttle, and other functions.<br>
- DIY Projects: Suitable for various hobby projects, including animatronics, automated systems, and educational kits.<br>

# TinkerCAD

Tinkercad is a free, online 3D design and modeling tool developed by Autodesk. It is designed to be accessible to beginners and is widely used for creating digital designs that can be turned into physical objects via 3D printing. Additionally, Tinkercad offers features for electronic circuit design and coding.<br>

<img src= "https://github.com/Layan002/Electrical-and-Electronics-Task1-Servo-motor-simulation/assets/107956591/753cae43-dd33-4554-a287-f918fca417dd" alt= "Servo" width= 500 > <br>

Here are the main applications of Tinkercad: 
### Applications:
- 3D Printing: Design models that can be exported and printed using a 3D printer.
- Prototyping: Quickly create and iterate on prototypes of designs.
- Education: Used in classrooms to teach students about 3D design, engineering, and electronics.
- Hobby Projects: Ideal for hobbyists working on DIY projects, such as model making and electronics.

### Breadboard
<img src= "https://github.com/Layan002/Electrical-and-Electronics-Task1-Servo-motor-simulation/assets/107956591/4a2e07b1-b471-441d-8815-5fd80056d750" alt= "Servo" width= 400 > <br>



### Arduino
<img src= "https://github.com/Layan002/Electrical-and-Electronics-Task1-Servo-motor-simulation/assets/107956591/b591c383-b39b-4e84-8fc5-0d54b5c485db" alt= "Servo" width= 400 > <br>




# Task Application
To apply this task, starting with the most basic fundamental application is very helpfull to understand both servo motor and TinkerCAD tools. 

## Single Servo motor
There are two type of servo motor usages: Sweep and Knop. Sweep doesn't contain potentiameters unlik Knop which contans them. Potentiameter is responsible about handle-controlling for the motors positions.

### Sweep
#### This part DOES NOT use a Potentiometer

We have three jumper-wires connected from the Servo motor to the Auirdoino: Power, Ground, and Signal. we connect the power to 5V (3.3V is not a good option), and the signal to any number in the side of PWM which stands for "Pulse Width Modulation". We use it because it provides a simple and efficient way to encode position information using a single digital signal.  <br>

#### Circuit Diagram
<img src= "https://github.com/Layan002/Electrical-and-Electronics-Task1-Servo-motor-simulation/assets/107956591/8ebe8a2f-a44c-4840-84ef-e5e505235871" alt= "Servo" width= 700><br>
#### Circuit Block-Code
<img src= "https://github.com/Layan002/Electrical-and-Electronics-Task1-Servo-motor-simulation/assets/107956591/4170cb03-a1a5-4915-a6bf-8758f870bc51" alt= "Servo" width= 400><br>
#### Circuit Code
``` CPP
// C++ code
//
#include <Servo.h>

int position = 0;

int i = 0;

int j = 0;

Servo servo_9;

void setup()
{
  servo_9.attach(9, 500, 2500);
}

void loop()
{
  position = 1;
  for (position = 1; position <= 170; position += 1) {
    servo_9.write(position);
    delay(20); // Wait for 20 millisecond(s)
  }
  for (position = 170; position >= 0; position -= 1) {
    servo_9.write(position);
    delay(20);
  }
}
```
You can notice that I've used the for loop to make the servo motor rotate. 

### Knop
#### This part uses a Potentiometer

#### Circuit Diagram
<img src= "https://github.com/Layan002/Electrical-and-Electronics-Task1-Servo-motor-simulation/assets/107956591/cb45c88a-be38-4f35-8a89-2e7e8d3c7882" alt= "Servo" width= 700><br>
#### Circuit Block-Code
<img src= "https://github.com/Layan002/Electrical-and-Electronics-Task1-Servo-motor-simulation/assets/107956591/abd76a20-952a-47aa-aa4b-597ae46513d2" alt= "Servo" width= 400><br>
#### Circuit Code
``` CPP
// C++ code
//
#include <Servo.h>

int outputValue = 0;

int sensorValue = 0;

Servo servo_9;

void setup()
{
  pinMode(A0, INPUT);
  servo_9.attach(9, 500, 2500);
}

void loop()
{
  sensorValue = analogRead(A0);
  outputValue = map(sensorValue, 0, 1023, 0, 180);
  servo_9.write(outputValue);
  delay(10); // Delay a little bit to improve simulation performance
}loading servo-and-potentio.ino…]()
```
You can notice here I didn't use the foor loop, because I have potentiometer. So, I've used maping to make the rotation degrees convert from the potentiometer’s full range (0 to 1023 degrees) to the servo’s range (0 to 180 degrees).

## Multiple Servos
In this part we will repeat our knowledge that we got from the single servo motor but with so many servos! Nothing differs. 

### Sweep
Multiple Servos with no potentiometer.
#### Circuit Layout
<img src= "https://github.com/Layan002/Electrical-and-Electronics-Task1-Servo-motor-simulation/assets/107956591/d743d160-7410-4edd-b631-0d5724131aae" alt= "Servo" width= 700><br>

#### Circuit Diagram
<img src= "https://github.com/Layan002/Electrical-and-Electronics-Task1-Servo-motor-simulation/assets/107956591/cb47ed22-0562-4690-a3f5-926631b371ea" alt= "Servo" width= 700><br>

#### Circuit code blocks
<p align="center">
  <img src="https://github.com/Layan002/Electrical-and-Electronics-Task1-Servo-motor-simulation/assets/107956591/07c2f941-493b-48a2-8912-0e7759a12d34" alt="image1" width="45%" />
  <img src="https://github.com/Layan002/Electrical-and-Electronics-Task1-Servo-motor-simulation/assets/107956591/bd0d1604-eba9-4002-8378-6dd707464edf" alt="image2" width="45%" />
</p>

#### Circuit Code

``` CPP
// C++ code
//
#include <Servo.h>

int position = 0;

int i = 0;

int j = 0;

int k = 0;

Servo servo_9;

Servo servo_10;

Servo servo_11;

Servo servo_12;

Servo servo_13;

Servo servo_7;

void setup()
{
  servo_9.attach(9, 500, 2500);
  servo_10.attach(10, 500, 2500);
  servo_11.attach(11, 500, 2500);
  servo_12.attach(12, 500, 2500);
  servo_13.attach(13, 500, 2500);
  servo_7.attach(7, 500, 2500);
}

void loop()
{
  position = 0;
  for (position = 1; position <= 179; position += 1) {
    delay(20); // Wait for 20 millisecond(s)
    servo_9.write(position);
    servo_10.write(position);
    servo_11.write(position);
    servo_12.write(position);
    servo_13.write(position);
    servo_7.write(position);
  }
  for (position = 179; position >= 1; position -= 1) {
    delay(20); // Wait for 20 millisecond(s)
    servo_9.write(position);
    servo_10.write(position);
    servo_11.write(position);
    servo_12.write(position);
    servo_13.write(position);
    servo_7.write(position);
  }
}
```

### Knop
Multiple Servos with multiple potentiometers.
#### Circuit Layout
<img src= "https://github.com/Layan002/Electrical-and-Electronics-Task1-Servo-motor-simulation/assets/107956591/24a87c00-9795-4fad-b89a-7364cba58a63" alt= "Servo" width= 700><br>

#### Circuit Diagram
<img src= "https://github.com/Layan002/Electrical-and-Electronics-Task1-Servo-motor-simulation/assets/107956591/322dafab-bcba-4be5-bfc3-536419c8ed90" alt= "Servo" width= 700><br>

#### Circuit code blocks
<p align="center">
  <img src="https://github.com/Layan002/Electrical-and-Electronics-Task1-Servo-motor-simulation/assets/107956591/17732916-34d4-4ee5-8a2e-203f21b98dfd" alt="six-knop1" width="45%" />
  <img src="https://github.com/Layan002/Electrical-and-Electronics-Task1-Servo-motor-simulation/assets/107956591/0ea90a3b-ea07-4f98-a218-d360f2186f3b" alt="Six-knop-blocks2" width="45%" />
</p>

#### Circuit Code
``` CPP
// C++ code
//
#include <Servo.h>

int outputValue = 0;

int sensorValue = 0;

int sensorValue1 = 0;

int outputValue1 = 0;

int sensorValue2 = 0;

int outputValue2 = 0;

int senserValue3 = 0;

int senserValue4 = 0;

int senserValue5 = 0;

int outputValue3 = 0;

int outputValue4 = 0;

int outputValue5 = 0;

Servo servo_9;

Servo servo_10;

Servo servo_11;

Servo servo_12;

Servo servo_13;

Servo servo_7;

void setup()
{
  pinMode(A0, INPUT);
  servo_9.attach(9, 500, 2500);
  pinMode(A1, INPUT);
  servo_10.attach(10, 500, 2500);
  pinMode(A2, INPUT);
  servo_11.attach(11, 500, 2500);
  pinMode(A3, INPUT);
  servo_12.attach(12, 500, 2500);
  pinMode(A4, INPUT);
  servo_13.attach(13, 500, 2500);
  pinMode(A5, INPUT);
  servo_7.attach(7, 500, 2500);
}

void loop()
{
  sensorValue = analogRead(A0);
  outputValue = map(sensorValue, 0, 1023, 0, 180);
  servo_9.write(outputValue);

  sensorValue1 = analogRead(A1);
  outputValue1 = map(sensorValue1, 0, 1023, 0, 180);
  servo_10.write(outputValue1);

  sensorValue2 = analogRead(A2);
  outputValue2 = map(sensorValue2, 0, 1023, 0, 180);
  servo_11.write(outputValue2);

  senserValue3 = analogRead(A3);
  outputValue3 = map(senserValue3, 0, 1023, 0, 180);
  servo_12.write(outputValue3);

  senserValue4 = analogRead(A4);
  outputValue4 = map(senserValue4, 0, 1023, 0, 180);
  servo_13.write(outputValue4);

  senserValue5 = analogRead(A5);
  outputValue5 = map(senserValue5, 0, 1023, 0, 180);
  servo_7.write(outputValue5);
  delay(10); // Delay a little bit to improve simulation performance
}
```
# Conclusion
To conclude this task, we've learnt so many things about each of TinkerCAD, Auirdoino, and servo SG90 motor. We distinguished the differences between both sweep and knop. Finally, we've simulated successfully wether the single or multiple servo motors. 
