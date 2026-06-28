# Bill of Materials (BOM) - Autonomous Mars Rover

## Main Components
| Component | Quantity | Specification / Part Number | Notes |
| :--- | :---: | :--- | :--- |
| **Battery** | 1 | 22.2V 6S LiPo (XT90-S connector) | Max total system draw calculated at ~50.61A[cite: 2, 3]. |
| **Main Fuse** | 1 | 60A - 80A | Place right after the battery on the main power switch[cite: 3]. |
| **Power Distribution Board** | 2 | >50A Rating | To handle the ~1123.65W maximum theoretical load[cite: 2]. |
| **DC Motors** | 6 | Pro-Range Planetary Gear 12V 96RPM (PG36M555-50.9K) | Max torque at 12V / 12A[cite: 2]. |
| **Servos** | 6 | DSSERVO 60KG DS5160 180° Metal Gear | Max torque at 7.4V/7.5V and 5.4A stall current[cite: 2]. |
| **Motor Drivers** | 6 | Cytron MD20A (20Amp 6V-30V) | Connect to Arduino Mega for PWM/DIR control[cite: 2, 3]. |
| **Compute Modules** | 1 | Arduino Mega (Rev3) | Primary real-time control[cite: 3]. |
| **Compute Modules** | 1 | Jetson Orin Nano | Consumes ~15W working[cite: 2]. |

## Power Regulation Modules
| Component | Quantity | Specification | Target Component |
| :--- | :---: | :--- | :--- |
| **Buck Converter (Motors)** | 6 | 200W / 20A | Steps 22.2V down to 12.0V for MD20A inputs[cite: 2, 3]. |
| **UBEC (Servos)** | 6 | 8A | Steps 22.2V down to 7.4V (or 6.0V depending on servo limits)[cite: 2, 3]. |
| **Buck Converter (Logic)** | 1 | XL4015 (5A) | Steps 22.2V down to 8.0-9.0V to feed Arduino Mega VIN[cite: 2, 3]. |
| **Buck Converter (Vision)** | 1 | LM2596 (or 5-6A buck) | Steps 22.2V down to 5V (4-5A) for Jetson Orin Nano[cite: 2, 3]. |
