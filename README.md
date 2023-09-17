# pes_physicaldesign
## DAY 1
### Inception of open-source EDA, OpenLANE and Sky130 PDK
<details>
<summary> How to talk to computers </summary>
  
**Introduction to QFN-48 Package, chip, pads, core, die and IPs**

How computers work
* An Arduino board is a well-known open-source electronics platform that encompasses a microcontroller and a development environment.
* It represents a compact computing chip responsible for executing instructions and managing the operations of your electronic project.
* The functionality of Arduino boards revolves around enabling you to create and upload code that dictates how the microcontroller on the board behaves.
  
![268251110-74ac0bd8-41ad-425a-9b16-9b66bfe2271e](https://github.com/apoorvaaaa5/pes_physicaldesign/assets/117642634/5ee9dd49-9c17-43ec-9a4d-4389619d3b38)

The arduino can be designed as board like:

![268251310-2f2197ba-eebc-4025-941d-22e4a893e033](https://github.com/apoorvaaaa5/pes_physicaldesign/assets/117642634/3dfe5a7d-aa0a-451f-868c-d35bbed65193)


* When we examine the IC, it resembles an image referred to as a "chip," although it's technically known as a "PACKAGE."
* These packages are assigned names, such as "QFN-48," and there are various package types available with different configurations.
* The specific pin locations for this package are determined by the Arduino board.
* The size of the package is 7mm x 7mm.
* The chip itself, positioned in the center of the package, is the primary processing unit. It is connected to the package using a method called "wire bonding," facilitating the transfer of signals from external sources into the chip.
* Opening the chip reveals multiple components, including "PADs," which are like metal connectors on the chip's bottom.
* These PADs link the chip to a circuit, allowing external signals to enter for processing.
* The open space within the chip is known as the "Core." This Core functions as the chip's brain, responsible for most of the thinking and information processing.
* It houses digital logic elements such as AND gates, OR gates, and MUXs.
  
* The chip itself, known as the "Die," is the heart of a computer chip. It's a small, flat piece of silicon containing the electronic circuits where critical computations and operations occur. It's manufactured on a "Silicon Wafer."
* The typical Core of a CHIP consists of components like SoC (e.g., RISC-V SoC), SRAM, ADCs, DACs, PLL, SPI, and other elements.
* Collectively, SRAM, ADC, DAC, PLL, and others are referred to as "Foundry IP's" (Intellectual Properties).
* "Foundry" is a pivotal term in chip design, as it refers to the place where chips are manufactured. Foundries encompass machines used in chip production.
* The digital blocks situated within the SoC and the SPI interface are commonly termed "Macros."

![268251815-7b63d0f5-53be-404d-8ad6-4b8bb52c661f](https://github.com/apoorvaaaa5/pes_physicaldesign/assets/117642634/805ef6b4-bfa5-4f6e-8bab-9a6bb1b4f8d1)


**Introduction to RISC-V**

Definition of RISC-V:
* RISC-V, known as "RISC-V instruction set architecture" or "ISA," is a language of computing that facilitates communication with computers.
* It operates as an open-source instruction set architecture (ISA) founded on well-established principles of reduced instruction set computing (RISC).
Understanding Instruction Set Architecture (ISA):
* ISA encompasses the instructions a computer's processor can execute, essentially defining its capabilities.
Execution Flow for C Programs on Hardware:
* To execute a C program on specific hardware with a particular layout (e.g., qFlow), a specific flow is followed:
  * The C program is initially compiled into its corresponding assembly language program, which utilizes RISC-V assembly language.
  * This assembly language program is further transformed into machine language, represented as binary code (1's and 0's), understood by the hardware.
  * Although represented in hexadecimal in this context, it is eventually converted into binary format.
  * These binary instructions are then executed within the hardware layout to produce the desired output.
  * An intermediary layer between the C program and the layout is the "HDL" (Hardware Description Language).
  
Definition of HDL:
* HDL stands for "Hardware Description Language."
* It is a specialized programming language employed to articulate the structure and behavior of electronic circuits and systems.
* HDLs play a pivotal role in the design, simulation, and synthesis of digital circuits, including those within microprocessors, memory chips, and integrated circuits.
Types of HDLs:
* There are two primary types of HDLs:
  * Verilog:
    * Developed by Phil Moorby and Prabhu Goel in the 1980s.
  * VHDL (VHSIC Hardware Description Language):
    * Developed by the U.S. Department of Defense in the 1980s.
Implementation of RISC-V Specifications:
* To realize RISC-V specifications effectively, the use of RTL (Register-Transfer Level) is essential.
* In the presented context, the RTL used is the picorv32 CPU core, which serves as an implementation of these RISC-V specifications.
RTL-GDS Flow:
* The utilization of RTL facilitates the implementation of RISC-V specifications.
* The transition from RTL to GDS (Graphics Data System) marks the progression in the design flow, ensuring that the chip's physical layout and manufacturing processes are aligned with RISC-V specifications.

**From Software Applications to Hardware**
* Apps: Application software is a type of computer software that is designed to perform specific tasks or functions for end-users.
* System software: System software refers to a category of computer software that acts as an intermediary between the hardware components of a computer system and the user-facing application software. It provides essential services, manages hardware resources, and enables the execution of application programs.
* Operating System: The operating system is a fundamental piece of software that manages hardware resources and provides various services for both users and application programs. It controls tasks such as memory management, process scheduling, file system management, and user interface interaction.
* Compiler: A compiler is a type of software tool that translates high-level programming code written by developers into assembly-level language.
* Assembler: An assembler is a software tool that translates assembly language code into machine code or binary code that can be directly executed by a computer's processor.
* RTL: RTL serves as an abstraction level in the design process that represents the behavior of a digital circuit in terms of registers and the operations that transfer data between them.
* Hardware: Hardware refers to the physical components of a computer system or any electronic device. It encompasses all the tangible parts that make up a computing or electronic device and enable it to perform various tasks.

![268254760-43c4f8e8-d9b4-4d65-9285-64f5068b7b7a](https://github.com/apoorvaaaa5/pes_physicaldesign/assets/117642634/9f206e12-6421-4eeb-be47-57f0080caa6f)


</details>
<details>
<summary> SoC Design and OpenLane </summary>
  
**Introduction to all Components of Open-source Digital ASIC Design**
To implement Digital ASIC design, several essential components are required. These components include RTL IP's (Register Transfer Level Intellectual Properties), EDA Tools (Electronic Design Automation Tools), and PDK data (Process Design Kit data).
What is PDK?
* PDK (Process Design Kit) is a set of files provided by semiconductor manufacturers.
* It helps designers utilize the manufacturer's fabrication process to create integrated circuits (ICs).
* PDK includes comprehensive information, models, and files specific to the manufacturer's process technology.
* Designers rely on PDK to develop and validate their designs for a particular manufacturing process.
What are EDA Tools?
* EDA (Electronic Design Automation) tools are software applications and utilities used in the design and development of electronic systems.
* These systems encompass integrated circuits (ICs), printed circuit boards (PCBs), and other electronic components.
* EDA tools are critical for designing and testing electronic hardware to ensure proper functionality before manufacturing.
* They automate various aspects of the design process, improving efficiency and reducing errors.
Open-source Digital ASIC Design Components
For open-source Digital ASIC Design, three key elements are crucial:
* RTL IP's: These can be sourced from open repositories such as librecores.org, opencores.org, and GitHub, among others.
* EDA Tools: Open-source EDA tools like qflow, openROAD, and openLANE are available for design and validation.
* PDK: Open-source PDKs, like the Foss 130nm production PDK, provide the process-specific data necessary for designing ASICs.
Achieving 100% Open-source Digital ASIC Design
* The combination of RTL IP's, open-source EDA tools, and open-source PDKs enables the realization of 100% open-source Digital ASIC design.
ASIC Design Flow
* The methodology for open-source Digital ASIC Design is implemented through a structured flow.
* This flow involves a software tool known as "RTL to GDS2."
* The primary objective of the ASIC Design Flow is to take the design from RTL (Register Transfer Level) and convert it into the GDS2 format, which is used for the final layout of the ASIC.

**Simplified RTL to GDS2 Flow**
The simplified RTL to GDS2 flow is a sequence of major implementation steps for designing an Application-Specific Integrated Circuit (ASIC). It starts with an RTL (Register Transfer Level) model and ends with a fabricated masked set layout in the GDS2 format.
1) Synthesis:
* The first step involves synthesis, where the RTL design is translated into circuits composed of components from a standard Cell Library (SCL).
* The result is a gate-level netlist described in Hardware Description Language (HDL), functionally equivalent to RTL.
* Cells from the library have regular layouts, with variable cell widths but discrete sizes.
* Different EDA tools use various views of these cells, including electrical models, HDL, SPICE, and layout views.
3) Floor Planning and Power Planning:
* In this step, you perform floor planning and power planning based on whether you are implementing a single component (macro) or the entire chip.
* The goal is to plan the silicon area and create a robust power distribution network to supply power to the circuits.
* In chip floor planning, the chip die is partitioned between different chip components.
* In macro floor planning, you define the macro's dimensions, pin locations, routing tracks, and rows for later placement and routing steps.
* Power planning involves constructing a power network, often using multiple VDD and ground pins connected to components through power rings and metal power straps.
3) Placement:
* Placement is the third step and involves placing the gate-level netlist cells on vertical rows.
* Connected cells must be placed close to each other to reduce interconnect delays and facilitate successful routing.
* Placement occurs in two steps: global placement and detailed placement.
* Global placement aims to find optimal positions for cells, which may not be legal and can result in overlaps or going off rows.
* Detailed placement minimally alters the positions obtained in global placement to make them legal.
4) Clock Tree Synthesis (CTS):
* Clock tree synthesis is the fourth step, focusing on routing the clock signals before routing other signals.
* It involves creating a clock distribution network to deliver the clock to all clock cells (e.g., flip-flops).
* The clock network resembles a tree, with the clock source as the root and clock elements as the leaves.
* CTS aims to minimize clock skew (arrival time differences) and latency, ensuring a synchronized clock across the design.
5) Routing:
* The fifth step is routing, where signals are routed after clock routing.
* Given the placements and a fixed number of metal layers, a valid pattern of horizontal and vertical wires is found to connect cells together.
* Routing tools use metal layers defined by the PDK, which specify thickness, pitch, tracks, and minimum width.
* Routers often use grid routing methods, breaking routing into global and detailed routing stages.
6) Sign-Off:
* The final step is sign-off, which includes various verifications.
* Physical verification checks include:
  * Design Rule Checking (DRC) to ensure the layout adheres to design rules.
  * Layout vs. Schematic (LVS) to verify that the layout matches the gate-level netlist.
  * Timing verification includes Static Timing Analysis (STA) to ensure that all timing constraints are met, and the circuit operates at the designated clock frequency.
This simplified RTL to GDS2 flow is a fundamental process for designing ASICs, ensuring that the design is correctly synthesized, placed, routed, and verified before fabrication.
