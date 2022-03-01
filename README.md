# Design of 1-bit Full Adder using CMOS
This repository presents the design of 1-bit full adder implemented in 28nm CMOS technology using Synopsys Custom Compiler as a part of the cloud based analog IC design hackathon.

## Table of contents

## Introduction
Arithmetic operations are used extensively in most VLSI applications, such as digital signal processing, image and video processing, and microprocessors. The most widely utilised operations include addition, subtraction, multiplication, and multiply and accumulate (MAC). All of these modules are built around the 1-bit full-adder cell. 

## Full Adder
A full adder is a circuit that creates two outputs, a sum and a carry, by adding two single-bit binary values with a carry input [1]. The truth table of the full adder taken from [2] is listed in Fig. 1. The sum and carry_out signals of the full adder are defined as the following two combinational Boolean functions of the three input variables A, B and C. <br/>
```
sum = A exor B exor C
carry_out = AB + AC + BC
```
A gate-level realization of these two functions is shown in Fig. 2 from [3]. Instead of realizing the two functions separately, the sum output is generated using the carry out signal. As a result of this implementation, the circuit complexity will be reduced, and chip space will be saved.

Fig. 1.	 Truth table of full-adder

Fig. 2.	Gate-level schematic of the 1-bit full adder circuit

## Reference circuit design
Fig. 3 shows the transistor-level design of the CMOS 1-bit full adder circuit from [3]. The circuit is realized in conventional CMOS design style using a total of 28 MOSFET transistors consisting of 14 NMOS and 14 PMOS transistors. The advantage of complementary CMOS style is its robustness against voltage scaling and transistor sizing, which are essential to provide reliable operation at low voltage with arbitrary transistor sizes [4].

Fig. 3.	Transistor level schematic of 1-bit full-adder using CMOS

## Reference waveform
The input and output voltage waveforms of the 1-bit CMOS full adder are shown Fig. 4 from [3].

Fig. 4.	Input and output waveforms of CMOS 1-bit full-adder circuit

## Tools used
- Synopsys Custom Compiler - The Synopsys Custom Compiler™ design environment is a modern solution for full-custom analog, custom digital, and mixed-signal IC design. As the heart of the Synopsys Custom Design Platform, Custom Compiler provides design entry, simulation management and analysis, and custom layout editing features. This tool was used to design the circuit on a transistor level.

- Synopsys PrimeWave - PrimeWave™ Design Environment is a comprehensive and flexible environment for simulation setup and analysis of analog, RF, mixed-signal design, custom-digital and memory designs within the Synopsys Custom Design Platform. This tool helped in various types of simulations of the above designed circuit.

- Synopsys 28nm PDK - The Synopsys 28nm Process Design Kit (PDK) was used in creation and simulation of the above designed circuit.

## Schematics Implementation of Full Adder

Fig. 5. 1-bit full-adder schematic design

Fig. 6. Symbol created for 1-bit full adder

Fig. 5 shows the implementation of 1-bit full adder circuit in the Synopsys Custom Complier. The transistor level schematic consists of 28 MOSFET transistors out of which 28 are NMOS-4T transistors and the other 28 are PMOS-4T transistors. Three input pins have been used for the inputs A, B and C. VDD and GND pins are also input pins. Two output pins are used for the outputs Sum and Carry_out. Fig. 6 shows the symbol created for the 1-bit full adder from the schematic. Table1 shows the transistor sizing of each transistor used in the design.

Fig. 7. Transistor sizing of 1-bit full adder

Table 1. Width and length of each transistor

Fig. 8. Testbench circuit of 1-bit full adder

Fig. 8 shows the testbench circuit created for the simulation of 1-bit full adder. The VDD pin is connected to a DC voltage of 0.9V.  The input pins A, B and C are connected to vpulse whose parameters are given in table []. The output pins Sum and Carry_out are connected to capacitive load of 1pF. 

## Transient Analysis

Fig. 9. Test suite window of transient analysis using PrimeWave

Transient analysis is performed for the simulation of 1-bit full adder using PrimeWave. The SAED 32nm PDK is chosen as model file and the section is TT. The stop time for the simulation is set to 4 µs with a time step of 0.5 µs. Fig. 10 shows the waveform obtained which depicts the voltage of inputs A, B, C and outputs Carry_out and Sum over a period of 4 µs.

Fig. 10. Resultant waveform of 1-bit full adder

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


