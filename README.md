anwarsiraj1234/Smart_Light_Sensor_Workshop
# Smart Light Sensor: Automatic Night Light using LDR and Arduino Uno

**Made by Sir Anwar Siraj, DS & AI Robotics, for Teachers**

This repository contains a colorful, step-by-step teaching presentation
(`Smart_Light_Sensor_Workshop.pptx`) and the Arduino code for a simple
light-sensor project. It was prepared for a Teachers' Workshop so that
teachers can learn the project and teach it to their students.

## What the project does

An LDR (Light Dependent Resistor) measures how bright the room is.
- **Dark room:** the LED turns ON automatically.
- **Bright room:** the LED turns OFF.

## Components

| Component | Quantity | Purpose |
|---|---|---|
| Arduino Uno | 1 | Reads the sensor and controls the LED |
| USB cable | 1 | Power and code upload |
| Breadboard | 1 | Build the circuit without soldering |
| LDR | 1 | Light sensor (2 legs, no polarity) |
| Resistor 10 kΩ | 1 | Forms a voltage divider with the LDR |
| LED (any color) | 1 | Output |
| Jumper wires | 4+ | Connections |
| Resistor 220 Ω | optional | Protects the LED |

## Circuit connections

- **5V (positive)** to LDR Leg 1
- **LDR Leg 2** to **A0** and to one leg of the 10 kΩ resistor
- Other leg of the 10 kΩ resistor to **GND (negative)**
- **LED long leg (+)** to **pin 13**, **short leg (−)** to **GND**

## How it works

1. The LDR and the 10 kΩ resistor share the 5 V (voltage divider).
2. In the dark, LDR resistance goes UP, so the voltage at A0 goes DOWN.
3. Arduino reads A0 as a number from 0 to 1023 (0 V = 0, 5 V = 1023).
4. If the reading is less than or equal to the threshold (70), the LED turns ON.

## What is a threshold?

A threshold is a decision line: a limit number. Arduino only understands
numbers, so the threshold tells it which number means "dark".
In this project `threshold = 70` (about 0.34 V). Readings of 70 or less mean
dark, so the LED turns ON. The best value depends on your room, so test and
adjust it.

### How to choose your threshold

1. Open the Serial Monitor (speed 9600).
2. Cover the LDR with a finger and note the DARK number.
3. Shine a torch and note the BRIGHT number.
4. Choose a number in between, near the dark value, and update `int threshold`.

## Code

```cpp
// CODE
// MADE BY SIR ANWAR SIRAJ, DS & AI ROBOTICS

int ldrPin = A0;
int led = 13;
int threshold = 70;

void setup()
{
  Serial.begin(9600);
  pinMode(led, OUTPUT);
}

void loop()
{
  int data = analogRead(ldrPin);
  Serial.println("");
  Serial.print("Light Sensor ");
  Serial.print("Value = ");
  Serial.print(data);
  if(data <= threshold)
  {
    digitalWrite(led, HIGH);
  }
  else
  {
    digitalWrite(led, LOW);
  }
}
```

## Presentation contents (18 slides)

1. Title
2. What the project does
3. Components needed
4. LDR full form (Light Dependent Resistor)
5. The LDR in detail (two legs, no polarity)
6. Resistor, LED and Arduino explained
7. Voltage divider
8. Why the LED turns ON in the dark (one word: voltage)
9. Circuit diagram (schematic)
10. Physical circuit diagram (Arduino, LDR, LED)
11. Step-by-step wiring
12. Full code
13. Code explained line by line
14. What is a threshold and why we need it
15. What 70 and 1023 mean (readings and voltage)
16. How to choose the threshold (4 steps)
17. Threshold: dark or bright, plus troubleshooting
18. Summary and "Try it" activities

## Try it

- Change the threshold to 200
- Use a different LED pin
- Make the LED blink in the dark
- Add `delay(200)` to slow down the Serial Monitor

## Credits

Made by **Sir Anwar Siraj, DS & AI Robotics**, for Teachers.
