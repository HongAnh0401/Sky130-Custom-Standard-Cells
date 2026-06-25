# Sky130 Custom Standard Cells

This project focuses on designing and optimizing custom standard cells using the Sky130 Open PDK. The objective is to improve Propagation Delay by adjusting transistor sizing while maintaining compatibility with ASIC design flows.

## BEFORE
The figure below shows an imbalance between the **low-to-high (tpLH)** and **high-to-low (tpHL)** propagation delays. Since tpHL = 10.32ps while tpLH = 20.54ps, the inverter exhibits significantly slower rising transitions than falling transitions.
<img width="1480" height="583" alt="standard" src="https://github.com/user-attachments/assets/60d91f3f-9d51-49a7-b4d9-3c15dc135d41" />

In case of **Fan-Out 4**: tPHL ≈ 36ps, tPLH​ ≈ 80ps
<img width="1920" height="1080" alt="sweepfo4std" src="https://github.com/user-attachments/assets/17381349-7874-4815-9ddd-b67ff8115d43" />

As a result, the rising transition is significantly slower than falling, also it almost become distorted.

## AFTER

In contrast, Figure below shows the simulation results of the custom cell. The measured propagation delays are tPHL ≈ 12.3 ps and tPLH ≈ 12.5 ps. These values are nearly identical, indicating that the rising and falling delays have been successfully balanced. This improvement was achieved by optimizing the transistor sizing (W/L ratio, including the PMOS-to-NMOS width ratio) during the design process.

<img width="1481" height="570" alt="custom" src="https://github.com/user-attachments/assets/52cd536c-249c-47a0-963c-60f4210f94d3" />

In case of **Fan-Out 4**: tPHL ≈ 48ps, tPLH​ ≈ 54ps

<img width="1920" height="1080" alt="sweepfo4cust" src="https://github.com/user-attachments/assets/9c50515c-69ab-4944-a902-b5a3d7886848" />



The design flow includes schematic design in Xschem, transistor-level simulation using Ngspice, physical layout implementation in Magic VLSI, DRC/LVS verification, post-layout simulation, and characterization for integration into OpenLane.

The project implements and evaluates custom versions of INV, NAND2, and NOR2 cells, comparing their timing performance against the standard cells provided in the Sky130 library.
