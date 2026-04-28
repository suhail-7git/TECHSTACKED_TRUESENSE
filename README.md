# TECHSTACKED_TRUESENSE: TrueSense Active Stabilizer 🦾

## Project Description
The NeuroGrip Active Stabilizer is a wearable, edge-computing exoskeleton designed to assist patients with Parkinson's disease, essential tremors, and stroke-induced spasticity. By fusing data from a 6-DOF IMU and an array of 5 Time-of-Flight (ToF) laser sensors, the glove tracks precise wrist orientation and individual finger mobility in real-time. 

A closed-loop control system actuates 5 independent micro-servos via a dedicated PWM driver to physically counteract hand tremors and provide programmable active-resistance therapy, bridging the gap between passive diagnostics and active physical rehabilitation.

## Tech Stack Used
* **Microcontroller:** Arduino Uno
* **Sensors:** * 1x MPU6050 (6-DOF IMU for wrist tracking)
  * 5x VL53L0X (ToF Lasers for individual finger tracking)
* **Actuators:** 5x MG90S Metal-Gear Micro Servos
* **Drivers:** PCA9685 (16-Channel 12-bit PWM Servo Driver)
* **Power Architecture:** 12V 5A Mains Adapter stepped down to isolated 5.0V via LM2596 Buck Converter for high-current servo loads.
* **Language:** C++ (Arduino IDE)

## Setup Steps
1. **Power Isolation:** Connect the 12V adapter to the LM2596 Buck Converter and tune the output to exactly `5.0V`. Route this 5V power *only* to the `V+` terminal of the PCA9685. 
2. **Common Ground:** Tie the Ground of the Buck Converter to the Ground of the Arduino to ensure I2C data integrity.
3. **I2C Bus & XSHUT Wiring:** * Daisy-chain the SDA and SCL pins of the MPU6050, PCA9685, and all 5 VL53L0X sensors to Arduino `A4` and `A5`.
   * Wire the `XSHUT` pins of the 5 VL53L0X sensors to Arduino Digital Pins `2, 3, 4, 5, and 6` to allow dynamic I2C address reassignment during the boot sequence.
4. **Actuators:** Connect the 5 MG90S servos to Ports 0-4 on the PCA9685.
5. **Software:** Upload the main `.ino` file. Ensure the Arduino remains powered via USB to isolate logic power from motor noise.

## Demo Instructions
1. **Calibration:** Place the glove perfectly flat and motionless on the table. Power on the Arduino. The system requires 2 seconds to auto-calibrate the MPU6050 offsets and sequentially boot the 5 ToF sensors.
2. **Mounting:** Once calibration is complete, the user carefully straps the exoskeleton onto their hand.
3. **Tremor Cancellation Demo:** The user simulates a 4Hz-8Hz hand tremor. The MPU6050 detects the oscillations, and the Arduino commands the PCA9685 to actuate the servos in inverse motion, physically stabilizing the hand.
4. **Therapy Tracking Demo:** As the user curls individual fingers, the VL53L0X sensors track the millimeter-accurate range of motion, providing real-time biomechanical feedback.
