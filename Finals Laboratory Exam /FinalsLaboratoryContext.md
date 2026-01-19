# **Final Laboratory Exam – IoT API Trigger System**

## 📘 Introduction
This project showcases a practical implementation of an IoT trigger mechanism where a physical button activates an online service. Instead of hosting a server on the microcontroller, the device functions purely as an input generator, while the computer and Python script handle all networking tasks. The work reflects real-world IoT workflows used in smart devices that trigger cloud events through simple physical interactions.

---

## 🛠 System Purpose
The design provides a **physical activation button** specifically for **Group 3**, enabling them to send a remote toggle request to the instructor’s API. When a user presses the button:

1. The Arduino detects the press.
2. It transmits the group ID (`3`) through Serial.
3. A Python script captures the incoming data.
4. The script formats a web request to the server.
5. The server updates the status tied to Group 3.

This allows a basic hardware action to control a cloud-side event.

---

## 🧱 System Architecture

### **1️⃣ Edge Device (Arduino)**
- A push button is connected to **Digital Pin 4**.
- `INPUT_PULLUP` is used to stabilize the button state.
- The Arduino handles simple signal processing only — no networking capability is required here.

### **2️⃣ Gateway Device (Computer + Python Script)**
- The computer reads serial data continuously via COM7.
- It interprets the incoming values and forwards them to the cloud.
- The gateway serves as the communication bridge for the Arduino.

### **3️⃣ Cloud Endpoint (Instructor API Server)**
- When the script receives Group ID `3`, it constructs a URL such as: http://172.20.10.3:8000/led/group/3/toggle
- A GET request triggers the API’s toggle function.
- The server updates the status for Group 3 on its dashboard or connected device.
  
---

## 💻 Code Breakdown

### **Arduino Code Highlights**
- **Debounce Logic:** Prevents repeated signals caused by mechanical noise in the button.
- **Serial Output:** Sends only the numeric group identifier once a stable press is confirmed.
- **Simple Workflow:** All complex tasks are offloaded to the Python gateway.

---

### **Python Script Highlights**
- **Serial Reading:** Continuously monitors incoming data.
- **Input Verification:** Ensures that the Arduino’s message is valid before sending a request.
- **Dynamic URL Creation:** The group value is inserted directly into the server route.
- **Error Handling:** Network or serial failures are caught to prevent system crashes.

---

## 📡 IoT Principles Demonstrated

### **🔹 Hardware-to-Software Integration**
A basic hardware interface (button press) triggers high-level software actions.

### **🔹 Gateway-Based Networking**
Since the Arduino lacks onboard networking, the computer acts as a middle layer to reach the API.

### **🔹 REST API Interaction**
The Python script sends structured HTTP requests to control remote resources.

### **🔹 Noise Filtering via Debouncing**
Ensures the system reflects intentional button presses only.

## 📌 Summary
This final exam activity successfully connects a **physical input** to a **cloud-triggered action**, demonstrating how IoT systems transform basic hardware events into web-based operations. The project emphasizes:

- clean signal processing  
- reliable serial-to-network communication  
- modular separation between hardware and software  
- practical use of API-driven automation  

A single button press becomes a complete edge-to-cloud event pipeline — a small but powerful example of IoT in action.



