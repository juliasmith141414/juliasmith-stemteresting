# API

## 🌈 Overview

The tables below describe the messages sent from the distance sensor subsystem (Julia) using `uint8_t` binary flags (0 = False, 1 = True). All messages are formatted using the class UART protocol and occupy the data field (bytes 5–61) of the 64-byte message frame.

## 📋 Tables

### 🟥 Safety Response Message (to Motor)

🚨 This message tells the motor subsystem whether the user is currently in a safe position.

| Field | Value |
|-------|-------|
| 📦 **Byte 1** | `User_Safe_Flag` |
| 📐 **Variable Type** | `uint8_t` |
| 🔻 **Min Value** | `0` (User Not Safe) |
| 🔺 **Max Value** | `1` (User Safe) |
| 🔢 **Example** | `1` |
| 💡 **Use** | Tells the motor whether to activate based on user position |

### 🟧 OLED Display Message (to OLED)

🖥️ This message instructs the OLED display what message to show based on user status.

| Field | Value |
|-------|-------|
| 📦 **Byte 1** | `OLED_Display_Flag` |
| 📐 **Variable Type** | `uint8_t` |
| 🔻 **Min Value** | `0` (Display 'Stand on X') |
| 🔺 **Max Value** | `1` (Display 'Initializing') |
| 🔢 **Example** | `1` |
| 💡 **Use** | Tells the OLED whether to show initialization or waiting instructions |

### 🟨 Machine Use Status Message (to WiFi)

📶 This message tells the WiFi module whether the machine is currently in use.

| Field | Value |
|-------|-------|
| 📦 **Byte 1** | `Machine_Use_Status` |
| 📐 **Variable Type** | `uint8_t` |
| 🔻 **Min Value** | `0` (Idle) |
| 🔺 **Max Value** | `1` (In Use) |
| 🔢 **Example** | `1` |
| 💡 **Use** | Tells the WiFi module whether the machine is active |
 
## 🔧 MPLAB File Contents Overview

This MPLAB X project implements the firmware for the distance sensor subsystem in our team’s UART-based communication network. It continuously reads simulated distance data and broadcasts key system state messages to other subsystems (Motor, OLED, and WiFi) using a standardized UART protocol.

## 🗂️ Files

<ul style="list-style-type: none; padding-left: 0;">
  <li>
    <a href="https://github.com/user-attachments/files/19400781/CLASSIC_MESSAGE_STRUCTURE.X.zip)" style="color:#ff8c00; text-decoration: none;">📁 <strong>MPLABS Zip File</strong></a>
  </li>
  </ul>

## 📑 Key Features

- **UART Messaging Protocol** 
  Each message follows the class-defined structure:  
  [Prefix1] [Prefix2] [Sender] [Receiver] [Message Type] [Data...] [Suffix1] [Suffix2]  
  All messages are 64 bytes in length and framed for reliability.

- **Subsystem Communication**  
  This subsystem transmits:
  - User distance data (MSG_DISTANCE_DATA) – broadcast to all
  - Safety flag (MSG_SAFETY_RESPONSE) – sent to Motor subsystem
  - Display flag (MSG_OLED_FLAG) – sent to OLED subsystem
  - Machine use status (MSG_MACHINE_STATUS) – sent to WiFi module

- **Timeout Handling & Message Trashing**  
  Messages from the subsystem itself or malformed data are discarded using timer interrupts.

- **Message Forwarding**  
  The subsystem forwards any UART messages not addressed to itself to maintain the daisy-chain topology.

- **Code Structure**  
  The main logic resides in main.c with UART handling and timed messaging built using MCC-generated peripheral drivers (EUSART1, Timer1).


## 🔗 Links

<ul style="list-style-type: none; padding-left: 0;">
  <li>
    <a href="home_page_link_here" style="color:#004dff; text-decoration: none;">🏠 <strong>Home</strong></a>
  </li>
  <li>
    <a href="team_page_link_here" style="color:#004dff; text-decoration: none;">👥 <strong>Team Page</strong></a>
  </li>
</ul>
