# 9-Channel Industrial Relay Card

## What this project is
This is a high-reliability, 9-channel relay control board designed to handle heavy-duty industrial loads like lift motors, brakes, and fans. Instead of using flimsy jumper wires that can easily shake loose, I built this entire board using Through-Hole Technology (THT) and heavy-duty screw terminals so it can take a lot of continuous vibration and keep running smoothly.

## Why I made it
I wanted to design a replication of the durable cards used in real industrial elevator systems. Most hobbyist relay boards aren't built to handle continuous mechanical stress or high startup current spikes. By designing my own PCB layout with widened power tracks and robust components, I created something that is tough enough to replace actual industrial cards.

---

## 📸 Project Gallery

### 3D Project Render
![3D PCB View](production/3D_PCB1_2026-05-09.png)

### PCB Layout & Routing Traces
![PCB Routing View](Screenshots/Screenshot%202026-05-18%20173530.png)

### Circuit Schematic
![Circuit Schematic](Schemetic/SCH_Schematic1_1-P1_2026-05-18.png)

---

## 🧠 Circuit Design Logic

### The "Empty Pin" Trick
To make sure the standard 5-pin industrial relays sit completely flat and secure on the board, I used a full 5-hole drilling layout based on the O/E/N 58 standard. However, since I don't want any power running through the Normally Closed (NC) state, Pin 3 has a physical hole for mechanical stability but absolutely no copper tracks routed to it. It stays completely electronically isolated.

### Protection & LEDs
Every single one of the 9 channels has its own protection and status loop:
* **Flyback Diodes:** I put a 1N4007 diode directly across each relay coil. The silver cathode line faces the positive rail to stop the coil's magnetic field collapse from frying the control circuit.
* **Status LEDs:** I wired a 3mm LED with a 10kΩ resistor across the coil pins. If power is reaching the relay coil, the LED lights up immediately so you can troubleshoot errors instantly just by looking at the card.

### PCB Layout Choices
* **Control Lines:** Kept thin at 0.254mm – 0.3mm since they only carry low signal currents.
* **Power & Load Rails:** Widened up to 1.5mm – 2.0mm. This is super important because motor and brake startup current spikes will burn right through standard thin PCB traces.
* **Hole Sizes:** Set to 1.4mm to easily fit the extra-thick legs of heavy-duty Vicco relays.

---

## 🛠️ How to Assemble & Test
1. **Watch the Polarity:** Make sure the silver band on the 1N4007 diodes faces the positive rail, and the long leg of the LEDs goes to the positive side.
2. **Bench Testing:** Hook up 12V DC to the input terminal blocks. The channel's LED should turn on right away, and you should hear a loud, clean mechanical "click" from the relay.

---

## 📊 Bill of Materials (BOM)

| Component Reference Designator | Component Description | Quantity | Package / Footprint Type | Purpose / Function |
| :--- | :--- | :---: | :--- | :--- |
| RELAY1, RELAY2, RELAY3, RELAY4, RELAY5, RELAY6 | 12V DC Industrial Relays (SLOW, COM, LIL, CIL, FAN, INS) | 6 | 5-Pin Square THT | Control-side logic switching and signaling circuits | 
| K1, K2, K3, K4 | 12V DC Power Relays (UP, DOWN, BRAKE, RAM) | 4 | 4-Pin / Dual-Line Rectangular THT | Switches heavy-duty motor, brake, and directional coils | 
| Diodes (D10 - D19) | 1N4007 Rectifier Diodes | 10 | DO-41 (Axial Through-Hole) | Flyback voltage spike suppression across relay coils | 
| LEDs (U1 - U10) | 3mm Red LEDs | 10 | Radial THT (2.54mm pitch) | Individual channel active status indicators | 
| Resistors (R10 - R19) | 10kΩ Resistors | 10 | Axial Through-Hole | Current-limiting resistors for status circuits | 
| Terminal Blocks | 2-Pin Screw Terminal Blocks | 11 | THT (5.08mm pitch) | Secure wire connections for signal lines and low power | 
| Terminal Blocks | 3-Pin Screw Terminal Blocks | 3 | THT (5.08mm pitch) | High-voltage/high-current terminal load outputs |
