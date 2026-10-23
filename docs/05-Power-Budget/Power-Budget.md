---
title: Power Budget
tags:
- power-budget
- audio
---

## Overview

This power budget checks that the selected regulator and power supply can power every major component in my audio subsystem at the same time, with a 25% safety margin. It follows the class power budget template. Current values come from each component's datasheet, using maximum or worst-case values.

<img width="2200" height="1100" alt="Screenshot 2026-10-23 103602" src="https://github.com/user-attachments/assets/c1688cc6-483f-499c-8e96-4ab1356647c1" />
<img width="2192" height="885" alt="Screenshot 2026-10-23 103633" src="https://github.com/user-attachments/assets/561cd612-c583-41fb-a46c-6ca2c0a59dfa" />



## Summary
 
| Item | Value |
|---|---|
| Power rails | One 5V regulated rail |
| Total current on 5V rail (with 25% margin) | 429 mA |
| 5V regulator | STMicroelectronics L7805CV, 1500 mA. **1071 mA remaining** |
| External power source | Adafruit 63, 9V 1000 mA wall adapter. **563 mA remaining** |
| Battery life | Not applicable (wall supply) |
 
Both "remaining current" values are positive, so the regulator and wall supply can power the whole subsystem at worst-case load.
 
## Calculations
 
- **Speaker current:** The speaker draws its power through the LM386 amplifier, the same way a motor draws current through its motor driver. The LM386N-1 delivers about 325 mW into 8 Ω, so the worst-case peak speaker current is √(2 × 0.325 W ÷ 8 Ω) = **285 mA**.
- **LM386 quiescent current:** 8 mA maximum (datasheet).
- **5V rail total:** 50 mA (Curiosity Nano) + 8 mA (LM386) + 285 mA (speaker) = 343 mA. With the 25% margin: 343 × 1.25 = **429 mA**.
- **Current drawn from the 9V supply:** The L7805 is a linear regulator, so its input current equals its output current plus its 8 mA quiescent current: 429 + 8 = **437 mA**.
- **Regulator heat:** (9V − 5V) × 0.429 A + 9V × 0.008 A = **1.79 W**. With the TO-220 package's 50 °C/W junction-to-ambient rating, that is about 89 °C above room temperature, close to the 125 °C junction limit. A TO-220 heatsink is used to keep the regulator cool.
- **Curiosity Nano current:** 50 mA is a conservative estimate (MCU core at 64 MHz plus I/O) and will be checked against the PIC18F57Q43 datasheet.
For comparison, a 9V alkaline battery (Energizer 522, about 600 mAh) would last only about 600 ÷ 437 ≈ **1.4 hours** at worst-case load, which is why a wall supply was chosen. Full regulator and power supply comparisons are on the Component Selection page.
 
