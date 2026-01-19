# **Laboratory Activity #5 – Python-Arduino Integration**

## 📘 Project Overview
This activity bridges **high-level software** and **embedded hardware** by using Python as an external control interface for Arduino.  
Unlike previous labs that relied on the Arduino IDE Serial Monitor, this project demonstrates a **client-server style architecture**, where a Python script acts as a client and the Arduino functions as the server.  

It provides a foundation for **commercial IoT dashboards and remote control applications**.

---

## 🎯 System Features
- **Remote Control Interface:** Python script presents a menu to toggle LEDs:
  - `[R] Red ON/OFF`  
  - `[G] Green ON/OFF`  
  - `[B] Blue ON/OFF`  
  - `[A] All ON` / `[O] All OFF`  
  - Special modes like **Violet**  
- **Physical Hardware:** Three LEDs (Red, Green, Blue) connected to Arduino.  
- **Real-Time Response:** Selecting a command in Python immediately toggles the corresponding LED.  

---

## 🛠 Hardware Setup
- **LED Pins:**  
  - Red → Pin 8  
  - Green → Pin 9  
  - Blue → Pin 10  
- **Arduino:** Connected to the computer via USB (e.g., COM7).  
- **Python:** Runs a CLI script to send commands to Arduino.  

---

## ⚙ How It Works

### **1️⃣ User Input (Python Client)**
- Python script displays a **menu of commands**.  
- Input is converted to lowercase and encoded as bytes using `.encode()`.  
- Serial library (`import serial`) transmits data to Arduino over USB.

### **2️⃣ Arduino Processing (Server)**
- Arduino continuously listens on the Serial port.  
- Incoming commands are **trimmed** and **parsed**.  
- Based on the command character:
  - The corresponding function (`toggleRed()`, `toggleGreen()`, `toggleBlue()`) is executed.  
  - LEDs change state (On → Off, Off → On).

### **3️⃣ Modular Code Structure**
- **Header File (`ArduinoFromPythonHeader.h`):**
  - Defines **LED pins** and **state variables**.  
  - Tracks current state for toggle logic (`redState = !redState`).  

- **Main Sketch (`.ino`):**
  - Uses **switch-case logic** to handle commands efficiently.  
  - Validates input to prevent errors from empty or multi-character inputs.  

- **Python Script (`ArduinoFromPython.py`):**
  - Runs a **continuous loop** for CLI interaction.  
  - Sends encoded commands over Serial until `"x"` is pressed to exit.

---

## 📡 IoT Concepts Demonstrated
- **Cross-Platform Communication:** Integrates Python and Arduino (C++) via **Serial/UART protocol**.  
- **State Management:** Tracks hardware state to allow toggling between On and Off.  
- **Modular Design:** Separates hardware definitions and functions into a header file for clean, maintainable code.  
- **Command Line Interface (CLI):** Enables real-time interaction with hardware from a text-based interface.  

---

## ✅ Summary
This activity highlights **software-hardware integration** in IoT systems.  
Through the combinination of Python and Arduino, users can **remotely control physical devices**, implement **state-aware toggling**, and design **modular, maintainable code** suitable for real-world IoT applications.
