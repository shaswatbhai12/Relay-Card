1. Project Overview
This project is a high-reliability, 9-channel relay control board designed to replace or replicate industrial cards. It focuses on driving heavy-duty loads such as motors, brakes, and fans. The design prioritizes durability by using Through-Hole Technology (THT) and Screw Terminal connections instead of fragile jumper wires.

2. Technical Specifications
Operating Voltage: 12V DC (Coil)

Switching Capacity: Up to 10A / 230V AC

Component Mounting: Through-Hole (Axial and DIP)

Safety Feature: "Empty Pin" Footprint for physical stability without electrical connection to the Normally Closed (NC) state.

Feedback System: Individual LED indicators connected in parallel to the relay coils.

4. Circuit Design Logic
A. The "Empty Pin" Space (Mechanical Fit)
To ensure the 5-pin industrial relays sit flat on the board, a 5-hole drilling pattern is used (based on the O/E/N 58 standard).

Implementation: While the board has a hole for Pin 3 (Normally Closed), no copper track is routed to it.

Result: The relay is physically secure, but the NC circuit is electronically isolated, meeting the "empty pin" requirement.

B. Protection & Indicator Logic
Each of the 9 channels includes a protection circuit and a status indicator:

Flyback Diode: A 1N4007 is placed across the relay coil. The silver line (cathode) must face the positive voltage rail to prevent the coil's magnetic field collapse from damaging the control circuit.

Coil-Side LED: To match professional industrial cards, the LED and its 10k$\Omega$ resistor are connected across the coil pins.

ON: Power is reaching the relay coil.

OFF: No control signal is present.

5. PCB Layout Guidelines
Track Widths
Control Signals: 0.254mm – 0.3mm

Power & Load Rails: 1.5mm – 2.0mm (Essential for handling motor startup current).

Footprint Spacing
Grid: 2.54mm (Standard)

Relay Hole Size: 1.4mm (To accommodate the thick legs of Vicco relays).

Resistor Spacing: 7.5mm – 10.0mm (To allow for easy leg bending).

6. Assembly & Troubleshooting
Polarity Check: Verify the orientation of the 1N4007 diodes and the long leg (anode) of the LEDs.

Testing: Apply 12V to the input terminals. The corresponding LED should light up, and an audible "click" should be heard from the relay.