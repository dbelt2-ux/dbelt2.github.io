---
title: PCB Design
tags:
- pcb design
- audio
---

# PCB Design
 
## Overview
 
This is the printed circuit board for the **audio subsystem** of Team 206's pet feeder. It was laid out in KiCad and is milled on the LPKF ProtoMat S63 in Peralta 109.
 
**Board specifications**
 
| Item | Value |
|---|---|
| Size | 100 mm × 100 mm |
| Layers | 2 (top and bottom copper), plated through-holes |
| Copper | 0.5 oz/ft² |
| Solder mask / silkscreen | None |
| Minimum signal trace | 0.381 mm (15 mil) |
| Power traces (+5 V and 9–12 V input) | 1.016 mm (40 mil) |
| Minimum clearance | 0.254 mm (10 mil) |
| Minimum annular ring | 0.381 mm (15 mil) |
| Ground plane | GND pour on both layers |
| Vias | None |
 
**Layout:**
- The **Curiosity Nano** sits on the left edge, with its USB end hanging over the top of the board so the programming cable can plug in. It mounts in female headers using a custom footprint (`DB_Curiosity_Nano`) from my own footprint library, `DB_Audio_FP`.
- The **2x12 GPIO breakout (J5)** is right next to the Nano. Its pins are ordered to match the Nano's pin order, so most connections are short, straight traces.
- The **power section** (barrel jack, fuse, L7805 regulator with heatsink) is in the bottom-right corner. Its 9–12 V input and 5 V traces are 40 mil wide.
- The **audio section** (LM386, volume pot, filter and output parts) is in the top-right, and the speaker header (J3) is on the right edge.
- The **ribbon header (J2)** to the team hub board is on the top edge.
- The **debug parts** (debug LED, power LED, button, test points) are along the bottom.
**Routing:** Right-side Nano pins are routed on the bottom layer. Left-side pins are routed on the top layer around the end of the Nano. Every trace stays on one layer, so the board has no vias. The total current draw is well under 500 mA, so 40 mil power traces are enough for 0.5 oz copper.
 
**Verification:** KiCad's Design Rules Check passes with **0 errors and 0 unconnected items**, using the Peralta mill rules. The schematic parity check also passes, and the Gerber files pass the design-for-manufacturing check with no errors. My initials (**DB**) are on the top copper layer.
 
[PCB top layer]<img width="2524" height="2524" alt="DB_PCB_Top" src="https://github.com/user-attachments/assets/6c6057b2-560d-4944-b51e-34dd5e3feb72" />
 
**Figure 1:** Top copper layer (F.Cu) with ground pour.
 
[PCB bottom layer]<img width="2524" height="2524" alt="DB_PCB_Bottom" src="https://github.com/user-attachments/assets/6712af7e-b259-4afa-9459-cb5d4f08d3ae" />

 
**Figure 2:** Bottom copper layer (B.Cu) with ground pour, viewed from the top of the board.
 
## Resources
 
- The PCB layout (top and bottom layers) as a PDF is available [here](https://github.com/user-attachments/files/34603415/DB_PCB_Layout.pdf)
- The KiCad project, including my custom symbol and footprint libraries, is available [here](https://github.com/user-attachments/files/34603430/DB_Audio_Subsystem3.zip)
- The Gerber and drill files submitted for manufacturing are available [here](https://github.com/user-attachments/files/34603440/DonovanBelt206.zip)
