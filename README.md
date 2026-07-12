# Ultrasonic-SLAM-Quadruped-Robot
An open-source, budget-friendly 12-DOF quadruped spider robot capable of biological-inspired legged locomotion and real-time 2D environmental obstacle mapping (SLAM). This project utilizes a dual-microcontroller architecture to decouple structural gait mathematics from real-time obstacle calculations.

<img width="1280" height="960" alt="robot-pic-2" src="https://github.com/user-attachments/assets/58af32bf-232a-40de-986e-9791e9a9e903" />
<img width="899" height="1599" alt="robot-pic-3" src="https://github.com/user-attachments/assets/df2511e2-1378-4a13-b39e-0fd25926d9a9" />
<img width="1280" height="720" alt="robot-pic-1" src="https://github.com/user-attachments/assets/ed592ea5-b429-4ab0-83bd-82df36e84df2" />

Key Features
* **12-DOF Legged Locomotion:** 4 legs, each featuring 3 degrees of freedom (Coxa, Femur, Tibia) powered by SG90 servo motors.
* **Full Inverse Kinematics (IK) Engine:** Runs on an 8-bit Arduino Nano to compute accurate continuous joint transitions dynamically using Cartesian-to-Polar coordinates.
* **Stable Tripod Walking Gait:** Implements smooth multi-directional walking patterns (forward, backward, left/right spot turns) alongside custom gesture sequences (hand waves, dancing routines).
* **Decoupled SLAM Subsystem:** Dedicated ESP32 microcontroller tracking range profiles via an HC-SR04 ultrasonic module.
* **Real-time Map Visualization:** Streams real-time scalar distance array inputs over serial communication to a Python Matplotlib rendering framework for immediate 2D obstacle scatter mapping.

---

## 🛠️ Hardware Architecture & Connections

### Components
* **Locomotion MCU:** Arduino Nano (ATmega328P)
* **Sensing/Slam MCU:** ESP32 Developer Board
* **Actuators:** 12x SG90 Servo Motors (1.8 kg-cm torque)
* **Range Finder:** HC-SR04 Ultrasonic Sensor
* **Chassis:** 3D Printed Spider Quadruped Frame
* **Power Units:** External 5V/3A Regulated PSU (for Servos) + Dedicated Logic Input


> ⚠️ **IMPORTANT NOTE:** Do not run the 12 servo motors directly off the microcontroller's 5V pin. The joint stall currents can peak up to 4A during gait loops. Use a robust separate external power source while bridging the grounds together for reliable signal referencing.

---

## 📂 Repository Contents

* `/Firmware`: Contains core microcontroller software scripts.
  * `Neutral_Position.ino` - Calibration code bringing all 12 servo linkages directly to a clean 90° reference configuration.
  * `Quadruped_Gait_Control.ino` - Structural implementation of Cartesian Inverse Kinematics, Tripod Gait algorithms, and specialized gesture variations.
  * `SLAM_Ultrasonic_Sensing.ino` - High-frequency sensor controller utilizing interrupt metrics to measure distances and pipe data stream.

---

💻 Software Setup Guide

### 1. Actuator Alignment & Calibration
Before mounting the mechanical leg horns, upload `Neutral_Position.ino` to the Arduino Nano. Secure the chassis assemblies while the drive shafts are held accurately at exactly 90 degrees.

### 2. Main Firmware Upload
* Deploy `Program1.ino` to the Arduino Nano using your Arduino IDE environment (Ensure `FlexiTimer2` dependency library is pre-installed).
* Upload `SLAM_V.1.ino` onto your ESP32 board.

### 3. Executing Python 2D Map Dashboards
Ensure your desktop environment has Python 3 and its terminal dependencies configured. Run the following to establish visualization tracking
* OR 
#### After uploading and running the slam arduino code, open online matplotlib compilier and and paste the code from Slam_matplotlib_code to online matplotlib compilier to get the 2d-mapped output

For Hardware 3D-printed Structures:
http://bit.ly/2wdEbmO
