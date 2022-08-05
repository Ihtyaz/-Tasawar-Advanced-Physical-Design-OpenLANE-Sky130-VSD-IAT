# Advanced Physical Design - OpenLANE-Sky130 | VSD-IAT 

The repository is intended to house all proceedings, compilations and documents/reports pertaining to the [Advanced Physical Design](https://www.vlsisystemdesign.com/advanced-physical-design-using-openlane-sky130/) workshop organized and conducted by [VSD-IAT](https://www.vlsisystemdesign.com/).

Any discrepancies or misrepresentations are to be formally reported to the author.

The following sections would discuss and elaborate on the different topics that have been discussed within the workshop.

## 1. Inception of open-source EDA, OpenLANE and Sky130 PDK



### A. Computer Communication


* Fundamental Terminologies

*IC Package* - The term is associated to the enclosure that houses the semiconductor circuit design or device. This is generally practiced to protect the contents from corrosion or physical stress. In addition, it also facilitates electrical connection on a Printed Circuit Board (PCB). The type of IC packaging depends on the type of design the package will house and the associated requirments.


<p align="center">
  <img src="https://i.imgur.com/ATUGv6k.png">
</p>
 

*Wire Bonds* - A method pursued in order to facilitate boundary pin connections between the IC device (chip) and the packaging system.

<p align="center">
  <img src="https://gcdnb.pbrd.co/images/MXn667EtOMIV.png?o=1">
</p>


*Pads* - Pads serve as pathway for the transmission of signals to the chip or away from the chip, that is, for the transmission of input and output signals.

*Core* - The core region within a design is where all the associated digital logic components and foundry IPs are situated.

*Die* - Die refers to the entirety of a chip that gets manufactured on a silicon wafer.


<p align="center">
  <img src="https://gcdnb.pbrd.co/images/G4MYFstpfPcY.png?o=1">
</p>


*IP* - IP refers to intellectual property which serves as a large reusable unit of predefined functionality that can be integrated within a bigger ASIC design.

*Macros* - Macros are digital units or blocks within a design that communicate with other macros or IPs.

<p align="center">
  <img src="https://i.imgur.com/H5eqJuh.png">
</p>



* RISC-V

The project will employ the RISC-V architecture with the aid of RTL specifications and it's corresponding layout to drive the pnr cycle. The architecture of a RISC-V processor constitutes instructions that is used to communicate with the device, this is called Instruction Set Architecture; generally generated using a compiler in the form of RTL and used by an assembler to generate hardware representation of the instructions in binary (synthesized gate-leve netlist).


<p align="center">
  <img src="https://gcdnb.pbrd.co/images/IntXxm4Nv5cW.png?o=1">
</p>



### B. Designing an SoC


* Resources

To develop an ASIC/SoC design, three important resources would be essential.

i. Access to EDA tools - Tools that would help out with the proceedings of an ASIC/SoC design <br /> <br />
ii. Process Design Kit (PDK) - A compilation of files provided by a foundry to designers for the pnr cycle. Usually contains Design Rule files, spice device models, standard cell libraries, technology libraries and layout data (standard cells GDSII) <br /> <br />
iii. RTL Design - Digital Design specification in hardware description language that defines a system's digital segments; usually constitutes clocks, sequential and combinational elements.

* ASIC flow

For ASIC implementation, the design is taken through RTL to GDSII using Physical or PnR implementation. 

i. The design RTL code which contains abstract register-level information is synthesized to a gate-level representation using standard cell components (logic gates). The generated gate-level netlist and the RTL specification are functionally equivalent. <br /> <br />
ii. Standard cells usually constitue layout the represents the corresponding gate-level definition. They usually have a fixed height but varying widths (adhering to multiples of a standard unit). Standard cells can have multiple views employed by different tools - Electrical, HDL, SPICE/CDL, layout (GDSII) and abstract ( Macro LEF). <br /> <br />
iii. The PnR cycle is initiated through floor planning and power planning proceedings. It is essential to define the area for implemention the design on a particular chip and also defining a robust power distribution network for the design to operate. <br /> <br />
Floor planning is done on two different levels; chip floor planning & block floor planning. Chip floor planning usually involves die partitioning into system blocks and IO pad placement, while block floor planning includes core area definition, io pin placement and row & track definitions. <br /> <br />
Power planning may include use of multiple power and ground sources, whose supplies are distribution consistently throughout the design with the help of power stripes (uses higher metal layers to reduce resistance). <br /> <br />
iv. Subsequently, placement of gate-level netlist cells is performed on the rows within the core region of the die. This is done in two steps; global placement and detail placement. Global placement determines optimized placement of standard cells without paying heed to legalization (overlapping cells & violating row boundaries), while detail placement slighlty revamps the placement of standard cells to ensure legalization. <br /> <br />
v. Clock Tree Snythesis is performed before signal routing to dispense clock signals to all sequential elements. The clock tree network of the design must be routed prior to signal routing to ensure the construction of a solid network with the objective of minimal worst skew. <br /> <br />
vi. Once the clock tree is routed, the signal routing takes placement using the technology metal layers made available through the tech-LEF file in the PDK. Routing is done adhering to the metal track definitions and orientations for each metal layers. The metal tracks form a routing grid that helps divide the routing resources efficiently. Routing as-well is done in two steps; global routing and detail routing. Global routing determines and assigns routing guides from available routing resources without adhering to the design rules, while detail routing makes use of the routing guides to physically implement the assigned routes by adhering to design rules. <br /> <br />
vii. Once routing is complete, the final layout is ready which must be made to go through Physical Verification (DRC & LVS) to ensure manufacturability and Timing Verification (STA) to ensure synchronization of data. <br /> <br />


<p align="center">
  <img src="https://gcdnb.pbrd.co/images/k98T8MPSmA0r.png?o=1">
</p>



* Flow Associated Tools

i. RTL Translation (Registers to Logic Gates) & Standard Cell Mapping -  Yosys & abc <br /> <br />
ii. Synthesis Exploration (to determine best synthesis strategy with respect to power or timing) - OpenLane utility <br /> <br />
iii. Design Exploration (to determine best design configuration) - OpenLane utility <br /> <br />
iv. DFT (for post-fabrication fault testing; involves scan insertion, ATPG, Fault Coverage & Simulation) - Fault <br /> <br />
v. Physical Implementation (Floor/Power Planning, Placement, CTS, Routing and Physical Cells insertion) - OpenROAD <br /> <br />
vi. LEC (Functional Equivalence Check between synthesized gate-level netlist & physically implemented netlist) - Yosys <br /> <br />
vii. 





