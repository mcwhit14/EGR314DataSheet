---
title: Individal Block Diagram
tags:
- tag1
- tag2
---

## Overview
This needs to be updated with a brief purpose for having the block diagram.
The distance sensing subsystem detects nearby obstacles using the VL53L4CX time of flight sensor. The sensor communicates with the ESP32 microcontroller over the I2C interface. The ESP32 processes the distance data and determines whether the rover is approaching an obstacle. If the measured distance falls below a safety threshold, the microcontroller sends a command over UART to the motor subsystem to stop or reduce speed. This design prevents collisions and protects the rover from physical damage.




## Block Diagram 


 <img width="494" height="524" alt="image" src="https://github.com/user-attachments/assets/4380a51f-03d1-4494-946c-f02b2dd62cfa" />

