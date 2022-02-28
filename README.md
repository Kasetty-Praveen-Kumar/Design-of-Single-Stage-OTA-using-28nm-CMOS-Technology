# Design-of-Single-Stage-OTA-using-28nm-CMOS-Technology
# Abstract
<p align="justify">
In this repository, CMOS-based single-stage operational transconductance amplifier (OTA) is presented with a unity gain bandwidth (UGB) of 30MHz. The CMOS based OTA (CMOSOTA) is designed by sizing (W/L) of the MOSFETs using gm/Id methodology. The mathematical expressions for performance specifications are applied over the graphical models to evaluate the required W/L. Finally, the performance parameters such as DC gain UGB are verified through simulation. This design is implemented using Synopsys Custom Compiler on as a part of Cloud Based Analog IC Design Hackathon.
</p>

# Introduction
<p align="justify">
The operational transconductance amplifier (OTA) is a voltage controlled current source whose output current is proportional to differential input voltage [1-3]. Fig. 1 shows the schematic of single stage OTA comprises a differential amplifier, and a current mirror circuit to fix the biasing current.
</p>

<p align="center">
    <img width="460" height="300" src="https://user-images.githubusercontent.com/93975942/155961072-21f34a8c-f604-4a30-9c54-32ec55580501.png">
</p>

<p align="center">
        Fig. 1. Schematic of Single Stage OTA [1]
</p>

The transfer function of the OTA is expressed in terms of the operating point parameters as follows,
     <p align="center">   A<sub>v</sub>(s) = g<sub>m1,2</sub>R<sub>0</sub>/(1+sC<sub>L</sub>R<sub>0</sub>)  </p>     
where g_{m1,2} is the transconductance of differential amplifier, R_0 is the output resistance and C_L is the load capacitance. The design specifications of OTA are shown in Table 1.
| Left-Aligned  | Center Aligned  | Right Aligned |
| :------------ |:---------------:| -----:|
| col 3 is      | some wordy text | $1600 |
| col 2 is      | centered        |   $12 |
| zebra stripes | are neat        |    $1 |
