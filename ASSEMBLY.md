# Hardware Assembly & Layout Guidelines

## ⚡ Power Distribution & Wiring
* **Main Power Routing:** Use ≥12–10 AWG wire or very wide copper pours for the path from the battery to the main rail and motor bucks[cite: 3].
* **Motor Driver Routing:** Use ≥14 AWG wire or wide pours between the buck converters and the Cytron MD20A modules, as each motor can hit double-digit amps upon stalling[cite: 3].
* **Logic & Servo Power:** 18–20 AWG wire is sufficient for UBECs and logic rails[cite: 3].
* **Grounding:** All grounds must be common. Run separate solid ground pours for power and logic, then join them at a single star point near the battery return[cite: 3].

## 🕳️ PCB Manufacturing Specifications
When fabricating or modifying the PCB, adhere to the following drill and pad sizes:
* **Small signal pins (Arduino headers, jumper wires):** Drill = 1.0 mm, Pad = 2.0 mm (minimum) or 2.2 mm (recommended)[cite: 3].
* **Medium connector pins:** Drill = 1.2 mm, Pad = 2.2 mm[cite: 3].
* **High-current screw terminals / Motor drivers:** Drill = 2.0–2.5 mm, Pad = 3.5–4.0 mm[cite: 3].

## 🔌 Decoupling & Protection
* **Motor Drivers:** Add a ≥470 µF electrolytic capacitor close to each MD20A VMOTOR pin pair[cite: 3].
* **Servos:** Place a 1,000–2,200 µF electrolytic capacitor at each servo power output on the PCB to handle surge currents[cite: 3].
