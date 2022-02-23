# Design and Implementation of Combinational Logic Based Electronic Buzzer Circuit using CMOS
This repository contains the design for a CMOS digital combinational logic based electronic buzzer circuit that selects the output basedon  the relative time of application of input, implemented using Synopsys Custom Compiler on 28nm CMOS technology


# Table of Contents
   * [Abstract](#abstract)
  * [Reference Circuit Details](#reference-circuit-details)
  * [Reference Circuit Diagram](#reference-circuit-diagram)
  * [Reference Circuit Waveform](#reference-circuit-waveform)
- [Simulation in Synopsys](#simulation-in-synopsys)
  * [Schematic](#schematic)
  * [Symbol](#symbol)
  * [Parameters set for Pulse Voltage Source for VIN](#parameters-set-for-pulse-voltage-source-for-vin)
  * [Parameters set for DC Voltage Source for VDDL](#parameters-set-for-dc-voltage-source-for-vddl)
  * [Parameters set for DC Voltage Source for VDDH](#parameters-set-for-dc-voltage-source-for-vddh)
  * [Parameters set for DC Voltage Source for Vbias](#parameters-set-for-dc-voltage-source-for-vbias)
  * [Transient Settings](#transient-settings)
  * [Netlist](#netlist)
  * [Waveform](#waveform)
  * [Conclusion](#conclusion)
  * [Acknowledgement](#acknowlegement)
  * [References](#references)


## Abstract

Design for a CMOS digital combinational logicbased electronic buzzer circuit that selects the output based
on the relative time of application of input. There are three
independent digital input points, corresponding to which there
are three outputs. The output corresponding to the first applied
input becomes high from an initial low state and remains stable
at that state, unaffected by any change in input signals from the
other two input points. The output returns to its initial low state
only when the first input signal is removed. The circuit is purely
combinational as the outputs are independent of any clock signal. [1]

## Reference Circuit Details

The electronic buzzer circuit selects the output corresponding to the the input applied first. The other two inputs become
don’t cares, and do not affect the output until the first input
signal becomes low again. The proposed circuit utilizes the
properties of ’D-type Latch’, also called transparent latch,
without using the enable. The latch circuit composed of NOR
gates and NOT gates, is slightly modified to meet the design
requirements.
Fig. 3 represents the digital combinational logic design of
the circuit using NOR and NOT gates. Fig. 1 and Fig. 2
represent the NOR and NOT gates using CMOS circuit which
is comprised of two parts - the pull-up lattice composed of
PMOS circuit and the pull-down lattice composed of NMOS
circuit. PMOS circuit is connected to supply voltage VDD
and NMOS circuit is connected to Ground terminal. Fig. 4
represents the various output waveforms. The inputs are taken
as A, B and C with outputs as Q1, Q2 and Q3 corresponding
to the respective inputs.
Q1 = (A’+QA+B+C)’,
Q2 = (B’+QB+A+C)’,
Q3 = (C’+QC+A+B)’ [1]

## Reference Circuit Diagram
<p align="center">
<img src="Schematic_2.jpg"></br>
  Fig. 1:  Reference Combinational logic circuit design.
 <p align="center">
 <img src="NOT gate_2.jpg"></br>
  Fig. 2:  CMOS 2 input NOT Gate
 <p align="center">
 <img src="Nor gate_2.jpg"></br>
  Fig. 3:  CMOS 4 input NOR Gate
</p>

## Reference Circuit Waveforms
<p align="center">
<img src="Waveform-2_2 (1).jpg"></br>
  Fig. 4:  Waveforms
</p>

# Simulation in Synopsys
## Schematic
<p align="center">
<img src="Images/HV_Tolerant_LS_Schematic.png"></br>
  Fig. 5: 
</p>

## Symbol
<p align="center">
<img src="Images/HV_Tolerant_LS_Symbol.png"></br>
  Fig. 6: HV Tolerant Level shifter using Symbol reference 
</p>
Note: To make the CMOS Level circuit more compatible and Industry ready a Symbol reference has been created. So, it makes easy whenever a testbench of different Parameters needs to be tested.

## Parameters set for Pulse Voltage Source for VIN
<p align="center">
<img src="Images/VIN PARAMETERS.png"></br>
  Fig. 5: Pulse Voltage Source Input VIN set at 1.05V 
</p>

## Parameters set for DC Voltage Source for VDDL
<p align="center">
<img src="Images/VDDL PARAMETER SUPPLY.png"></br>
  Fig. 6: Low VDD Supply set for the Inverter connection in the Circuit set at 1.05V 
</p>

## Parameters set for DC Voltage Source for VDDH
<p align="center">
<img src="Images/VDDH PARAMETER SUPPLY.png"></br>
  Fig. 7: High Voltage Supply given at VDDH to check the Level Shift set at 3.3V 
</p>

## Parameters set for DC Voltage Source for Vbias
<p align="center">
<img src="Images/Vbias PARAMETER SUPPLY.png"></br>
  Fig. 8: The Voltage Limiter (V-limit) from the Circuit Vbias is set at 0.6V
</p>

## Transient Settings
<p align="center">
<img src="Images/TRANSIENT ANALYSIS INPUTS.png"></br>
  Fig. 9: The Transient Analysis inputs Run at 1us step with stop time 30us 
</p>

## Netlist
```
*  Generated for: PrimeSim
*  Design library name: sm_hvt_levelshifter
*  Design cell name: hvt_levelshifter_tb
*  Design view name: schematic
.lib 'saed32nm.lib' TT

*Custom Compiler Version S-2021.09
*Wed Feb 23 02:17:30 2022

.global gnd!
********************************************************************************
* Library          : sm_hvt_levelshifter
* Cell             : hvt_levelshifter
* View             : schematic
* View Search List : hspice hspiceD schematic spice veriloga
* View Stop List   : hspice hspiceD
********************************************************************************
.subckt hvt_levelshifter gnd_1 out vddh vddl vin
xm8 net85 net94 gnd_1 gnd_1 n105 w=0.1u l=0.03u nf=1 m=1
xm7 net83 vin gnd_1 gnd_1 n105 w=0.1u l=0.03u nf=1 m=1
xm6 net43 net44 net85 gnd_1 n105 w=0.1u l=0.03u nf=1 m=1
xm5 net39 net44 net83 gnd_1 n105 w=0.1u l=0.03u nf=1 m=1
xm4 out net103 net19 net44 n105 w=0.1u l=0.03u nf=1 m=1
xm3 net19 net51 net44 net44 n105 w=0.1u l=0.03u nf=1 m=1
xm2 net9 out net44 net44 n105 w=0.1u l=0.03u nf=1 m=1
xm1 net51 net63 net9 net44 n105 w=0.1u l=0.03u nf=1 m=1
xm0 net94 vin gnd_1 gnd_1 n105 w=0.1u l=0.03u nf=1 m=1
xm15 net63 net103 vddh vddh p105 w=0.1u l=0.03u nf=1 m=1
xm14 net103 net63 vddh vddh p105 w=0.1u l=0.03u nf=1 m=1
xm13 out net103 vddh vddh p105 w=0.1u l=0.03u nf=1 m=1
xm12 net51 net63 vddh vddh p105 w=0.1u l=0.03u nf=1 m=1
xm11 net94 vin vddl vddl p105 w=0.1u l=0.03u nf=1 m=1
xm10 net43 net44 net63 vddh p105 w=0.1u l=0.03u nf=1 m=1
xm9 net39 net44 net103 vddh p105 w=0.1u l=0.03u nf=1 m=1
vbias net44 gnd! dc=0.6
.ends hvt_levelshifter

********************************************************************************
* Library          : sm_hvt_levelshifter
* Cell             : hvt_levelshifter_tb
* View             : schematic
* View Search List : hspice hspiceD schematic spice veriloga
* View Stop List   : hspice hspiceD
********************************************************************************
xi0 gnd! out net8 net6 net10 hvt_levelshifter
v6 net8 gnd! dc=3.3
v5 net6 gnd! dc=1.05
v9 net10 gnd! dc=1.05 pulse ( 0 1.05 0 0.1u 0.1u 5u 10u )








.tran '1u' '30u' name=tran

.option primesim_remove_probe_prefix = 0
.probe v(*) i(*) level=1
.probe tran v(out) v(net10)

.temp 25



.option primesim_output=wdf


.option parhier = LOCAL






.end

```
## Waveform
<p align="center">
<img src="Images/HV_Tolerant_LS_Waveforms.png"></br>
  Fig. 10: High Voltage level shift for 1.05V VIN to 3.3V VDDH Supply 
</p>
<p align="center">
<img src="Images/PrimeSim Waveforms for HVTLS.png"></br>
  Fig. 11: Simulation waveforms evident for Level Shift Tolerating High Voltage 
</p>

## Conclusion
Thus, A HV-tolerant level shifter that shifts both digital levels from VDDH and Vbias = VSS to Vbias = VDD and ground, respectively, can easily be derived from the one shown in Fig. 3 Schematic using a complementary circuit topology. Such complementary level shifter can be useful when designing the shootthrough control circuit presented in some integrated dc–dc converters. is verified using 28nm Technology node of Synopsys.

## Acknowledgement
1. Kunal Ghosh, Co-founder, VSD Corp. Pvt. Ltd. - kunalpghosh@gmail.com
2. Chinmay panda, IIT Hyderabad
3. Sameer Durgoji, NIT Karnataka
## References
[1] Marcelino B. dos Santos, Member, IEEE “Level Shifters and DCVSL for a Low-Voltage CMOS 4.2-V Buck Converter”- 2008
[2] Yang Yintang “A high performance 90 nm CMOS SAR ADC with hybrid architecture.”- 2010



