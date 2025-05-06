# Block Diagram
![Smith Individual Block Diagram drawio](https://github.com/user-attachments/assets/62a99dc5-8048-45bb-b4ae-7a00291f79a5)<br>
This is the block diagram for my distance sensor subsystem. The sensor will collect and send distance data constantly when the subsystem is powered on. Raw distance data will be sent to Xander Heafey's OLED subsystem so it can be displayed on his screen when the user selects it. Logic inside the distance sensor subsystem code will assign either a 0 or 1 to distance results based on whether the user is a safe distance from the spinning centrifuge. These values are then sent over UART to Sara Bohart's motor driver subsystem and Ella Greetis's MQTT subsystem.
<br>
<br>
This block diagram was developed with user safety in mind. UART endures quick enough communication for fast response times. I added an OLED screen to my subsystem as well, to make debugging easier. A reset switch, connected to the engage pin on the ESP 32, ensures progamming is updated efficiently.

### Decision-Making Process
I started by identifying each component required for my subsystem: the ESP32-S3 microcontroller, the VL53L1X distance sensor, an optional OLED for debugging, and UART connections to other subsystems. I verified compatibility using datasheets and ensured that all chosen components were solderable and power-compatible. I planned wiring and signal flow to prioritize safety-critical latency and avoid GPIO conflicts. The layout reflects actual hardware tests on the breadboard.

### Alignment with Product Requirements
This block diagram satisfies the product requirements by ensuring the user is warned or protected when approaching dangerous distances from the centrifuge. It includes UART-based data sharing to teammates and a visual OLED interface for real-time debugging. All signals are labeled and directional, components are properly boxed by voltage, and all I/O and power needs are represented based on real testing. The UART, I2C, and GPIO pin allocations directly correspond to the pinout diagram in my component selection document.

<h2>Additional Links</h2>
<ul>
    <li><a href="https://drive.google.com/file/d/1-fcG4vHEsaQ0qRLLkd0bO_16-h85Aeg2/view?usp=sharing">Block Diagram Link</a></li>
    <li><a href="https://github.com/user-attachments/files/20051273/block.pdf">Block Diagram PDF</a></li>
    <li><a href="https://juliasmith141414.github.io/juliasmith-stemteresting/">Home</a></li>
    <li><a href="https://egr314-2025-s-301.github.io/main-page/">Team Page</a></li>
</ul>


