# **Laboratory Activity #4 – Arduino Serial Connection**

## Project Overview
This activity introduces **two-way communication** between an Arduino and a computer via **Serial Communication (UART)**. Unlike previous projects that ran autonomously, this system allows **real-time human intervention**, enabling users to control hardware behavior by sending text commands through the Arduino Serial Monitor.

---

## System Features
- **Light Monitoring:** Continuously reads brightness from a photoresistor.  
- **Persistent Alarm:** When brightness exceeds a threshold (220), the system enters **Alarm Mode**, blinking an LED endlessly.  
- **Latching State:** Once triggered, the alarm **remains active**, even if the light level drops.  
- **Manual Reset:** Users stop the alarm by typing `"stop"` in the Serial Monitor.  

---

## Hardware Setup
- **Photoresistor:** Connected to **Pin A2** to measure ambient light.  
- **LED:** Connected to **Digital Pin 12** as a visual alarm indicator.  
- **Arduino:** Powered via USB, connected to a computer for Serial communication.  

---

## How It Works

### **1️⃣ Input**
- **Hardware:** Photoresistor reads light intensity (0–1023).  
- **Software:** Arduino listens for commands from the computer via USB Serial port.  

### **2️⃣ Processing**
- **Data Conversion:** `readBright()` maps analog values (0–1023) to 0–255 for easier threshold comparison.  
- **Trigger Logic:** When brightness ≥ `brightThreshold` (220), a boolean flag `choice = true` activates the alarm state.  

### **3️⃣ Latching Alarm**
- Once triggered, the program enters a **blocking while loop**:
  - The LED blinks continuously with **100 ms delay**.  
  - Sensor readings are paused until the user intervenes.  

### **4️⃣ Serial Command Handling**
- `Serial.readStringUntil('\n')` captures user input.  
- `input.toLowerCase()` ensures case-insensitive command recognition.  
- Typing `"stop"` breaks the loop and **turns off the LED**, resetting the system.  

---

## IoT Concepts Demonstrated
- **Serial Communication (UART):** Two-way interface for sending and receiving data between Arduino and computer.  
- **State Retention (Latching):** The system remembers an event and persists in a state until explicitly reset.  
- **String Manipulation:** Case-insensitive command processing improves user interaction.  
- **Blocking vs Non-Blocking Behavior:** The program halts sensor reading while the alarm is active, demonstrating trade-offs in real-time systems.  

---

## Summary
This activity emphasizes **interactive IoT systems**, where hardware reacts to both environmental input and **user commands**.  
It teaches **latching states, Serial communication, and string handling**, providing a foundation for safety-critical applications that require **human acknowledgment** to reset triggered events.
