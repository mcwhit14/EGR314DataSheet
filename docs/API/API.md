---
title: API
---

# API

## Subsystem Role

My subsystem is the **distance sensor subsystem** for the rover. Its main role is to measure obstacle distance using a Time-of-Flight distance sensor and determine when the rover is too close to an object. When the measured distance falls below a defined threshold, this subsystem sends a message over the daisy chained UART network to the motor subsystem so the rover can stop and avoid collision. The onboard LED on this PCB is used only as a local debugging and visualization aid, where the flash rate changes based on measured distance, but this LED behavior is not part of the UART API.


---

## Team Message Context

The team message structure already defines standard message types for the overall rover system, including motor reports, environmental sensor data, distance sensor data, system status, error codes, and heartbeat messages. In the team report, **Message Type 12** is defined as **Distance Sensor Data Report**, and the team communication structure shows that the distance sensor subsystem communicates with the rest of the rover over the daisy chained UART network. 

For my subsystem, the most important behavior is not continuously broadcasting every measured distance value, but instead using the distance measurement to determine whether the rover is too close to an obstacle and then sending a message that causes the motor subsystem to stop.

---

## Messages Used by This Subsystem

### Messages Sent by This Subsystem
- **Message Type 12 – Distance Sensor Data Report** 

### Messages Received / Processed by This Subsystem
- **Message Type 16 – Heartbeat / Alive Signal** 
- Any correctly framed packet addressed to another subsystem must be forwarded through the daisy chain. 

### Main Functional Use
This subsystem continuously reads obstacle distance locally, but only acts on the measurement when the obstacle is within a critical stopping threshold. In this design, the chosen stop threshold is:

- **0.50 meters**

If the rover detects an object at or below 0.50 m, it sends a distance message intended for the motor subsystem so that the motor system can stop movement.

---

## Primary Message Definition

### Message Type 12 – Distance Sensor Data Report

According to the team report, Message Type 12 contains the message type followed by a floating point distance value in meters. 

| Byte(s) | Variable Name | C Data Type | Number of Bytes | Minimum Recognized Value | Maximum Recognized Value | Example |
|---|---|---:|---:|---:|---:|---:|
| 1–2 | message_type | uint16_t | 2 | 12 | 12 | 12 |
| 3–6 | distance_m | float | 4 | 0.00 | 6.00 | 0.42 |

**Total payload length:** 6 bytes

### Functional Interpretation
- If `distance_m > 0.50`, the subsystem does not issue an emergency stop request.
- If `distance_m <= 0.50`, the subsystem sends this message to notify the motor subsystem that an obstacle is dangerously close.
- This message is therefore used as the trigger for an emergency stop behavior.

---

## Optional Shared Message

### Message Type 16 – Heartbeat / Alive Signal

The team report defines Message Type 16 as a heartbeat packet containing a system state and error flag. This subsystem can receive or forward heartbeat messages as part of the daisy chained network.

| Byte(s) | Variable Name | C Data Type | Number of Bytes | Minimum Recognized Value | Maximum Recognized Value | Example |
|---|---|---:|---:|---:|---:|---:|
| 1–2 | message_type | uint16_t | 2 | 16 | 16 | 16 |
| 3 | system_state | uint8_t | 1 | 0 | 255 | 1 |
| 4 | error_flag | uint8_t | 1 | 0 | 1 | 0 |

**Total payload length:** 4 bytes

---

## Distance Threshold Logic

The local distance sensor logic is simple:

- The sensor continuously measures obstacle distance.
- The subsystem compares the measured value to a threshold of **0.50 m**.
- If the obstacle is farther than 0.50 m away, no emergency stop message is sent.
- If the obstacle is 0.50 m away or closer, the subsystem sends a UART message to the motor subsystem indicating a dangerous obstacle condition.

This design reduces unnecessary network traffic while still ensuring the rover can quickly stop when an object is too close.

---

## Local LED Behavior

The LED on this board is a local debugging feature and is not part of the UART communication protocol. Its purpose is to visually indicate how close an object is to the rover.

### LED behavior
- **Far object** → LED flashes slowly
- **Closer object** → LED flashes faster
- **Very close object** → LED flashes very rapidly
- **Obstacle ≤ 0.50 m** → subsystem also sends an emergency stop-related distance message to the motor subsystem

This allows quick visual testing of the subsystem without needing to inspect UART traffic.

---

## Receiver Requirements

The receiver on this subsystem will:

1. Read all incoming UART packets from the daisy-chained network.
2. Ignore characters received outside a valid packet frame.
3. Ignore malformed packets.
4. Ignore packets larger than the defined buffer size.
5. Discard messages that originated from this subsystem and have looped back.
6. Forward packets intended for another subsystem.
7. Process packets addressed to this subsystem.
8. Send a unique acknowledgement whenever a correctly formatted message is received.

---

## Sender Requirements

The sender on this subsystem will:

1. Read the current obstacle distance from the ToF sensor.
2. Compare the reading against the stop threshold.
3. If the threshold is crossed, build a valid Message Type 12 packet.
4. Ensure the payload size stays within the class protocol limits.
5. Avoid invalid formatting or malformed payload content.
6. Transmit at a controlled rate using non-blocking timing.
7. Prioritize forwarding received messages before sending its own message. 

---

## Example Message Data

### Example 1 – Safe distance
| Field | Value |
|---|---:|
| message_type | 12 |
| distance_m | 1.35 |

Interpretation: obstacle detected, but not close enough to stop the rover.

### Example 2 – Emergency stop condition
| Field | Value |
|---|---:|
| message_type | 12 |
| distance_m | 0.42 |

Interpretation: obstacle is inside the 0.50 m stop threshold, so the motor subsystem should stop the rover.



---

## Example Handling Code

```c
typedef struct {
    uint16_t message_type;
    float distance_m;
} distance_report_t;

distance_report_t tx_distance_msg;

void build_distance_message(float measured_distance) {
    if (measured_distance < 0.0f) {
        measured_distance = 0.0f;
    }

    if (measured_distance > 6.0f) {
        measured_distance = 6.0f;
    }

    tx_distance_msg.message_type = 12;
    tx_distance_msg.distance_m = measured_distance;
}
