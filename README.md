# Sky130 Custom Standard Cells

This project focuses on designing and optimizing custom standard cells using the Sky130 Open PDK. The objective is to improve Propagation Delay by adjusting transistor sizing while maintaining compatibility with ASIC design flows.

## BEFORE
The figure below shows an imbalance between the **low-to-high (tpLH)** and **high-to-low (tpHL)** propagation delays of the **sky130_fd_sc_hd__inv_1**. Since **tpHL = 10.32ps while tpLH = 20.54ps**, the inverter exhibits significantly slower rising transitions than falling transitions.

<img width="1480" height="583" alt="standard" src="https://github.com/user-attachments/assets/60d91f3f-9d51-49a7-b4d9-3c15dc135d41" />

In case of **Fan-Out 4**: tPHL ≈ 36ps, tPLH​ ≈ 80ps
<img width="1920" height="1080" alt="sweepfo4std" src="https://github.com/user-attachments/assets/17381349-7874-4815-9ddd-b67ff8115d43" />

As a result, the rising transition is significantly slower than falling, also it almost become distorted.

## AFTER

In contrast, Figure below shows the simulation results of the custom cell. The measured propagation delays are **tPHL ≈ 12.3 ps and tPLH ≈ 12.5 ps**. These values are nearly identical, indicating that the rising and falling delays have been successfully balanced. This improvement was achieved by optimizing the transistor sizing (W/L ratio, including the PMOS-to-NMOS width ratio) during the design process.

<img width="1481" height="570" alt="custom" src="https://github.com/user-attachments/assets/52cd536c-249c-47a0-963c-60f4210f94d3" />

In case of **Fan-Out 4**: tPHL ≈ 48ps, tPLH​ ≈ 54ps
<img width="1920" height="1080" alt="sweepfo4cust" src="https://github.com/user-attachments/assets/9c50515c-69ab-4944-a902-b5a3d7886848" />

By balancing the rise and fall propagation delays, the custom cell provides consistent timing, reduces waveform distortion, and improves overall circuit performance.

#
The design flow includes **schematic design** in **Xschem**, Simulation using **Ngspice**, Physical Layout in **Magic VLSI**, DRC/LVS verification, post-layout simulation, and characterization for integration into **OpenLane Flow**:

<img width="806" height="577" alt="Screenshot from 2026-03-09 14-53-04" src="https://github.com/user-attachments/assets/be1e2cd3-dd19-494a-ab90-f3f925a7fedf" />

The project currently evaluate custom versions of INV1, NAND2, and NOR2 cells, since when NAND2 nand NOR2 has it N/Pmos conectivity in series, lead to big values of Parasitics R,C and delays. In that case, the method is detecting worst-case of Rise/Fall delays and optimize:
## NAND2_1
<img width="817" height="377" alt="image" src="https://github.com/user-attachments/assets/ceed58ad-c739-44b1-b873-de2cd1da6979" />
## NOR2_1
<img width="808" height="366" alt="image" src="https://github.com/user-attachments/assets/548ec116-7555-4eea-8787-408e81d2e890" />

# MAGIC LAYOUT
## INV_1
<img width="539" height="705" alt="Screenshot from 2026-03-10 11-51-35" src="https://github.com/user-attachments/assets/6eecdc13-a353-49e3-bda5-eb89fa9299d2" />

## NAND2_1
<img width="539" height="705" alt="Screenshot from 2026-03-10 11-50-30" src="https://github.com/user-attachments/assets/7039abef-6cf0-4dd5-b4da-f27a63b58849" />

## NOR2_1
<img width="539" height="705" alt="Screenshot from 2026-03-10 11-51-01" src="https://github.com/user-attachments/assets/ef4c17cc-4b5b-420a-9b11-09b9fd3835b2" />

