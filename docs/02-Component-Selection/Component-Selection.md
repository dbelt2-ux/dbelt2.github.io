---
title: Component Selection
tags:
- component-selection
- audio
---

## Overview

This page compares possible solutions for every major component in my individual subsystem, the **audio subsystem** of Team 206's automated pet feeder. Each block in my individual block diagram (audio amplifier, speaker, voltage regulator and external power supply) has at least three options. Each option lists its pros, cons, unit cost and a link to the product, and each section ends with my final choice and the reasoning behind it. The microcontroller (PIC18F57Q43 Curiosity Nano) is not included because it was selected for the class.

All of the components on this page belong to my individual subsystem: **Audio**.

**Design requirements that drive these choices:**

- The PIC generates tones with a PWM signal on RC3, so the amplifier must accept a single-ended input and run from the 5V rail.
- The speaker only needs to play short chimes and alert tones, loud enough to hear across a room.
- All logic and audio parts run from one 5V regulated rail, fed by a 9V wall supply.
- Parts must be solderable on our custom PCB and come with full datasheets.

---

## Audio Amplifier

**Individual Subsystem: Audio**

| Solution | Pros | Cons |
|---|---|---|
|<img width="381" height="272" alt="Screenshot 2026-10-16 162413" src="https://github.com/user-attachments/assets/3586249d-26d4-41ac-b290-ee652f6e1ce9" /> **Option 1:** [Diodes Inc. PAM8302AADCR mono class-D amplifier (SO-8)](https://www.mouser.com/c/?q=PAM8302AADCR) <br> $0.62 / each | • Class-D, about 85–88% efficient, so it runs cool <br> • Up to 1.5 W into 8 Ω at 5V <br> • Runs on 2.0–5.5V, a direct fit for the 5V rail <br> • Very low cost <br> • Shutdown pin (1 µA max) lets the PIC turn the amp off when idle <br> • Built-in thermal and short-circuit protection | • Surface-mount (SO-8), so it's harder to hand-solder than a DIP part <br> • Class-D output switches at high frequency, so careful PCB layout is needed to limit noise <br> • Fixed internal gain (about 24 dB), so volume must be set with an input resistor or in software |
| Solution | Pros | Cons |
| <img width="638" height="643" alt="Screenshot 2026-10-16 162724" src="https://github.com/user-attachments/assets/3e996b3f-1c36-4b81-8e6d-bcda21a53ed9" /> **Option 2:** [Texas Instruments TPA2005D1DGN mono class-D amplifier (MSOP-8)](https://www.digikey.com/en/products/result?keywords=TPA2005D1DGN) <br> $1.62 / each | • Class-D, efficient and cool-running <br> • Runs on 2.5–5.5V <br> • Gain is set with two external resistors, so it's easy to tune <br> • Well-documented TI part with reference designs | • Lower output power (1.4 W into 8 Ω) <br> • MSOP-8 package is very small and difficult to hand-solder <br> • About 2.6× the cost of the PAM8302A ($1.62 vs. $0.62) |
| Solution | Pros | Cons |
| <img width="635" height="486" alt="Screenshot 2026-10-16 162821" src="https://github.com/user-attachments/assets/1d0b2886-fd86-4d65-a396-79448650ba90" /> **Option 3:** [Texas Instruments LM386N-1/NOPB class-AB amplifier (DIP-8)](https://www.digikey.com/en/products/detail/texas-instruments/LM386N-1-NOPB/6284) <br> $1.18 / each | • Through-hole DIP-8, very easy to solder and breadboard <br> • Classic, widely used part with many example circuits <br> • Low cost | • Only about 325 mW output at 5V, which may be too quiet <br> • Class-AB is much less efficient, so more power is wasted as heat <br> • Needs a large output coupling capacitor (about 250 µF) <br> • Minimum supply of 4V leaves little headroom on a 5V rail |
| Solution | Pros | Cons |
| **Option 4 (custom):** Single NPN transistor speaker driver (e.g., 2N3904 + base resistor) <br> < $0.50 in parts | • Extremely cheap and simple <br> • All through-hole, easy to build <br> • Fine for basic beeps driven straight from PWM | • No real amplification of tone quality; output is a harsh square wave <br> • No protection, so a shorted speaker can damage the transistor <br> • Difficult to control volume <br> • Needs a flyback diode and current-limiting resistor, which adds design work |

**Choice:** Option 3, the Texas Instruments LM386N-1/NOPB

**Rationale:** The LM386 is a through-hole DIP-8 part, so the same chip works on the breadboard and on my PCB, and it can sit in an IC socket so a damaged chip is easy to replace. My subsystem only plays short feeding chimes and alert tones, so its output of about 325 mW into 8 Ω is loud enough. Its very common design is well documented, which lowers the risk for my first PCB. It is also inexpensive ($1.18), and its maximum quiescent current is only 8 mA. The PAM8302A and TPA2005D1 give more power, but both are surface-mount only and would need a separate breakout board for prototyping. Their class-D switching output also requires more careful PCB layout.

---

## Speaker

**Individual Subsystem: Audio**

| Solution | Pros | Cons |
|---|---|---|
| <img width="273" height="421" alt="Screenshot 2026-10-16 163255" src="https://github.com/user-attachments/assets/15fb562c-0aac-4453-9259-d1e3b0f29770" />  **Option 1:** [PUI Audio AS04008PO-2-R 8 Ω speaker (40 × 28 mm)](https://puiaudio.com/product/speakers-and-receivers/as04008po-2-r) <br> $3.57 / each | • 8 Ω impedance matches the PAM8302A's 1.5 W rating <br> • 1 W rated, 2 W maximum input, so it can't be overdriven by the amp <br> • Loud for its size (84 dB SPL) <br> • Wide 450 Hz–20 kHz frequency range covers chime and alert tones <br> • Small oval shape fits easily inside the feeder enclosure <br> • Full manufacturer datasheet | • Highest cost of the three options <br> • Weaker low-frequency response (below 450 Hz) because of its small size |
| Solutions | Pros | Cons |
| <img width="639" height="635" alt="Screenshot 2026-10-16 163531" src="https://github.com/user-attachments/assets/9c2caec5-a788-4f2e-b0a8-66886f98ece4" /> **Option 2:** [Adafruit 3923 Mini Oval Speaker – 8 Ω 1 W](https://www.digikey.com/en/products/detail/adafruit-industries-llc/3923/9658610) <br> $2.60 / each | • 8 Ω, 1 W, a good match for the amplifier <br> • Comes with a pre-attached 2-pin cable (Molex PicoBlade) <br> • Low cost and compact | • Less detailed specifications (no published SPL or frequency response) <br> • The amp can deliver 1.5 W, which is above this speaker's 1 W rating, so the volume must be limited <br> • Connector needs a matching header on the PCB, or the wires must be cut |
| Solution | Pros | Cons |
| <img width="817" height="565" alt="Screenshot 2026-10-16 163858" src="https://github.com/user-attachments/assets/35e72181-7283-4983-901e-3de846bfc913" /> **Option 3:** [Adafruit 1314 Speaker – 3" diameter, 4 Ω 3 W](https://www.adafruit.com/product/1314) <br> $1.95 / each | • Lowest cost <br> • Larger cone gives fuller, louder sound <br> • 3 W rating can't be overdriven by the amp | • 4 Ω load makes the amp draw much more current (up to 2.5 W out, roughly 0.6 A from 5V) <br> • 3" diameter is bulky inside the feeder <br> • Not RoHS compliant <br> • Minimal datasheet |

**Choice:** Option 1, the PUI Audio AS04008PO-2-R

**Rationale:** The 8 Ω impedance pairs with the PAM8302A to keep the amplifier's maximum current around 0.35 A. With the 4 Ω speaker it would be about 0.6 A, which would put a much larger load on my regulator and power supply. Its 2 W maximum input rating is above the amplifier's 1.5 W maximum output, so the speaker can't be damaged at full volume. The Adafruit mini oval speaker could be damaged at full volume, since its rating is 1 W. At 84 dB SPL it is loud enough to get a pet's attention across a room, and its small 40 × 28 mm size fits inside the feeder. It costs more than the other two options, but at $3.57 the difference is small, and it has the most complete datasheet for designing the board.

---

## Voltage Regulator (5V Rail)

**Individual Subsystem: Audio**

| Solution | Pros | Cons |
|---|---|---|
| <img width="539" height="500" alt="Screenshot 2026-10-16 163950" src="https://github.com/user-attachments/assets/b4dc94f5-395a-4773-8ba4-3fd7dc409b4a" /> **Option 1:** [Murata OKI-78SR-5/1.5-W36-C switching regulator, 5V 1.5A](https://www.mouser.com/c/?q=OKI-78SR-5%2F1.5-W36-C) <br> $6.00 / each | • Switching regulator, about 90% efficient, so little heat and no heatsink needed <br> • 1.5 A output gives plenty of margin over my about 0.5 A load <br> • Wide 7–36V input works with the 9V supply <br> • Drop-in pin replacement for a 7805 (3-pin through-hole SIP) <br> • Draws less current from the 9V supply than a linear regulator | • About 10× the cost of a 7805 <br> • Switching regulators add some output ripple and noise <br> • Taller package takes more vertical space |
| Solution | Pros | Cons|
| <img width="636" height="642" alt="Screenshot 2026-10-16 164355" src="https://github.com/user-attachments/assets/be3f9562-9700-4d84-a39f-54ef5b44fe65" /> **Option 2:** [STMicroelectronics L7805CV linear regulator, 5V 1.5A (TO-220)](https://www.digikey.com/en/products/result?keywords=L7805CV) <br> $0.60 / each | • Very cheap and easy to find <br> • Very simple circuit: only two capacitors needed <br> • Clean, low-noise output <br> • TO-220 through-hole is easy to solder | • Linear: wastes (9V − 5V) × load current as heat, about 2 W at my load <br> • Would need a heatsink to stay within safe temperature <br> • Draws the full load current from the 9V supply, so the supply works harder <br> • 2V dropout |
| Solution | Pros | Cons |
| <img width="1083" height="832" alt="Screenshot 2026-10-16 164415" src="https://github.com/user-attachments/assets/e2901568-3cb1-43ae-a300-42cf5241940b" /> **Option 3:** [Pololu D24V10F5 step-down regulator, 5V 1A](https://www.pololu.com/product/2831) <br> $12.95 / each | • 80–93% efficient switching regulator <br> • Very small module (18 × 13 mm) <br> • Very low quiescent current (about 200 µA) <br> • Has an enable pin | • Most expensive option <br> • 1 A output leaves less margin than the 1.5 A options <br> • It's a pre-built module, not a single component, so it takes header space on the PCB |

**Choice:** Option 1, the Murata OKI-78SR-5/1.5-W36-C

**Rationale:** My 5V rail needs about 0.51 A including a 25% safety margin (see the Power Budget page). A linear L7805 would turn about 2 W into heat at that load, enough to need a heatsink, and it would draw the full 0.51 A from the 9V supply. The OKI-78SR is about 90% efficient, so it stays cool without a heatsink and draws only about 0.32 A from the 9V supply. It also matches the 5V 1.5A regulator in my block diagram and uses the same 3-pin layout as a 7805, so the PCB footprint stays simple. The Pololu module also works, but it costs twice as much and has less current margin.

---

## External Power Supply

**Individual Subsystem: Audio**

| Solution | Pros | Cons |
|---|---|---|
| <img width="939" height="583" alt="Screenshot 2026-10-16 164638" src="https://github.com/user-attachments/assets/de8bb2e5-ba14-48d6-bed7-5a29d4fc3059" /> **Option 1:** [Adafruit 63 – 9 VDC 1000 mA regulated switching wall adapter](https://www.adafruit.com/product/63) <br> $8.95 / each | • 9V 1A output matches my block diagram <br> • 1 A is about 3× my estimated 9V-side draw of about 0.32 A <br> • UL listed and regulated <br> • Standard 2.1 mm center-positive barrel plug <br> • Low cost | • Must be plugged into a wall outlet, so the feeder can't run during a power outage <br> • Limited published specs compared to industrial adapters |
| Solution | Pros | Cons |
| <img width="338" height="368" alt="Screenshot 2026-10-16 164646" src="https://github.com/user-attachments/assets/a9c38a7d-2931-4b15-bdda-e91fa40d6dc0" /> **Option 2:** [CUI / Bel Power SWI12-9-N-P5 9V 1.2A wall adapter](https://www.newark.com/cui/swi12-9-n-p5/adapter-ac-dc-9v-1-2a-rohs-compliant/dp/13AJ1382) <br> $18.11 / each | • 9V at 1.2 A (10.8 W) gives slightly more margin <br> • Detailed manufacturer datasheet <br> • 2.1 × 5.5 mm center-positive barrel plug | • About 2× the cost of Option 1 <br> • Extra current capacity isn't needed for my load |
| Solution | Pros | Cons |
| <img width="233" height="227" alt="Screenshot 2026-10-16 164657" src="https://github.com/user-attachments/assets/2b19e82e-3a37-42c0-b7ef-7eb813b55866" /> **Option 3:** [Energizer 522 9V alkaline battery](https://www.jameco.com/z/ALK-9V-522-Energizer-9V-Energizer-reg-Alkaline-Battery_198731.html) <br> $2.95 / each | • Portable; no outlet needed <br> • Keeps working during power outages <br> • Cheapest up-front cost | • Only about 600 mAh, which is about 1.9 hours at my worst-case load <br> • Voltage drops as it discharges <br> • Needs frequent replacement, which is impractical for a pet feeder that runs all day |

**Choice:** Option 1, the Adafruit 63 9V 1A wall adapter

**Rationale:** A pet feeder runs continuously, so a wall supply makes more sense than a battery. A 9V battery would last only about 2 hours at worst-case load. The Adafruit adapter provides 9V at 1 A, which is about three times the 0.32 A my regulator draws at worst case, so it has plenty of headroom. It is UL listed, uses a standard barrel plug, and costs half as much as the CUI adapter.

---

## Summary of Selected Components

| Block | Selected Part | Manufacturer | Unit Cost |
|---|---|---|---|
| Audio Amplifier | PAM8302AADCR | Diodes Incorporated | $0.62 |
| Speaker | AS04008PO-2-R | PUI Audio | $3.57 |
| Voltage Regulator | OKI-78SR-5/1.5-W36-C | Murata Power Solutions | $6.00 |
| Power Supply | 9 VDC 1000 mA adapter (63) | Adafruit | $8.95 |
| **Total** | | | **$19.14** |

*Prices are quantity-1 prices checked in October 2026 and may change.*
