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
    src="https://user-images.githubusercontent.com/100487608/156110589-50051fab-167f-4a30-abca-e396cb9edde7.png"
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
- Synopsys Custom Compiler - The Synopsys Custom Compiler™ design environment is a modern solution for full-custom analog, custom digital, and mixed-signal IC design. As the heart of the Synopsys Custom Design Platform, Custom Compiler provides design entry, simulation management and analysis, and custom layout editing features. This tool was used to design the circuit on a transistor level.

- Synopsys PrimeWave - PrimeWave™ Design Environment is a comprehensive and flexible environment for simulation setup and analysis of analog, RF, mixed-signal design, custom-digital and memory designs within the Synopsys Custom Design Platform. This tool helped in various types of simulations of the above designed circuit.

- Synopsys 28nm PDK - The Synopsys 28nm Process Design Kit (PDK) was used in creation and simulation of the above designed circuit.

## Schematics Implementation of Full Adder

<p align="center">
  <img 
    src="https://user-images.githubusercontent.com/100487608/156110610-13dbfd5f-63d8-4a66-ba19-a83aa74bcd9a.png"
  >
  <br/>Fig. 5. 1-bit full-adder schematic design
</p>


<p align="center">
  <img 
    src="https://user-images.githubusercontent.com/100487608/156110619-45b92053-d703-4f8d-8a2d-09866010ebb5.png"
  >
  <br/>Fig. 6. Symbol created for 1-bit full adder
</p>


Fig. 5 shows the implementation of 1-bit full adder circuit in the Synopsys Custom Complier. The transistor level schematic consists of 28 MOSFET transistors out of which 28 are NMOS-4T transistors and the other 28 are PMOS-4T transistors. Three input pins have been used for the inputs A, B and C. VDD and GND pins are also input pins. Two output pins are used for the outputs Sum and Carry_out. Fig. 6 shows the symbol created for the 1-bit full adder from the schematic. Table1 shows the transistor sizing of each transistor used in the design.

<p align="center">
  <img 
    src="https://user-images.githubusercontent.com/100487608/156122503-1b1d903f-8338-4f56-98b6-071a618a7909.png"
  >
  <br/>Fig. 7. Transistor sizing of 1-bit full adder
</p>

<p align="center">
  
| Transistors	| Length |	Width per finger |	Number of fingers |	Total width	| (W/L) |
| :---: | :---: | :---: | :---: | :---: | :---: |
| M1, M17	| 0.03 µm	| 0.1 µm	| 1	| 0.1 µm	| 0.1 µm/0.03 µm |
|M2, M18, M9, M10, M11, M12	| 0.03 µm	| 0.1 µm	| 2	| 0.2 µm	| 0.2 µm/0.03 µm |
|M3, M4, M5	| 0.03 µm	| 0.1 µm	| 3	| 0.3 µm	| 0.3 µm/0.03 µm |
|M13, M14, M15, M16, M19, M20, M21, M22, M23	| 0.03 µm	| 0.1 µm	| 4	| 0.4 µm	| 0.4 µm/0.03 µm |
|M6, M7, M8	| 0.03 µm	| 0.1 µm	| 6	| 0.6 µm	| 0.6 µm/0.03 µm |
|M24, M25, M26, M27, M28	| 0.03 µm	| 0.1 µm	| 8	| 0.8 µm	| 0.8 µm/0.03 µm |

Table 1. Width and length of each transistor

</p>

<p align="center">
  <img 
    src="https://user-images.githubusercontent.com/100487608/156110626-2f7694d5-f9b1-47e9-9fa6-ec4aa414795c.png"
  >
  <br/>Fig. 8. Testbench circuit of 1-bit full adder
</p>


Fig. 8 shows the testbench circuit created for the simulation of 1-bit full adder. The VDD pin is connected to a DC voltage of 0.9V.  The input pins A, B and C are connected to vpulse whose parameters are given in table 2. The output pins Sum and Carry_out are connected to capacitive load of 1pF. 

<p align="center">
  
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
    src="https://user-images.githubusercontent.com/100487608/156110653-27f66b55-3536-4cc8-b898-35af83308021.png"
  >
  <br/>Fig. 10. Resultant waveform of 1-bit full adder
</p>


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
