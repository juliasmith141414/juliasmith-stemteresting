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

This section compares three microcontroller options for the subsystem: the ESP32-S3-WROOM-1-N4 (final selection), the PIC18F47Q10 (original classroom-based choice), and the ESP32-WROOM-32 (a popular alternative ESP variant). The comparison focuses on communication flexibility, compatibility with I2C peripherals, ease of development, and solderability.

---

### [ESP32-S3-WROOM-1-N4](https://www.digikey.com/en/products/detail/espressif-systems/ESP32-S3-WROOM-1-N4/16162639) – $5.06  
![MFG_Attachment-2-ESP32-S3-WROOM-1](https://github.com/user-attachments/assets/375f18d5-2e0d-474b-b8d2-364e079eaf60)

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
| Flexible I2C pin assignments | Slightly higher power consumption |
| Built-in Wi-Fi + BLE | Slightly more expensive |
| Fast dev cycle using MicroPython or Arduino | |
| Community support and driver libraries | |

---

### [PIC18F47Q10](https://www.digikey.com/en/products/detail/microchip-technology/pic18f47q10-i-pt/10187786) – ~$3.00  
![pic](https://github.com/user-attachments/assets/3443e163-f268-498f-bc5c-8a70c2ffd998)

| **Specs** | **Value** |
|-----------|-----------|
| Package | TQFP-44 or DIP |
| Supply Voltage Range | 1.8–5.5 V |
| Max Current | ~200 mA |
| Max GPIO Current | ~25 mA per pin |
| Interfaces | UART, I2C, SPI, ADC, PWM, GPIO |
| Wireless | None |
| External Interrupts | Supported |

| **Pros** | **Cons** |
|----------|----------|
| Familiar from in-class labs | No built-in wireless |
| Wide voltage input range | Fewer libraries and slower development |
| Supported by MCC in MPLAB X | Limited RAM and speed |
| Easy to solder and test in lab | Not as flexible with I2C/SPI pins |

---

### [ESP32-WROOM-32UE-N4](https://www.digikey.com/en/products/detail/espressif-systems/ESP32-WROOM-32UE-N4/11613136) – $4.40  
![ESP32-WROOM-32UE-N4](https://github.com/user-attachments/assets/6f7ffa71-822c-4632-82b7-8f0d28e40bcc)


| **Specs** | **Value** |
|-----------|-----------|
| Package | PCB surface-mount module |
| Supply Voltage Range | 2.3–3.6 V |
| Max Current | ~500 mA |
| Max GPIO Current | 40 mA per pin |
| Interfaces | UART, I2C, SPI, ADC, PWM, GPIO |
| Wireless | Wi-Fi + BLE (U.FL external antenna) |
| External Interrupts | Supported |
| CPU | Dual-core Xtensa @ 240 MHz |
| Flash | 4 MB |
| RAM | 520 KB |

| **Pros** | **Cons** |
|----------|----------|
| U.FL connector for external antenna improves wireless signal in enclosures | Fewer hardware instructions compared to S3 |
| Dual-core performance for multitasking | Fewer GPIOs due to flash memory sharing pins |
| Lower cost than ESP32-S3-WROOM-1-N4 | No vector instructions or advanced acceleration |
| Well-supported in Arduino and ESP-IDF | Slightly older architecture with fewer new libraries |

**Why Not Chosen:**  
While the ESP32-WROOM-32UE-N4 offers excellent wireless connectivity with an external antenna and a similar power envelope to the S3, it lacks some critical performance features. Most notably, it does not support vector instructions or hardware acceleration required for advanced peripherals. Additionally, GPIO allocation is less flexible due to internal flash wiring, which increases the risk of pin conflicts. Given our system's reliance on reliable I²C communication and the potential need for multiple peripherals, the S3’s improved I/O multiplexing and library compatibility made it the better fit for our design.

---


### Comparison Table

| Feature                    | **ESP32-S3-WROOM-1-N4** | **ESP32-WROOM-32** | **PIC18F47Q10** |
|----------------------------|--------------------------|---------------------|------------------|
| Wireless                   | Wi-Fi + BLE              | Wi-Fi + BLE         | ❌ None          |
| I2C Pin Flexibility        | Any GPIO                 | Limited             | Limited          |
| Development Environment    | MicroPython / Arduino    | Arduino / ESP-IDF   | MPLAB X + MCC    |
| Processing Power           | Dual-core w/ vector ops  | Dual-core           | Single-core      |
| Memory (RAM / Flash)       | 512KB RAM / 8MB Flash     | 520KB / 4MB         | 4KB RAM / 64KB Flash |
| Power Consumption          | Higher                   | Medium              | Low              |
| Ease of Use in Lab         | Moderate                 | High (dev boards)   | High             |
| Community / Library Support| Extensive                | Strong              | Moderate         |
| Price                     | $5.06                    | ~$4.50              | ~$3.00           |

---

**✅ Final Selection: ESP32-S3-WROOM-1-N4**  
This microcontroller was chosen for its combination of power, flexibility, and compatibility. It supports all needed communication protocols (especially I2C) with flexible GPIO assignment, integrates Wi-Fi and BLE for potential future use, and is backed by strong community support. While it is slightly more expensive than the other two options, its ability to simplify both firmware and hardware integration justifies the cost in the context of our design needs.


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
## ESP32-S3-WROOM-1-N4

| **ESP Info**                                | **Answer**                                  |
|---------------------------------------------|----------------------------------------------|
| Model                                        | ESP32-S3                                     |
| Product Page URL                            | [Link](https://www.espressif.com/en/products/socs/esp32-s3) |
| ESP32-S3-WROOM-1-N4 Datasheet URL           | [Datasheet](https://www.espressif.com/sites/default/files/documentation/esp32-s3-wroom-1_wroom-1u_datasheet_en.pdf) |
| ESP32 S3 Datasheet URL                      | [Datasheet](https://www.espressif.com/sites/default/files/documentation/esp32-s3_datasheet_en.pdf) |
| ESP32 S3 Technical Reference Manual URL     | [Technical Manual](https://www.espressif.com/sites/default/files/documentation/esp32-s3_technical_reference_manual_en.pdf) |
| Vendor link                                 | [DigiKey](https://www.digikey.com/en/products/detail/espressif-systems/ESP32-S3-WROOM-1-N4/16162639) |
| Code Examples                               | [Github](https://github.com/drakxtwo/vl53l1x_pico.git)|
| External Resources URL(s)                   | [Awesome MicroPython](https://awesome-micropython.com/?utm_source=chatgpt.com#distance-ir) |
| Unit cost                                   | $5.06                                        |
| Absolute Maximum Current for entire IC      | 0.5A                                         |
| Supply Voltage Range                        | 3.0 (min) / 3.3 (nominal) / 3.6 (max)        |
| Maximum GPIO current (per pin)              | 40 mA                                        |
| Supports External Interrupts?               | Yes                                          |
| Required Programming Hardware, Cost, URL    | [Link](https://docs.espressif.com/projects/esp-idf/en/stable/esp32s3/get-started/index.html) |

## Distance Sensor Needs for ESP 32

| Module          | # Available | Needed | Pins Chosen                         |
|-----------------|-------------|--------|-------------------------------------|
| UART2           | 3           | 1      | IO17 (TX), IO46 (RX)                |
| I2C (Sensor)    | 5           | 1      | IO5 (SCL), IO4 (SDA)                |
| I2C (OLED)      | 4           | 1      | IO7 (SCL), IO6 (SDA)                |
| GPIO (LEDs)     | 33          | 5      | IO14, IO21, IO47, IO48, IO45        |
| USB Programmer  | 4           | 2      | IO19 (D-), IO20 (D+)                |
| Reset Switch    | 1           | 1      | IO3 (EN)                            |

## Final Major Components Selected

| **Component**      | **Part Number**             | **Source** | **Unit Price** |
|-------------------|-----------------------------|------------|----------------|
| Voltage Regulator | LM2575D2T-3.3R4G            | DigiKey    | $3.32          |
| Microcontroller   | ESP32-S3-WROOM-1-N4         | DigiKey    | $5.06          |
| Distance Sensor   | VL53L1X (Adafruit 3967)     | DigiKey    | $14.95         |

These components meet the project's design goals for sensor control, data processing, and communication. Their solderability and known compatibility with each other ensured fast prototyping and successful integration.

## Power Budget
The power budget (below) shows the maximum current each major component pulls from the power supply and the maximum current the power supply can provide. 
![powerbudget](https://github.com/user-attachments/assets/13dd7ff3-c585-48f6-b871-d8983342dfea)

Upon testing it is clear this power budget is accurate. The subsystem works as expected with no exceptions. 


---
<h2>Additional Links</h2>
<ul>
    <li><a href="https://github.com/user-attachments/files/20051370/Julia.Power.Budget.-.Sheet1.1.pdf">Power Budget PDF</a></li>    
    <li><a href="https://juliasmith141414.github.io/juliasmith-stemteresting/">Home</a></li>
    <li><a href="https://egr314-2025-s-301.github.io/main-page/">Team Page</a></li>
</ul>
---
