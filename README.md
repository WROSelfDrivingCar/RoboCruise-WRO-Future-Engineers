# RoboCruise-WRO-Future-Engineers
"Developing innovative autonomous solutions for the WRO Future Engineers challenge, combining robotics, AI, and engineering creativity."
Engineering materials

This repository contains engineering materials of a self-driven vehicle's model participating in the WRO Future Engineers competition in the season 2024.

**Content**

**t-photos** contains 2 photos of the team (an official one and one funny photo with all team members)

**v-photos** contains 6 photos of the vehicle (from every side, from top and bottom)

**video** contains the video.md file with the link to a video where driving demonstration exists

**schemes** contains one or several schematic diagrams in form of JPEG, PNG or PDF of the electromechanical components illustrating all the elements (electronic components and motors) used in the vehicle and how they connect to each other.

**src** contains code of control software for all components which were programmed to participate in the competition

**models** is for the files for models used by 3D printers, laser cutting machines and CNC machines to produce the vehicle elements. If there is nothing to add to this location, the directory can be removed.

**other** is for other files which can be used to understand how to prepare the vehicle for the competition. It may include documentation how to connect to a SBC/SBM and upload files there, datasets, hardware specifications, communication protocols descriptions etc. If there is nothing to add to this location, the directory can be removed.


**Introduction**

Technical Clarifications
Our self-driving car project for WRO consists of the following key modules and components, detailing how they interact with each other and how to build, compile, and upload the code:

**1. Code Modules**
The code for the self-driving car is divided into several key modules:

**a. Color Sensor Module (Arduino Nano):**

**Purpose:** The color sensor is used to detect colored lines or objects on the path, and accordingly, the car turns left, right, or moves straight.
**Components Involved:**
**Arduino Nano:** Microcontroller for handling inputs from the color sensor and controlling the motors.
**Color Sensor:** Detects colors and sends data to the Arduino Nano to trigger turning decisions.
**Interaction:** This module processes color sensor data and communicates directly with the motor control module to make turning decisions.
**Code:** The color sensor readings are processed in real-time by the Arduino Nano to make decisions about which direction the car should move.

**b. Obstacle Detection Module (Raspberry Pi + Webcam):**

P**urpose:** Uses the Raspberry Pi with a webcam to detect obstacles in the car's path.
**Components Involved:**
**Raspberry Pi:** Acts as the main processor for image recognition and obstacle detection.
**Webcam:** Captures images in real-time and feeds them to the Raspberry Pi for processing.
**Interaction:** The Raspberry Pi processes the camera feed using OpenCV to detect obstacles. Upon detecting an obstacle, it sends signals to the Arduino Nano to stop or avoid the obstacle.
Code: Python code running on the Raspberry Pi uses computer vision algorithms to detect obstacles and communicate with the Arduino via GPIO or serial.

**c. Motor Control Module (L293D and Arduino Nano):**

**Purpose:** Controls the forward and backward movement and turning of the car based on inputs from the color sensor and obstacle detection modules.
**Components Involved:**
**L293D Motor Driver:** Used to control the DC motors.
**DC Motors:** Provide movement for the car.
**Arduino Nano:** Receives inputs from the sensors and sends control signals to the L293D to drive the motors.
**Interaction:** This module receives commands from the color sensor and obstacle detection modules to move the car in the correct direction, speed, and stop when necessary.
**Code:** Functions are programmed to turn left, right, move forward, or stop the car by controlling the motor driver via the Arduino.

**2. Electromechanical Components**
The following electromechanical components are essential in controlling and powering the vehicle:

**a. L293D Motor Driver:**

Purpose: It controls the motors by allowing the Arduino Nano to set the direction and speed of the car.
Interaction: The motor driver receives digital signals from the Arduino Nano to control the movement of the car.

**b. LM2596 Voltage Regulator:**

Purpose: Regulates the voltage from the car’s main power supply to ensure stable voltage for the Raspberry Pi and other components.
Interaction: The LM2596 ensures that the Raspberry Pi and Arduino receive stable voltage, protecting the system from fluctuations.

**c. 7805 Voltage Regulator:**

Purpose: Provides a regulated 5V output for components like the Arduino Nano and sensors.
Interaction: This regulator provides consistent power to ensure the reliable operation of sensors and the microcontroller.
3. Building, Compiling, and Uploading Code
The process to build, compile, and upload the code to the vehicle’s controllers involves the following steps:

**a. Arduino Nano (For Motor and Color Sensor Control):**

**Code Compilation:**
The Arduino IDE is used to write, compile, and upload the code to the Arduino Nano.
Ensure the correct libraries (e.g., for Servo control, color sensor) are installed.
**Code Upload:**
Connect the Arduino Nano to the computer via USB.
Select the correct board (Arduino Nano) and port in the Arduino IDE.
Upload the code using the “Upload” button in the IDE.

**b. Raspberry Pi (For Obstacle Detection):**

**Setting Up the Environment:**
Install the required Python packages such as opencv-python for image processing.
Setup the camera using the raspi-config command to enable the camera module.
**Code Execution:**
The Python script for obstacle detection is run directly on the Raspberry Pi. Use SSH or directly connect to the Pi using a monitor to execute the script.
The script processes the video feed and sends commands to the Arduino via GPIO pins or serial communication.

**c. Power Management:**

**LM2596:** Set the voltage output to match the Raspberry Pi's power requirements (typically 5V) before connecting it to the system.
7805: Use the 7805 to regulate power for the Arduino Nano and sensors, ensuring stable operation.

**d. Motor Driver (L293D):**

The L293D is connected to the Arduino Nano and motors to control movement.
Based on sensor inputs, the Arduino sends signals to the L293D to drive the motors for movement and turning.

**4. Testing and Calibration**
After uploading the code, the following steps should be followed:

Test the Color Sensor: Ensure it detects colors correctly and triggers appropriate turns.
Test the Obstacle Detection: Ensure the camera detects obstacles and stops or navigates the vehicle around them.
Calibrate Motors: Test motor responses to commands for forward, backward, left, and right movements.
This technical structure ensures that all code modules are effectively related to their respective hardware components and provides a clear pathway to build, compile, and upload the code to the vehicle's controllers.

