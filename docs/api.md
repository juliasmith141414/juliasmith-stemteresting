# API

## Overview

The tables below describe the messages sent from the distance sensor subsystem (ESP32) using `uint8_t` binary flags (`0` = False, `1` = True) or ASCII-encoded numerical data. All messages are formatted using a standardized 64-byte UART protocol and occupy the data field (bytes 5–61) of the message frame.

## Message Tables

### Safety Response Message (to Motor)

This message indicates whether the user is currently in a safe position based on distance readings.

| Field              | Value                        |
|-------------------|------------------------------|
| Byte 1            | `User_Safe_Flag`             |
| Variable Type     | `uint8_t`                    |
| Min Value         | `0` (User Not Safe)          |
| Max Value         | `1` (User Safe)              |
| Example           | `1`                          |
| Purpose           | Controls braking behavior of the motor subsystem |

### OLED Display Message (to OLED)

This message instructs the OLED display what message to show depending on system state.

| Field              | Value                        |
|-------------------|------------------------------|
| Byte 1            | `OLED_Display_Flag`          |
| Variable Type     | `uint8_t`                    |
| Min Value         | `0` (Display 'Stand on X')   |
| Max Value         | `1` (Display 'Initializing') |
| Example           | `0`                          |
| Purpose           | Communicates screen status to user |

### Distance Data Message (to Xander Heafey's Subsystem)

This message transmits the measured distance in millimeters as an ASCII-encoded string.

| Field              | Value                              |
|-------------------|-------------------------------------|
| Bytes 1–N         | ASCII-encoded distance in mm        |
| Variable Type     | `bytes`                             |
| Example           | `"325"`                             |
| Purpose           | Provides real-time distance to Xander’s subsystem for logging or analytics |

### Machine Use Status Message (to WiFi)

This message indicates whether the machine is currently in use or idle.

| Field              | Value                        |
|-------------------|------------------------------|
| Byte 1            | `Machine_Use_Status`         |
| Variable Type     | `uint8_t`                    |
| Min Value         | `0` (Idle)                   |
| Max Value         | `1` (In Use)                 |
| Example           | `1`                          |
| Purpose           | Broadcasts usage status to the WiFi subsystem |

## ESP32 File Overview

This project implements the firmware for the distance sensor subsystem using an ESP32 microcontroller. It continuously reads distance values from the VL53L1X sensor and transmits structured UART messages to the motor, OLED, and WiFi subsystems.

### Files

- [ESP32 VL53L1X Firmware (Zip)](https://github.com/user-attachments/files/20049301/vl53l1x_pico.zip)

### Key Features

- **UART Messaging Protocol**  
  Each message follows the class-defined structure:  
  `[Prefix1] [Prefix2] [Sender] [Receiver] [Message Type/Data...] [Suffix1] [Suffix2]`  
  All messages are framed with `AZ` (prefix) and `YB` (suffix) and padded to 64 bytes if needed.

- **Subsystem Communication**  
  This subsystem transmits:
  - ASCII distance string – to Xander (Data Logger)
  - Binary safety flag – to Motor subsystem
  - Binary display flag – to OLED subsystem
  - Binary machine-use flag – to WiFi module

- **Distance Logic**  
  The system reads distance via I²C from the VL53L1X sensor. Thresholds are applied to determine if the user is standing in a safe zone.

- **Framing and Filtering**  
  Messages not addressed to the ESP32 are forwarded along the daisy-chain bus. Malformed or duplicate messages are filtered out.

- **Timing and Buffer Management**  
  Includes timeout handling, garbage cleanup, and scheduled message transmission via `uasyncio`.

<h2>Additional Links and Files</h2>
<ul>
    <li><a href="https://github.com/user-attachments/files/20049301/vl53l1x_pico.zip">Code Repository File</a></li>
    <li><a href="https://juliasmith141414.github.io/juliasmith-stemteresting/">Home</a></li>
    <li><a href="https://egr314-2025-s-301.github.io/main-page/">Team Page</a></li>
</ul>
