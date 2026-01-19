# **Laboratory Activity #2 – Working with Analog Signals: Fading LEDs**

## 📘 Project Overview
This activity demonstrates how to **simulate analog behavior** on a digital Arduino board using **Pulse Width Modulation (PWM)**. Unlike simple on/off control, PWM allows LEDs to **gradually fade in and out**, creating smooth transitions in brightness. This project builds on the previous running-light activity by introducing **variable output control** through software.

---

## 🎯 Objectives
1. Explore **analog signal simulation** using a digital microcontroller.  
2. Understand **PWM** and how it controls LED brightness.  
3. Apply nested loops and variable control to manage **dynamic output**.

---

## 💡 System Features
- Smooth **fade-in** and **fade-out** sequences across five LEDs.  
- LEDs light up in order from **pin 12 → pin 8** and fade back in reverse.  
- Each LED’s brightness changes gradually, rather than snapping on/off instantly.  
- The fade speed is controlled using a small delay to make the effect visible.

---

## 🛠 Hardware Setup
- **Arduino Uno** connected to a breadboard.  
- **LEDs:** Connected to **pins 12, 11, 10, 9, and 8**.  
- **Power:** Arduino powered via USB or external source.  

---

## ⚙ How It Works

### **1️⃣ Signal Processing (PWM)**
- Arduino uses **Pulse Width Modulation (PWM)** to simulate analog voltages.  
- `analogWrite(pin, value)` sets the LED brightness:
  - `0` → always off  
  - `255` → fully on  
  - Intermediate values → partial brightness  

### **2️⃣ Fading Logic**
- **Fade-In Sequence:**  
  - LEDs light up one by one from **pin 12 → pin 8**.  
  - Each LED gradually increases brightness from `0 → 255` using a nested while loop.  
  - `delay(1)` between increments ensures smooth visual fading.

- **Fade-Out Sequence:**  
  - After all LEDs reach full brightness, they **dim one by one** in the same order.  
  - The inner loop decreases brightness from `255 → 0` for each LED.  

### **3️⃣ Code Structure**
- **Initialization:** `setup()` configures all LED pins as **OUTPUT**.  
- **Nested Loops:** Outer loop iterates through LEDs; inner loop controls brightness levels.  
- **Variable Control:** A variable (e.g., `power`) dynamically adjusts LED intensity.  

---

## 📡 IoT Concepts Demonstrated
- **Analog vs. Digital Output:** Shows how digital devices can simulate analog behavior.  
- **Pulse Width Modulation (PWM):** Controls power delivery to LEDs for dimming effects.  
- **Nested Control Structures:** Loops inside loops manage both **fade duration** and **LED sequence**.  
- **Dynamic Variable Control:** Hardware state changes in real-time using variables rather than fixed values.  

---

## ✅ Summary
This activity reinforces the concept that **digital devices can mimic analog behavior** through software. By combining PWM with nested loops and variable state control, the system creates a **smooth fading LED sequence**, providing hands-on experience with signal modulation, dynamic control, and advanced Arduino programming.
