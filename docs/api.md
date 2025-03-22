# API
This table describes the messages sent from the distance sensor subsystem (Julia) using `uint8_t` binary flags (0 = False, 1 = True). All messages are formatted using the class UART protocol and occupy the data field (bytes 5–61) of the 64-byte message frame.
 
## Safety Response Message (to Motor)

This message tells the motor subsystem whether the user is currently in a safe position.

| Field           | Value |
|-----------------|-------|
| **Byte 1**      | `User_Safe_Flag` |
| **Variable Type** | `uint8_t` |
| **Min Value**     | `0` (User Not Safe) |
| **Max Value**     | `1` (User Safe) |
| **Example**       | `1` |
| **Use**           | Tells the motor whether to activate based on user position |

---

## OLED Display Message (to OLED)

This message instructs the OLED display what message to show based on user status.

| Field           | Value |
|-----------------|-------|
| **Byte 1**      | `OLED_Display_Flag` |
| **Variable Type** | `uint8_t` |
| **Min Value**     | `0` (Display 'Stand on X') |
| **Max Value**     | `1` (Display 'Initializing') |
| **Example**       | `1` |
| **Use**           | Tells the OLED whether to show initialization or waiting instructions |

---

## Machine Use Status Message (to WiFi)

This message tells the WiFi module whether the machine is currently in use.

| Field           | Value |
|-----------------|-------|
| **Byte 1**      | `Machine_Use_Status` |
| **Variable Type** | `uint8_t` |
| **Min Value**     | `0` (Idle) |
| **Max Value**     | `1` (In Use) |
| **Example**       | `1` |
| **Use**           | Tells the WiFi module whether the machine is active |
