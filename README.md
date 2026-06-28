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

## ⚙️ Hardware Interfaces
Communication between the Power Distribution Board and the Control Board is handled via a precise **20-pin IDC connector interface**. Common ground references and isolated shields are strictly established to prevent ground loops.

### 20-Pin IDC Interface Mapping

| IDC Pin | Arduino Mega Pin | Signal Name | Target Connection (Bottom PCB) | Signal Type / Design Note |
| :---: | :---: | :--- | :--- | :--- |
| **1** | 5V (VCC) | `LOGIC_5V` | Logic Power Reference | Pull-ups / Sensor logic ref |
| **2** | D2 | `M1_PWM` | Cytron M1 MD20A PWM | Motor 1 Speed Control |
| **3** | D22 | `M1_DIR` | Cytron M1 MD20A DIR | Motor 1 Direction |
| **4** | GND | `LOGIC_GND` | Motor Driver Logic GND | Isolated Ground Shield |
| **5** | D3 | `M2_PWM` | Cytron M2 MD20A PWM | Motor 2 Speed Control |
| **6** | D23 | `M2_DIR` | Cytron M2 MD20A DIR | Motor 2 Direction |
| **7** | GND | `LOGIC_GND` | Motor Driver Logic GND | Isolated Ground Shield |
| **8** | D4 | `M3_PWM` | Cytron M3 MD20A PWM | Motor 3 Speed Control |
| **9** | D24 | `M3_DIR` | Cytron M3 MD20A DIR | Motor 3 Direction |
| **10** | GND | `LOGIC_GND` | Motor Driver Logic GND | Isolated Ground Shield |
| **11** | D5 | `M4_PWM` | Cytron M4 MD20A PWM | Motor 4 Speed Control |
| **12** | D25 | `M4_DIR` | Cytron M4 MD20A DIR | Motor 4 Direction |
| **13** | GND | `LOGIC_GND` | Motor Driver Logic GND | Isolated Ground Shield |
| **14** | D6 | `M5_PWM` | Cytron M5 MD20A PWM | Motor 5 Speed Control |
| **15** | D26 | `M5_DIR` | Cytron M5 MD20A DIR | Motor 5 Direction |
| **16** | D7 | `M6_PWM` | Cytron M6 MD20A PWM | Motor 6 Speed Control |
| **17** | D27 | `M6_DIR` | Cytron M6 MD20A DIR | Motor 6 Direction |
| **18** | D30 | `S1_SIGNAL` | Ultra Torque Servo 1 | Servo 1 Position Command |
| **19** | D31 | `S2_SIGNAL` | Ultra Torque Servo 2 | Servo 2 Position Command |
| **20** | D32 | `S3_SIGNAL` | Ultra Torque Servo 3 | Servo 3 Position Command |

## 📁 Repository Structure
* `/Schematics`: PDF and source files for the schematic capture.
* `/PCB_Layout`: Board files for both the 4-layer Power Board and 2-layer Control Board.
* `/Gerber_Files`: Manufacturing files ready for fabrication.
* `/BOM`: Bill of Materials, including specific part numbers for the 20-pin IDC, automotive fuses, and ICs.

## 🛠️ Testing & Validation Status
- [x] Assembly and component clearance verification.
- [x] Voltage regulation and current draw analysis under load.
- [x] Logic signal transmission across the IDC interface.
- [ ] Physical obstacle navigation testing (System Level).

---
*Designed and engineered for reliable autonomous operation in challenging terrain.*
