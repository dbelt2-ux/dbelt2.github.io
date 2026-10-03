---
title: Individual Block Diagram
tags:
- Block-Diagram
- Audio
---

## Overview

This block diagram aims to show the audio subsystem of Team 206's automated pet feeder. It lays out how the hardware on my board is connected, which microcontroller pins and peripherals are going to be used, and how my board communicates with my teammates' boards. It will be updated with final part numbers before the design review.

**Power source:** The subsystem is powered by a 9V, 1A unregulated supply, which feeds a voltage regulator that provides 5V at up to 1.5A.

**Power levels:** All components on the board run from the 5V regulated rail, including the PIC18F57Q43 Curiosity Nano and the audio amplifier. The 9V rail is used only as the input to the regulator.

**Sensors:** This subsystem has no sensors of its own. Its inputs are two digital signals from AJ's board, which tell it when to play a sound.

**Actuator:** An 8 Ω speaker, driven by a class-D audio amplifier. The microcontroller generates tones using its PWM1 peripheral on pin RC3. The amplifier boosts that signal and drives the speaker over two pins.

**Team connections:** My board connects only to AJ's board, which acts as the hub of our team's design. The two boards are linked by an 8-pin ribbon cable:

| Ribbon Pin | Direction | My MCU Pin | Purpose |
|---|---|---|---|
| 1 | AJ → Donovan | RB0 | Play feeding chime |
| 2 | AJ → Donovan | RB1 | Play alert tone |
| 3–7 | — | — | Unused |
| 8 | — | GND | Shared ground |

Both signals are 5V digital, one pin each. Every ribbon cable pin connects directly to a microcontroller pin, not to a sensor or actuator.



## Block Diagram 


<img width="617" height="750" alt="Donovan_Block_Diagram drawio" src="https://github.com/user-attachments/assets/dc877aa0-0e9e-4fed-ac5b-dcb893f8deec" />

