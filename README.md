# Design-of-Single-Stage-OTA-using-28nm-CMOS-Technology
# Abstract
<p align="justify">
In this repository, CMOS-based single-stage operational transconductance amplifier (OTA) is presented with a unity gain bandwidth (UGB) of 30MHz. The CMOS based OTA (CMOSOTA) is designed by sizing (W/L) of the MOSFETs using gm/Id methodology. The mathematical expressions for performance specifications are applied over the graphical models to evaluate the required W/L. Finally, the performance parameters such as DC gain UGB are verified through simulation. This design is implemented using Synopsys Custom Compiler on as a part of Cloud Based Analog IC Design Hackathon.
</p>

# Introduction
<p align="justify">
The operational transconductance amplifier (OTA) is a voltage controlled current source whose output current is proportional to differential input voltage [1-3]. Fig. 1 shows the schematic of single stage OTA comprises a differential amplifier, and a current mirror circuit to fix the biasing current.
</p>
![Circuit diagram of OTA](https://user-images.githubusercontent.com/93975942/155960642-10438ddc-a0e1-4d48-9e03-bb13bf4d2431.png)
