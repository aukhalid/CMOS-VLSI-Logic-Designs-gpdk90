# CMOS VLSI Logic Designs using gpdk90

<p align="center">
  <img src="https://img.shields.io/badge/Cadence%20Virtuoso-yellow?style=for-the-badge&logo=cadence&logoColor=black" alt="Cadence Virtuoso Badge">
  <img src="https://img.shields.io/badge/PDK-gpdk90-blue?style=for-the-badge&logoColor=white" alt="PDK Badge">
</p>

This project presents the design and implementation of fundamental digital logic gates, a complete set of CMOS standard cells, and digital system designs using **Cadence Virtuoso** with the **gpdk90** open-source PDK. Each cell and system has been designed from a transistor-level perspective, following a comprehensive VLSI design flow.

<p align="center">
  <img src="https://user-images.githubusercontent.com/12101375/133129188-51f7d5c7-1d12-4f3b-8d1e-2d2c12574e4c.png" alt="VLSI Design Flow Diagram">
</p>

---

## 👨‍💻 Presented By

- **Name:** Ahasan Ullah Khalid
- **Institution:** Chittagong University of Engineering and Technology (CUET)
- **Department:** Electronics & Telecommunication Engineering (ETE)
- **GitHub:** [github.com/aukhalid](https://github.com/aukhalid)
- **Website:** [aukhalid.vercel.app](https://aukhalid.vercel.app)

---

## 📝 Table of Contents

- [Project Overview](#project-overview)
- [VLSI Design Flow](#vlsi-design-flow)
- [Tools and Technology](#tools-and-technology)
- [Project Structure](#project-structure)
- [Standard Cells](#standard-cells)
    - [CMOS Inverter (NOT Gate)](#cmos-inverter-not-gate)
    - [NAND2X1 (2-Input NAND Gate)](#nand2x1-2-input-nand-gate)
    - [AND2X1 (2-Input AND Gate)](#and2x1-2-input-and-gate)
    - [NOR2X1 (2-Input NOR Gate)](#nor2x1-2-input-nor-gate)
    - [OR2X1 (2-Input OR Gate)](#or2x1-2-input-or-gate)
    - [M1_NWELL](#m1_nwell)
    - [M1_PSUB](#m1_psub)
- [Digital Blocks and Systems](#digital-blocks-and-systems)
    - [Half Adder (with NAND Gates)](#half-adder-with-nand-gates)
    - [Full Adder](#full-adder)
    - [1x2 De-multiplexer](#1-x-2-de-multiplexer)
    - [1x8 De-Multiplexer](#1-x-8-de-multiplexer)

---

## Project Overview

This repository showcases the complete **VLSI design flow** for various digital circuits, starting from fundamental gates to more complex systems. The project meticulously follows these steps for each component:

- **Transistor-level schematic design:** Creating the logical representation of the circuit.
- **DRC-clean layout implementation:** Designing the physical layout of the circuit on silicon, ensuring it meets manufacturing rules.
- **Symbol creation for hierarchical use:** Generating a simplified graphical symbol for easy integration into larger designs.
- **Circuit simulation in ADE L:** Running pre-layout and post-layout simulations to verify functionality.
- **Verification against theoretical truth tables:** Confirming that the circuit's behavior matches its intended logical function.

---

## Tools and Technology

- **Cadence Virtuoso:** The primary EDA tool used for schematic capture, layout design, and simulation.
- **gpdk90 Open-Source PDK:** The process design kit (PDK) providing the technology-specific design rules and device models.
- **CMOS VLSI Design Principles:** The theoretical foundation for all circuit implementations.

---

## Project Structure

The project is divided into two major sections:

### Standard Cells

This section includes the foundational building blocks of digital logic.

- Inverter (NOT Gate)
- 2-input NAND Gate (NAND2X1)
- 2-input AND Gate (AND2X1)
- 2-input NOR Gate (NOR2X1)
- 2-input OR Gate (OR2X1)
- M1_NWELL (PMOS well connection)
- M1_PSUB (NMOS substrate connection)

### Digital Blocks and Systems

This section demonstrates the use of standard cells to create more complex digital systems using a hierarchical design approach.

- Half Adder (HA)
- Full Adder (FA)
- 1 x 2 De-Multiplexer
- 1 x 8 De-Multiplexer

---

## Standard Cells

Each standard cell entry is presented with the following format:

- **Objective:** The goal of the design.
- **Description:** A brief overview of the circuit's function and implementation.
- **Design Steps:** A step-by-step guide to the design process.
- **Schematic Diagram:** The transistor-level schematic.
- **Layout:** The physical representation of the circuit.
- **Symbol:** The hierarchical symbol.
- **Simulation & Verification:** The simulation results and a truth table.

### CMOS Inverter (NOT Gate)

**Objective:** To create the simplest form of a logic gate that outputs the complement of the input signal.

**Description:** The CMOS inverter is composed of a PMOS and an NMOS transistor. The PMOS transistor pulls the output up to VDD when the input is low, and the NMOS transistor pulls the output down to GND when the input is high.

| A | Y |
|---|---|
| 0 | 1 |
| 1 | 0 |

**Design Steps:**
- **Schematic Design:** Place a PMOS (source to VDD) and an NMOS (source to GND). Connect their drains to the output `Y` and their gates to the input `A`.
- **Layout Design:** Draw diffusion layers for PMOS (in N-well) and NMOS (on P-substrate). Route metal layers for VDD, GND, input `A`, and output `Y`.
- **Symbol Creation:** Generate a standard inverter symbol with input `A` and output `Y`.
- **Simulation:** Run a transient analysis with a pulsed input and verify the inverted output waveform.

**Schematic Diagram:**


**Layout:**


**Symbol:**


**Simulation & Verification:**

The simulation confirmed that when the input `A` is low, the output `Y` is high, and vice versa.

---

### NAND2X1 (2-Input NAND Gate)

**Objective:** To design, lay out, and verify a 2-input CMOS NAND gate.

**Description:** A 2-input CMOS NAND gate outputs logic '0' only when both inputs are '1'. It uses two parallel PMOS transistors in the pull-up network (PUN) and two series NMOS transistors in the pull-down network (PDN).

**Truth Table:**

| A | B | Y |
|---|---|---|
| 0 | 0 | 1 |
| 0 | 1 | 1 |
| 1 | 0 | 1 |
| 1 | 1 | 0 |

**Design Steps:**
- **Schematic (Transistor-Level):** Instantiate two PMOS in parallel between VDD and `Y`. Instantiate two NMOS in series between `Y` and GND.
- **Layout:** Arrange the transistors, route connections, and add well/substrate taps. Ensure DRC compliance.
- **LVS & Extraction:** Run LVS to verify the layout matches the schematic.
- **Symbol:** Create a symbol with inputs `A`, `B`, and output `Y`.

**Schematic Diagram:**


**Layout:**


**Symbol:**


**Simulation & Verification:**

Transient analysis confirmed that the output `Y` is low only when both inputs `A` and `B` are high.

---

### AND2X1 (2-Input AND Gate)

**Objective:** To design and verify a 2-input AND gate using a hierarchical approach by cascading a NAND gate and an Inverter.

**Description:** The Boolean expression for an AND gate is $Y=A \cdot B$. This can be efficiently implemented in CMOS by using a NAND gate ($A \cdot B$) followed by an inverter ($A \cdot B$).

**Truth Table:**

| A | B | Y |
|---|---|---|
| 0 | 0 | 0 |
| 0 | 1 | 0 |
| 1 | 0 | 0 |
| 1 | 1 | 1 |

**Design Steps:**
- **Hierarchical Schematic:** Instantiate the `NAND2X1` and `Inverter` standard cells.
- **Schematic Capture:** Connect the inputs `A` and `B` to the `NAND2X1`. Connect the output of the `NAND2X1` to the input of the `Inverter`. The `Inverter`'s output is the final output `Y`.
- **Layout:** Place the `NAND2X1` and `Inverter` layouts and route the interconnections.
- **Simulation:** Run a transient analysis to verify the output `Y` is high only when both inputs `A` and `B` are high.

**Schematic Diagram:**


**Layout:**


**Symbol:**


**Simulation & Verification:**

The simulation confirmed that the circuit performs the AND function correctly.

---

### NOR2X1 (2-Input NOR Gate)

**Objective:** To design and verify a 2-input NOR gate from a transistor-level perspective.

**Description:** A NOR gate outputs a low signal if any of its inputs are high. It is implemented with two series PMOS transistors and two parallel NMOS transistors. The Boolean expression is $Y = \overline{A+B}$.

**Truth Table:**

| A | B | Y |
|---|---|---|
| 0 | 0 | 1 |
| 0 | 1 | 0 |
| 1 | 0 | 0 |
| 1 | 1 | 0 |

**Design Steps:**
- **Schematic Design:** Use two series PMOS transistors for the pull-up network and two parallel NMOS transistors for the pull-down network.
- **Layout Generation:** Place the transistors and route the connections to form the series and parallel networks.
- **DRC/LVS:** Verify the layout against the design rules and schematic.
- **Simulation:** Perform a transient analysis to check all four input combinations.

**Schematic Diagram:**


**Symbol:**


**Layout:**


**Simulation & Verification:**

The simulation results matched the NOR gate's truth table, validating the design.

---

### OR2X1 (2-Input OR Gate)

**Objective:** To design a 2-input OR gate using a hierarchical approach by cascading a NOR gate and an Inverter.

**Description:** An OR gate outputs a high signal if any of its inputs are high. The expression $Y=A+B$ can be implemented by inverting the output of a NOR gate, as $\overline{\overline{A+B}} = A+B$.

**Truth Table:**

| A | B | Y |
|---|---|---|
| 0 | 0 | 0 |
| 0 | 1 | 1 |
| 1 | 0 | 1 |
| 1 | 1 | 1 |

**Design Steps:**
- **Hierarchical Schematic:** Instantiate the `NOR2X1` and `Inverter` standard cells.
- **Schematic Capture:** Connect the inputs `A` and `B` to the `NOR2X1`. Connect the output of the `NOR2X1` to the input of the `Inverter`. The `Inverter`'s output is `Y`.
- **Layout:** Arrange the layouts of the two cells and route the connections.
- **Simulation:** Run a transient analysis and confirm the output `Y` matches the OR gate's truth table.

**Schematic Diagram:**


**Layout:**


**Symbol:**


**Simulation & Verification:**

The simulation successfully validated the OR gate's operation.

---

### M1_NWELL

**Objective:** To understand the purpose and physical representation of the N-Well layer.

**Description:** The **M1_NWELL** layer represents the N-Well, a region of the silicon substrate doped with n-type impurities. It provides the necessary environment to house PMOS transistors, whose body must be tied to the highest potential (VDD).

**Layout:**

In the layout, this layer encloses all PMOS transistors and is connected to VDD via a P-type tap.

### M1_PSUB

**Objective:** To understand the purpose and physical representation of the P-Substrate layer.

**Description:** The **M1_PSUB** layer represents the connection to the P-Substrate, the bulk silicon wafer. It provides a stable body potential for NMOS transistors, which are built directly on the substrate. This layer must be connected to the lowest potential (GND) to prevent latch-up.

**Layout:**

In the layout, this layer is represented by a specific contact that ties a metal layer to the P-Substrate, typically connected to GND via N-type taps.

---

## Digital Blocks and Systems

Each entry in this section is also presented with the same format as the standard cells, demonstrating the hierarchical design approach.

### Half Adder (with NAND Gates)

**Objective:** To design a 1-bit half adder circuit using only 2-input NAND gates, demonstrating the universality of the NAND gate.

**Description:** A half adder adds two single bits `A` and `B` to produce a `Sum` and a `Carry`. The logic is `Sum = A XOR B` and `Carry = A AND B`. These functions are implemented using a network of NAND gates.

**Truth Table:**

| A | B | Sum | Carry |
|---|---|---|---|
| 0 | 0 | 0 | 0 |
| 0 | 1 | 1 | 0 |
| 1 | 0 | 1 | 0 |
| 1 | 1 | 0 | 1 |

**Design Steps:**
- **Schematic Design:** Build the circuit by instantiating `NAND2X1` cells to form the XOR and AND logic functions.
- **Layout Generation:** Place the NAND gate layouts and route the connections.
- **Simulation:** Run a transient analysis to verify the `Sum` and `Carry` outputs match the truth table.

**Schematic Diagram:**


**Layout:**


**Symbol:**


[Image of Half Adder Symbol]


**Simulation & Verification:**

The simulation confirmed that the circuit correctly performs 1-bit binary addition.

---

### Full Adder

**Objective:** To design and verify a 1-bit full adder circuit using a hierarchical approach, building it from NAND-based half adders and OR gates.

**Description:** A full adder adds three single-bit numbers (`A`, `B`, `Cin`) to produce a `Sum` and a `Cout`. The circuit is built by cascading two half adders and an OR gate.

**Truth Table:**

| A | B | Cin | Y (Sum) | Cout |
|---|---|---|---|---|
| 0 | 0 | 0 | 0 | 0 |
| 0 | 0 | 1 | 1 | 0 |
| 0 | 1 | 0 | 1 | 0 |
| 0 | 1 | 1 | 0 | 1 |
| 1 | 0 | 0 | 1 | 0 |
| 1 | 0 | 1 | 0 | 1 |
| 1 | 1 | 0 | 0 | 1 |
| 1 | 1 | 1 | 1 | 1 |

**Design Steps:**
- **Hierarchical Schematic:** Instantiate two NAND-based half adders and an OR gate.
- **Schematic Capture:** Connect the inputs `A`, `B`, and `Cin` to form the full adder circuit.
- **Layout Generation:** Place the sub-blocks and route the connections.
- **Simulation:** Run a transient analysis to test all eight input combinations.

**Schematic Diagram:**


**Layout:**


**Symbol:**


**Simulation & Verification:**

The simulation results validated that the full adder correctly performed 1-bit binary addition with a carry-in.

---

### 1 x 2 De-multiplexer

**Objective:** To design a 1x2 demultiplexer (DEMUX) circuit using only 2-input NAND gates.

**Description:** A 1x2 DEMUX routes a single data input (`D`) to one of two outputs (`Y0`, `Y1`) based on the value of a select line (`S`). The logic is $Y_0 = D \cdot \overline{S}$ and $Y_1 = D \cdot S$.

**Truth Table:**

| S | D | Y0 | Y1 |
|---|---|---|---|
| 0 | 0 | 0 | 0 |
| 0 | 1 | 1 | 0 |
| 1 | 0 | 0 | 0 |
| 1 | 1 | 0 | 1 |

**Design Steps:**
- **Schematic Design:** Build the AND gate logic using NAND gates to realize the output expressions.
- **Layout Generation:** Place the NAND gate layouts and route the connections.
- **Simulation:** Verify that the data input is correctly routed to the selected output.

**Schematic Diagram:**


**Layout:**


**Symbol:**


**Simulation & Verification:**

The simulation confirmed that the circuit performed the demultiplexing operation as intended.

---

### 1 x 8 De-Multiplexer

**Objective:** To design a 1-to-8 demultiplexer (DEMUX) using a hierarchical approach, building it entirely from pre-existing 1x2 demultiplexer standard cells.

**Description:** A 1x8 DEMUX routes a single data input (`D`) to one of eight outputs (`Y0` to `Y7`) based on the value of three select lines (`S0`, `S1`, `S2`). This circuit is built by cascading seven 1x2 DEMUX units in a three-stage tree structure.

**Design Steps:**
- **Hierarchical Schematic:** Instantiate and connect seven `DEMUX1X2` cells in a tree structure.
- **Schematic Capture:** Connect the data input `D` and select lines `S0`, `S1`, and `S2` to the appropriate inputs of the `DEMUX1X2` cells.
- **Layout:** The layout is created by placing the seven `DEMUX1X2` layouts.
