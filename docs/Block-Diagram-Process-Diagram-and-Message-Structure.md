---
title: Block Diagram, Process Diagram, and Message Structure
tags:
- tag1
- tag2
---
## Team Block Diagram
![EGR_314_Team_Block_Diaram-Page-1 drawio](https://github.com/user-attachments/assets/bdf843b4-6444-43c4-8d9b-3085cfe64fee) <br>
This image shows how our individual systems would connect to eachother to send messages over UART. As this is only meant to show the daisy-chain connection, the detainls of each system have been left out. For more detailed versions of the individual systems, check out our individual githubs! <br>
[Xander's Human Machine Interface](https://xanderheafey.github.io/Block-Diagram/)<br>
[Sara's Motor](https://sarabohart.github.io/blockdiagram/)<br>
[Julia's Sensor](https://juliasmith141414.github.io/blockdiagram/)<br>
[Ella's Bidirectional Internet Communication](https://starfruwuit.github.io/egr314report/01BlockDiagram/)
## Process Diagram
![301 Sequence Diagram](https://github.com/user-attachments/assets/b03f7472-f672-4f33-be5f-4564422824ab) <br>
This process diagram shows how the messages will be transfered over the daisy chain. 
## Message Structure
### Key
Systems	| IDS
--------|------------
Xander	|XH(uint16_t)
Sara	  |SB(uint16_t)
Julia	  |JS(uint16_t)
Ella	  |EG(uint16_t)

Message Type Byte 1-2 (uint16_t)	|Description	|Byte 1-2 (uint16_t)	|Byte 3 (uint8_t)	|Byte 4 (uint16_t)	|M	|Byte 63 (uint16_t)	|Byte 64 (uint16_t)|
----------------------------------|-------------|---------------------|-----------------|-------------------|---|-------------------|------------------|
1	|Desired speed	|0x01(uint16_t)|XH(uint16_t)	|SB(uint16_t)	|Change Speed(uint16_t)	|0x6e (uint16_t)	|0x64 (uint16_t)|
2	|User Safe?	|0x02(uint16_t)	|SB(uint16_t)	|JS(uint16_t)	|Check Distance(unit16_t)	|0x6e (uint16_t)	|0x64 (uint16_t)|
3	|Motor On	|0x03(uint16_t)	|JS(uint16_t)	|SB(uint16_t)	|Yes(uint16_t)	|0x6e (uint16_t)	|0x64 (uint16_t)|
4	|Motor Off	|0x04(uint16_t)	|JS(uint16_t)	|SB(uint16_t)	|No(uint16_t)	|0x6e (uint16_t)	|0x64 (uint16_t)|
5	|Direct Drive	|0x05(uint16_t)	|XH(uint16_t)	|SB(uint16_t)	|Change Direction(uint16_t)	|0x6e (uint16_t)	|0x64 (uint16_t)|
6	|Motor Speed	|0x06(uint16_t)	|SB(uint16_t)	|EG(uint16_t)	|Speed(uint16_t)	|0x6e (uint16_t)	|0x64 (uint16_t)|
