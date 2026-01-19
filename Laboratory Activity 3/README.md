# **Laboratory Activity #3 – Fire Sensor Simulation**

## Project Overview
This project focuses on the **input side of IoT systems** by integrating environmental sensors to monitor real-world conditions.  
The system simulates a **fire alarm** by continuously reading temperature and light intensity, then triggering alerts when danger conditions are detected.  

Unlike previous activities that controlled outputs (LEDs), this project emphasizes **environmental sensing** and **decision-making** based on sensor data.

---

## System Features
- **Real-time Monitoring:** Continuously reads temperature and ambient light.  
- **Detection Logic:** Triggers an alarm only when both conditions are met:  
  - Temperature ≥ 50°C  
  - Brightness ≥ 220 (raw sensor value)  
- **Alarm System:** Activates a **fast-blinking red LED** and a **high-pitched buzzer** when fire conditions are detected.  
- **False Alarm Prevention:** The "AND" logic ensures alarms only trigger when both temperature and brightness indicate a potential fire.

---

## Hardware Setup
- **Thermistor (Pin A0):** Measures temperature (e.g., TMP36 or NTC Thermistor).  
- **Photoresistor (Pin A2):** Measures ambient light intensity.  
- **Red LED (Pin 12):** Visual alarm indicator.  
- **Buzzer (Pin 11):** Audible alarm indicator.  
- **Arduino:** Powered via USB or external source.  

---

## How It Works

### **1️⃣ Sensor Fusion**
- Combines readings from **temperature** and **light sensors** to create a more reliable alarm system.  
- Each sensor provides analog values (0–1023), which the Arduino converts into **Celsius** for temperature and raw units for brightness.

### **2️⃣ Temperature Processing**
- The `readTempC` function converts analog voltage from the thermistor into temperature using a calibration formula (e.g., simplified Steinhart-Hart equation).  
- Calibration constants such as **beta (3950)** and **resistance (10.0 kΩ)** ensure accurate readings.

### **3️⃣ Detection Logic**
- The main loop checks:
```cpp
if(currentTemp >= tempThreshold && currentBright >= brightThreshold)
