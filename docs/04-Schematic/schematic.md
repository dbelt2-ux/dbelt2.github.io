# Schematic

## Overview

This schematic is designed to support the **audio subsystem** of Team 206's pet feeder. A PIC18F57Q43 Curiosity Nano generates a PWM tone on RC3, which is filtered and amplified by an LM386 audio amplifier to drive an off-board speaker. The board talks to the team hub (AJ's board) over UART through an 8-pin IDC ribbon cable.

**Power:** A 9–12 V wall adapter enters through a through-hole barrel jack and a removable 1 A fuse, then an L7805 linear regulator produces the 5 V rail. The regulator has 0.33 µF input and 0.1 µF output capacitors, a 10 µF bulk capacitor supports the rail, and a green LED shows when 5 V is present. Jumpers JP1 and JP2 isolate the amplifier and the microcontroller from the 5 V rail for troubleshooting.

**Controller:** The PIC18F57Q43 Curiosity Nano (custom symbol) is powered through VBUS with a 0.1 µF bypass capacitor. It is programmed through the Curiosity Nano's onboard USB debugger. UART RX/TX (RB0/RB1) and five additional I/O lines go to the ribbon cable, along with ground.

**Audio:** The PWM signal passes through a 1 kΩ / 47 nF low-pass filter and a 1 µF coupling capacitor, then a 10 kΩ volume potentiometer into the LM386 (gain of 20). The output drives the speaker through a 220 µF coupling capacitor, with a 10 Ω / 47 nF network for stability.

**Debug and expansion:** A red debug LED (RD3), a hardware-debounced push button with a 10 kΩ pull-up (RD4), four test points (+5 V, GND, AUDIO_PWM, amplifier output), an 8-pin expansion header, and a 2x12 header that breaks out all unused GPIO pins.

<img width="1236" height="872" alt="Screenshot 2026-10-30 153902" src="https://github.com/user-attachments/assets/e1197e47-064a-4d10-877c-28565a10be41" />



**Figure 1:** Audio subsystem schematic.

## Resources

The schematic as a PDF download is available [here](https://github.com/user-attachments/files/34198544/DB_Audio_Subsystem.4.pdf)
, and the Zip folder of the project [here](https://github.com/user-attachments/files/34203704/DB_Audio_Subsystem1.zip)

.
