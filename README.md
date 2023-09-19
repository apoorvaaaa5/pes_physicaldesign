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
# Getting familiar with open-source EDA tools
**Design preparation steps**
Type the following command to open the Openlane EDA tool

`cd Desktop/work/tools/`
`cd openlane_working_dir/`
`cd openlane`
`docker`

Now the shell opens. In the shell type `./flow.tcl -interactive`

To import all packages type `package require openlane 0.9`

![268514097-a9aa9cfa-d74d-41bb-babd-3335ba2e37a0](https://github.com/apoorvaaaa5/pes_physicaldesign/assets/117642634/24a9c520-767a-4313-a062-49f39edf9fe8)


* After preparing the design, we can see that a new 'runs' folder is created.
* To synthesize the design we type `run_synthesis`
* After the synthesis we calculate the flop ratio as: no. of flops/number of cells
* Here we have done it for dfxtp_2 (2:1 dmux)
* Also under the runs folder we can check out the netlist file generated after synthesis.

![268560449-e8b1fc0a-cd4a-46f5-8048-3a1ef0ea80b6](https://github.com/apoorvaaaa5/pes_physicaldesign/assets/117642634/e2c07edf-712c-4003-9bfc-83036d1b2ef6)
![268517973-a96a1184-5347-4793-b79e-9e98beef5876](https://github.com/apoorvaaaa5/pes_physicaldesign/assets/117642634/b37a4e36-5906-45cf-8d82-252fc61e9771)
![268518396-62f44d5c-a2a8-4a41-a063-860600e14698](https://github.com/apoorvaaaa5/pes_physicaldesign/assets/117642634/c9c4c273-c054-42a1-98a6-34cf66b2962b)

</details>

<details>
<summary>DAY2</summary>
  
# Chip Floor planning considerations

**Utilization Factor and Aspect Ratio**
Define Width and height of core and die: The die refers to the entire semiconductor chip, including the core, I/O pads, and any additional features.The core refers to the central area of the chip where most of the active circuitry resides. It includes components like the CPU, GPU, memory, and other logic.

**Utilization factor**=Area occupied by netlist/Area of the core

**Aspect ratio**=Height/width
* **Pre-placed cells**: Preplaced cells are a group of fixed-location standard cells that are manually placed by the chip designer in specific locations on the silicon die during the chip floor planning process. Unlike regular standard cells, which are placed automatically by Electronic Design Automation (EDA) tools, preplaced cells are positioned by the designer before automated placement and routing.
  
![268558724-2821dbea-1e2b-408b-9abf-5a0e2b65e126](https://github.com/apoorvaaaa5/pes_physicaldesign/assets/117642634/abe4fd06-0ae3-4c0a-826d-d3d8b842e153)


* **Decoupling capacitors**: A decoupling capacitor, often referred to simply as a "decap," is an essential electronic component used in electronic circuits, particularly on printed circuit boards (PCBs) and integrated circuits (ICs). Its primary purpose is to stabilize and filter the power supply voltage to ensure that sensitive components receive a stable and noise-free supply of power. Here are the key aspects of decoupling capacitors:

* **Pin Placement**:Pin placement is an essential part of floorplanning to minimize buffering and improve power consumption and timing delays we use the HDL netlist to determine where a specific pin should be placed in the circuit. We join the common pins and try to keep the connections as efficient as possible. In the pin placement step, we use the HDL netlist to determine where a specific pin should be placed in the circuit. We join the common pins and try to keep the connections as efficient as possible. Pins are placed in the Die area.
# Steps to run floorplan
Give the command `run_floorplan` after run_synthesis

![268560659-1ffd0935-dadf-4ddb-841f-7e29cbdfa2a6](https://github.com/apoorvaaaa5/pes_physicaldesign/assets/117642634/aa85bb91-86d2-4859-b74b-fad728766840)


To open the Floorplan we go to the following directory:
`vsduser@vsdsquadron:~/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/11-09_15-36/results/floorplan`

Then type the following command:
`magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.floorplan.def &`

The layout looks like this:
![268559069-6242cf1b-14e4-4691-9852-b40cd2c2de12](https://github.com/apoorvaaaa5/pes_physicaldesign/assets/117642634/4d993121-e00a-40a5-bb57-8efe9ba1d9f8)


The zoomed-in view:
![268559132-5210b11c-409c-4bdc-ad97-8b359c0fa987](https://github.com/apoorvaaaa5/pes_physicaldesign/assets/117642634/adb856bf-3dff-49b4-96c6-ae5dea5d54b0)


**Library Binding and Placement**
Netlist Binding and Initial Place Design: The Library consists of cells, sizes of cells, various flavors and shapes of the cells, Timing, Power, and delay information. Now, we have the floorplan, netlist, and representation of components of netlist in the library. Place all the components such that the timing is not disturbed and distribute them properly.
![268559909-9f0e948c-d8c4-4931-bdfa-c74813443e20](https://github.com/apoorvaaaa5/pes_physicaldesign/assets/117642634/5b5322fa-6c4d-478d-ad53-2ac55b601785)


# Placement
* After run_floorplan, give the command `run_placement`
![268560869-68bd746d-fc98-4095-9b5f-adb54eddb58e](https://github.com/apoorvaaaa5/pes_physicaldesign/assets/117642634/27251be5-e80b-4993-a345-565e3274310a)


* To view the placement type the command `magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.placement.def`
![268559775-24dbfecf-c9de-4889-8074-2c7c9539a9f1](https://github.com/apoorvaaaa5/pes_physicaldesign/assets/117642634/a53a8ee2-0275-4efa-b62c-c4178736a77b)


* After we zoom in we can see the placement of the standard cells in the standard cell rows.
![268559794-c8bf3138-63db-4dd1-8023-00c3ee6244f8](https://github.com/apoorvaaaa5/pes_physicaldesign/assets/117642634/fef20a41-acbe-4193-9b87-25168763ec15)

# Cell Design and Characterization Flow

**Cell Design Flow**
* Inputs - PDKs (Process design kits), DRC & LVS rules, SPICE models, library & user-defined specs.
* Design Steps - The design steps of cell design involve Circuit Design, Layout Design, and Characterization. The software GUNA is used for characterization. The characterization can be classified as Timing characterization, Power characterization, and Noise characterization.
* Outputs - Outputs of the Design are CDL (Circuit Description Language), GDSII, LEF, extracted Spice netlist (.cir), timing, noise, and power.libs, function.

**Characterization**: timing, noise power.libs functions read in the models and tech files and generate extracted spice Netlist. Read the subcircuits and attach power sources. Apply stimulus to characterization setup, provide necessary output capacitance loads, and provide necessary simulation commands.

**This is for an inverter**
* Read the model files.
* Read the extracted SPICE netlist.
* Recognize the behavior of the buffer.
* Attaching the necessary power sources
* Apply the stimulus, which is the input signal to the circuit.
* Read the sub-circuit of the inverter.
* Provide necessary output capacitances.
* Provide the necessary simulation commands
  
# General Timing characterization parameters
**Timing threshold**:
* slew_low_rise_thr - 20% from bottom power supply when the signal is rising
* slew_high_rise_thr - 20% from top power supply when the signal is rising
* slew_low_fall_thr - 20% from bottom power supply when the signal is falling
* slew_high_fall_thr - 20% from top power supply when the signal is falling
* in_rise_thr - 50% point on the rising edge of input
* in_fall_thr - 50% point on the falling edge of input
* out_rise_thr - 50% point on the rising edge of ouput
* out_fall_thr - 50% point on the falling edge of ouput
  
These are the main parameters that we use to calculate factors such as propogation delay and transition time

**propogation delay**= time(out_thr) - time(in_thr)
**Transition time**= time(slew_high_rise_thr) - time(slew_low_rise_thr)
</details>
# DAY-3

# Design Library cell using Magic Layout and NGSpice Characterization

## SPICE Deck creation for CMOS Inverter

SPICE deck contains the information of netlist such as:
- Connectivity Information
- Component values
- 'Nodes' identified
- 'Node' names

![267311221-fde8c66e-6547-49a2-bdad-478c812d5419](https://github.com/apoorvaaaa5/pes_physicaldesign/assets/117642634/2253799b-fcab-43f5-835c-0c257db56244)


### [CMOS_INVERTER.cir]()

```
*** MODEL DESCRIPTIONS ***
*** NETLIST DESCRIPTION ***
M1 out in vdd vdd pmos W=0.375u L=0.25u
M2 out in 0 0 nmos W=0.375u L=0.25u

cload out 0 10f

Vdd vdd 0 2.5
Vin in 0 2.5
*** SIMULATION Commands ***

.op
.dc Vin 0 2.5 0.05
*** include tsmc_025um_model.mod ***
.LIB "tsmc_025um_models.mod" CMOS_MODELS
.end
```

SPICE Simulation steps
```
cd <folder where the .cir file is present>
source CMOS_INVERTER.cir
run
setplot
dc1
display
plot out vs in
```

Observe the output. It should be symmetric ie., the threshold voltage should be at vdd/2 if it isnt, try to increase the PMOS width and run the simulation again. One of the important parameters tthat defines the **ROBUSTNESS** of the CMOS is ```Switching Threshold (Vm)``` @Vm : Vin = Vout

## Fabrication Process for a CMOS Inverter

Fabrication of CMOS Inverter is a 16-Mask process

### 1. Selecting the substrate 

- P-Type substrate with resistivity around (5-50 ohm) doping level (10^15 cm^-3) and orientation (100).
- Note that substrate doping should be less than well doping (used to fabricate NMOS and PMOS)

### 2. Create active resistance

This step creates pockets for NMOS and PMOS
1. Grow SiO2(~40nm) on Psub
2. deposit ~80nm Si3N4 on SiO2
3. deposit 1um layer of photoresist(used to define regions)
4. photolithography
5. etch out Si3N4 and SiO2 using a suitable solvent
6. Place the obtained structure in oxidartion furnace due to which field oxide is grown.This process is called ```LOCOS``` that is ```Local oxidation of silicon```
7. Etch out Si3N4 using hot phosphoric acid

### 3.NWel and PWel formation

- Apply photoresist, apply mask that covers NMOS
- Expose to UV, Wash, remove mask, appl boron(p-type) using Ion Implantation at an energy of 200Kev(for diffusion)
- repeat it for the other half using phosphorous @400Kev because phosphorous is heavier
- Wells have been created but the depth is low. Therefore subject it to high temperature furnace which increases the well depth.

### 4. Formation of Gate

- We repeat the step 3 but at low energy with p-type implant as boron @60Kev and n-type implant as Arsenic.
- Due to this The SiO2 is damaged as the dopants penetrate through it.
- Therefore original SiO2 is etched out using dilute HF solution and regrown to give high quality oxide(~10 nm thin)
- Finally for the gate to form, apply N-type ion implants for low gate resistance.
- Now mask on small width of Nwell and PWell above SiO2  and perform photolithography
- Gate Formation is Done

### 5. Lighlt Doped Drain Formation(LDD Formation)

- On the surface of SiO2 corresponding to NWell, apply photoresist, mask it, put phosphorous to make N-Implant on p-well(N-)
- Similarly do it for the other side using boron that forms (p-) implant
- This LDD has to be protected from further process
- so, Deposit 0.1um thick SiO2 on full structure and etch out using plasma anisotropic etching that results in formation of side wall spacers..

### 6. Source and Drain Formation

- Mask Nwell structure, deposit arsenic @75KeV that forms an N+ implant on Pwell
- use boron for P+ implant formation on Nwell
- Subject it to high temperature furnace that results in required thickness of N+,P+,N-,P- implants.

### 7. Steps to form contacts and interconnects

- Etch thin SiO2 oxide in HF solution
- Deposit Titanium of wafer surface using sputtering all over the structure
- Wafer heated at 600-700 degree in ambient N2 environment for 60 sec that reults in low resistance TiSi2 where the gate of both MOS is present.
- At the other places, TiN is formed that's used for local communication
- Etch off TiN on and half around gate structure of both MOS using RCA Cleaning

### 8. Higher level metal formation

- On the resulted structure, deposit a thick layer of (1um) SiO2 doped with P/B known as phosphoborosilicate glass
- To make the added surface plain, use CMP (Chemical Metal Polishing)
- For the creation of contact pins, proper holes with contacts have to be made
- This can be done using Al, W and TiN layer depositions.
- Deposit a layer of Si3N4 that acts as dielectric to protect the chip.

### 9. Final STructure

![267354600-0e355a75-55ff-4723-96ae-4abd5845697c](https://github.com/apoorvaaaa5/pes_physicaldesign/assets/117642634/8c22080b-f080-4c69-baec-1e087e50108e)


## Inverter Layout using Magic

```
cd Desktop/work/tools/openlane_working_dir/openlane/vsdstdcelldesign
magic -T sky130A.tech sky130_inv.mag
```

## Exploring the Layout displayed by MAGIC

Select the specific layer/device by hovering over the object and pressing, s, iteratively, until you traverse the hierarchy to the specified object:

![267333476-1a918a4c-da78-4c9f-b553-e080ddd3e7e7](https://github.com/apoorvaaaa5/pes_physicaldesign/assets/117642634/629a91f3-cc79-4a91-afd5-100ab74ed617)



- select a region from the layout, go to the console and type ```what``` to display the information of selected area
- To select a region, place ```cursor``` on that point and  press```s```. More the number of times you press ```s```, higher the abstraction selected.

![267363442-fdd5bf6b-3483-4471-9b68-d98fa0b80af3](https://github.com/apoorvaaaa5/pes_physicaldesign/assets/117642634/342be7db-9b32-4221-aeec-8c9b2d5bc61a)


refer to [inverter](https://github.com/nickson-jose/vsdstdcelldesign) to create layout for CMOS Inverter

### DRC Check

To check for DRC Errors, select a region (left click for starting point, right click at end point) and see the DRC column at the top that shows how many DRC errors are present.The Details of DRC Errors will be printed on the console.

![267381950-eebc0109-4408-40fa-a18e-ead67419cfa7](https://github.com/apoorvaaaa5/pes_physicaldesign/assets/117642634/1dc70af4-5a6f-46b9-b5d6-45d434145cbb)


For more information on DRC errors plase refer to: [DRC_Erros](https://skywater-pdk--136.org.readthedocs.build/en/136/)
For more information on how to fix these DRC errors using Magic please refer to: [fix_DRC](http://opencircuitdesign.com/magic/)


## Extracting PEX to SPICE with MAGIC

Select Full inverter layout. Then

![267383524-36c93dc8-6c1e-4ac4-9eac-f2c7a001b82a](https://github.com/apoorvaaaa5/pes_physicaldesign/assets/117642634/ecdec3f2-d440-4a3c-b84b-5947885ec568)


The above file has details of inverter netlist but the sources and their values are not specified. So we have to modify the file.

- Grid size from the layout is 0.01u
- specify the library for MOS
- create VDD, VSS, Input pulse Va
- specify the type of analysis to be done

<summary>DAY 4 : Pre-Layout timing analysis and importance of good clock tree</summary>
<br>

## Extraction of LEF 

Place and routing (PnR) is performed using an abstract view of the GDS files generated by Magic. The abstract information will include metal and pin information. The PnR tool will use the abstract view information, formally defined as LEF information, to perform interconnect routing in conjunction to routing guides generated from the PnR flow.

- Technology LEF - Contains layer information, via information, and restricted DRC rules
- Cell LEF - Abstract information of standard cells

From PnR POV, We have to follow certain guidelines to get standard cell set
1. Input and output ports must lie on the intersection of vertical and horizontal tracks
2. Width of the standard cell should be odd multiples of the track pitch and height should be odd multiple of vertical track pitch


Track info can be found at :

``` ~/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/openlane/sky130fd_sc_hd/tracks.info```

<img width="297" alt="Screenshot 2023-09-19 162329" src="https://github.com/apoorvaaaa5/pes_physicaldesign/assets/117642634/71316298-3e80-4390-9291-5c682e24f2f0">



