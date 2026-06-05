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

The earth post is optional — the turntable earth wire can bypass the box entirely and connect directly to the phono stage or SUT ground terminal if preferred. The aluminium enclosure is part of the ground — all RCA shields and the earth post share a common ground bus inside the box.

## Circuit Description

A passive resistor summing network switched in and out of circuit by a 4PDT toggle switch (MTS-402, ON-ON, 12 pins). Uses a verified circuit topology ensuring the summing network is completely disconnected in stereo mode — no loading of the stereo signal whatsoever.

- **Stereo position (switch up):** L input passes directly to L output, R input passes directly to R output. Summing network completely disconnected. Zero crosstalk.
- **Mono position (switch down):** L input passes through R1 and R input through R2 to a common summing node. R3 connects the summing node to ground for correct output impedance. Both L and R outputs receive the identical summed mono signal.

### What is the summing node?

The summing node is not a component — it is a physical junction point in the wiring where several wires are soldered together. It carries the combined L+R audio signal and is at audio signal potential, not at ground.

At the summing node the following wires meet:
- Free leg of R1 — carries the L channel signal (after passing through the 10kΩ resistor from T1b)
- Free leg of R2 — carries the R channel signal (after passing through the 10kΩ resistor from T2b)
- One leg of R3 — the other leg of R3 goes to the ground bus, setting the output impedance
- Wire to T3b — the summed signal travels from the node through T3b to C3, which is the L output hot pin
- Wire to T4b — the summed signal travels from the node through T4b to C4, which is the R output hot pin

The L and R signals combine at this junction. R3 to ground does not pull the node to ground level — it simply provides an impedance reference. The node itself sits at the combined L+R signal voltage.

In practice the summing node is simply a short length of wire with all the above connections soldered to it, or a small tag strip used as a convenient junction point.

## Components

| Component | Value/Type | Qty |
|-----------|-----------|-----|
| RCA panel mount sockets | — | 4 |
| Resistor R1 | 10kΩ 1% | 1 |
| Resistor R2 | 10kΩ 1% | 1 |
| Resistor R3 | 33kΩ | 1 |
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

*Commons — always connected to their respective signal points:*
- C1 → L input hot
- C2 → R input hot
- C3 → L output hot
- C4 → R output hot

*Bottom throws T-a — active in stereo (switch up):*
- T1a → L output hot (L input signal passes straight through to L output)
- T2a → R output hot (R input signal passes straight through to R output)
- T3a → L input hot (L output tied back to L input, completing the direct path)
- T4a → R input hot (R output tied back to R input, completing the direct path)

*Top throws T-b — active in mono (switch down):*
- T1b → R1 (10kΩ) → summing node (L input signal enters summing network)
- T2b → R2 (10kΩ) → summing node (R input signal enters summing network)
- T3b → summing node (summed signal travels from node → T3b → C3 → L output hot)
- T4b → summing node (summed signal travels from node → T4b → C4 → R output hot)
- Summing node → R3 (33kΩ) → ground bus (sets output impedance)

**Ground bus:**
Run a single wire along the inside of the rear panel daisy-chaining all four RCA socket shields. Also connect to this bus: earth post, and the free leg of R3. Note that R3 connects the summing node to ground but the summing node itself is not part of the ground bus — it carries the audio signal.

## Wiring Procedure

### Before you start
- Mount all four RCA sockets, earth post and MTS-402 switch in the enclosure before any wiring
- Have this README open for reference
- Use a multimeter in continuity mode to verify switch pin positions before soldering
- With tab facing up: bottom row = stereo (switch up), top row = mono (switch down)
- Tin all component pins and wire ends before soldering

### Wire lengths
The switch is on the front panel and the RCA sockets are on the rear panel, 100mm apart. Every connection between the switch and the RCA sockets requires a wire running the full length of the enclosure.

