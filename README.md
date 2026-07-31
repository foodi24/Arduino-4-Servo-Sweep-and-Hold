# 🤖 Arduino 4 Servo Sweep and Hold

This project demonstrates how to control four servo motors using an Arduino Uno and the Servo library. The program makes all four servos perform a sweep motion simultaneously for 2 seconds, then moves them to a fixed position of 90 degrees where they remain.

---

## 📖 Project Overview

The objective of this project is to program multiple servo motors to perform synchronized movement using the Arduino IDE. The project is designed to demonstrate basic servo motor control and timing using the built-in Servo library.

---

## 🎯 Features

- Control four servo motors simultaneously
- Perform a sweep motion from 0° to 180°
- Run the sweep for 2 seconds
- Automatically move all servos to 90°
- Hold all servos at 90° after the sweep
- Simple and easy-to-understand Arduino code

---

## 🛠 Components Used

- Arduino Uno
- 4 × Servo Motors (SG90 or equivalent)
- Jumper Wires
- USB Cable
- Arduino IDE

---

## 🔌 Wiring

| Servo | Signal Pin |
|--------|------------|
| Servo 1 | D3 |
| Servo 2 | D5 |
| Servo 3 | D6 |
| Servo 4 | D9 |

**Power Connections**
- All servo VCC → 5V
- All servo GND → GND

---

## 💻 Software

- Arduino IDE
- Servo Library (`#include <Servo.h>`)

---

## ▶️ How It Works

1. The Arduino initializes four servo motors.
2. All servos perform a synchronized sweep movement.
3. The sweep continues for approximately 2 seconds.
4. All servos move to 90 degrees.
5. The program keeps the servos at 90 degrees.

---



---

## 🎓 Learning Outcomes

- Understanding servo motor control
- Using the Arduino Servo library
- Controlling multiple servo motors
- Working with loops and timing functions
- Creating synchronized motor movements

---


## Link of the design
https://www.tinkercad.com/things/clOTGDf7XO8/editel?returnTo=%2Fdashboard&sharecode=dv8nTTlT6qowvqCk1JlKnqcpc4iIHhH1G0U95NjszSU


---



## Code
#include <Servo.h>

Servo servo1;
Servo servo2;
Servo servo3;
Servo servo4;

int pos = 0;

void setup() {
  servo1.attach(3);
  servo2.attach(3);
  servo3.attach(6);
  servo4.attach(9);
}

void loop() {
  unsigned long startTime = millis();

  // Run the Sweep example for 2 seconds
  while (millis() - startTime < 2000) {

    for (pos = 0; pos <= 180 && millis() - startTime < 2000; pos++) {
      servo1.write(pos);
      servo2.write(pos);
      servo3.write(pos);
      servo4.write(pos);
      delay(15);
    }

    for (pos = 180; pos >= 0 && millis() - startTime < 2000; pos--) {
      servo1.write(pos);
      servo2.write(pos);
      servo3.write(pos);
      servo4.write(pos);
      delay(15);
    }
  }

  // Hold all servos at 90°
  servo1.write(90);
  servo2.write(90);
  servo3.write(90);
  servo4.write(90);

  // Stop the program
  while (true) {
    // Servos remain at 90°
  }
}


