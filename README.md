# Autonomous Mars Rover: Dual-PCB Electrical Architecture

## 📌 Project Overview
This repository contains the schematic and PCB design files for the electrical subsystem of an Autonomous Mars Rover prototype. The system features a robust, split-board architecture designed to safely manage high-current power distribution while maintaining signal integrity for low-voltage logic and control systems. 

## 🏗️ System Architecture
To isolate high-power noise from sensitive microcontrollers, the design is split into two specialized printed circuit boards:

### 1. Power Distribution Board (4-Layer)
Handles all high-current routing, power regulation, and battery management.
* **Power Source:** 22.2V, 22000mAh LiPo battery.
* **Power Delivery:** * Regulates and distributes **12V** to the drive system.
  * Regulates and distributes **7.5V** to the servo UBECs.
* **Circuit Protection:** Hierarchical safety architecture using automotive blade fuses. Features a primary **70-80A main fuse** paired with dedicated subsystem fuses to prevent overcurrent events.

### 2. Control & Logic Board (2-Layer)
Houses the low-voltage control routing and interfaces with the primary compute units.
* **Compute Modules:** Designed to integrate with an **Arduino Mega** (real-time motor control) and a **Jetson Orin Nano** (high-level autonomy and vision).
* **Signal Routing:** Manages PWM, direction, and logic signals for the actuators.

## ⚙️ Hardware Integration
The PCBs are designed to seamlessly interface with the rover's physical actuators:
* **Drive System:** 6x 12V DC planetary gear motors driven by **Cytron MD20A** motor drivers.
* **Steering/Actuation:** 6x high-torque servos.

### Board-to-Board Interfacing
Communication between the Power Distribution Board and the Control Board is handled via a precise **20-pin IDC connector interface**. 
* **Pinout Configuration:** 6x PWM, 6x DIR, 6x Signal, and 2x GND.
* **Signal Integrity:** Common ground references are strictly established between the power and logic components to prevent ground loops and ensure reliable data transmission.

## 🛠️ Testing & Validation Status
- [x] Assembly and component clearance verification.
- [x] Voltage regulation and current draw analysis under load.
- [x] Logic signal transmission across the IDC interface.
- [x] Physical obstacle navigation testing (System Level).

---
*Designed and engineered for reliable autonomous operation in challenging terrain.*
