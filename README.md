Multi-Sensor Integration: MPU6050 & VL53L0X with Arduino
This project demonstrates how to interface and test two powerful I2C sensors using an Arduino Uno: the MPU6050 (6-Axis Accelerometer and Gyroscope) and the VL53L0X (Time-of-Flight Laser Distance Sensor).
Overview
The goal of this project is to provide a reliable testing suite for newly soldered sensors. By utilizing the I2C protocol, both sensors share the same data lines, allowing for a compact and efficient hardware setup.
•	MPU6050: Measures orientation, tilt, and rotational velocity.
•	VL53L0X: Measures precise distance up to 1.2m–2m using an invisible laser.
________________________________________
Hardware Requirements
•	Microcontroller: Arduino Uno (or compatible)
•	Sensors: * MPU6050 (GY-521 Breakout)
o	VL53L0X (ToF Sensor)
•	Wiring: Breadboard and Jumper Wires
•	Tools: Soldering iron (for header pins)
________________________________________
 Wiring Diagram
Both sensors use I2C Communication. On the Arduino Uno, this means they share the same pins (A4 and A5).
Sensor Pin	Arduino Uno Pin	Description
VCC / VIN	5V	Power Supply
GND	GND	Ground
SCL	A5	I2C Clock
SDA	A4	I2C Data
XSHUT (VL53L0X)	D4	Shutdown Pin (Used for hardware reset)
Note: Ensure your solder joints are clean and "volcano-shaped." If the VL53L0X gives a constant reading (e.g., 53mm), clean the sensor lens and check for bridges on your solder points.
________________________________________
Software Setup
1. Libraries Required
Install the following via the Arduino Library Manager:
•	Adafruit_VL53L0X
•	Wire.h (Built-in)
2. Configuration
Ensure your Serial Monitor is set to 115200 Baud to view the output correctly.
________________________________________
Project Structure
•	MPU6050_Test.ino: Basic script to verify raw accelerometer and gyroscope data.
•	VL53L0X_Test.ino: Script to verify laser distance measurements and handle sensor resets.
•	Combined_Sensor_Suite.ino: (Optional) A script that runs both sensors simultaneously.
________________________________________
 Troubleshooting
•	Sensor not found? Run an "I2C Scanner" sketch to see if the addresses (0x68 for MPU6050 and 0x29 for VL53L0X) are detected.
•	Frozen Readings? Check for "cold" solder joints. Re-heat the pin with your soldering iron and add a tiny bit of fresh solder.
•	8191 Reading? This indicates a VL53L0X timeout. Ensure the protective plastic film is removed from the sensor face.


