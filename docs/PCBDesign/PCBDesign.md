# PCB Design

## Overview

The PCB was designed to support the ESP32 microcontroller and integrate the subsystem’s sensor and communication components into a compact and reliable hardware platform. The goal was to transition from a breadboard prototype to a fully functional printed circuit board.

## PCB Layout Image

<img width="611" height="524" alt="image" src="https://github.com/user-attachments/assets/03d4f0ae-5a9d-43b2-b65e-c3ad2017fd6a" />


<img width="617" height="526" alt="image" src="https://github.com/user-attachments/assets/64c05da7-3f23-4f25-adb4-8b0348395d17" />

---

## Design Process

The schematic and PCB layout were created using KiCad. The design included:

- ESP32 module footprint
- Sensor connections (I2C interface)
- Power regulation components
- UART communication pins
- Required resistors and capacitors

Special attention was given to correct pin mapping, component placement, and routing to ensure reliable operation.

---

## Power Design

The board was powered from a shared system supply and locally regulated to 5V and 3.3V as required.

Key considerations included:

- Stable voltage supply to the ESP32 and sensor
- Proper placement of decoupling capacitors
- Sufficient trace width for power lines

Power stability was critical during testing and required careful debugging.

---

## PCB Layout

The PCB was designed as a two-layer board with:

- A ground plane for improved stability
- Short and efficient signal routing
- Separation of power and signal paths where possible

Component placement was optimized to simplify routing and reduce interference.

---

## Challenges

Several challenges were encountered during the PCB design and bring-up process:

- Incorrect pin mappings between the ESP32 and sensor
- I2C communication issues due to missing or incorrect pull-up resistors
- Power instability affecting sensor performance
- Initial layout decisions requiring revision after testing

These issues required iterative debugging across both hardware and firmware.

---

## Testing and Debugging

After fabrication, the board was tested through a series of steps:

- Verifying power rails (3.3V and 5V)
- Confirming ESP32 functionality and successful flashing
- Testing sensor detection and data output
- Debugging communication issues

Testing revealed the importance of validating both electrical connections and software configuration.

---

## Key Takeaways

- PCB design requires careful planning of both hardware and firmware integration  
- Power distribution and grounding significantly impact system stability  
- Small design errors can lead to major debugging challenges  
- Iterative testing is essential to achieving a functional design

Gerber Files Can be found in this (*Zip*)(Gerbers_V2_zip.zip)
