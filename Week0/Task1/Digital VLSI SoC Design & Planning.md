# Digital VLSI SoC Design & Planning

Designing a System-on-Chip (SoC) is a structured journey that starts with specifications and ends with a verified layout ready for fabrication. At each stage, the outputs (O0, O1, O2, O3, O4) are carefully compared to maintain design consistency.

---

## Step 1: Chip Modelling (Specification Stage)
- The design begins with **specification modeling** using a C model.  
- A **testbench in C language** verifies the intended functionality and generates the first reference output (O0).  
- This stage ensures that the specification itself is valid before moving further.  
- **Deliverables:** C testbench, expected output vectors (O0).  

---

## Step 2: RTL Design & Architecture
- The specification is converted into **RTL (Verilog)**, often referred to as the "soft copy of the hardware."  
- This RTL output (O1) must match the original specification outputs (O0).  
- **Verification checkpoint:** O0 = O1.  
- **Deliverables:** Verilog RTL, RTL testbench, simulation results.  

---

## Step 3: RTL Partitioning
- The Verilog RTL is divided into **processor** and **peripherals/IPs**.  
- Flow:  
  - Processor → synthesized into **Gate Level Netlist (synth P1)**.  
  - Peripherals/IPs → represented as **synthesizable RTL macros**.  
  - Analog IPs → modeled as **functional RTL**.  
- **Goal:** Partitioning must not change the functionality.  
- **Verification checkpoint:** O1 = O2.  

---

## Step 4: SoC Integration
- The processor, peripherals, and IPs are connected together at the SoC level.  
- Integration involves **GPIOs, buses, and interfaces** to create the full SoC.  
- At this stage, O2 is validated against the integrated SoC output (O3).  
- **Verification checkpoint:** O2 = O3.  
- **Deliverables:** Top-level RTL, integration scripts.  

---

## Step 5: Physical Design (PD)
- With the SoC RTL ready, the **physical design flow** begins:  
  - Floorplanning  
  - Placement  
  - Clock Tree Synthesis (CTS)  
  - Routing  
- Hardened macros (e.g., SRAM, analog IPs) are used as-is.  
- The processor is implemented as **soft logic** unless hardened.  
- **Deliverables:** PD reports (floorplan, placement, CTS, routing).  

---

## Step 6: GDSII & Sign-off
- Final physical layout is converted into **GDSII format**.  
- Sign-off checks ensure manufacturing readiness:  
  - **DRC (Design Rule Check)**  
  - **LVS (Layout vs. Schematic)**  
- Once passed, the design is ready for **tape-out**.  
- **Verification checkpoint:** O3 preserved in layout.  

---

## Step 7: Final Verification & Applications
- Final stage includes **full-chip testbench with peripherals**.  
- The chip’s behavior is verified at O4, ensuring consistency across all stages:  
  **O0 = O1 = O2 = O3 = O4.**  
- Applications of the designed SoC include:  
  - Smart devices (iWatch)  
  - Arduino-based boards  
  - TV panels  
  - AC and home appliances  

---

## Summary
The SoC design flow guarantees that the **specification, RTL, integration, physical design, and final GDSII** all remain functionally equivalent. The golden principle of SoC verification is maintained:  

**O0 = O1 = O2 = O3 = O4**
