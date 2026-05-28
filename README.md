# My 10-Channel Lift Relay Board

Hey, I built this custom relay board to replicate the heavy-duty cards used in real elevator/lift control setups. I noticed that generic relay boards you buy online are way too fragile and use jumper wires that easily shake loose under continuous vibration. I wanted to make something way tougher using through-hole parts and screw terminals so the wires stay locked in place.

Here is the 3D view of my board:
![3D PCB View](Production/3D_PCB1_2026-05-09.png)

This is a close up of my trace layout:
![PCB Routing View](Screenshots/Screenshot%202026-05-18%20173530.png)

And here is my schematic layout from EasyEDA:
![Circuit Schematic](Screenshots/SCH_Schematic1_1-P1_2026-05-18)

### How I designed it
I used two different types of relays for this board. There are 6 square 5-pin relays for the control logic (handling things like slow speed, common signals, the fan, etc.), and 4 rectangular power relays to handle the heavier directions and brakes (UP, DOWN, BRAKE, RAM).

A cool trick I did for the 5-pin relays was using an "empty pin" setup. I used a standard 5-hole footprint so they sit completely flat and stable on the board, but I didn't route any copper tracks to Pin 3 (Normally Closed). This keeps the NC circuit totally isolated while keeping the relay physically solid.

For protection, I put a 1N4007 flyback diode across every single relay coil to stop voltage spikes from damaging the circuit when the coils turn off. I also wired a small 3mm LED with a 10k resistor next to each relay so you can see instantly if a channel is getting power. 

Because lift motors and brakes draw a lot of sudden startup current, I widened the main power and load tracks to 1.5mm - 2.0mm so they don't burn out. The low-power signal tracks are kept normal at around 0.254mm.

### My Component List (BOM)
* 6 square 5-pin industrial relays (12V DC coils)
* 4 rectangular power relays (12V DC coils)
* 10 rectifier diodes (1N4007)
* 10 red LEDs (3mm size)
* 10 resistors (10k ohms)
* 11 two-pin screw terminal blocks (5.08mm pitch)
* 3 three-pin screw terminal blocks (5.08mm pitch)
