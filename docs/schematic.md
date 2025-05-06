# Schematic

## Overview

This page documents the final schematic and PCB layout of my distance sensor subsystem. It uses an ESP32-S3-WROOM-1-N4 microcontroller to control a VL53L1X Time-of-Flight sensor and transmit processed data via UART. The board was designed using Altium, with all components selected to be surface-mount and suitable for hand soldering. The system includes regulated power from a 3.3V switching regulator, UART and I²C communication, an onboard OLED for debugging, and expansion headers.

This hardware design enables the subsystem to:
- Continuously collect distance readings
- Classify the distance as safe (1) or unsafe (0)
- Transmit results via UART to teammate subsystems
- Optionally display raw distance on an OLED screen during debugging

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

## Bill of Materials
The bill of Materials below shows the necessary components to build one complete distance sensor subsystem board.
<img width="796" alt="BOM" src="https://github.com/user-attachments/assets/448b0d76-822a-4298-a584-1d6c9d30a84a" />

## Functionality Justification

This schematic satisfies all subsystem and user requirements by:
- Ensuring reliable sensor readings with millimeter accuracy
- Providing real-time binary decision data over UART
- Including an OLED to visually debug distance readings
- Supporting USB programming with no extra hardware
- Allowing safe operation near dangerous machinery

The ESP32’s I/O multiplexing allowed flexible pin routing. All signal types were considered (I²C, UART, digital out). The regulator supports a wide 9–12V input and provides clean 3.3V power.

## Design and Decision-Making Process

Design began with modeling the sensor and ESP32 on a breadboard. Once UART and I²C worked reliably, the schematic was designed with all required features: USB programming, power switching, debugging pins, pullups, and a reset switch. The PCB layout emphasized hand-solderability, avoiding fine-pitch ICs.

Ribbon cable integration was double-checked to ensure correct signal direction and voltage compatibility. Extra test pads and headers were added to future-proof the board.

## Proposed Improvements for Version 2.0
If a Version 2.0 were developed, I would fix some problems I ran into. Specifically the pin choice for SCL and SDA lines. Originally I picked two SDA and SCL lines; keeping the bus for the distance sensor and the OLED screen seperate. This was an unecessary precaution on my part. In a perfected version I would use a dedicated I²C multiplexer to simplify bus sharing with the OLED and distance sensor. Additionally, in the schematic above the selected SCL2 line is on IO39; a dedicated boot pin. This mistake necessitated that I cut the trace to the SCL2 line, and manually jump the boot pin to GND in order to flash the ESP 32. This is cumbersome and inefficient. The manual boot method also increases the likely hood of accidentally shorting the device and causing damage. To circumvent this, IO39 should be connected to a switch identical to the setup for the EN pin. This would allow the user to initialize boot with a button instead; saving time and reducing the possibility for error. In turn the SDA and SCL lines would be shared between the oled and distance sensor.

I would also remove the unecesary debug headers and 0 ohm resistors once the design was perfected. I would also use an alternate variation on the female usb connector (B4) that lay parallel to the baord instead of perpendicular in order to prioritize sturdiness. 

In order to operate reliably in any environment, a clamp should be placed on the D+ and D- lines between the USB connector (B4) and the ESP 32 (A1). This ensures consistent operation even when other noise is present.

Overall the initial PCB operated very well because I used breakout debug headers everywhere. If I was unsure of a component's placement, I added a header, or  0 ohm resistor. This allowed me to make changes even after receiving the board.

I would also like to eliminate the need for the daughter board entirely. Fabrication and budget limitations led me to use the daughter board version of the distance sensor, however, idealy, these would be custom fabricated on a smaller, seperate PCB. Overall, this would reduce the price of manfacuring on large scales by about $9.00 per board. 

These enhancements would reduce board size, improve debugging, and better isolate each feature.

<h2>Files and Links</h2>
<ul>
    <li><a href="https://github.com/user-attachments/files/20047904/JAS_SCHEMATIC_ESP32.pdf">Schematic PDF</a></li>
    <li><a href="https://github.com/user-attachments/files/20047940/altium_distance_sensor.zip">Altium Project ZIP</a></li>
    <li><a href="https://github.com/user-attachments/files/20051808/Project.Outputs.for.PCB_Projectfinalfinal.zip">Gerber Files ZIP</a></li>
    <li><a href="https://github.com/user-attachments/files/20051945/JULIA.BOM.-.Sheet1.pdf">Bill of Materials PDF</a></li><br>
    <li><a href="https://juliasmith141414.github.io/">Home</a></li>
    <li><a href="https://egr314-2025-s-301.github.io/main-page/">Team Page</a></li>
</ul>
