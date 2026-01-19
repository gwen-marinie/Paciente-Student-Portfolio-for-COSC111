# **Laboratory Activity #6 – Bi-Directional Serial Communication**

## 📘 Project Overview
This activity introduces **bi-directional (full-duplex) communication** between an Arduino and a Python script, creating a **closed-loop IoT system**.  
Unlike previous labs with one-way control, this project enables **simultaneous sending and receiving** of data, mimicking the architecture of real-world IoT devices and cloud servers.

---

## 🎯 System Features
- **Round-Trip Interaction:** Physical button presses trigger responses from Python, which then sends commands back to Arduino.  
- **Real-Time LED Control:** Arduino toggles LEDs based on Python instructions.  
- **Automated Logic:** Python processes hardware events automatically without manual typing.  
- **Full-Duplex Communication:** Both Arduino and Python act as **senders and receivers** simultaneously.

---

## 🛠 Hardware Setup
- **Inputs:** Three push buttons connected to pins **12, 11, 10**.  
- **Outputs:** Three LEDs connected to pins **7 (Red), 6 (Green), 5 (Blue)**.  
- **Arduino:** Powered via USB and connected to a Python-enabled computer.  
- **Pull-up Resistors:** Internal `INPUT_PULLUP` configuration used for stable button signals.

---

## ⚙ How It Works

### **1️⃣ Signal Flow**
1. User presses a button on the breadboard.  
2. Arduino detects the press and sends a code (e.g., `'R'`) to Python.  
3. Python reads the code, processes it, and decides the appropriate response.  
4. Python sends a command back to Arduino (e.g., `'1'`).  
5. Arduino toggles the corresponding LED based on the received command.  

### **2️⃣ Edge Detection**
- Arduino uses **state change detection** to send a signal **only when the button is pressed**, preventing repeated messages while the button is held down.  

### **3️⃣ Modular Code Structure**
- **Python Script (`lab_activity6.py`):**
  - Infinite loop listens for incoming data from Arduino.  
  - Conditional logic automates responses to hardware events (e.g., `'R' → send_command('1')`).  

- **Arduino Sketch (`laboratory_activity_6.ino`):**
  - Monitors **button states** and sends codes to Python.  
  - Listens for incoming commands (`'1'`, `'2'`, `'3'`) and toggles LEDs accordingly.  

- **Configuration Header (`myFunctions.h`):**
  - Defines pins for buttons and LEDs.  
  - Uses `INPUT_PULLUP` to simplify wiring and prevent floating signals.  

---

## 📡 IoT Concepts Demonstrated
- **Full-Duplex Communication:** Devices can **send and receive simultaneously**.  
- **Edge Detection:** Events are triggered **only on signal transitions** (button press), not steady states.  
- **Latency Awareness:** Demonstrates minimal delay between hardware input and output via Serial communication.  
- **Internal Pull-Up Resistors:** Uses Arduino’s built-in resistors for clean, stable button readings.  

---

## ✅ Summary
This lab demonstrates how to create a **real-time, bi-directional IoT system** using Arduino and Python.  
It teaches **closed-loop communication, edge detection, and modular programming**, providing a foundation for responsive and interactive IoT applications.
