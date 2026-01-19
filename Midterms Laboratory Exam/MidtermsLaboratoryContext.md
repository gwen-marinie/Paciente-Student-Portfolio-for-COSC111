# **Midterm Laboratory Exam – Smart Light Monitoring System**

## 📘 Introduction
This project represents the Midterm Laboratory Exam and integrates multiple lessons from earlier activities into a unified smart monitoring system. It features a **dual-mode light detection setup** that measures environmental brightness and displays the results using a three-color LED indicator. The device can run autonomously or respond to user-defined settings through typed commands, making it adaptable to different lighting conditions.

---

## 🌟 System Features
The Smart Light Monitoring System operates in two functional modes:

### **1️⃣ Automatic Mode (Default)**
- The system evaluates ambient light using predefined standards.
- Based on light intensity, it activates:
  - **Green LED** → Low light  
  - **Yellow LED** → Medium light  
  - **Red LED** → High light  
- Behavior follows fixed built-in thresholds representing typical lighting conditions like *Cloudy* or *Clear* environments.

---

### **2️⃣ Manual Mode**
- Users can modify the light sensitivity in real-time.
- Through the Serial Monitor, commands can be entered to redefine the threshold values.
- Examples:
SET LOW 30
SET HIGH 80
MODE MANUAL

- This mode lets users adjust the response of the system without editing or re-uploading the Arduino code.

---

### **📊 Real-Time Feedback**
The system continuously prints:
- Current light percentage
- Which LED is active
- Whether Automatic or Manual mode is running  
This provides a simple live dashboard for monitoring behavior every second.

---

## 🧱 How the System Works

### **🔸 Input**
- A **photoresistor** on **Analog Pin A0** reads the ambient light level.
- Raw readings range from `0` to `1023`.

### **🔸 Processing**
- Values are converted into a 0–100% brightness scale using `map()`.
- The system checks whether `automaticMode` is enabled and selects the appropriate logic path.

### **🔸 Output**
- Three LEDs connected to:
- **Pin 11 — Green**
- **Pin 12 — Yellow**
- **Pin 13 — Red**
- Only one LED lights up at a time based on the intensity level.

### **🔸 User Interface**
- A simple command-line interface accepts text commands to modify thresholds or switch modes.

---

## 🧠 Code Breakdown

### **State Machine Behavior**
The program structure changes depending on whether Automatic or Manual mode is active.  
This creates two isolated sets of behavior controlled by the variable `automaticMode`.

---

### **Threshold System**
- Default thresholds:
- `lowThreshold = 40`
- `highThreshold = 70`
- In **Manual Mode**, users can modify these values instantly.
- The system verifies that:
- Low must always be less than High.
- Inputs must be valid before being applied.

---

### **Automatic Mode Logic**
- Light ≤ 40% → Green LED  
- Light between 41–70% → Yellow LED  
- Light ≥ 71% → Red LED  
These values are fixed and represent built-in factory settings.

---

### **Manual Mode Logic**
- Uses user-defined values instead of fixed presets.
- The LED boundaries shift dynamically depending on the modified thresholds.
- This allows fine tuning for different rooms, environments, or brightness sources.

---

### **Command Parsing Engine**
The `processCommand()` function interprets incoming text:

#### Supported Commands:
MODE AUTO
MODE MANUAL
SET LOW <value>
SET HIGH <value>

#### Features:
- Extracts numbers from command strings.
- Ignores invalid formats.
- Validates relationship between thresholds.
- Updates global variables only when Manual mode is active.

---

## 📡 IoT Concepts Demonstrated

### **🔹 Dynamic Configuration**
Parameters can be updated while the system is running — essential for adapting deployed IoT devices to real-world changes.

### **🔹 String-Based Command Processing**
The system reads and interprets multi-part text commands, similar to how higher-level IoT systems receive cloud configuration messages.

### **🔹 Multi-Mode Operation**
Implements autonomous and user-controlled behavior within a single program.

### **🔹 Data Normalization**
Raw sensor values are mapped into a more readable percentage format for easier monitoring and decision-making.

---

## ✅ Summary
This Smart Light Monitoring System showcases how sensors, user commands, and LED indicators can create an adaptable and interactive IoT device. With adjustable thresholds, real-time feedback, and multi-mode operation, it demonstrates essential concepts in environmental monitoring and embedded system design.

