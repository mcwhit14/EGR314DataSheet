---
title: Component Selection Example
---


### Style 2

> Also acceptable, more markdown friendly

**External Distance Sensor Module**

1. Adafruit VL53L4CX Time of Flight Distance Sensor - ~1 to 6000mm - STEMMA QT / Qwiic

    ![](<img width="480" height="485" alt="image" src="https://github.com/user-attachments/assets/46bf3807-8ccc-4e6e-8e09-fc0a8359070f" />
)

    * $14.95/each
    * [link to product](https://www.adafruit.com/product/5425?gad_source=1&gad_campaignid=21079227318&gbraid=0AAAAADx9JvSl8RUK5UpuGQcb53-oEMddy&gclid=Cj0KCQiA-YvMBhDtARIsAHZuUzJpbgO8iYHooJXRqa52AmxdyV115lKm72l8DtRN0tQkdX5DKgdkqPMaAj8PEALw_wcB)

    | Pros                                      | Cons                                                             |
    | ----------------------------------------- | ---------------------------------------------------------------- |
    | Inexpensive                               | Daughter Board |
    | Long Range(Up to 6m)                    |real world range depeds on reflectivity and ambiant light                                        |
    |  |

2. Adafruit VL53L1X Time of Flight Distance Sensor - ~30 to 4000mm - STEMMA QT / Qwiic

    ![](image3.png)

    * $14.95/each
    * [Link to product](https://www.adafruit.com/product/3967?gad_source=1&gad_campaignid=21079227318&gbraid=0AAAAADx9JvQBEa_pZJ0CxJy2nNGHELEVm&gclid=EAIaIQobChMIj6OwhJTSkgMVZQbvAh11ji6SEAQYASABEgJPGvD_BwE)

    | Pros                                                              | Cons                |
    | ----------------------------------------------------------------- | ------------------- |
    | Used commonly                                      | shorter max range then LC4CX      |
    | still long range                               | Daughter board |
    | |

3. Adafruit VL53L4CXV0DH/1 

    ![](image3.png)

    * $14.95/each
    * [Link to product](https://www.adafruit.com/product/3967?gad_source=1&gad_campaignid=21079227318&gbraid=0AAAAADx9JvQBEa_pZJ0CxJy2nNGHELEVm&gclid=EAIaIQobChMIj6OwhJTSkgMVZQbvAh11ji6SEAQYASABEgJPGvD_BwE)

    | Pros                                                              | Cons                |
    | ----------------------------------------------------------------- | ------------------- |
    | smallest footprint                                    | too small to hand solder    |
    | lowest cost                               | needs careful alignment and mechanical design |
    |no daughter board |

**Choice:** Option 1:Adafruit VL53L4CX Time of Flight Distance Sensor

**Rationale:** The VL534CX is made for long range Time of flight and  displays accurate measurements up to 6m with a 18 deggree Field of View. This greatly checks off the requirement of the team needing a sensor that can see at least beyond 2m. 


**External Microcontroller Module**

1. PIC18F47Q10

    ![](image3.png)

    * $10.19/each
    * [Link to product](https://www.microchip.com/en-us/product/pic18f47q10)

    | Pros                                                              | Cons                |
    | ----------------------------------------------------------------- | ------------------- |
    | No background Wifi stacks                                    | MPlab debugging workflow can be slow    |
    |Predictable                           | Toolchain issues |
    | Lower Power consumption|

2. ESP32

    ![](image3.png)

    * $14.95/each
    * [Link to product](https://www.digikey.com/en/products/detail/espressif-systems/ESP32-DEVKITC-32UE/12091813?gclsrc=aw.ds&gad_source=4&gad_campaignid=20243136172&gbraid=0AAAAADrbLljmLZc8BiWTA5yG0T-yNVJ6B&gclid=EAIaIQobChMItNWL-IzTkgMVuzdECB2H0gLgEAQYBiABEgLFLfD_BwE)

    | Pros                                                              | Cons                |
    | ----------------------------------------------------------------- | ------------------- |
    | Arduino Libraries available                                    | Complicates power budget   |
    | Immediate print debugging                              | Background tasks can affect timing  |
    |less intergration mismatch |

**Choice:** Option 1: ESP32

**Rationale:** The ESP32 offers faster intergration due to broad example code availability along with built in serial/wifi features. The PIC on the other hand is a reliable platform that aligns smoothly with the course but slightly lower level functionality creating potential longer time for debugging, printing, logging and quick iteration, with MPLab toolchain commonly creating issues. 



** Power Supply Module**

1. Share 5V Rail and local 3.3V on subsystem board

    

    | Pros                                                              | Cons                |
    | ----------------------------------------------------------------- | ------------------- |
    | Each subsystem derives what it needs                                   | Requires team to have a stable 5V distrubuition plan  |
    | Easy to meet SMT final requirement                      | Heat waste |
    | Simple to debug and meaure |

2. Share 5V rail and local buck converter to 3.3V with LM2575T

    ![](image3.png)

    * $1.92/each
    * [Link to product](https://www.digikey.com/en/products/detail/texas-instruments/LM2575T-5.0-NOPB/108660?gclsrc=aw.ds&gad_source=4&gad_campaignid=17338792030&gbraid=0AAAAADrbLlhqbShfo1S6gTZvX0YYw1fR2&gclid=EAIaIQobChMI7M21zJ7TkgMVJCFECB2nygTmEAQYASABEgIB0PD_BwE)

    | Pros                                                              | Cons                |
    | ----------------------------------------------------------------- | ------------------- |
    | Less Heat                                 | LM2575 is through hole   |
    | Can handle higher current                            | switching noise can affect sensitive measurements  |
    |less intergration mismatch |

3. Independent power using MB102 breadboard power module

    ![](image3.png)

    * $5.56/each
    * [Link to product](https://www.digikey.com/en/products/detail/bud-industries/BBP-32701/8602382?gclsrc=aw.ds&gad_source=4&gad_campaignid=20243136172&gbraid=0AAAAADrbLljmLZc8BiWTA5yG0T-yNVJ6B&gclid=EAIaIQobChMIpZ6UqJ7TkgMVMD5ECB0N1hIQEAQYASABEgJTt_D_BwE)

    | Pros                                                              | Cons                |
    | ----------------------------------------------------------------- | ------------------- |
    | Very fast for in lab use                                | through hole   |
    | Easy to sawp 3.3V to 5V                          | Not Robust for a finished PCB |
    |Good standalone testing when team power isnt ready |




**Choice:** Option 1: ESP32

**Rationale:** I choose to use a shared 5V supply with a local 3.3V regulator on the distance sensor subsystem. This minimizes the system wiring complexity while providing clean stable power for the ESP32 and ToF Sensor


