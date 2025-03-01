# Component Selection

## Objective
The purpose of this page is to compare, and contrast multiple solutions for each major component in my subsystem design. This includes identifying off-the-shelf and custom electrical or mechanical components, assessing compatibility with project specifications, and articulating rationale for final choices.

## Electrical Block Diagram
<img width="444" alt="block diagram image on git" src="https://github.com/user-attachments/assets/f0ce3cfd-3833-4a22-a8e6-265df952e3ed" style="max-width: 300px; height: auto;" /> <br>

This diagram outlines the key components and subsystems: microcontroller, distance sensor (via I²C), motor driver, and actuators. Each subsystem requires separate research and component selection.

---

## Major Component Selections

### **Microcontroller: PIC18F47Q10-I/PT**
<img src="https://github.com/user-attachments/assets/2f574860-11a0-4407-83ab-fafb947c047d" width="300" height="300" /> <br>
**Cost:** $1.49 <br>
**Operating Voltage:** 1.8V - 5.5V <br>
[Datasheet](https://arizonastateu-my.sharepoint.com/:b:/g/personal/jasmi157_sundevils_asu_edu/EY412CZrEBFCm1RPcBUdK0ABFQC27qYPnXhWjqNXUzvurw?e=bMb4OQ)  

| **Pros**                                                  | **Cons**                                                |
|-----------------------------------------------------------|---------------------------------------------------------|
| Compatible with **MPLab Snap Programmer**                 | Requires **MCC configuration** for all peripherals       |
| Supports **multiple communication protocols** (UART, I²C) | Higher complexity than simpler microcontrollers          |
| Extensively documented with **sample code**               | Surface-mount version may be difficult to solder         |
| Integrated **ADC, PWM, and GPIO**                        | Slightly higher cost than lower-performance alternatives |

---

### **MPLab Snap Programmer: PG160100**
<img src="https://github.com/user-attachments/assets/1ad9faf8-0440-4068-9b8d-6f026b02ac68" width="300" height="400" /> <br>
**Cost:** $14.99
**Operating Voltage:** 1.20V - 5.5V
[Datasheet](https://arizonastateu-my.sharepoint.com/:b:/g/personal/jasmi157_sundevils_asu_edu/EQGcT4hhqEpHhpjXQ1mo-LEBesul2oAfO8pAhaCQ58yQCQ?e=vgC0Pv)  

| **Pros**                                                  | **Cons**                                                |
|-----------------------------------------------------------|---------------------------------------------------------|
| Affordable and **official Microchip support**             | May require **firmware updates**                        |
| **Compatible** with multiple PIC microcontrollers         | Limited debugging features                              |
| Easy to integrate with **MPLab X IDE**                    | Not as durable as other higher-end programmers          |

---

## **Voltage Regulators**

#### **Option 1: LM2574MX-3.3/NOPB (Chosen)**
<img src="https://github.com/user-attachments/assets/1e9eaddd-e5c4-426c-9f26-3c28b0cb6cc6" width="300" height="300" /> <br>
[Datasheet](https://github.com/user-attachments/files/19035115/LM2574MX-3.3-NOPB.pdf)<br>
**Max Current:** **0.5A**  
**Efficiency:** ~72% at 12V input  
**Operating Voltage:** 4.75V – 40V  
**Switching Frequency:** 52kHz  

| **Pros**                                              | **Cons**                                      |
|-------------------------------------------------------|-----------------------------------------------|
| **Compact and simple step-down (buck) regulator**     | **Lower current capacity (0.5A max)**        |
| **Fixed 3.3V output – no external resistors needed**  | **Requires external inductor & diode**       |
| **Wide input voltage range (4.75V - 40V)**            | **Less efficient than higher-frequency buck converters** |
| **Thermal shutdown & current limiting protection**    | **Lower efficiency (~72%) compared to newer switchers** |
| **Minimal external components required**             | **Limited to applications with low current needs** |

---

#### **Option 2: AMS1117-3.3V (Alternative)**
<img src="https://github.com/user-attachments/assets/d1f93a3a-8333-49b8-9a18-0645716dbe16" width="300" height="300" /> <br>
[Datasheet](https://arizonastateu-my.sharepoint.com/:b:/g/personal/jasmi157_sundevils_asu_edu/EXAMPLE_AMS1117.pdf) 
**Max Current:** **800mA**  
**Efficiency:** **Linear, ~50-60%**  
**Operating Voltage:** **4.5V – 15V**  

| **Pros**                                      | **Cons**                                        |
|-----------------------------------------------|-------------------------------------------------|
| **Small & simple to use (3-pin LDO)**         | **Lower efficiency** compared to switching regulators |
| **Minimal external components required**      | **Dissipates more heat (wasted as power loss)** |
| **Cost-effective & widely available**         | Max **800mA**, less than LM2575                 |
| **Ideal for low-noise applications**         | Requires good heat dissipation if near max load |

---

#### **Option 3: MP2315 Step-Down Regulator (Alternative)**
<img src="https://github.com/user-attachments/assets/0ec08087-8771-4c70-b557-854364f03e4d" width="300" height="300" /> <br>
[Datasheet](https://arizonastateu-my.sharepoint.com/:b:/g/personal/jasmi157_sundevils_asu_edu/EXAMPLE_MP2315.pdf)  
**Max Current:** **2.5A**  
**Efficiency:** **Up to 90%**  
**Operating Voltage:** **4.5V – 24V**  

| **Pros**                                             | **Cons**                                      |
|------------------------------------------------------|-----------------------------------------------|
| **High efficiency (~90%) saves power**               | Requires **external inductor & capacitors**  |
| **Compact size** (SMT, small footprint)              | Slightly more complex than AMS1117          |
| **Supports up to 2.5A** (ideal for high-power loads) | Higher cost than AMS1117                    |
| **Adjustable output voltage available**              | More difficult to solder for beginners       |


---

### **Distance Sensor Options**

#### **Option 1: VL53L1CXV0FY/1**
<img src="https://github.com/user-attachments/assets/60dd9436-97b2-49df-bd5d-6accfdb9a356" width="300" height="300" /> <br>
[Datasheet](https://arizonastateu-my.sharepoint.com/:b:/g/personal/jasmi157_sundevils_asu_edu/EbF6q-VkyolOulMk80JgWMkB3oZ_hcvkSHapQ7gW-guFWQ?e=OiwQhq)  
[Product Link](https://www.digikey.com/en/products/detail/stmicroelectronics/VL53L1CXV0FY-1/8258055)  
**Cost:** $5.77  
**Max Range:** 4 Meters  
**Operating Voltage:** 2.6V - 3.5V  
**FOV:** 27° <br>
**Communication:** I²C  
**Mount:** Surface  

| **Pros**                                                 | **Cons**                                                 |
|----------------------------------------------------------|----------------------------------------------------------|
| **Extended range** up to 4 meters                        | Surface-mount **LGA-16** package may require reflow soldering |
| **I²C communication** simplifies integration with MCUs   | Requires **precise alignment** for accurate measurements  |
| Supports **variable timing budgets** for power efficiency| More expensive than **VL53L0X**                          |
| **Multi-target detection** with programmable distance modes | Sensitive to ambient lighting conditions in some environments |

---

#### **Option 2: VL53L0X**
<img src="https://github.com/user-attachments/assets/e787c161-59c0-4130-a716-be647bf55d72" width="300" height="300" /> <br>
[Datasheet](https://arizonastateu-my.sharepoint.com/:b:/g/personal/jasmi157_sundevils_asu_edu/EVZtUUkWE9xGhCSLo-Ec1scBudzi0_jGqGujjsDPeXDivA?e=c6nOMb)  
[Product Link](https://estore.st.com/en/products/imaging-and-photonics-solutions/time-of-flight-sensors/vl53l0x.html)  
**Cost:** $2.64  
**Max Range:** 2 Meters  
**Operating Voltage:** 2.8V - 3.3V  
**FOV:** 25° <br>
**Communication:** I²C  
**Mount:** Surface  

| **Pros**                                                | **Cons**                                               |
|---------------------------------------------------------|--------------------------------------------------------|
| Compact and **low-cost** sensor for short-range sensing | **Limited range** (up to 1.2 meters)                   |
| Higher FOV of 25°        | **LGA package** can be difficult to solder manually     |
| **Low power consumption** ideal for portable devices    | Sensitive to ambient lighting interference              |

---

#### **Option 3: TMF8801 Time-of-Flight Distance Sensor**
<img src="https://github.com/user-attachments/assets/f16c2f09-108c-432d-8cc9-10be5da8c93b" width="300" height="300" /> <br>
[Datasheet](https://github.com/user-attachments/files/19034104/2304140030_Advanced-Monolithic-Systems-TMF8801-1B_C1852800.pdf) <br>
[Product Link](https://jlcpcb.com/partdetail/Ams-TMF88011B/C1852800)  
**Cost:** $3.57
**Max Range:** 2.5 Meters  
**Operating Voltage:** 2.7V – 3.6V  
**Communication:** I²C  
**Mount:** Surface-Mount (OLGA-12 Package)  
**Field of View:** 3&deg;  

| **Pros**                                                  | **Cons**                                                  |
|-----------------------------------------------------------|-----------------------------------------------------------|
| Compact **surface-mount package** suitable for space-constrained designs | Low FOV of 3°  |
| Operates at **3.3V**, compatible with low-voltage MCUs     | Limited to **2.5 meters** maximum range                   |
| **Low power consumption**, ideal for battery-powered applications | Very small, may be difficult to mount manually      |
| **High accuracy** with minimal ambient light sensitivity  | May require **external components** for optimal operation |


---

### **Final Component Selections**
After evaluating range, cost, and ease of integration, the **VL53L1CXV0FY/1** sensor was selected due to its **extended range capabilities**, **multi-target detection**, and **FOV of 27°**, making it the best fit for our users.

For voltage regulation, the **LM2574MX-3.3/NOPB** was chosen as the final voltage regulator. It provides **moderate efficiency (~72%)**, supports up to **0.5A output current**, and includes **built-in protections** such as thermal shutdown and current limiting. Its **switching regulator design** reduces power dissipation compared to linear regulators, making it a reliable choice for low-power applications within the system.

---

## **Power Budget**
![image](https://github.com/user-attachments/assets/039d18e6-2ede-46cf-98b2-902b85683dc9)  <br>
<h2>Additional Links</h2>
<ul>
    <li><a href="https://docs.google.com/spreadsheets/d/12uf9W3mrbqPYXF1pln1ugqOVY8jhmh9nDuVUHxvh6Tg/edit?usp=sharing">Power Budget Spreadsheet</a></li>
    <li><a href="https://arizonastateu-my.sharepoint.com/:b:/g/personal/jasmi157_sundevils_asu_edu/EY98v2uzDuJGu2QtrsfiZEkBGJH39mKIZ5E7EZyC-jLRFQ?e=B9aNIO">Power Budget PDF</a></li> <br>
    <li><a href="https://juliasmith141414.github.io/">Home</a></li>
    <li><a href="https://egr314-2025-s-301.github.io/main-page/">Team Page</a></li>
</ul>

---
