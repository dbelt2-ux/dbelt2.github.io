---
title: Welcome
tags:
- tag1
- tag2
---
<center>
<font size= "6"> Donovan Belt Datasheet</font><br>
as part of<br>
<font size= "8"> Automatic Pet Feeder</font><br>
for<br>
<font size= "5"> Team 206 </font><br>

**Submission: December, 07, 2026**
</center>

## Introduction

This datasheet documents my individual subsystem for Team 206's Automatic Pet Feeder: the **audio subsystem**. It covers how the subsystem was designed, from the block diagram and component selection through the power budget, schematic and bill of materials, so a reader can understand what the board does, how it connects to the rest of the team's system, and how it was built.

## Project Summary

The Automatic Pet Feeder dispenses food on a schedule, monitors how much food is left, and alerts the owner and the pet with light and sound. The system is split across three boards, each controlled by its own PIC18F57Q43 Curiosity Nano and connected by 8-pin ribbon cables:

- **Justin Gonzalez – Sensing & User Input:** Photoresistors that detect the food level, plus pushbuttons for user input.
- **AJ Bowers – Motor Control (hub):** Color sensors and two motors with H-bridge drivers that dispense the food. AJ's board connects to both other boards.
- **Donovan Belt – Audio:** Plays a feeding chime and alert tones through a speaker.

My board receives two digital signals from AJ's board over the ribbon cable, one for a feeding chime and one for an alert. The PIC generates the tone with PWM, and an LM386 amplifier drives an 8 Ω speaker. This gives the feeder an audible cue when food is dispensed or when the food level is low.

For the full team design, see the [team report](https://asu-egr304-2026-f-206.github.io/).

## My Contribution

I designed, documented and will build the audio subsystem. Each section of this datasheet covers one stage of that work:

- Block Diagram: How my board is laid out and how it connects to AJ's board
- Component Selection: The options compared for each major part, and why I chose the LM386 amplifier, PUI Audio speaker, L7805 regulator and 9V wall supply
- Power Budget: Current draw on the 5V rail and confirmation that the regulator and supply can handle it
- Schematic: The full circuit for the audio board
- Bill of Materials: Every part on the board, where it comes from, and its datasheet
