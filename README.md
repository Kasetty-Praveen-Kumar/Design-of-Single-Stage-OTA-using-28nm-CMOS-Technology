# Design of Single Stage OTA using 28nm CMOS Technology

# Table of Contents
* [Abstract](https://github.com/Kasetty-Praveen-Kumar/Design-of-Single-Stage-OTA-using-28nm-CMOS-Technology/blob/main/README.md#abstract)
* [Introduction](https://github.com/Kasetty-Praveen-Kumar/Design-of-Single-Stage-OTA-using-28nm-CMOS-Technology/blob/main/README.md#introduction)
* [Design of OTA](https://github.com/Kasetty-Praveen-Kumar/Design-of-Single-Stage-OTA-using-28nm-CMOS-Technology/edit/main/README.md#design-of-ota)
* [Simulation Results](https://github.com/Kasetty-Praveen-Kumar/Design-of-Single-Stage-OTA-using-28nm-CMOS-Technology/edit/main/README.md#simulation-results)
* [Netlist](https://github.com/Kasetty-Praveen-Kumar/Design-of-Single-Stage-OTA-using-28nm-CMOS-Technology/edit/main/README.md#netlist)
* [Conclusion](https://github.com/Kasetty-Praveen-Kumar/Design-of-Single-Stage-OTA-using-28nm-CMOS-Technology/edit/main/README.md#conclusion)
* [Acknowledgment](https://github.com/Kasetty-Praveen-Kumar/Design-of-Single-Stage-OTA-using-28nm-CMOS-Technology/edit/main/README.md#acknowledgment)
* [References](https://github.com/Kasetty-Praveen-Kumar/Design-of-Single-Stage-OTA-using-28nm-CMOS-Technology/edit/main/README.md#references)

# Abstract
<p align="justify">
In this repository, CMOS-based single-stage operational transconductance amplifier (OTA) is presented with a unity gain bandwidth (UGB) of 30MHz. The CMOS based OTA (CMOSOTA) is designed by sizing (W/L) of the MOSFETs using gm/Id methodology. The mathematical expressions for performance specifications are applied over the graphical models to evaluate the required W/L. Finally, the performance parameters such as DC gain UGB are verified through simulation. This design is implemented using Synopsys Custom Compiler as a part of Cloud Based Analog IC Design Hackathon.
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
    <img src="https://user-images.githubusercontent.com/93975942/155971782-c46ab4ab-0c60-49b3-a93a-752fc9e5ad99.png">
</p>

<p align="center">
        Fig. 3. Normalized drain current (I<sub>d</sub>/W) w.r.t (g<sub>m</sub>/I<sub>d</sub>)
</p>

<p align="justify">
In similar manner, the W&L values of p-type MOSFET current mirror load are also obtained. Finally, to fix the biasing current (I<sub>d</sub>) through the OTA, a reference current (I<sub>ref</sub>) of 20µA was chosen. The biasing circuit (M6) shown in Fig. 1 mirrors the current to M5 transistor. To get I<sub>d</sub> = 100µA, the W/L ratio of M5 transistor should be five times to that of M6 transistor.  Finally, the OTA is simulated under a supply voltage of 1.8 V (Vdd = 0.9 V, Vss = −0.9 V) with the transistor sizes as shown in Table 2.
</p>

Table 2 W and L values of MOSFETS
| Transistors       | L(µm)  | W (µm)   |
| :------------     |:------:| :------: |
| M<sub>1,2</sub>   | 2      | 60       |
| M<sub>3,4</sub>   | 3      | 104      |
| M<sub>5,6</sub>   | 0.03   | 0.1,0.5  |

<p align="justify">
The OTA is designed with the desired W and L specifications using Synopsys custom compiler tool by creating a libary in the Library manager. Fig. 4 and 5 shows the schematic view and symbol view of the OTA, repectively. The operating point of the OTA is verifed by obtaining the drain currents of all the MOSFETS of OTA through operating point analysis.    
</p>

<p align="center">
    <img src="https://user-images.githubusercontent.com/93975942/155974832-e21bb485-f3cc-4709-902b-af0eb00ebe1d.jpg">
</p>

<p align="center">
        Fig. 4. Schematic view of the OTA
</p>

<p align="center">
    <img src="https://user-images.githubusercontent.com/93975942/155974851-9d6fba7b-9843-4bb0-896d-2c01bab368e2.png">
</p>

<p align="center">
        Fig. 5. Symbol of the OTA
</p>

<p align="center">
    <img src="https://user-images.githubusercontent.com/93975942/155974620-7579c660-0c7b-4328-948d-c0f96a819cc2.jpg">
</p>

<p align="center">
        Fig. 6. Operating Point  Analysis depicting the drain currents flowing through the MOSFETs
</p>

# Simulation Results
<p align="justify">
The transient analysis is carried out using Synopsys Primewave tool to perform the functional verification of the designed OTA. Fig. 7 shows the testbench schematic for single ended input (only V1). Since, the input is applied only to non-inverting terminal of OTA, the output waveform shown in Fig. 8 is in same phase with the input. 
<p> 

<p align="center">
    <img src="https://user-images.githubusercontent.com/93975942/155991309-5ee8a228-a7d1-4536-a19d-cd3025c11d2c.png">
</p>

<p align="center">
        Fig. 7. Testbench for transient analysis with single ended input (only V1)
</p>

<p align="center">
    <img src="https://user-images.githubusercontent.com/93975942/155991265-38c24573-b3f4-4538-9a97-738e94c7414e.png">
</p>

<p align="center">
        Fig. 8. Transient analysis ouput with single ended input V1
</p>

<p align="justify">
Fig. 9 and 10 shows the testbench schematic for single ended input (only V2) and the corresponding output which has 1800 phase shift w.r.t input V2 since it is applied to inverting terminal of OTA. 
<p> 

<p align="center">
    <img src="https://user-images.githubusercontent.com/93975942/155991309-5ee8a228-a7d1-4536-a19d-cd3025c11d2c.png">
</p>

<p align="center">
        Fig. 9. Testbench for transient analysis with single ended input (only V2)
</p>

<p align="center">
    <img src="https://user-images.githubusercontent.com/93975942/155991265-38c24573-b3f4-4538-9a97-738e94c7414e.png">
</p>

<p align="center">
        Fig. 10. Transient analysis ouput with single ended input V2
</p>

<p align="justify">
    From the Fig. 8 and Fig. 10, it can be observed that for an input voltage of 10mV, the OTA amplifies the input signal to 120 mV. Thus, the open-loop gain obtained from the designed OTA is A<sub>v</sub> = V<sub>out</sub>/V<sub>in</sub> = 12. In dB scale, A<sub>v</sub>(dB) = 20*log(A<sub>v</sub>) = 22 dB. Similarly, Fig. 11 and 12 shows the testbench schematic and the output wave form for the case of differential input. If both the inputs V1 and V2 are applied then the phase of output depends on the differential input. If V1>V2 then the output is in same phase with V1, otherwise out of phase with V1. 
</p>

<p align="center">
    <img src="https://user-images.githubusercontent.com/93975942/155993909-02c30609-1b81-4c12-987c-17c81e50d019.png">
</p>

<p align="center">
        Fig. 11. Testbench for transient analysis with differential input (both V1 and V2)
</p>

<p align="center">
    <img src="https://user-images.githubusercontent.com/93975942/155993957-35a5b892-0456-4f4d-8a01-64369258f193.jpg">
</p>

<p align="center">
        Fig. 12. Transient analysis ouput with differential input (both V1 and V2)
</p>

<p align="justify">
From Fig. 12 it can be observed that, for a differential input (V1-V2) of 5mV, the ouput signal amplitude is ≈58mV which results a gain of 11.6. Thus, it can be seen that the gain of the amplifier is same as that of single ended inputs. To verify the UGB of the OTA, AC analysis is performed by sweeping the frequency of the signal form 10Hz to 10GHz. From the Ac analysis, the UGB of the OTA is found to be 29.3 MHz with the gain of 22dB. Fig. 13 and Fig. 14 shows the bode plot of the OTA deicting the obtained UGB and the open-loop gain, respectively. 
</p> 

<p align="center">
    <img src="https://user-images.githubusercontent.com/93975942/155997078-1b785721-f2c9-4de2-8d33-a248d957bb9e.jpg">
</p>

<p align="center">
        Fig. 11. Bode plot depicting the UGB of the single stage OTA
</p>

<p align="center">
    <img src="https://user-images.githubusercontent.com/93975942/155997310-db4e24e4-d56d-4be0-ac1d-27365a3e681a.jpg">
</p>

<p align="center">
        Fig. 12. Bode plot depicting the open-loop gain of the single stage OTA
</p>

# Netlist
The netlist of the simulated circuit can be found here: [netlist](https://github.com/Kasetty-Praveen-Kumar/Design-of-Single-Stage-OTA-using-28nm-CMOS-Technology/blob/main/Netlist.txt)

# Conclusion

# Acknowledgment

# REFERENCES
1.	R. U. Ahmed, E. A. Vijaykumar, and P. Saha, “Single-stage operational transconductance amplifier design in UTBSOI technology based on gm/id methodology,” ELECTRONICS, vol. 23, no. 2, 2019.
2.	M. N. Sabry, H. Omran, M. Dessouky, “Systematic design and optimization of operational transconductance amplifier using gm/Id design methodology,” Microelectronics Journal, vol. 75, pp. 87-96, 2018.
3.	C. Fendely, “CMOS exactly solvable chaotic oscillator,” M. S. thesis, Aurburn University, Alabama, Dec. 2019. Accessed on Feb 2022. [Online]. Available: https://etd.auburn.edu/bitstream/handle/10415/6966/CF_Thesis_FinalDraft.pdf?sequence=2. 
