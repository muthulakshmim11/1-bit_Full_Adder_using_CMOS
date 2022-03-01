# Design of 1-bit Full Adder using CMOS
This repository presents the design of 1-bit full adder implemented in 28nm CMOS technology using Synopsys Custom Compiler as a part of the cloud based analog IC design hackathon.

## Table of contents
- [Introduction](#introduction)
- [Full Adder](#full-adder)
- [Reference Circuit Design](#reference-circuit-design)
- [Reference Waveform](#reference-waveform)
- [Tools Used](#tools-used)
- [Schematics Implementation of Full Adder](#schematics-implementation-of-full-adder)
- [Transient Analysis](#transient-analysis)
- [Netlist](#netlist)
- [Conclusion](#conclusion)
- [Author](#author)
- [Acknowledgments](#acknowledgments)
- [References](#references)


## Introduction
Arithmetic operations are used extensively in most VLSI applications, such as digital signal processing, image and video processing, and microprocessors. The most widely utilised operations include addition, subtraction, multiplication, and multiply and accumulate (MAC). All of these modules are built around the 1-bit full-adder cell. 

## Full Adder
A full adder is a circuit that creates two outputs, a sum and a carry, by adding two single-bit binary values with a carry input [1]. The truth table of the full adder taken from [2] is listed in Fig. 1. The sum and carry_out signals of the full adder are defined as the following two combinational Boolean functions of the three input variables A, B and C. <br/>
```
sum = A exor B exor C
carry_out = AB + AC + BC
```
A gate-level realization of these two functions is shown in Fig. 2 from [3]. Instead of realizing the two functions separately, the sum output is generated using the carry out signal. As a result of this implementation, the circuit complexity will be reduced, and chip space will be saved.
<p align="center">
  <img 
    src="https://user-images.githubusercontent.com/100487608/156110568-1f0a99a7-9d34-44fb-bbf4-60864b1b3b9e.png"
  >
  <br/>Fig. 1.	 Truth table of full-adder
</p>

<p align="center">
  <img 
    src="https://user-images.githubusercontent.com/100487608/156186959-38a64265-614a-4460-bbf8-8d6c6c790197.png"
       width="700"
       height="300"
  >
  <br/>Fig. 2.	Gate-level schematic of the 1-bit full adder circuit
</p>


## Reference Circuit Design
Fig. 3 shows the transistor-level design of the CMOS 1-bit full adder circuit from [3]. The circuit is realized in conventional CMOS design style using a total of 28 MOSFET transistors consisting of 14 NMOS and 14 PMOS transistors. The advantage of complementary CMOS style is its robustness against voltage scaling and transistor sizing, which are essential to provide reliable operation at low voltage with arbitrary transistor sizes [4].

<p align="center">
  <img 
    src="https://user-images.githubusercontent.com/100487608/156110593-b2733c4b-e2e7-4374-969a-d4d7f5654069.png"
  >
  <br/>Fig. 3.	Transistor level schematic of 1-bit full-adder using CMOS
</p>


## Reference Waveform
The input and output voltage waveforms of the 1-bit CMOS full adder are shown Fig. 4 from [3].

<p align="center">
  <img 
    src="https://user-images.githubusercontent.com/100487608/156110602-14fe9cf7-f68f-405c-8fda-2627b0fdff4e.png"
  >
  <br/>Fig. 4.	Input and output waveforms of CMOS 1-bit full-adder circuit
</p>


## Tools Used
- Synopsys Custom Compiler - The Synopsys Custom Compiler™ design environment is a modern solution for full-custom analog, custom digital, and mixed-signal IC design. As the heart of the Synopsys Custom Design Platform, Custom Compiler provides design entry, simulation management and analysis, and custom layout editing features. This tool is used to design the transistor level circuit.

- Synopsys PrimeWave - PrimeWave™ Design Environment is a comprehensive and flexible environment for simulation setup and analysis of analog, RF, mixed-signal design, custom-digital and memory designs within the Synopsys Custom Design Platform. This tool helped in simulation of transient analysis of the design.

- Synopsys 32/28nm PDK - The Synopsys 32/28nm Process Design Kit (PDK) is used for the implementation of the circuit.

## Schematics Implementation of Full Adder

<p align="center">
  <img 
    src="https://user-images.githubusercontent.com/100487608/156110610-13dbfd5f-63d8-4a66-ba19-a83aa74bcd9a.png"
  >
  <br/>Fig. 5. 1-bit full-adder schematic design<br/>
</p>


<p align="center">
  <img 
    src="https://user-images.githubusercontent.com/100487608/156110619-45b92053-d703-4f8d-8a2d-09866010ebb5.png"
  >
  <br/>Fig. 6. Symbol created for 1-bit full adder
</p>


Fig. 5 shows the implementation of 1-bit full adder circuit in the Synopsys Custom Complier. The transistor level schematic consists of 28 MOSFET transistors out of which 28 are NMOS-4T transistors and the other 28 are PMOS-4T transistors. The transistors are taken from SAED_PDK_32_28 library. Three input pins have been used for the inputs A, B and C. VDD and GND pins are also input pins. Two output pins are used for the outputs Sum and Carry_out. Fig. 6 shows the symbol created for the 1-bit full adder from the schematic. Table 1 shows the transistor sizing of each transistor used in the design.

<p align="center">
  <img 
    src="https://user-images.githubusercontent.com/100487608/156122503-1b1d903f-8338-4f56-98b6-071a618a7909.png"
  >
  <br/>Fig. 7. Transistor sizing of 1-bit full adder
</p>


<div align="center">
  
| Transistors	| Length |	Width per finger |	Number of fingers |	Total width	| (W/L) |
| :---: | :---: | :---: | :---: | :---: | :---: |
| M1, M17	| 0.03 µm	| 0.1 µm	| 1	| 0.1 µm	| 0.1 µm/0.03 µm |
|M2, M18, M9, M10, M11, M12	| 0.03 µm	| 0.1 µm	| 2	| 0.2 µm	| 0.2 µm/0.03 µm |
|M3, M4, M5	| 0.03 µm	| 0.1 µm	| 3	| 0.3 µm	| 0.3 µm/0.03 µm |
|M13, M14, M15, M16, M19, M20, M21, M22, M23	| 0.03 µm	| 0.1 µm	| 4	| 0.4 µm	| 0.4 µm/0.03 µm |
|M6, M7, M8	| 0.03 µm	| 0.1 µm	| 6	| 0.6 µm	| 0.6 µm/0.03 µm |
|M24, M25, M26, M27, M28	| 0.03 µm	| 0.1 µm	| 8	| 0.8 µm	| 0.8 µm/0.03 µm |
  
</div>

<p align="center">
Table 1. Width and length of each transistor
</p>

<p align="center">
  <img 
    src="https://user-images.githubusercontent.com/100487608/156110626-2f7694d5-f9b1-47e9-9fa6-ec4aa414795c.png"
  >
  <br/> Fig. 8. Testbench circuit of 1-bit full adder
</p>


Fig. 8 shows the testbench circuit created for the simulation of 1-bit full adder. The VDD pin is connected to a DC voltage of 0.9V taken from analog library.  The input pins A, B and C are connected to vpulse whose parameters are given in table 2. the rise and fall time are set to 200 ps and the voltage is set to 0.9V. The output pins Sum and Carry_out are connected to capacitive load of 1pF. 


<div align="center">
  
| Parameters	| Input A |	Input B |	Input C |
| :---: | :---: | :---: | :---: | 
| DC Voltage	| 0 V	| 0 V	| 0 V |
| Voltage 1	| 0 V	| 0 V	| 0 V |
| Voltage 2	| 0.9 V	| 0.9 V	| 0.9 V |
| Delay time	| 0 s	| 0 s	| 0 s |
| Rise time	| 200 ps	| 200 ps	| 200 ps |
| Fall time	| 200 ps	| 200 ps	| 200 ps |
| Pulse width	| 2 µs	| 1 µs	| 0.5 µs |
| Period	| 4 µs	| 2 µs	| 1 µs |

</div>

<p align="center">
Table 2. Parameters of voltage inputs
</p>


## Transient Analysis

<p align="center">
  <img 
    src="https://user-images.githubusercontent.com/100487608/156110643-927b46fe-6f55-445c-9fe6-b80ac665213c.png"
  >
  <br/>Fig. 9. Test suite window of transient analysis using PrimeWave
</p>


Transient analysis is performed for the simulation of 1-bit full adder using PrimeWave. The SAED 32nm PDK is chosen as model file and the section is TT. The stop time for the simulation is set to 4 µs with a time step of 0.5 µs. Fig. 10 shows the waveform obtained which depicts the voltage of inputs A, B, C and outputs Carry_out and Sum over a period of 4 µs.

<p align="center">
  <img 
    src="https://user-images.githubusercontent.com/100487608/156193700-06ac399b-132d-47ae-a431-f9024edd78aa.png"
  >
  <br/>Fig. 10. Resultant waveform of 1-bit full adder
</p>

## Netlist
```
*  Generated for: PrimeSim
*  Design library name: muthulakshmi_lib
*  Design cell name: mm_1b_FullAdder_tb
*  Design view name: schematic
.lib 'saed32nm.lib' TT

*Custom Compiler Version S-2021.09
*Tue Mar  1 14:01:35 2022

.global gnd!
********************************************************************************
* Library          : muthulakshmi_lib
* Cell             : mm_1b_FullAdder
* View             : schematic
* View Search List : hspice hspiceD schematic spice veriloga
* View Stop List   : hspice hspiceD
********************************************************************************
.subckt mm_1b_fulladder a b c carry_out gnd_1 sum vdd
xm98 net238 b vdd vdd p105 w=0.8u l=0.03u nf=8 m=1
xm74 sum net218 vdd vdd p105 w=0.2u l=0.03u nf=2 m=1
xm82 net174 b vdd vdd p105 w=0.8u l=0.03u nf=8 m=1
xm73 carry_out net234 vdd vdd p105 w=0.2u l=0.03u nf=2 m=1
xm81 net174 a vdd vdd p105 w=0.8u l=0.03u nf=8 m=1
xm80 net234 c net174 vdd p105 w=0.8u l=0.03u nf=8 m=1
xm97 net234 a net238 vdd p105 w=0.8u l=0.03u nf=8 m=1
xm96 net226 c vdd vdd p105 w=0.4u l=0.03u nf=4 m=1
xm95 net226 b vdd vdd p105 w=0.4u l=0.03u nf=4 m=1
xm94 net226 a vdd vdd p105 w=0.4u l=0.03u nf=4 m=1
xm93 net218 net234 net226 vdd p105 w=0.4u l=0.03u nf=4 m=1
xm91 net210 b net214 vdd p105 w=0.6u l=0.03u nf=6 m=1
xm90 net218 a net210 vdd p105 w=0.6u l=0.03u nf=6 m=1
xm92 net214 c vdd vdd p105 w=0.6u l=0.03u nf=6 m=1
xm85 net218 a net186 gnd_1 n105 w=0.3u l=0.03u nf=3 m=1
xm84 net186 b net182 gnd_1 n105 w=0.3u l=0.03u nf=3 m=1
xm83 net182 c gnd_1 gnd_1 n105 w=0.3u l=0.03u nf=3 m=1
xm71 carry_out net234 gnd_1 gnd_1 n105 w=0.1u l=0.03u nf=1 m=1
xm77 net156 a gnd_1 gnd_1 n105 w=0.4u l=0.03u nf=4 m=1
xm76 net234 a net150 gnd_1 n105 w=0.4u l=0.03u nf=4 m=1
xm72 sum net218 gnd_1 gnd_1 n105 w=0.1u l=0.03u nf=1 m=1
xm79 net234 c net156 gnd_1 n105 w=0.4u l=0.03u nf=4 m=1
xm75 net150 b gnd_1 gnd_1 n105 w=0.4u l=0.03u nf=4 m=1
xm78 net156 b gnd_1 gnd_1 n105 w=0.4u l=0.03u nf=4 m=1
xm89 net218 net234 net196 gnd_1 n105 w=0.2u l=0.03u nf=2 m=1
xm88 net196 a gnd_1 gnd_1 n105 w=0.2u l=0.03u nf=2 m=1
xm87 net196 b gnd_1 gnd_1 n105 w=0.2u l=0.03u nf=2 m=1
xm86 net196 c gnd_1 gnd_1 n105 w=0.2u l=0.03u nf=2 m=1
.ends mm_1b_fulladder

********************************************************************************
* Library          : muthulakshmi_lib
* Cell             : mm_1b_FullAdder_tb
* View             : schematic
* View Search List : hspice hspiceD schematic spice veriloga
* View Stop List   : hspice hspiceD
********************************************************************************
xi0 a b c carry_out gnd! sum net23 mm_1b_fulladder
v1 net23 gnd! dc=0.9
c3 sum gnd! c=1p
c2 carry_out gnd! c=1p
v6 a gnd! dc=0 pulse ( 0 0.9 0 200p 200p 2u 4u )
v5 b gnd! dc=0 pulse ( 0 0.9 0 200p 200p 1u 2u )
v4 c gnd! dc=0 pulse ( 0 0.9 0 200p 200p 0.5u 1u )


.tran '0.5u' '4u' name=tran

.option primesim_remove_probe_prefix = 0
.probe v(*) i(*) level=1
.probe tran v(a) v(b) v(c) v(carry_out) v(sum)

.temp 25

.option primesim_output=wdf

.option parhier = LOCAL


.end
```


## Conclusion

Thus, 1-bit full adder has been designed and implemented in 28nm CMOS technology using Synopsys Custom Compiler. The functionality of the design has been verified using waveforms obtained from transient analysis by PrimeWave simulation.

## Author

Muthulakshmi M, B. E. (ECE), Thiagarajar College of Engineering, Madurai - 625015.

## Acknowledgments

1.	[Synopsys India](https://www.synopsys.com/)
2.	[Cloud Based Analog IC Design Hackathon](https://www.iith.ac.in/events/2022/02/15/Cloud-Based-Analog-IC-Design-Hackathon/)
3.	[VLSI Custom Design (VSD) Corp. Pvt. Ltd India](https://www.vlsisystemdesign.com/)
4.	Kunal Ghosh, Co-founder, VSD Corp. Pvt. Ltd. - kunalpghosh@gmail.com
5.	Chinmay panda, IIT Hyderabad
6.	Sameer Durgoji, NIT Karnataka

## References

1. Yogita Hiremath, Akalpita L. Kulkarni, Dr. J. S. Baligar, “Design and Implementation of Ripple Carry Adder using area efficient full adder cell in 180nm CMOS Technology”, International Journal of Science, Engineering and Technology Research (IJSETR), Volume 3, Issue 5, May 2014.<br/>
2.	M. Morris Mano and Michael D. Ciletti, “Digital Design: With an Introduction to Verilog HDL”, 5th ed., January 2013.<br/>
3.	Sung-Mo Kang and Yusuf Leblebici , “CMOS Digital Integrated Circuits Analysis & Design”, 3rd ed., December 2002.<br/>
4.	Subodh Wairya, Rajendra Kumar Nagaria, Sudarshan Tiwari, "Performance Analysis of High Speed Hybrid CMOS Full Adder Circuits for Low Voltage VLSI Design", VLSI Design, vol. 2012, Article ID 173079, 18 pages, 2012.
