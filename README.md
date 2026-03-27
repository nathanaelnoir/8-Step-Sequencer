[![KiCad 9](https://img.shields.io/badge/KiCad-9-blue)](https://kicad.org)
[![Schematic v1.0](https://img.shields.io/badge/Sch-v1.0-blueviolet)](KiCad/sequencer.kicad_sch)
[![PCB v1.0](https://img.shields.io/badge/PCB-v1.0-blue)](KiCad/sequencer.kicad_pcb)
[![PCBs: 1](https://img.shields.io/badge/PCBs-1-brightgreen)](KiCad/sequencer.kicad_pcb)
[![Format: Eurorack](https://img.shields.io/badge/Format-Eurorack-0093ff)](#)
[![License: TBD](https://img.shields.io/badge/License-TBD-lightgrey)](#license--contributing)
[![Instagram](https://img.shields.io/badge/Instagram-@moonsofmercury-E4405F?logo=instagram&logoColor=white)](https://www.instagram.com/moonsofmercury/)

# Modulo-8 Sequencer

Modulo-8 Sequencer is a compact 8-step Eurorack sequencer with internal/external clocking, reset, gate output, and CV output.

## Contents

- Overview
- Features
- Quick start (KiCad 9)
- Files
- Build & assembly notes
- Testing
- License & contributing

## Overview

This repository holds the KiCad 9 project for the Modulo-8 Sequencer. Designed by Dirty Dream / Nathanael Noir, the module is built around a CD4017BE step counter and TL074 analog stage, with eight step controls, eight step LEDs, internal clock generation, external clock/reset connectivity, and Eurorack-standard power.

The current project title block is `8 Step Sequencer`, while the panel artwork and module name are `Modulo-8 Sequencer`. Revision in the KiCad files is `v1.0`.

## Features

- 8-step sequencer architecture based on `CD4017BE` + `TL074`.
- Internal clock plus external `CLOCK IN`.
- Dedicated `RESET`, `CLOCK OUT`, `GATE OUT`, and `CV OUT` jack connections.
- Eight step LEDs (`STEP 1` through `STEP 8`) for visual position indication.
- Eight front-panel 100 k step potentiometers for per-step CV setting.
- Rotary switch connected across `Count0` to `Count7` for step-count / loop selection.
- Standard Eurorack power: `+12 V / -12 V / GND` via a 2x5 (10-pin) header.
- Mixed construction: SMD passives / diodes / transistors plus through-hole jacks, LEDs, switches, trimmers, rotary switch, and power header.

## Quick start

1. Install KiCad 9.
2. Open the project: `KiCad/sequencer.kicad_pro`.
3. Review the hierarchical sheets, then run ERC/DRC before exporting manufacturing files.

## Files

- `KiCad/sequencer.kicad_sch` - top-level schematic
- `KiCad/internal_clock.kicad_sch` - internal clock sheet
- `KiCad/switches_led.kicad_sch` - step switching / LED / CV selection sheet
- `KiCad/power.kicad_sch` - Eurorack power sheet
- `KiCad/sequencer.kicad_pcb` - PCB
- `KiCad/sequencer.kicad_pro` - KiCad project file
- `KiCad/sequencer.kicad_prl` - local KiCad project state

Note: there is a single PCB layout file (`KiCad/sequencer.kicad_pcb`) for this project.

## Build & assembly notes

- Observe pin-1 orientation for `U1` (`TL074`) and `U3` (`CD4017BE`).
- Confirm the 10-pin Eurorack power header orientation before first power-up.
- Front-panel hardware includes five 3.5 mm jacks: `CLOCK OUT`, `GATE OUT`, `CLOCK IN`, `CV OUT`, and `RESET`.
- The board uses eight 100 k step pots, eight step LEDs, multiple toggle switches, one rotary switch, and two trimmers (`RV1`, `RV2`) that should be calibrated after assembly.
- Ferrite beads and local rail decoupling are present on the power section; populate exactly as shown in the schematic/PCB.
- Assembly is a mixed SMD + THT workflow, not a pure through-hole build.

## Testing

1. With the module unpatched, power it from a current-limited Eurorack supply and verify `+12 V`, `-12 V`, and `GND` at the power header and test points.
2. Confirm the internal clock advances the step LEDs in order and produces pulses at `CLOCK OUT`.
3. Patch a known external clock into `CLOCK IN` and verify the sequencer advances reliably from the incoming clock.
4. Trigger `RESET` and verify the sequence returns to the first step / selected loop point.
5. Check that `GATE OUT` produces the expected rhythmic pattern and that `CV OUT` changes according to the eight step potentiometer settings.

## License & contributing

No `LICENSE` file is present in the repository yet, so usage terms are not formally declared at the moment.

If you want, I can add a license file and update this section later. Contributions, issues, and build notes are still useful in the meantime.
