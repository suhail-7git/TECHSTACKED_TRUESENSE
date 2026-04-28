# Active Tremor-Cancellation Device 

## Project Description
A low-cost, edge-computing embedded system designed to cancel out 4Hz to 8Hz hand tremors for patients with Parkinson's disease or essential tremors. By utilizing a Proportional-Derivative (PD) loop and a Complementary Filter, the system reads real-time IMU data and actuates micro-servos to keep the spoon perfectly level, replacing prohibitively expensive commercial solutions.

## Tech Stack Used
* **Microcontroller:** Arduino Uno
* **Sensors:** MPU6050 (6-DOF IMU)
* **Actuators:** 2x MG90S Metal-Gear Micro Servos
* **Power:** 12V 5A Adapter stepped down via LM2596 Buck Converter
* **Language:** C++ (Arduino IDE)

## Setup Steps
1. Connect the LM2596 Buck Converter to the 12V supply and tune the potentiometer to exactly `5.0V` using a multimeter.
2. Wire the 5V output to the Red/Brown wires of the MG90S servos. 
3. Wire the MPU6050 via I2C (`SDA` to `A4`, `SCL` to `A5`).
4. Ensure the Buck Converter Ground and Arduino Ground are tied together.
5. Upload `tremor_spoon.ino` to the Arduino.

## Demo Instructions
1. Place the device flat on the table and power it on. Allow 2 seconds for servos to center.
2. Open the Arduino IDE **Serial Plotter** at `115200` baud rate to view the live stabilization graph.
3. Pour a small amount of water into the spoon attachment.
4. Pick up the handle and simulate a physical hand tremor. The servos will actuate inversely to keep the water from spilling.
