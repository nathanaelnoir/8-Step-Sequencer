[![KiCad 9](https://img.shields.io/badge/KiCad-9-blue)](https://kicad.org)
[![Schematic v1.0](https://img.shields.io/badge/Sch-v1.0-blueviolet)](KiCad/sequencer.kicad_sch)
[![PCB v1.0](https://img.shields.io/badge/PCB-v1.0-blue)](KiCad/sequencer.kicad_pcb)
[![PCBs: 1](https://img.shields.io/badge/PCBs-1-brightgreen)](KiCad/sequencer.kicad_pcb)
[![Format: Eurorack](https://img.shields.io/badge/Format-Eurorack-0093ff)](#)
[![License: TBD](https://img.shields.io/badge/License-TBD-lightgrey)](#license--contributing)
[![Instagram](https://img.shields.io/badge/Instagram-@moonsofmercury-E4405F?logo=instagram&logoColor=white)](https://www.instagram.com/moonsofmercury/)

# Modulo-8 Sequencer

Modulo-8 Sequencer is an 8-step Eurorack sequencer with an onboard clock, external clock/reset inputs, and separate clock, gate, and CV outputs.

## Contents

- Overview
- Features
- Quick start (KiCad 9)
- Files
- Build & assembly notes
- Testing
- License & contributing

## Overview

This repository contains the KiCad 9 design files for Modulo-8 Sequencer, a straightforward 8-step CV/gate sequencer for Eurorack. Eight pots set the step voltages, the LEDs show the current position, and the module can run from its own clock or from an external pulse. `CLOCK OUT`, `GATE OUT`, `CV OUT`, and `RESET` are all available on the front panel.

The KiCad title block still says `8 Step Sequencer`, but the panel artwork and module name are `Modulo-8 Sequencer`. Current revision in the project files is `v1.0`.

## Features

- 8-step sequencer built around `CD4017BE` and `TL074`.
- Internal clock plus external `CLOCK IN`.
- Separate `CLOCK OUT`, `GATE OUT`, `CV OUT`, and `RESET` jacks.
- Eight 100 k step pots for setting the sequence voltage.
- Eight step LEDs for visual feedback.
- Rotary switch wired across `Count0` to `Count7` for loop-length / step-count selection.
- Standard Eurorack power: `+12 V / -12 V / GND` on a 10-pin header.
- Mixed build: SMD passives, diodes, and transistors, with through-hole panel hardware.

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

- Check pin-1 orientation on `U1` (`TL074`) and `U3` (`CD4017BE`) before soldering.
- Double-check the Eurorack power header orientation before applying power. Getting that wrong is an easy way to ruin the build.
- Panel hardware is not minimal: five 3.5 mm jacks, eight step pots, eight LEDs, several toggle switches, one rotary switch, and two trimmers (`RV1`, `RV2`).
- The power section includes ferrite beads and local decoupling on the rails. Populate it exactly as shown.
- This is a mixed SMD + THT build, so it makes sense to solder the low-profile SMD parts first and leave the panel hardware for last.

## Testing

1. Power the module from a current-limited Eurorack supply and verify `+12 V`, `-12 V`, and `GND` at the header and test points before patching anything.
2. Let the internal clock run and check that the step LEDs advance in order and that `CLOCK OUT` is pulsing.
3. Feed a known clock into `CLOCK IN` and confirm the sequence advances cleanly from the external source.
4. Trigger `RESET` and make sure the sequencer returns to step 1 or to the selected loop point.
5. Watch `GATE OUT` and `CV OUT` on a scope or with downstream modules and confirm that the outputs follow the programmed steps.

## License & contributing

No `LICENSE` file has been added to this repository yet. Until that changes, assume the design is shared for reference, not under an explicit open-source license.

If a license is added later, this section can be updated properly.
