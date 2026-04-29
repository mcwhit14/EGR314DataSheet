---
title: Individal Block Diagram
tags:
- tag1
- tag2
---

## Overview
This needs to be updated with a brief purpose for having the block diagram.
The distance sensing subsystem detects nearby obstacles using the VL53L4CX time of flight sensor. The sensor communicates with the ESP32 microcontroller over the I2C interface. The ESP32 processes the distance data and determines whether the rover is approaching an obstacle. If the measured distance falls below a safety threshold, the microcontroller sends a command over UART to the motor subsystem to stop or reduce speed. This design prevents collisions and protects the rover from physical damage.

## Design Decisions
The ESP32 was selected due to its integrated wireless capabilities, processing power, and compatibility with I2C and UART communication. The VL53L4CX sensor was chosen for its high accuracy and long-range measurement capability (up to ~6 meters).

The block diagram was structured to clearly separate:
- sensing (VL53L4CX)
- processing (ESP32)
- communication (UART protocol)

This modular design allows easy debugging, scalability, and integration with other system components.

## Requirements Alignment
This design meets system requirements by:
- providing real-time distance sensing
- enabling fast communication with other modules
- supporting emergency stop detection based on distance thresholds


## Block Diagram 
<img width="756" height="806" alt="314_IndividualBlock (1)" src="https://github.com/user-attachments/assets/97488dbe-c699-4617-adf4-4e01033c2d67" />



 

