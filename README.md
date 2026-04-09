# Passive Mono Summing Box

A passive stereo-to-mono summing box for analogue audio, designed for insertion
between a step-up transformer (SUT) and a phono stage input.

## Use Case

Denon DL-103 MC cartridge → Rothwell MCL SUT → **this box** → integrated amp phono input

Designed for a system where the amplifier has no mono switch. Allows clean
switching between stereo and mono playback on demand, with zero crosstalk in
stereo mode.

## Circuit

Passive resistor summing network (2x 10kΩ) switched by an MTS-202 DPDT ON-ON
toggle switch, wired as DPST ON-OFF. In stereo position the resistors are
completely disconnected. In mono position L+R are summed to a common node.
6dB level drop in mono mode — compensate with volume control.

## Files

| File | Description |
|------|-------------|
| `mono_sum_mts202_earth.svg` | Circuit schematic with earth post |
| `notes.txt` | Full wiring notes and component list |
| `README.md` | This file |

## Components

- 4x RCA panel mount sockets
- 2x 10kΩ resistors
- 1x MTS-202 DPDT ON-ON toggle switch (6 pins)
- 1x Earth/ground binding post
- 1x Aluminium enclosure (Hammond 1590B style, 112x60x31mm)

## Enclosure Layout

- **Connections face**: L IN, R IN, L OUT, R OUT (RCA), Earth post
- **Switch face**: MTS-202 toggle switch

See `notes.txt` for full wiring details and switch pin identification.
