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
where  g<sub>m1,2</sub> is the transconductance of differential amplifier, R<sub>0</sub> is the output resistance and C<sub>L</sub> is the load capacitance. The design specifications of OTA are shown in Table 1.
Table 1 Design Specifications of OTA
| Specifications                | Value |
| :------------                 |:------|
| UGB                           | 30MHz |
| Reference Current (Iref)      | 20µA  |
| Load Capacitor                | 1pF   |

# Design of OTA
<p align="justify">
In this design, gm/Id methodology is employed to evaluate the sizing of the MOS transistors. The Vdd and Vss are set to +0.9V and -0.9V, respectively. The DC simulation is performed on the both n-type and p-type MOSFETs by varying gate-to-source voltage (Vgs) from +0.3 to +1.8V. Since, three MOSFETs are stacked in OTA (see Fig.1), the drain-to-source voltage is set to (Vdd-Vss)/3 for the DC simulation. To avoid the short-channel effects, the transistor width (W) is set to 10µm [1, 2]. A finger width of 2µm is assumed, thus all widths are selected as multiples of 2µm. In general, OTAs use long channel length (L) in order to achieve high DC gain [1-3], so L = 2µm has been used in this design. The DC analysis is performed to obtain the MOS parameters such as Id, gm, gds, Vgs, Vth etc. These values are exported to .csv file and plotted using MATLAB.
</p>


<p align="center">
    <img src="https://user-images.githubusercontent.com/93975942/155969269-02a10da8-b57c-4280-a2c2-7d2002dbe1f1.png">
</p>

<p align="center">
        Fig. 2. DC Analysis Results of NMOS Transistor
</p>

The desired frequency response of the OTA is obtained based on the unity gain bandwidth (UGB) parameter as below,
     <p align="center">   UGB = g<sub>m1,2</sub>/(2&pi;C<sub>L</sub>R<sub>0</sub>)  </p>     

<p align="justify">
Substituting the desired values from Table I, yields g<sub>m1,2</sub> ≈ 188.4 µS. The biasing current (I<sub>d</sub>) of OTA is set to 100µA in this design. This provides the limit on required g<sub>m</sub>/I<sub>d</sub> ≈ 3.8 S/A. The desired W value of the n-type MOSFETs in differential pair is obtained by plotting the I<sub>d</sub>/W w.r.t g<sub>m</sub>/I<sub>d</sub> for a channel length of L=2µm as shown in Fig. 3 and then map the obtained gm/Id value on the Id/W plot.  This yields a current density ≈ 0.86µA/µm, thus the width is given by W<sub>1,2</sub> = I<sub>d1,2</sub>/(I<sub>d</sub>/W) ≈ 60µm.
</p>

<p align="center">
    <img width="300" height="300" src="https://user-images.githubusercontent.com/93975942/155971782-c46ab4ab-0c60-49b3-a93a-752fc9e5ad99.png">
</p>

<p align="center">
        Fig. 3. Normalized drain current (I<sub>d</sub>/W) w.r.t (g<sub>m</sub>/I<sub>d</sub>)
</p>
