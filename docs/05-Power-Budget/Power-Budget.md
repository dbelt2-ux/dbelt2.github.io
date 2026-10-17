---
title: Power Budget
tags:
- power-budget
- audio
---

## Overview

This power budget checks that the selected regulator and power supply can power every major component in my audio subsystem at the same time, with a 25% safety margin. It follows the class power budget template. Current values come from each component's datasheet, using maximum or worst-case values.

<img width="1258" height="629" alt="Screenshot 2026-10-16 171822" src="https://github.com/user-attachments/assets/92a67e8b-dfc4-4fa4-8b1c-953df9e8dfab" />
<img width="1255" height="512" alt="Screenshot 2026-10-16 171841" src="https://github.com/user-attachments/assets/f296ef9c-218d-4bf9-b8b0-e2c0066b314a" />



## Summary

| Item | Value |
|---|---|
| Power rails | One 5V regulated rail |
| Total current on 5V rail (with 25% margin) | 514 mA |
| 5V regulator | Murata OKI-78SR-5/1.5-W36-C, 1500 mA. **986 mA remaining** |
| External power source | Adafruit 63, 9V 1000 mA wall adapter. **683 mA remaining** |
| Battery life | Not applicable (wall supply) |

Both "remaining current" values are positive, so the regulator and wall supply can power the whole subsystem at worst-case load.

## Calculations

- **Speaker current:** The speaker draws its power through the amplifier, the same way a motor draws current through its motor driver. At the PAM8302A's maximum output of 1.5 W into 8 Ω at 85% efficiency: 1.5 W ÷ 0.85 ÷ 5V = **353 mA**.
- **5V rail total:** 50 mA (Curiosity Nano) + 8 mA (amplifier) + 353 mA (speaker) = 411 mA. With the 25% margin: 411 × 1.25 = **514 mA**.
- **Current drawn from the 9V supply:** The OKI-78SR is a switching regulator, about 90% efficient. 5V × 0.514 A ÷ 0.90 ÷ 9V = **317 mA**.
- **Curiosity Nano current:** 50 mA is a conservative estimate (MCU core at 64 MHz plus I/O) and will be checked against the PIC18F57Q43 datasheet.
- **Powering the Curiosity Nano:** 5V is applied to the VTG pin with VOFF tied to GND, which disables the board's own regulator. The maximum VTG voltage is 5.5V.

For comparison, a 9V alkaline battery (Energizer 522, about 600 mAh) would last only about 600 ÷ 317 ≈ **1.9 hours** at worst-case load, which is why a wall supply was chosen. Full regulator and power supply comparisons are on the Component Selection page.
