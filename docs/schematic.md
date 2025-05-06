# Final Schematic and PCB Design

## Overview

This page documents the final schematic and PCB layout of my distance sensor subsystem. It uses an ESP32-S3-WROOM-1-N4 microcontroller to control a VL53L1X Time-of-Flight sensor and transmit processed data via UART. The board was designed using Altium, with all components selected to be surface-mount and suitable for hand soldering. The system includes regulated power from a 3.3V switching regulator, UART and I²C communication, an onboard OLED for debugging, and expansion headers.

This hardware design enables the subsystem to:
- Continuously collect distance readings
- Classify the distance as safe (1) or unsafe (0)
- Transmit results via UART to teammate subsystems
- Optionally display raw distance on an OLED screen during debugging

---

## Schematic

![schematic](https://github.com/user-attachments/assets/f99bc89f-4a74-4043-bd7c-da7d3043d4cf)

Key features:
- ESP32-S3-WROOM-1-N4 microcontroller
- VL53L1X sensor via I²C (IO5, IO4)
- OLED screen via I²C (IO7, IO6)
- UART TX to downstream (IO17), RX from upstream (IO46)
- USB programming via IO19 (D-) and IO20 (D+)
- EN (IO3) connected to reset button
- Bypass capacitors and pull-ups per datasheets
- 0.1 µF caps on each power pin
- Switchable power from either barrel jack or ribbon cable

---

## PCB Top Layer
<img width="548" alt="top_pcb" src="https://github.com/user-attachments/assets/3b97d5df-dba3-4d25-bcd7-1ae6f64a5ea8" />

## PCB Bottom Layer
<img width="548" alt="bottom_pcb" src="https://github.com/user-attachments/assets/e360e623-efd1-489b-94ce-e66cfdb09660" />

## PCB 3D View
<img width="551" alt="3d_pcb_top" src="https://github.com/user-attachments/assets/219c89c0-2678-4348-9a92-8da911ca9e9a" />

## Final Team PCBs Top View
![IMG_3495](https://github.com/user-attachments/assets/319744ac-c69b-4caa-bee4-9716b6aa9672)

## Final Team PCBs Bottom View
![IMG_3496](https://github.com/user-attachments/assets/9721313e-c11a-46b6-ab50-37a94a1b4dd8)

## Functionality Justification

This schematic satisfies all subsystem and user requirements by:
- Ensuring reliable sensor readings with millimeter accuracy
- Providing real-time binary decision data over UART
- Including an OLED to visually debug distance readings
- Supporting USB programming with no extra hardware
- Allowing safe operation near dangerous machinery

The ESP32’s I/O multiplexing allowed flexible pin routing. All signal types were considered (I²C, UART, digital out). The regulator supports a wide 9–12V input and provides clean 3.3V power.

---

## Design and Decision-Making Process

Design began with modeling the sensor and ESP32 on a breadboard. Once UART and I²C worked reliably, the schematic was designed with all required features: USB programming, power switching, debugging pins, pullups, and a reset switch. The PCB layout emphasized hand-solderability, avoiding fine-pitch ICs.

Ribbon cable integration was double-checked to ensure correct signal direction and voltage compatibility. Extra test pads and headers were added to future-proof the board.

---

## Proposed Improvements for Version 2.0

If a Version 2.0 were developed, I would:
- Move the sensor closer to the board edge to improve line-of-sight
- Use a smaller 3.3V regulator with integrated passives to save board space
- Add a dedicated I²C multiplexer to simplify bus sharing with OLED
- Include current measurement test pads for debugging power consumption
- Add a screw terminal for secure off-board wiring

These enhancements would reduce board size, improve debugging, and better isolate each feature.

---

## Files and Links

- [Altium Project ZIP](https://github.com/user-attachments/files/20047940/altium_distance_sensor.zip)
- [Gerber Files ZIP](https://github.com/user-attachments/files/20051808/Project.Outputs.for.PCB_Projectfinalfinal.zip)
- [Schematic PDF](https://github.com/user-attachments/files/20047904/JAS_SCHEMATIC_ESP32.pdf)
- [Home Page](https://juliasmith141414.github.io/)
- [Team Page](https://egr314-2025-s-301.github.io/main-page/)
