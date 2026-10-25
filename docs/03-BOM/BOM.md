---
title: Bill of Materials
tags:
- bom
- audio
---

## Overview

This Bill of Materials lists every component in my audio subsystem schematic (DB_Audio_Subsystem, Rev 1), plus the supporting hardware needed to build and debug the board: IC socket, headers, jumper shunts, test points, heatsink and cabling. Parts are grouped by supplier. Order quantities cover one breadboard prototype, one PCB and 1–2 spares per part. Parts available in Peralta 109 or handed out in class are listed but not purchased.

- **DigiKey order:** 13 line items, **$50.81** subtotal
- **Purchased parts cost per board:** $16.98

## Purchased from DigiKey

| Description | Qty / Board | Unit Cost | Manufacturer | Mfr Part # | DigiKey Part # | # Ordered | Ref Des |
|---|---|---|---|---|---|---|---|
| Audio amplifier IC, 325 mW, 8-pin DIP | 1 | $1.180 | Texas Instruments | LM386N-1/NOPB | [296-44414-5-ND](https://www.digikey.com/en/products/result?keywords=296-44414-5-ND) | 3 | U3 |
| 5V 1.5A linear voltage regulator, TO-220 | 1 | $1.080 | STMicroelectronics | L7805CV | [497-1443-5-ND](https://www.digikey.com/en/products/result?keywords=497-1443-5-ND) | 3 | U1 |
| Heatsink for TO-220, 24.4 °C/W | 1 | $1.720 | Aavid (Boyd) | 577202B00000G | [HS107-ND](https://www.digikey.com/en/products/result?keywords=HS107-ND) | 4 | HS1 |
| Speaker, 8 Ω, 1 W (2 W max), 84 dB, wire leads | 1 | $6.780 | PUI Audio | AS04008PO-2-WR-R | [668-1114-ND](https://www.digikey.com/en/products/result?keywords=668-1114-ND) | 2 | J3 (speaker) |
| Trimmer potentiometer, 10 kΩ, 0.5 W, top adjust | 1 | $1.820 | Bourns | 3386P-1-103LF | [3386P-103LF-ND](https://www.digikey.com/en/products/result?keywords=3386P-103LF-ND) | 3 | RV1 |
| Shrouded box header, 2x4, 2.54 mm, vertical | 1 | $1.030 | Würth Elektronik | 61200821621 | [732-5395-ND](https://www.digikey.com/en/products/result?keywords=732-5395-ND) | 3 | J2 |
| PCB test point, miniature, red | 3 | $0.263 | Keystone | 5000 | [36-5000-ND](https://www.digikey.com/en/products/result?keywords=36-5000-ND) | 12 | TP1, TP3, TP4 |
| PCB test point, miniature, black | 1 | $0.270 | Keystone | 5001 | [36-5001-ND](https://www.digikey.com/en/products/result?keywords=36-5001-ND) | 4 | TP2 |
| Aluminum electrolytic capacitor, 220 µF, 25V, 8×11.5 mm | 1 | $0.370 | Nichicon | UVR1E221MPD | [493-1062-ND](https://www.digikey.com/en/products/result?keywords=493-1062-ND) | 4 | C7 |
| Aluminum electrolytic capacitor, 10 µF, 50V, 5×11 mm | 1 | $0.390 | Panasonic | EEU-FC1H100L | [P10316-ND](https://www.digikey.com/en/products/result?keywords=P10316-ND) | 4 | C10 |
| Jumper shunt, 2.54 mm, gold | 2 | $0.029 | Sullins | QPC02SXGN-RC | [S9337-ND](https://www.digikey.com/en/products/result?keywords=S9337-ND) | 10 | JP1, JP2 |
| Ceramic capacitor, 47 nF, 50V, X7R, radial 2.54 mm | 2 | $0.350 | KEMET | C315C473K5R5TA | [399-C315C473K5R5TA-ND](https://www.digikey.com/en/products/result?keywords=399-C315C473K5R5TA-ND) | 10 | C4, C8 |
| Ceramic capacitor, 1 µF, 50V, X7R, radial 5.0 mm | 2 | $0.397 | TDK | FK20X7R1H105KN000 | [445-FK20X7R1H105KN000-ND](https://www.digikey.com/en/products/result?keywords=445-FK20X7R1H105KN000-ND) | 10 | C1, C5 |

**DigiKey subtotal: $50.81**

## From Peralta 109 Stock, Class Kit, or Team

| Description | Qty / Board | Manufacturer | Mfr Part # | Supplier | Qty Needed | Ref Des |
|---|---|---|---|---|---|---|
| Ceramic capacitor, 0.1 µF, 50V, X7R, radial 5 mm | 4 | Vishay | K104K10X7RF5UH5 | PRLTA 109 | 8 | C2, C3, C6, C9 |
| Resistor, 1 kΩ, 1/4 W, axial | 2 | — | — | Class kit | 4 | R1, R5 |
| Resistor, 10 Ω, 1/4 W, axial | 1 | — | — | Class kit | 2 | R2 |
| Resistor, 330 Ω, 1/4 W, axial | 1 | — | — | Class kit | 2 | R3 |
| Resistor, 10 kΩ, 1/4 W, axial | 1 | — | — | Class kit | 2 | R4 |
| LED, red, 5 mm | 1 | — | — | Class kit | 2 | D1 |
| LED, green, 5 mm | 1 | — | — | Class kit | 2 | D2 |
| Tactile pushbutton, 6 mm | 1 | — | — | Class kit | 2 | SW1 |
| Fuse, 5x20 mm, 1 A | 1 | NTE Electronics | 74-5FG1A | PRLTA 109 | 2 | F1 |
| Fuse holder, 5x20 mm, PCB mount | 1 | Keystone | 4628 | Class kit | 1 | F1 |
| DC barrel jack, 2.1 mm | 1 | CUI Devices | PJ-102AH | Class kit | 1 | J1 |
| PIC18F57Q43 Curiosity Nano | 1 | Microchip | DM164150 | Class kit | 1 | U2 |
| IC socket, 8-pin DIP | 1 | Assmann WSW | A-08-LC-TT | PRLTA 109 | 2 | U3 (socket) |
| Female header strip, 1x40, 2.54 mm (cut to 1x28) | 2 | — | — | PRLTA 109 | 4 | U2 (socket) |
| Male header strip, 1x40, 2.54 mm (cut to size) | 1 | — | — | PRLTA 109 | 2 | J3, J4, JP1, JP2 |
| Male header, 2x12, 2.54 mm (optional, unused GPIO) | 1 | — | — | PRLTA 109 | 1 | J5 |
| Female header, 1x2 (speaker wire connector) | 1 | — | — | PRLTA 109 | 2 | J3 (speaker plug) |
| Screw and nut, #4-40 (heatsink mounting) | 1 | — | — | PRLTA 109 | 2 | HS1 |
| 9V wall power supply | 1 | — | — | Class kit | 1 | J1 (power) |
| 2x4 IDC ribbon cable to teammate's board | 1 | — | — | Team | 1 | J2 (cable) |

## Datasheets


