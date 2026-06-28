# Autonomous Mars Rover: Electrical & PCB Architecture

## 📌 Project Overview
This repository contains the schematic and PCB design files for the electrical subsystem of an Autonomous Mars Rover prototype. The system manages high-current power distribution for actuators while maintaining signal integrity for low-voltage control systems. 

To accommodate different manufacturing preferences and structural constraints, this repository offers **two distinct PCB architectures**: a split Dual-PCB design and an Integrated Single-PCB design.

## 🏗️ System Architectures

### Option A: Integrated Single-PCB (Combined)
A unified design where both the high-power distribution and the low-voltage logic are integrated onto a single, multi-layer board.
* **Direct Routing:** Eliminates the need for board-to-board connectors. The Arduino Mega and Jetson Orin Nano signals are routed directly to the motor drivers and UBECs on the same board.
* **Space-Efficient:** Ideal for chassis designs with constrained vertical mounting space.

> <img width="1186" height="733" alt="image" src="https://github.com/user-attachments/assets/b43eef76-336e-4bf0-b83b-f2d6e6e81924" /><img width="955" height="570" alt="image" src="https://github.com/user-attachments/assets/84fab42a-4081-4b79-b5df-8c1fd6ed8736" /><img width="1112" height="585" alt="image" src="https://github.com/user-attachments/assets/31e92a9e-694d-47b1-b4b4-8f5170fa9dda" />



### Option B: Dual-PCB Architecture (Split)
A robust, split-board architecture designed for maximum physical isolation of high-power noise from sensitive microcontrollers.
* **Power Distribution Board (4-Layer):** Handles 22.2V LiPo input, high-current routing, and hierarchical blade-fuse protection. Regulates 12V for motors and 7.5V for servos.
* **Control & Logic Board (2-Layer):** Houses the low-voltage routing for the Arduino Mega and Jetson Orin Nano. 
* **Connection:** Uses a 20-pin IDC connector to bridge signals between the two boards.

> <img width="776" height="579" alt="image" src="https://github.com/user-attachments/assets/8f1fc1b7-4f43-4479-9f7e-bae6867f2f5f" /><img width="856" height="859" alt="image" src="https://github.com/user-attachments/assets/4de9862c-5221-49f8-86f9-4ebf1d9ecd81" /><img width="901" height="940" alt="image" src="https://github.com/user-attachments/assets/27976c66-24a4-43f3-bdea-dac625b04451" />

> <img width="996" height="704" alt="image" src="https://github.com/user-attachments/assets/8c373ca3-2249-4699-af08-1ba54f14cb32" /><img width="1280" height="699" alt="image" src="https://github.com/user-attachments/assets/8dc0457b-9b69-4bae-b324-40a9fc4eec61" /><img width="1280" height="691" alt="image" src="https://github.com/user-attachments/assets/7fedf576-8c64-40e9-95f3-c9728c5b1a73" />

## ⚙️ Hardware Interfaces & Pin Mapping

The following table dictates the routing from the compute modules (Arduino Mega) to the motor drivers and servos. 
* *Note: For the Dual-PCB design, these map directly to the 20-pin IDC connector. For the Single-PCB design, these represent the direct internal traces.*

| Signal / Pin # | Arduino Mega Pin | Signal Name | Target Component | Signal Type / Design Note |
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

* `PCB Mars.zip` - Contains the files for the **Integrated Single-PCB** architecture.
* `PCB MARS_SHEET1.zip` - Contains the files for the **Control & Logic Board** (Dual-PCB).
* `PCB MARS_SHEET2.zip` - Contains the files for the **Power Distribution Board** (Dual-PCB).
* *(Add a note here if `New Text Document.txt` contains specific BOM or build notes)*

## 🛠️ Testing & Validation Status
- [x] Assembly and component clearance verification.
- [x] Voltage regulation and current draw analysis under load.
- [x] Logic signal transmission verification.
- [ ] Physical obstacle navigation testing (System Level).

---
*Designed and engineered for reliable autonomous operation in challenging terrain.*
