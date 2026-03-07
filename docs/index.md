---
title: Welcome
tags:
- tag1
- tag2
---
<center>
<font size= "6">(Myles White) Datasheet</font><br>
as part of<br>
<font size= "8"> Distance Sensor Subsystem</font><br>
for<br>
<font size= "5"> Team 305 </font><br>

**Submission: March, 6, 2026**
</center>

## Introduction

* This datasheet documents the design and implementation of the distance sensing subsystem used in the team’s autonomous rover project. The subsystem is responsible for detecting nearby obstacles and communicating proximity information to the rover motor control system. The design uses a time-of-flight distance sensor connected to an ESP32 microcontroller, which processes the sensor data and communicates with the motor subsystem to prevent collisions. This document describes the system architecture, component selection, power requirements, and schematic design used to implement this subsystem.

### Project Summary

* The team project focuses on developing an autonomous rover capable of navigating its environment while avoiding obstacles. The rover consists of multiple subsystems including motor control, sensing, communication, and power management. My subsystem focuses on obstacle detection using a time-of-flight distance sensor and an ESP32 microcontroller. The subsystem continuously monitors the distance to nearby objects and communicates this information to the motor subsystem so that the rover can slow down or stop when an obstacle is detected. Additional details about the full rover architecture can be found in the team report.
[team report.](https://egr314-s-2026-30.github.io/EGR314-S-2026-305.github.io/)


### My Contribution

My primary contribution to the project is the design and implementation of the rover’s distance sensing subsystem. This includes the development of the subsystem block diagram, component selection, power regulation design, and the complete schematic for the subsystem electronics. The subsystem integrates a VL53L4CX time-of-flight sensor with an ESP32 microcontroller using the I²C communication interface. The ESP32 processes the distance measurements and communicates with the motor subsystem through a UART interface to prevent collisions when objects are detected within a specified safety threshold. I was also responsible for generating the power budget and ensuring that the subsystem operates safely within the available power limits.

To review the details listed of the material used to construct the subsection, you can review it in the ["BOM"](https://embedded-systems-design.github.io/EGR304DataSheetTemplate/03-BOM/BOM/) section of the datasheet.

For all the sections
