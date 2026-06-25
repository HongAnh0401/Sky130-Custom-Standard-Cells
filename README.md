# Sky130 Custom Standard Cells

This project focuses on designing and optimizing custom standard cells using the Sky130 Open PDK. The objective is to improve Propagation Delay by adjusting transistor sizing while maintaining compatibility with ASIC design flows. 
The figure below shows an imbalance between the **low-to-high (tpLH)** and **high-to-low (tpHL)** propagation delays. Since tpHL = 10.32 ps while tpLH = 20.54 ps, the inverter exhibits significantly slower rising transitions than falling transitions.
<img width="1480" height="583" alt="standard" src="https://github.com/user-attachments/assets/60d91f3f-9d51-49a7-b4d9-3c15dc135d41" />


The design flow includes schematic design in Xschem, transistor-level simulation using Ngspice, physical layout implementation in Magic VLSI, DRC/LVS verification, post-layout simulation, and characterization for integration into OpenLane.

The project implements and evaluates custom versions of INV, NAND2, and NOR2 cells, comparing their timing performance against the standard cells provided in the Sky130 library.
