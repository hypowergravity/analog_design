# Analog and Digital Circuit Building Blocks (Topologies)

## What Are They Called?

Depending on the design domain, the same concept may be referred to by different names:

| Term | Typical Usage | Examples |
|--------|---------|----------|
| Circuit Topology | Analog/RF Design | Differential pair, folded cascode |
| Building Block | General Electronics | Op-amp, current mirror |
| Circuit Cell | IC Design | DFF cell, NAND cell |
| Analog Macrocell | Analog IC Design | OTA, PLL, bandgap reference |
| Standard Cell | Digital ASIC Design | NAND2, NOR2, INV, DFF |
| Primitive | FPGA Design | LUT, Flip-Flop, Buffer |
| Reference Design | Application-Level Circuits | ADC front-end, sensor interface |
| IP Block | SoC/System Design | UART, SPI, CPU, DMA |
| Circuit Template | Education and Research | Common-source amplifier |

### Industry Terminology

**Analog Designers**
- "Current mirror topology"
- "Folded cascode topology"
- "Differential amplifier topology"

**Digital Designers**
- "Standard-cell library"
- "Cell library"
- "Logic primitives"

So while "topology" is correct, digital designers more often refer to reusable blocks as **cells** or **standard cells**.

---

# Common Analog Building Blocks

| Building Block | Function |
|---------------|----------|
| Common Source Amplifier | Voltage gain |
| Common Gate Amplifier | Wide bandwidth |
| Source Follower | Buffer |
| Differential Pair | Differential amplification |
| Current Mirror | Current replication |
| Wilson Current Mirror | Improved current accuracy |
| Cascode Amplifier | High gain |
| Folded Cascode | High gain with low voltage operation |
| Comparator | Analog-to-digital boundary |
| Operational Amplifier (OTA/Op-Amp) | General-purpose analog processing |
| Bandgap Reference | Stable voltage reference |
| Oscillator | Signal generation |

### Example Hierarchy

```text
MOSFET
   ↓
Current Mirror
   ↓
Differential Pair
   ↓
Gain Stage
   ↓
Operational Amplifier
   ↓
Analog System
```

---

# Common Digital Building Blocks

## Combinational Logic

| Block | Function |
|---------|---------|
| Inverter (INV) | NOT operation |
| NAND Gate | Universal logic gate |
| NOR Gate | Universal logic gate |
| XOR Gate | Comparison/parity |
| Multiplexer (MUX) | Input selection |
| Decoder | Binary-to-one-hot conversion |
| Encoder | One-hot-to-binary conversion |
| Full Adder | Arithmetic |

## Sequential Logic

| Block | Function |
|---------|---------|
| SR Latch | Basic memory element |
| D Latch | Transparent storage |
| D Flip-Flop | Clocked storage |
| JK Flip-Flop | Universal sequential element |
| Register | Multi-bit storage |
| Counter | Sequence generation |

### Example Hierarchy

```text
CMOS Transistor
      ↓
Inverter
      ↓
Logic Gate
      ↓
Flip-Flop
      ↓
Register
      ↓
ALU
      ↓
CPU
```

---

# Open-Source Downloadable Libraries

## 1. SkyWater SKY130 PDK

Probably the most important open-source IC design library available today.

### Repository
https://github.com/google/skywater-pdk

### Standard Cell Library
https://github.com/google/skywater-pdk-libs-sky130_fd_sc_hd

### Contents

```text
Inverters
Buffers
NAND Gates
NOR Gates
XOR Gates
Multiplexers
Latches
Flip-Flops
Clock Cells
```

Example cell names:

```text
sky130_fd_sc_hd__inv_1
sky130_fd_sc_hd__nand2_1
sky130_fd_sc_hd__nor2_1
sky130_fd_sc_hd__dfxtp_1
```

Includes:

- SPICE netlists
- Layouts
- Timing views
- Liberty files
- LEF/DEF views

---

## 2. OpenPDKs

### Repository

https://github.com/RTimothyEdwards/open_pdks

### Contents

```text
Process Design Kits
Device Models
Layout Libraries
Basic Cells
Simulation Support
```

Useful for:

- Custom IC design
- Analog layout experiments
- Process exploration

---

## 3. Xschem

Excellent open-source schematic library environment.

