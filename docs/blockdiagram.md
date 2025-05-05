# Block Diagram
## Block Diagram of Subsystem: Distance Sensor

This is the block diagram for our distance sensor subsystem. The sensor will collect and send distance data constantly when the subsystem is powered on. Raw distance data will be sent to Xander Heafey's OLED subsystem so it can be displayed on his screen when the user selects it. Logic inside the distance sensor subsystem code will assign either a 0 or 1 to distance results based on whether the user is a safe distance from the spinning centrifuge. These values are then sent over UART to Sara Bohart's motor driver subsystem and Ella Greetis's MQTT subsystem.
<br>
<br>
This block diagram was developed with user safety in mind. UART endures fast enough communication for fast response times. I added an OLED screen to my subsystem as well, to make debugging easier.
<br>

![Smith Individual Block Diagram drawio](https://github.com/user-attachments/assets/62a99dc5-8048-45bb-b4ae-7a00291f79a5)


<h2>Additional Links</h2>
<ul>
    <li><a href="https://drive.google.com/file/d/1-fcG4vHEsaQ0qRLLkd0bO_16-h85Aeg2/view?usp=sharing">Block Diagram Link</a></li> <br>
    <li><a href="file:///C:/Users/Owner/Downloads/Smith%20Individual%20Block%20Diagram.drawio.pdf">Block Diagram PDF</a></li> <br>
    <li><a href="https://juliasmith141414.github.io/juliasmith-stemteresting/">Home</a></li>
    <li><a href="https://egr314-2025-s-301.github.io/main-page/">Team Page</a></li>
</ul>


