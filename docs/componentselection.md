# Component Selection

## Objective
The purpose of this page is to compare, and contrast multiple solutions for each major component in my subsystem design. This includes identifying off-the-shelf and custom electrical or mechanical components, assessing compatibility with project specifications, and articulating rationale for final choices.

---

## Role Description
As part of the project team, my role involves designing and integrating the sensor subsystem. This includes selecting an appropriate distance sensor, ensuring compatibility with the **PIC18F47Q10**, and configuring I²C communication. Additionally, I will assist with the microcontroller's programming, actuation, and communication subsystems.

---

## Electrical Block Diagram

![Smith Individual Block Diagram drawio V2](https://github.com/user-attachments/assets/62313fd9-333f-428a-a932-9d0ebc18b512)

This diagram outlines the key components and subsystems: microcontroller, distance sensor (via I²C), motor driver, and actuators. Each subsystem requires separate research and component selection.

---

## Major Component Selections

### **Microcontroller: PIC18F47Q10**
![image](https://github.com/user-attachments/assets/75a595da-e7bf-443a-b91f-c7affd50d812)  <br>
[Datasheet](https://arizonastateu-my.sharepoint.com/:b:/g/personal/jasmi157_sundevils_asu_edu/EY412CZrEBFCm1RPcBUdK0ABFQC27qYPnXhWjqNXUzvurw?e=bMb4OQ)  

| **Pros**                                                  | **Cons**                                                |
|-----------------------------------------------------------|---------------------------------------------------------|
| Compatible with **MPLab Snap Programmer**                 | Requires **MCC configuration** for all peripherals       |
| Supports **multiple communication protocols** (UART, I²C) | Higher complexity than simpler microcontrollers          |
| Extensively documented with **sample code**               | Surface-mount version may be difficult to solder         |
| Integrated **ADC, PWM, and GPIO**                        | Slightly higher cost than lower-performance alternatives |

---

### **Programmer: MPLab Snap Programmer**
![image](https://github.com/user-attachments/assets/1ad9faf8-0440-4068-9b8d-6f026b02ac68)  <br>
[Datasheet](https://arizonastateu-my.sharepoint.com/:b:/g/personal/jasmi157_sundevils_asu_edu/EQGcT4hhqEpHhpjXQ1mo-LEBesul2oAfO8pAhaCQ58yQCQ?e=vgC0Pv)  

| **Pros**                                                  | **Cons**                                                |
|-----------------------------------------------------------|---------------------------------------------------------|
| Affordable and **official Microchip support**             | May require **firmware updates**                        |
| **Compatible** with multiple PIC microcontrollers         | Limited debugging features                              |
| Easy to integrate with **MPLab X IDE**                    | Not as durable as other higher-end programmers          |

---

## **Voltage Regulators**

#### **Option 1: LM2575-3.3V (Chosen)**
![LM2575D2T-3-3R4G_C70337_front](https://github.com/user-attachments/assets/1e9eaddd-e5c4-426c-9f26-3c28b0cb6cc6)<br>
[Datasheet](https://arizonastateu-my.sharepoint.com/:b:/g/personal/jasmi157_sundevils_asu_edu/EXAMPLE_LM2575.pdf)  
**Max Current:** **1.0A**  
**Efficiency:** ~75-88%  
**Operating Voltage:** 4.75V – 40V  

| **Pros**                                               | **Cons**                                        |
|--------------------------------------------------------|-------------------------------------------------|
| **Handles up to 1.0A** output current                  | Requires **external inductor** for regulation   |
| **High efficiency** (compared to linear regulators)    | Slightly larger than other options              |
| **Built-in thermal shutdown & current limiting**       | Fixed output voltage version requires selection |
| **Switching regulator minimizes heat dissipation**     | Requires a **few external passive components**  |

---

#### **Option 2: AMS1117-3.3V (Alternative)**
![AMS1117-3 3](https://github.com/user-attachments/assets/d1f93a3a-8333-49b8-9a18-0645716dbe16)<br>
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
![MP2315GJ-Z VOLTAGE REGULATOR](https://github.com/user-attachments/assets/0ec08087-8771-4c70-b557-854364f03e4d)<br>
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
![VL53L1CXV0FY-1 DISTANCE SENSOR SMD](https://github.com/user-attachments/assets/60dd9436-97b2-49df-bd5d-6accfdb9a356) <br>
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
![image](https://github.com/user-attachments/assets/e787c161-59c0-4130-a716-be647bf55d72) <br> 
[Datasheet](https://arizonastateu-my.sharepoint.com/:b:/g/personal/jasmi157_sundevils_asu_edu/EVZtUUkWE9xGhCSLo-Ec1scBudzi0_jGqGujjsDPeXDivA?e=c6nOMb)  
[Product Link](https://estore.st.com/en/products/imaging-and-photonics-solutions/time-of-flight-sensors/vl53l0x.html)  
**Cost:** $2.64  
**Max Range:** 2 Meters  
**Operating Voltage:** 2.8V - 3.3V  
**Communication:** I²C  
**Mount:** Surface  

| **Pros**                                                | **Cons**                                               |
|---------------------------------------------------------|--------------------------------------------------------|
| Compact and **low-cost** sensor for short-range sensing | **Limited range** (up to 1.2 meters)                   |
| **I²C communication** for easy integration              | **LGA package** can be difficult to solder manually     |
| **Low power consumption** ideal for portable devices    | Sensitive to ambient lighting interference              |

---

#### **Option 3: VL53L5CX**
![image](https://github.com/user-attachments/assets/1aa3bbe1-f7fd-4b78-8c1a-2a87a2839143)  <br>
[Datasheet](https://arizonastateu-my.sharepoint.com/:b:/g/personal/jasmi157_sundevils_asu_edu/ETmD_ntduohApG-p0T8vbO0BsWPYG0gU-rsxDNol8xd_AQ?e=xIRxcY)  
[Product Link](https://www.digikey.com/en/products/detail/ams-osram-usa-inc/TMF8801-1B-OLGA12-LF-T-RDP/11477805)  
**Cost:** $5.91  
**Max Range:** 4 Meters  
**Operating Voltage:** 2.8V - 3.3V  
**Communication:** I²C  
**Mount:** Surface  

| **Pros**                                                   | **Cons**                                                  |
|------------------------------------------------------------|-----------------------------------------------------------|
| Measures up to **4 meters** with high accuracy             | Surface-mount **LGA-16** package requires reflow soldering |
| **Multi-zone detection** (up to 64 zones)                  | May require precise alignment for accurate measurements    |
| **Low power consumption** suitable for battery-powered systems | Sensitive to environmental conditions (e.g., ambient light)|
| Compatible with **I²C communication**                      | Complex multi-zone data handling may need additional processing power |
| Supports both **short-range and long-range modes**         | Higher price than simpler sensors                          |
| Reliable integration with **Microchip PIC microcontrollers** using MCC | Documentation may require some technical expertise to fully understand |

---

### **Final Component Selections**
After evaluating range, cost, and ease of integration, the **VL53L1CXV0FY/1** sensor was selected due to its **extended range capabilities** and **multi-target detection**, making it the best fit for our project requirements.

For voltage regulation, the **LM2575-3.3V** was chosen as the final voltage regulator. It provides **high efficiency (~75-88%)**, supports up to **1.0A output current**, and includes **built-in protections** such as thermal shutdown and current limiting. Its **switching regulator design** ensures minimal heat dissipation, making it well-suited for the power demands of the system.

---

## **Power Budget**
![image](https://github.com/user-attachments/assets/039d18e6-2ede-46cf-98b2-902b85683dc9)  
[EGR 314 Power Budget V2.pdf](https://github.com/user-attachments/files/19033580/EGR.314.Power.Budget.V2.pdf)  
[Link to Spreadsheet](https://docs.google.com/spreadsheets/d/12uf9W3mrbqPYXF1pln1ugqOVY8jhmh9nDuVUHxvh6Tg/edit?usp=sharing)

---