### Repository

https://github.com/StefanSchippers/xschem

### Analog Topologies Included

```text
Current Mirrors
Differential Pairs
Cascodes
Bandgaps
Comparators
Charge Pumps
PLLs
Operational Amplifiers
```

### Features

- Ready-to-simulate schematics
- ngspice integration
- Hierarchical design

This is one of the closest things to an open-source **analog topology library**.

---

## 4. ngspice Example Collection

### Repository

https://sourceforge.net/projects/ngspice/

### Example Circuits

```text
CMOS Inverter
Current Mirror
Differential Amplifier
Operational Amplifier
Oscillator
Active Filters
```

Useful for learning circuit behavior and simulation.

---

## 5. IHP Open PDK

### Repository

https://github.com/IHP-GmbH/IHP-Open-PDK

### Includes

```text
BiCMOS Devices
RF Building Blocks
Current Mirrors
Differential Amplifiers
Bandgap References
Mixed-Signal Cells
```

Suitable for RF and mixed-signal studies.

---

## 6. OpenROAD Libraries

### Repository

https://github.com/The-OpenROAD-Project/OpenROAD-flow-scripts

### Contents

```text
Standard Cell Libraries
Clock Cells
Flip-Flops
Buffers
Logic Gates
```

Useful for:

- ASIC design flow
- Physical implementation
- Timing closure experiments

---

## 7. OpenCores

### Repository

https://opencores.org/

### IP Blocks Available

```text
UART
SPI
I2C
Ethernet MAC
CPUs
DSP Cores
Memory Controllers
FIFOs
```

These are not transistor-level topologies but reusable digital IP blocks.

---

# Research and Academic Analog Libraries

## Berkeley Analog Generator (BAG)

### Repository

https://github.com/BerkeleyAnalog

### Reusable Blocks

```text
Current Mirrors
Comparators
OTAs
Bandgaps
ADCs
DACs
```

Targeted at analog IC research and generator-based design.

---

## ALIGN Analog Layout

### Repository

https://github.com/ALIGN-analoglayout/ALIGN-public

### Topologies Included

```text
Differential Pair
Current Mirror
Cascode
Operational Amplifier
Comparator
```

Provides automated layout generation from schematic-level topologies.

---

# Example Personal Topology Library Structure

Many professional analog designers maintain a private library organized as follows:

```text
Analog_Library/
│
├── Amplifiers/
│   ├── Common_Source
│   ├── Common_Gate
│   ├── Source_Follower
│   ├── Differential_Pair
│   ├── Folded_Cascode
│   └── Two_Stage_OTA
│
├── Biasing/
│   ├── Current_Mirror
│   ├── Wilson_Mirror
│   ├── Cascode_Mirror
│   └── Bandgap
│
├── Comparators/
│   ├── Dynamic
│   ├── Static
│   └── StrongARM
│
├── Data_Converters/
│   ├── Sample_Hold
│   ├── SAR_Block
│   └── Flash_Comparator
│
└── Filters/
    ├── Active_RC
    ├── GmC
    └── Switched_Capacitor
```

And a digital library:

```text
Digital_Library/
│
├── Inverters/
├── NAND/
├── NOR/
├── XOR/
├── Transmission_Gates/
├── Multiplexers/
├── Latches/
├── FlipFlops/
├── Registers/
├── Counters/
└── Arithmetic/
    ├── Half_Adder
    ├── Full_Adder
    ├── ALU
    └── Multiplier
```

---

# Recommended Starting Set

If you want a compact but highly useful library, start with:

## Analog (12 Schematics)

1. Common Source
2. Common Gate
3. Source Follower
4. Differential Pair
5. Active-Load Differential Pair
6. Current Mirror
7. Wilson Current Mirror
8. Cascode
9. Folded Cascode
10. Two-Stage Op-Amp
11. Comparator
12. Bandgap Reference

## Digital (12 Schematics)

1. CMOS Inverter
2. NAND
3. NOR
4. XOR
5. Transmission Gate
6. 2:1 Multiplexer
7. SR Latch
8. D Latch
9. D Flip-Flop
10. Register
11. Counter
12. Full Adder

Together, these 24 blocks represent the fundamental library from which most analog, mixed-signal, FPGA, and ASIC systems are ultimately built.
