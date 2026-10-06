# Autonomous Snowplow - Infinitely Hot
## SYSC 4805 - L3-G15
<img src="common/project_image.png" height="400" width="650" >

## Table of Contents
- [Members](#members)
- [TAs](#tas)
- [Project Description](#project-description)
- [Software Organization](#software-organization)
- [Technologies Used](#technologies-used)
- [Setup](#setup)

## Members

- Karran Dhillon
- Collin Dang
- Qasim Hamid
- Alex Tempel

## TAs

- Igor Bogdanov
- Mahya Shahmohammadimehrjardi

## Project Description

This project presents an Autonomous Snowplow designed to clear snow off an enclosed area without hitting obstacles in its path. This project contains constraints on time, speed of the robot, and pre-defined boundaries to ensure the system can autonomously adjust to different maps and moving objects. The project also involves designing a complex driving algorithm to account for objects along its path.

Our team, Infinitely Hot, composed of Carleton Computer Systems Engineering Students aims to showcase our solution to the design of the Autonomous Snowplow and it’s impacts on snow removal.

## Software Organization
```
project-l3-g15-infinitely-hot/
    main/
        AnalogDistanceSensor.hpp/.ino   <- Analog distance sensor unit
        CarMovement.hpp/.cpp            <- Motor driver unit
        IMU.hpp/.cpp                    <- Inertial Measurement Unit
        VL53L1X.h/.ino                  <- ToF long distance range unit
        VMA330.h/.ino                   <- IR obstacle avoidance unit
        WheelEncoder.hpp/.cpp           <- Wheel encoder unit
        LineFollower.hpp/.ino           <- line follower unit
        Ultrasonic.hpp/.ino             <- ultrasonic sensor unit
        main.ino                        <- main RTOS task algorithms
        unittest.hpp/cpp                <- unit test code for the individual sensors
    common/                             <- image and miscellaneous files
    documents/                          <- final report added here for documentation
```

## Technologies Used
**Control Mechanism:** RTOS with interrupt-driven main loop. Sensors will set global flags when a specific ISR must be run. Main driving algorithm will perform corrective action. Main loop does low-priority, normal forward driving.

**Sensors and Components:**
- Motor Driver/Controller
- Arduino Due
- 1 Line Follower Sensor
- 1 Analog Distance Sensor
- 2 Ultrasonic Sensors

**Note:** the software is capable of also using the wheel-encoder/VMA330/VL53L1X/IMU if desired.

## Setup
### FreeRTOS Setup
1) Download a zip of this repo `https://github.com/bdmihai/DueFreeRTOS/tree/master`

    1.1) Hit `<> Code` then `Download ZIP`
2) Go into the Arduino IDE and click `Sketch > Include Library > Add .ZIP library`
3) Select the downloaded .zip file from 1)

### Individual Sensor Setup
1) On the Arduino IDE, click `Sketch > Include Library > Manage Libraries`
2) Search for and install `LSM6 by Pololu` and click `Install` (for IMU sensor)

### Running the program
1) Load up the Arduino IDE. Make sure the `main/` folder is the root folder.
2) Plug in the Arduino Due to a USB Port. Make sure the IDE recognizes the port on the top-left
3) Click the right-arrow button on the top-left to compile and program the device. Will automatically run.
4) Make sure the switch on the motor driver and battery are on, otherwise, they will not receive power.
