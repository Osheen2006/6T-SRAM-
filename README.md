# 6T SRAM Cell Design and Analysis using Cadence Virtuoso
This project involves the design and simulation of a 6T SRAM cell using Cadence Virtuoso (GPDK180). It was designed at the schematic level, verified by transient and DC analyses, and evaluated for parameters such as power consumption. Finally, the physical layout was created and verified using DRC, LVS, and parasitic extraction.




## Project Overview

This project presents the design, simulation, physical layout, and parasitic analysis of a **6-Transistor Static Random Access Memory (6T SRAM) cell** using **Cadence Virtuoso** with **GPDK180 technology**.

The project covers the complete custom IC design flow from transistor-level schematic design to post-layout parasitic analysis.


## 6T SRAM Architecture

A 6T SRAM cell stores **one bit of data** using six MOS transistors:

- 2 PMOS pull-up transistors
- 2 NMOS pull-down transistors
- 2 NMOS access transistors

Two cross-coupled CMOS inverters form a bistable latch for data storage. The access transistors are controlled by the **Word Line (WL)** and connect the internal storage nodes to the complementary **Bit Lines (BL and BLB)**.

### Main Signals

| Signal | Description |
|--------|-------------|
| VDD | Supply Voltage |
| VSS | Ground |
| WL | Word Line |
| BL | Bit Line |
| BLB | Complementary Bit Line |
| Q | Storage Node |
| QB | Complementary Storage Node |


## Design Flow

The project follows the custom VLSI design flow:

```text
Schematic Design
      ↓
Symbol Generation
      ↓
Testbench Design
      ↓
Pre-Layout Simulation
      ↓
Layout Generation
      ↓
DRC Verification
      ↓
LVS Verification
      ↓
Parasitic Extraction

```



## Schematic Design

The transistor-level 6T SRAM schematic was designed using the **Cadence Virtuoso Schematic Editor**.

The design consists of two cross-coupled CMOS inverters and two access NMOS transistors. The schematic was checked for correct transistor connectivity and verified before simulation.
<img width="1731" height="841" alt="SCHEMATIC" src="https://github.com/user-attachments/assets/39d8f830-fb6d-4b9a-a73d-e724b0ff3bf7" />


### Transistor Dimensions

| Transistor Group | Width (W) | Length (L) |
|------------------|-----------|------------|
| Pull-Up PMOS | 1.0 µm | 0.18 µm |
| Pull-Down NMOS | 0.5 µm | 0.18 µm |
| Access NMOS | 0.75 µm | 0.18 µm |

---

## Symbol Generation and Testbench

A reusable symbol was generated from the SRAM schematic and instantiated in a separate testbench.

The testbench includes:

- 1.8 V DC supply
- Ground reference
- Word Line pulse source
- BL and BLB voltage sources
- SRAM storage nodes Q and QB for waveform observation

Simulations were performed using **Cadence ADE L and Spectre**.
<img width="1067" height="807" alt="tb" src="https://github.com/user-attachments/assets/7ae01b20-0bb4-4192-be5a-9d77d62b6e8d" />


---

## Write Operation

### Write Logic 1

For writing logic `1`:

```text
BL  = 1.8 V
BLB = 0 V
WL  = HIGH
```

The SRAM cell settles to:

```text
Q  = 1
QB = 0
```

The stored state is retained after WL is disabled.

### Write Logic 0

For writing logic `0`:

```text
BL  = 0 V
BLB = 1.8 V
WL  = HIGH
```

The SRAM cell settles to:

```text
Q  = 0
QB = 1
```

---

## Pre-Layout Analysis

The following analyses were performed before layout:

- Transient Analysis
- Write `0` verification
- Write `1` verification
- Hold operation verification
- DC Analysis
- DC Sweep
- Power Analysis
- Rise Time measurement 
- Fall Time measurement 
- Propagation Delay calculation

The Cadence Calculator was used to extract numerical performance parameters from the simulated waveforms.

---


Average power was obtained from the simulated power waveform.

---

## Layout Design

The physical layout of the 6T SRAM cell was created using **Cadence Virtuoso Layout XL**.

The layout was designed with emphasis on:

- Symmetrical transistor placement
- Compact cell structure
- Proper PMOS and NMOS placement
- Efficient local routing
- VDD and VSS power rails
- Correct BL, BLB, and WL routing
- Reduced interconnect length

Metal layers were used for signal and power routing, while appropriate contacts and vias were added between layout layers.

---

## Physical Verification

### Design Rule Check (DRC)

DRC was performed to verify that the layout satisfies the fabrication design rules of the GPDK180 technology.

The verification checks include:

- Minimum width
- Minimum spacing
- Layer enclosure
- Contact placement
- Via rules

### Layout Versus Schematic (LVS)

LVS verification was performed to compare the extracted layout netlist with the original SRAM schematic.

This ensures that the physical layout is electrically equivalent to the transistor-level schematic.
<img width="1742" height="754" alt="layout" src="https://github.com/user-attachments/assets/fcedb898-cbba-4ccd-a72e-de5b9394009d" />

---

## Parasitic Extraction and Analysis

Parasitic extraction was performed to identify the resistance and capacitance introduced by physical interconnections in the layout.

The extracted design includes:

- Parasitic resistance
- Parasitic capacitance


The static/extracted view was inspected to verify the extracted parasitic network.

Post-layout analysis was used to study the impact of parasitic effects on SRAM performance.
<img width="785" height="782" alt="parasitic_analysis" src="https://github.com/user-attachments/assets/e9439645-5c2f-4a12-8c87-80bc5ef0a3f5" />

---

## Tools and Technology

- **Cadence Virtuoso**
- **Cadence ADE L**
- **Spectre Simulator**
- **Virtuoso Layout XL**
- **GPDK180 CMOS Technology**
- **DRC and LVS Verification Tools**
- **Parasitic Extraction Tools**

---

## Key Outcomes

- Successfully designed a transistor-level 6T SRAM cell.
- Verified logic `0` and logic `1` write operations.
- Demonstrated SRAM data retention.
- Performed DC and transient simulations.
- Evaluated power and timing characteristics.
- Generated the physical layout of the SRAM cell.
- Performed DRC and LVS verification.
- Extracted and analyzed layout parasitic effects.
- Studied the complete schematic-to-layout custom IC design flow.

---

## Conclusion

The project demonstrates the complete design and verification flow of a **6T SRAM cell using Cadence Virtuoso**. The SRAM cell was verified at the schematic level, analyzed for functional and performance parameters, physically implemented through layout, and evaluated considering parasitic effects.

The project provides practical experience in **CMOS memory design, custom VLSI design flow, circuit simulation, physical verification, and post-layout analysis**.

---

## Author

**Osheen Mahajan**

Engineering Project – 6T SRAM Design and Analysis
````
