---
title: Power Budget
---

## Overview
The rover subsystem operates primarily on a 3.3V power rail supplied by a switching regulator. The ESP32 microcontroller represents the largest power consumer, with an estimated peak current of approximately 300 mA during active operation. The VL53L4CX distance sensor and debugging LED contribute minimal additional current draw. The total estimated current requirement of the subsystem is approximately 330 mA. A 25% safety margin was applied, resulting in a total required current of approximately 420 mA. The selected LM2575-3.3 switching regulator supports up to 1A output current, which provides sufficient headroom for stable operation.

<img width="372" height="538" alt="image" src="https://github.com/user-attachments/assets/f3f8dbf9-9b98-4c51-a089-ed9a82d47794" />


## Conclusions

From the prepared power budget, the subsystem requires approximately 330 mA on the 3.3 V power rail, or about 420 mA including a safety margin. The selected LM2575-3.3 regulator, capable of supplying up to 1 A, provides sufficient current to safely power the ESP32, distance sensor, and supporting components.

## Resouces

The power budget as a PDF download is available [*here*](PowerBudgetExample.pdf), and a Microsoft Excel Sheet [*here*](PowerBudgetExample.xlsx).
