# Component Selection

This document compares and justifies the selection of major electrical components used in my subsystem. All components are surface-mount and suitable for hand-soldering or reflow, based on Peralta lab constraints.

---

## 3.3V Voltage Regulator

### Option 1: [LM2575D2T-3.3R4G](https://www.digikey.com/en/products/detail/onsemi/LM2575D2T-3-3R4G/1476688?s=N4IgTCBcDaIDIFkwFYDsyAiYAqBaAzAHT4BKALAOIgC6AvkA) – $3.32
![LM2575D2T-3 3R4G](https://github.com/user-attachments/assets/f6508738-157a-43e2-9fbc-c0e109be11c5)

| **Pros** | **Cons** |
|----------|----------|
| 1A output current capacity | Large footprint |
| Fixed 3.3V simplifies design | Requires external diode and inductor |
| Easy to hand solder (TO-263-5) | Less efficient than modern buck converters |
| Previously used in other circuits | |

### Option 2: [TPS62152RGTR](https://www.digikey.com/en/products/detail/texas-instruments/TPS62152RGTR/2833441?s=N4IgTCBcDaICoAUDKA2MBGArGASgcThxAF0BfIA) – $1.42
![TPS62152RGTR](https://github.com/user-attachments/assets/eaa7be34-4257-473a-9a6d-83de6231d573)

| **Pros** | **Cons** |
|----------|----------|
| Compact package saves board space | QFN package difficult to solder by hand |
| Low cost | Requires multiple external passives |
| Fixed output simplifies design | No in-class experience with part |


### Option 3: [LM3671MF-3.3/NOPB](https://www.digikey.com/en/products/detail/texas-instruments/LM3671MF-3-3-NOPB/1590062?s=N4IgTCBcDaIDIFkDMA2A7ARgQMQLRIDokB6AOQHkAFAIRAF0BfIA) – $1.56
![LM3671MF-3 3](https://github.com/user-attachments/assets/83e80638-460a-4973-ab18-f6ed9c3c28aa)

| **Pros** | **Cons** |
|----------|----------|
| Smallest footprint of the three | Max output only 500 mA |
| SOT-23-5 package is easier to solder than QFN | Narrow input voltage range (2.7–5.5V) |
| Low quiescent current | |

**✅ Final Selection: LM2575D2T-3.3R4G**  
Chosen due to my familiarity with the component and the ease of soldering. While larger, it fits within our board space and supplies 1A, ensuring headroom for future expansion.

---

## Microcontroller Selection

### [ESP32-S3-WROOM-1-N4](https://www.digikey.com/en/products/detail/espressif-systems/ESP32-S3-WROOM-1-N4/16162639) – $5.06

| **Specs** | **Value** |
|-----------|-----------|
| Package | PCB surface-mount module |
| Supply Voltage Range | 3.0–3.6 V |
| Max Current | 500 mA |
| Max GPIO Current | 40 mA per pin |
| Interfaces | UART, I2C, SPI, ADC, PWM, GPIO |
| Wireless | Wi-Fi + BLE |
| External Interrupts | Supported |

| **Pros** | **Cons** |
|----------|----------|
| All GPIOs are flexible for I2C/UART | Slightly higher power consumption |
| Integrated Wi-Fi/BLE | More expensive than PIC18F47Q10 |
| Strong community and library support | |
| Fast development in MicroPython/Arduino | |

### Comparison with PIC18F47Q10

| **ESP32-S3-WROOM-1-N4** | **PIC18F47Q10** |
|-------------------------|------------------|
| Wi-Fi + BLE integrated | No wireless |
| Flexible GPIO mapping for I2C/SPI | Limited multiplexing |
| Faster CPU, more memory | Lower power consumption |
| More dev tools (VSCode, Arduino, MicroPython) | Requires MPLAB X / MCC |
| Better documentation for peripherals | Easier to learn in classroom context |

**✅ Final Selection: ESP32-S3-WROOM-1-N4**  
While initially working with the PIC18F47Q10, we switched to the ESP32 for its robust I2C support, GPIO flexibility, and fast prototyping tools. The switch was driven by sensor/display compatibility and ease of development.

---

## Distance Sensor

### [VL53L1X – Adafruit 3967](https://www.digikey.com/en/products/detail/adafruit-industries-llc/3967/17039169) – $14.95
![3967_distance_sensor](https://github.com/user-attachments/assets/78ddf26a-1d17-4409-8e99-2303e3e02603)\

| **Pros** | **Cons** |
|----------|----------|
| Up to 4m range | More expensive than analog options |
| Millimeter-level accuracy | Requires initialization/config |
| I2C interface for easy integration | |
| Library support available for ESP32 | |

### Option 2: [VL53L0X](https://www.adafruit.com/product/3317) – ~$12.50
![VL53L0X](https://github.com/user-attachments/assets/66e0db2a-4128-443d-b49a-b20d7abafcdc)

| **Pros** | **Cons** |
|----------|----------|
| Lower cost | 2m max range only |
| Good library support | Less suited for large distance |
| Small module | |

### Option 3: [SparkFun VL6180 Time-of-Flight Distance Sensor – Qwiic](https://www.adafruit.com/product/3316) – $13.95
![VL6180X](https://github.com/user-attachments/assets/597eadc2-a19e-4f6a-8bef-822d20d8cbea)

| **Pros** | **Cons** |
|----------|----------|
| I²C communication via Qwiic connector | Shorter range (0–200 mm) |
| Well-documented Arduino and ESP32 libraries | Less accurate at longer distances |
| Compact and low power consumption | |
| Easy integration with other Qwiic-compatible devices | |

This option is useful in applications where close-range detection is sufficient and rapid setup is preferred due to the Qwiic system’s plug-and-play design. While it lacks the extended range of the VL53L1X, it offers reliable performance in short-distance sensing tasks and fully meets the I²C communication requirement.


**✅ Final Selection: VL53L1X**  
Selected for its accuracy, compatibility with our ESP32-based subsystem, and wide sensing range. Surface-mount breakout simplifies PCB integration and library support accelerates development.

---

## Final Major Components Selected

| **Component**      | **Part Number**             | **Source** | **Unit Price** |
|-------------------|-----------------------------|------------|----------------|
| Voltage Regulator | LM2575D2T-3.3R4G            | DigiKey    | $3.32          |
| Microcontroller   | ESP32-S3-WROOM-1-N4         | DigiKey    | $5.06          |
| Distance Sensor   | VL53L1X (Adafruit 3967)     | DigiKey    | $14.95         |

These components meet the project's design goals for sensor control, data processing, and communication. Their solderability and known compatibility with each other ensured fast prototyping and successful integration.
