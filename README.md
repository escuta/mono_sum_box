# Passive Mono Summing Box

A passive stereo-to-mono summing box for analogue audio, designed for insertion between a phono source and a phono stage input.

## Use Case

For systems where the amplifier or preamplifier has no mono switch. Allows clean switching between stereo and mono playback on demand, with zero crosstalk in stereo mode. Suitable for insertion at line level after a step-up transformer, or directly between any line-level source and input.

## Signal Chain

```
Phono source → [this box] → Phono stage / amplifier input
```

## Earth/Ground Chain

```
Turntable earth wire → Earth post on box → wire to phono stage ground terminal
```

The earth post is optional — the turntable earth wire can bypass the box entirely and connect directly to the phono stage or SUT ground terminal if preferred. The aluminium enclosure is part of the ground — all RCA shields, the earth post and R3 summing node share a common ground bus inside the box.

## Circuit Description

A passive resistor summing network switched in and out of circuit by a 4PDT toggle switch (MTS-402, ON-ON, 12 pins). Uses a verified circuit topology ensuring the summing network is completely disconnected in stereo mode — no loading of the stereo signal whatsoever.

- **Stereo position (switch up):** L input passes directly to L output, R input passes directly to R output. Summing network completely disconnected. Zero crosstalk.
- **Mono position (switch down):** L input passes through R1 and R input through R2 to a common summing node. R3 connects the summing node to ground for correct impedance. Both L and R outputs receive the identical summed mono signal.

## Components

| Component | Value/Type | Qty |
|-----------|-----------|-----|
| RCA panel mount sockets | — | 4 |
| Resistor R1 | 10kΩ 1% | 1 |
| Resistor R2 | 10kΩ 1% | 1 |
| Resistor R3 | 20kΩ | 1 |
| Toggle switch | MTS-402 4PDT ON-ON, 12 pins | 1 |
| Earth/ground binding post | — | 1 |
| Aluminium enclosure | 100×56×56mm | 1 |

Note: R1 and R2 should be 1% tolerance for good left/right channel matching.

## Enclosure Layout

**Enclosure:** 100×56×56mm diecast aluminium. All connections on one 56×56mm face (rear). Switch on opposite 56×56mm face (front).

### Rear panel — 56×56mm

Four RCA sockets at corners, earth post at dead centre:

| Component | X from left | Y from top |
|-----------|-------------|------------|
| L OUT (top left) | 13mm | 13mm |
| R OUT (top right) | 43mm | 13mm |
| Earth post (centre) | 28mm | 28mm |
| L IN (bottom left) | 13mm | 43mm |
| R IN (bottom right) | 43mm | 43mm |

- RCA holes: **8–9mm diameter**
- Earth post hole: **6mm diameter**
- Pilot drill at 3mm first, centre punch each position before drilling

### Front panel — 56×56mm

Single hole at dead centre (intersection of panel diagonals):

- Switch hole: **6–7mm diameter** (MTS-402 shaft)
- Draw diagonals corner to corner, punch at intersection

## Switch Wiring — MTS-402 Pin Layout

The MTS-402 has 12 pins in three rows of four. The tab on the mounting washer faces upward. With tab up:

```
T1b  T2b  T3b  T4b   <- top row    (mono, switch down)
C1   C2   C3   C4    <- centre row (commons)
T1a  T2a  T3a  T4a   <- bottom row (stereo, switch up)
```

**Connect:**
- C1 → L input hot
- C2 → R input hot
- C3 → L output hot
- C4 → R output hot
- T1a → L output hot (stereo: L in → L out)
- T2a → R output hot (stereo: R in → R out)
- T3a → L input hot (stereo: L out tied back to L in)
- T4a → R input hot (stereo: R out tied back to R in)
- T1b → R1 (10kΩ) → summing node (mono: L in through resistor)
- T2b → R2 (10kΩ) → summing node (mono: R in through resistor)
- T3b → summing node (mono: L out receives summed signal)
- T4b → summing node (mono: R out receives summed signal)
- Summing node → R3 (20kΩ) → ground bus

**Ground bus:**
Run a single wire along the inside of the enclosure daisy-chaining all four RCA socket shields. Also connect to this bus: earth post, and the free leg of R3. This forms the common ground for the entire circuit.

## Files

| File | Description |
|------|-------------|
| `mono_sum_mts402.svg` | Circuit schematic |
| `README.md` | This file |

## Reference

Circuit topology based on verified passive stereo/mono summing designs. The 4PDT switch ensures complete isolation of the summing network in stereo mode, avoiding any loading of the stereo signal from the resistor network.
