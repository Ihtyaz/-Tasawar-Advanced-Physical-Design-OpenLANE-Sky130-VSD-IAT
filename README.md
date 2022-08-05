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

