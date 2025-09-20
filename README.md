# Pratyush-VSD-tapeout-
VSD Chip Tapeout 
Document summary of video
Chip Modelling (High-level design stage)
    • Specs (C model):
        ◦ The very first stage is writing a functional model of the chip in a high-level language like C/C++.
        ◦ This acts as the golden reference model – it describes what the chip should do, not how it will be implemented.
    • Testbench in C:
        ◦ A testbench is written in C to verify that the spec model works correctly.
    • Output (O1):
        ◦ A C model with testbench results is the first checkpoint before RTL coding starts.
RTL Architecture (RTL Design Stage)
    • Soft copy of hardware (Verilog/VHDL):
        ◦ The RTL architect takes the C model/specs and describes the hardware behavior using RTL (Verilog or VHDL).
        ◦ This is called the soft model of hardware.
    • Components designed at RTL:
        ◦ Processor core
        ◦ Peripherals / IPs (like UART, SPI, timers, etc.)
    • Synthesis process:
        ◦ The RTL is synthesized to generate a Gate-level Netlist (logic gates + flip-flops).
    • Macros & Analog IPs:
        ◦ Macros: Pre-synthesized blocks (like memories, multipliers) which can be instantiated as required.
        ◦ Analog IPs: Functional blocks that are not purely digital (PLL, ADC, etc.) described in functional RTL but implemented as hard macros.
    • Output (O2):
        ◦ Verified RTL description of the entire SoC, ready for synthesis and integration.


SoC Integration (Chip-level assembly stage)
    • Integration of all blocks:
        ◦ Processor, peripherals, macros, and analog IPs are combined into one SoC.
        ◦ GPIOs and bus interconnects are also added here.
    • Backend (Physical design flow):
        ◦ Steps like floorplanning, placement, clock tree synthesis (CTS), and routing are performed.
        ◦ Uses hard macros (HM) for analog and large IPs.
        ◦ The processor can be included as soft logic (synthesized) or as a hard macro depending on the case.
    • Output (O3):
        ◦ A fully integrated SoC netlist/layout.
Final ASIC Flow
    • Conversion to GDSII:
        ◦ The final physical layout is written out in GDSII format – the industry standard for chip fabrication.
    • Checks before tapeout:
        ◦ DRC (Design Rule Check): Ensures layout follows foundry rules.
        ◦ LVS (Layout vs. Schematic): Ensures the layout matches the logical netlist.
    • Tapeout:
        ◦ After clean DRC/LVS, the GDSII file is sent to the fab for manufacturing.


<img width="1920" height="1080" alt="Screenshot from 2025-09-20 21-07-59" src="https://github.com/user-attachments/assets/1d46a4f9-dcc4-49c8-910e-6e0614f8fa82" />

