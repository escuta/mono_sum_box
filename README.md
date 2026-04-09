# Passive Mono Summing Box

A passive stereo-to-mono summing box for analogue audio, designed for insertion between a step-up transformer (SUT) and a phono stage input.

## Use Case

Denon DL-103 MC cartridge → Rothwell MCL SUT → **this box** → integrated amp phono input

Designed for a system where the amplifier has no mono switch. Allows clean switching between stereo and mono playback on demand, with zero crosstalk in stereo mode.

## Signal Chain

```
Turntable (DL-103) → Rothwell MCL SUT → [this box] → Integrated amp phono input
```

## Earth/Ground Chain

```
Turntable earth wire → Earth post on box → wire to SUT ground terminal
```

The aluminium enclosure is part of the ground — all RCA shields, the earth post and the summing node share a common ground bus inside the box.

## Circuit Description

A passive resistor summing network switched in and out of circuit by a DPDT toggle switch (MTS-202, ON-ON, 6 pins, wired as DPST ON-OFF).

- **Stereo position (switch pos 1):** both poles connect to unused throws (N/C). Resistors are completely out of circuit. Clean stereo passthrough, zero crosstalk.
- **Mono position (switch pos 2):** both poles connect to the active throws, routing the left and right hot lines through 10kΩ resistors to a common summing node connected to ground. Both output channels carry the identical L+R summed mono signal. A 6dB level drop occurs — compensate with volume control.

## Components

| Component | Value/Type | Qty |
|-----------|-----------|-----|
| RCA panel mount sockets | — | 4 |
| Resistors | 10kΩ | 2 |
| Toggle switch | MTS-202 DPDT ON-ON, 6 pins | 1 |
| Earth/ground binding post | — | 1 |
| Aluminium enclosure | Hammond 1590B style, 112×60×31mm | 1 |

## Enclosure Layout

- **Connections face**: L IN, R IN, L OUT, R OUT (RCA), Earth post
- **Switch face**: MTS-202 toggle switch (opposite face)

## Switch Wiring — MTS-202 Pin Identification

The MTS-202 has 6 pins arranged in two rows of 3:

```
[T1b]  [COM1]  [T1a]   <- Pole 1 (Left channel)
[T2b]  [COM2]  [T2a]   <- Pole 2 (Right channel)
```

Centre pins (COM1, COM2) are the commons. Outer pins are throws — one side active in pos 1, other side active in pos 2. Use a multimeter in continuity mode to identify which throw is active in which position before soldering.

**Connect:**
- Signal tap from L hot line → COM1
- Signal tap from R hot line → COM2
- COM1 active throw (mono position) → R1 → summing node
- COM2 active throw (mono position) → R2 → summing node
- Summing node → ground bus
- Leave the two stereo-position throws completely unconnected (N/C)

## Files

| File | Description |
|------|-------------|
| `mono_sum_mts202_earth.svg` | Circuit schematic with earth post |
| `README.md` | This file |

## Context

This box was designed as part of a mono vinyl playback project. The owner's nephew uses a Denon DL-103 with a Rothwell MCL SUT into an integrated amplifier with no mono switch. The box provides a clean, passive mono sum with zero crosstalk in stereo mode, switchable on demand.

Related project: a 3-position speaker selector box for the owner's own system (Quad 34 preamp / dual Quad 303 power amps / Tannoy System 12 DMT II speakers).
