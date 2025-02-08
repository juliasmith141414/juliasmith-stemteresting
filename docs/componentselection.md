# Component Selection
## Microcontroller: PIC18F27/47Q10
![image](https://github.com/user-attachments/assets/75a595da-e7bf-443a-b91f-c7affd50d812) <br>
[Datasheet](https://arizonastateu-my.sharepoint.com/:b:/g/personal/jasmi157_sundevils_asu_edu/EY412CZrEBFCm1RPcBUdK0ABFQC27qYPnXhWjqNXUzvurw?e=bMb4OQ) <br>

## Programmer: MPLab Snap Programmer 
![image](https://github.com/user-attachments/assets/1ad9faf8-0440-4068-9b8d-6f026b02ac68) <br>
[Datasheet]([https://arizonastateu-my.sharepoint.com/:b:/g/personal/jasmi157_sundevils_asu_edu/EY412CZrEBFCm1RPcBUdK0ABFQC27qYPnXhWjqNXUzvurw?e=bMb4OQ](https://arizonastateu-my.sharepoint.com/:b:/g/personal/jasmi157_sundevils_asu_edu/EQGcT4hhqEpHhpjXQ1mo-LEBesul2oAfO8pAhaCQ58yQCQ?e=vgC0Pv)) <br>

## Distance Sensor
### Option 1: VL53L1CXV0FY/1
![image](https://github.com/user-attachments/assets/22add513-4aa3-4a45-926c-3bb4cddefcbf) <br>
[Datasheet](https://arizonastateu-my.sharepoint.com/:b:/g/personal/jasmi157_sundevils_asu_edu/EbF6q-VkyolOulMk80JgWMkB3oZ_hcvkSHapQ7gW-guFWQ?e=OiwQhq "Datasheet Link") <br>
[Product Link](https://www.digikey.com/en/products/detail/stmicroelectronics/VL53L1CXV0FY-1/8258055?gclsrc=aw.ds&&utm_adgroup=Sensors%20%26%20Transducers&utm_source=google&utm_medium=cpc&utm_campaign=Dynamic%20Search_EN_Product&utm_term=&utm_content=Sensors%20%26%20Transducers&utm_id=go_cmp-120565755_adg-9159613635_ad-665604606719_dsa-118454329515_dev-c_ext-_prd-_sig-Cj0KCQiA-5a9BhCBARIsACwMkJ5tpM-SWtOWcLFeYXKLWrr322Ie9MSGfVXNjbXu15Vl1KLtmgiQEdUaApbPEALw_wcB&gad_source=1&gclid=Cj0KCQiA-5a9BhCBARIsACwMkJ5tpM-SWtOWcLFeYXKLWrr322Ie9MSGfVXNjbXu15Vl1KLtmgiQEdUaApbPEALw_wcB&gclsrc=aw.ds) <br>
$5.77 <br>
Max range: 4 Meters <br>
Operating Voltage: 2.6V - 3.5V <br>
Communication: I2C <br>
Mount: Surface <br>

### **VL53L1CXV0FY/1 Sensor**

| **Pros**                                                 | **Cons**                                                 |
|----------------------------------------------------------|----------------------------------------------------------|
| **Extended range** up to 4 meters                        | Surface-mount **LGA-16** package may require reflow soldering |
| **I²C communication** simplifies integration with MCUs   | Requires **precise alignment** for accurate measurements  |
| Supports **variable timing budgets** for power efficiency| More expensive than **VL53L0X**                          |
| **Multi-target detection** with programmable distance modes | Slightly larger LGA footprint than smaller sensors        |
| Compatible with **Microchip PIC microcontrollers** via MCC | Sensitive to ambient lighting conditions in some environments |
| Excellent for both short and long-range applications     | Initial setup may require calibration                     | <br>

### **Option 2: VL53L0X**
![image](https://github.com/user-attachments/assets/e787c161-59c0-4130-a716-be647bf55d72) <br>
[Datasheet](https://arizonastateu-my.sharepoint.com/:b:/g/personal/jasmi157_sundevils_asu_edu/EVZtUUkWE9xGhCSLo-Ec1scBudzi0_jGqGujjsDPeXDivA?e=c6nOMb) <br>
[Product Link](https://estore.st.com/en/products/imaging-and-photonics-solutions/time-of-flight-sensors/vl53l0x.html) <br>
$2.64 <br>
Max range: 2 Meters <br>
Operating Voltage: 2.8V - 3.3V <br>
Communication: I2C <br>
Mount: Surface <br>

### **VL53L0X Sensor**

| **Pros**                                                | **Cons**                                               |
|---------------------------------------------------------|--------------------------------------------------------|
| Compact and **low-cost** sensor for short-range sensing | **Limited range** (up to 1.2 meters)                   |
| **I²C communication** for easy integration              | **LGA package** can be difficult to solder manually     |
| **Low power consumption** ideal for portable devices    | Sensitive to ambient lighting interference              |
| Available with extensive documentation and example code | Less accurate at distances near the upper limit         |
| Compatible with **Microchip PIC microcontrollers** via MCC | Requires calibration for optimal performance            |
| Fast response time suitable for real-time applications  | Fewer advanced features compared to newer ToF sensors   | <br>


### **Option 3: VL53L5CX**
![image](https://github.com/user-attachments/assets/1aa3bbe1-f7fd-4b78-8c1a-2a87a2839143) <br>
[Datasheet](https://arizonastateu-my.sharepoint.com/:b:/g/personal/jasmi157_sundevils_asu_edu/ETmD_ntduohApG-p0T8vbO0BsWPYG0gU-rsxDNol8xd_AQ?e=xIRxcY) <br>
[Product Link](https://www.digikey.com/en/products/detail/ams-osram-usa-inc/TMF8801-1B-OLGA12-LF-T-RDP/11477805?gclsrc=aw.ds&&utm_adgroup=General&utm_source=google&utm_medium=cpc&utm_campaign=PMax%20Shopping_Product_Zombie%20SKUs&utm_term=&utm_content=General&utm_id=go_cmp-17815035045_adg-_ad-__dev-c_ext-_prd-11477805_sig-Cj0KCQiA-5a9BhCBARIsACwMkJ415ydI0m81_pdt0JT6dCtN3Qli_Api3Z743eGKMrIpfMpnrbdwwvoaAuVGEALw_wcB&gad_source=1&gclid=Cj0KCQiA-5a9BhCBARIsACwMkJ415ydI0m81_pdt0JT6dCtN3Qli_Api3Z743eGKMrIpfMpnrbdwwvoaAuVGEALw_wcB&gclsrc=aw.ds) <br>
$5.91 <br>
Max range: 400 cm <br>
Operating Voltage: 2.8V - 3.3V <br>
Communication: I2C <br>
Mount: Surface <br>


### **VL53L5CX Sensor**

| **Pros**                                                   | **Cons**                                                  |
|------------------------------------------------------------|-----------------------------------------------------------|
| Measures up to **4 meters** with high accuracy             | Surface-mount **LGA-16** package requires reflow soldering |
| **Multi-zone detection** (up to 64 zones)                  | May require precise alignment for accurate measurements    |
| **Low power consumption** suitable for battery-powered systems | Sensitive to environmental conditions (e.g., ambient light)|
| Compatible with **I²C communication**                      | Complex multi-zone data handling may need additional processing power |
| Supports both **short-range and long-range modes**         | Higher price than simpler sensors                          |
| Reliable integration with **Microchip PIC microcontrollers** using MCC | Documentation may require some technical expertise to fully understand | <br>

