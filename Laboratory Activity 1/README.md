# **Arduino Running Light Circuit**

## Project Overview
This project demonstrates a **running light circuit** using an Arduino, designed to reinforce core concepts in digital signals and IoT system implementation.  

The program controls **five LEDs** connected to **pins 8 through 12**. The LEDs illuminate in sequence from **pin 12 to pin 8**, turning **on one by one**, then **off one by one**, with a **1-second delay** between each change. The cycle repeats continuously, creating a simple running-light pattern.

---

## Objectives
1. Review Arduino as a device for **IoT systems implementation**.  
2. Demonstrate **digital signal control** using an Arduino circuit.

---

## Hardware Setup
- **LEDs:** Connected to pins **8, 9, 10, 11, and 12**  
- **Arduino:** Powered via USB or external source  

---

## Instructions Implemented
- **Running light sequence:** LEDs turn on from **pin 12 → 8** sequentially, then turn off from **pin 12 → 8**.  
- **Delay:** Each LED changes state after **1 second**.  
- **Digital control:** LEDs are switched on/off using the `digitalWrite()` function.  

---

## How It Works
1. The Arduino code cycles through the pins **backwards** from 12 to 8.  
2. Each LED turns **on** with `digitalWrite(pin, HIGH)` for **1 second**.  
3. After all LEDs are on, the program turns them **off** in the same order.  
4. The loop repeats, producing a continuous forward and backward running-light pattern.  

---

## ✅ Applications
- Learning **Arduino digital output** control  
- Visual demonstration of **sequential digital signals**  
- Introductory exercise for **IoT system circuits**