Cut the following wires at **120mm** to allow comfortable slack:
- C1 to L IN hot
- C2 to R IN hot
- C3 to L OUT hot
- C4 to R OUT hot
- T1a to L OUT hot
- T2a to R OUT hot
- T3a to L IN hot
- T4a to R IN hot
- T3b to summing node
- T4b to summing node

Route all long wires neatly along one side of the enclosure interior before soldering the far ends. The resistors and summing node can be located anywhere convenient along this run — midway or near the switch end both work well.

### Step 1 — Ground bus
Run a single wire along the inside of the rear panel, soldering it to the shield/sleeve pin of each RCA socket in turn:

```
L OUT shield → R OUT shield → L IN shield → R IN shield
```

Also solder to this wire:
- Earth post (inside lug)
- One leg of R3 (33kΩ) — leave the other leg free for now

Verify continuity between all four RCA shields and the earth post before proceeding.

### Step 2 — Connect commons to RCA hot pins
These four wires run 120mm from the switch to the RCA sockets. Solder the switch end first, route along the enclosure interior, then solder the RCA end.

- C1 → L IN hot
- C2 → R IN hot
- C3 → L OUT hot
- C4 → R OUT hot

### Step 3 — Stereo direct path (T-a throws, bottom row)
These four wires (120mm each) complete the direct stereo passthrough when the switch is up.

- T1a → L OUT hot (join at L OUT RCA hot pin, alongside C3 wire)
- T2a → R OUT hot (join at R OUT RCA hot pin, alongside C4 wire)
- T3a → L IN hot (join at L IN RCA hot pin, alongside C1 wire)
- T4a → R IN hot (join at R IN RCA hot pin, alongside C2 wire)

**Test before continuing:**
- Switch UP: continuity L IN hot → L OUT hot ✓
- Switch UP: continuity R IN hot → R OUT hot ✓
- Switch UP: no continuity L IN hot → R IN hot ✓

### Step 4 — Build the summing network
The resistors and summing node can be located anywhere along the inside of the enclosure — midway along the length works well.

1. Solder one leg of R1 (10kΩ) to T1b on the switch
2. Solder one leg of R2 (10kΩ) to T2b on the switch
3. Run R1 and R2 along the enclosure to your chosen summing node location
4. Twist the free legs of R1 and R2 together with the free leg of R3 (33kΩ) and solder — this junction is the **summing node**
5. Connect the other leg of R3 to the ground bus

### Step 5 — Connect summing node to outputs
Run two wires (120mm) from the summing node back to the switch:

- Summing node → T3b
- Summing node → T4b

When the switch is down (mono), the signal path is:
```
Summing node → T3b → C3 → L OUT hot
Summing node → T4b → C4 → R OUT hot
```

### Step 6 — Final checks
**Switch UP (stereo):**
- [ ] Continuity: L IN hot → L OUT hot
- [ ] Continuity: R IN hot → R OUT hot
- [ ] No continuity: L IN hot → R IN hot
- [ ] No continuity: L OUT hot → R OUT hot
- [ ] No continuity: any hot pin → any shield pin

**Switch DOWN (mono):**
- [ ] Continuity: L IN hot → L OUT hot (reads ~10kΩ resistance — correct)
- [ ] Continuity: R IN hot → R OUT hot (reads ~10kΩ resistance — correct)
- [ ] Continuity: L OUT hot → R OUT hot (both connected via summing node)
- [ ] No continuity: any hot pin → any shield pin (direct short)

Note: in mono position the multimeter reads resistance, not zero ohms — this is correct as the signal passes through resistors.

### Step 7 — Close up and label
Label the rear panel:
- Top left: L OUT
- Top right: R OUT
- Centre: ⏚
- Bottom left: L IN
- Bottom right: R IN

Front panel: STEREO (switch up) / MONO (switch down)

## Files

| File | Description |
|------|-------------|
| `mono_sum_mts402.svg` | Circuit schematic |
| `README.md` | This file |

## Reference

Circuit topology based on verified passive stereo/mono summing designs. The 4PDT switch ensures complete isolation of the summing network in stereo mode, avoiding any loading of the stereo signal from the resistor network.
