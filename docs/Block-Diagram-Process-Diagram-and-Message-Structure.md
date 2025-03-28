---
title: Block Diagram, Process Diagram, and Message Structure
tags:
- tag1
- tag2
---
## Team Block Diagram
This image shows how our individual systems would connect to eachother to send messages over UART. As this is only meant to show the daisy-chain connection, the detainls of each system have been left out. For more detailed versions of the individual systems, check out our individual githubs! <br>
![EGR_314_Team_Block_Diaram-Page-1 drawio](https://github.com/user-attachments/assets/bdf843b4-6444-43c4-8d9b-3085cfe64fee) <br>
[Xander's Human Machine Interface](https://xanderheafey.github.io/Block-Diagram/)<br>
[Sara's Motor](https://sarabohart.github.io/blockdiagram/)<br>
[Julia's Sensor](https://juliasmith141414.github.io/blockdiagram/)<br>
[Ella's Bidirectional Internet Communication](https://starfruwuit.github.io/egr314report/01BlockDiagram/)
## Process Diagram
<br> This process diagram shows how the messages will be transfered over the daisy chain. 
![301 Sequence Diagram](https://github.com/user-attachments/assets/b03f7472-f672-4f33-be5f-4564422824ab) 
## Message Structure
This table details the messages that will be sent between the boards. The identifiers at the begining of the messages show who is sending the message to whom. The messages are labled with English identifiers for ease of reading. <br>

Message Type Byte 1-2 (uint16_t)	|Description	|Byte 1-2 (uint16_t)	|Byte 3 (uint8_t)	|Byte 4 (uint16_t)	|M	|Byte 63 (uint16_t)	|Byte 64 (uint16_t)|
----------------------------------|-------------|---------------------|-----------------|-------------------|---|-------------------|------------------|
1	|Desired speed	|0x01(uint16_t)|H(uint16_t)	|B(uint16_t)	|Change Speed(uint16_t)	|0x6e (uint16_t)	|0x64 (uint16_t)|
2	|User Safe?	|0x02(uint16_t)	|B(uint16_t)	|S(uint16_t)	|Check Distance(unit16_t)	|0x6e (uint16_t)	|0x64 (uint16_t)|
3	|Motor On	|0x03(uint16_t)	|S(uint16_t)	|B(uint16_t)	|Yes(uint16_t)	|0x6e (uint16_t)	|0x64 (uint16_t)|
4	|Motor Off	|0x04(uint16_t)	|S(uint16_t)	|B(uint16_t)	|No(uint16_t)	|0x6e (uint16_t)	|0x64 (uint16_t)|
5	|Direct Drive	|0x05(uint16_t)	|H(uint16_t)	|B(uint16_t)	|Change Direction(uint16_t)	|0x6e (uint16_t)	|0x64 (uint16_t)|
6	|Motor Speed	|0x06(uint16_t)	|B(uint16_t)	|G(uint16_t)	|Speed(uint16_t)	|0x6e (uint16_t)	|0x64 (uint16_t)|

### Key
Systems	| IDS
--------|------------
Xander	|H(uint16_t)
Sara	  |B(uint16_t)
Julia	  |S(uint16_t)
Ella	  |G(uint16_t)

<br>The IDs are assigned based on the sender and receiver's last names, as X would interfear with the brodcast character defined by the course.<br>
### Sample String
For example, the string sent from Xander to Sara concerning the direction and speed of the motor would be written as follows:<br>
**AZHB05YB** <br>
AZ identifies the start of a string<br>
H means that Xander's system is sending the message<br>
B means that the message is meant to be received by Sara's system<br>
1 indicates the direction Sara's motor should spin <br>
5 indicates the speed should be representitive of Jupiter's gravity <br>
YB indicates the end of the string
