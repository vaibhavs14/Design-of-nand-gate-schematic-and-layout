# Design-of-nand-gate-schematic-and-layout
---
This project contains the design of an CMOS nand gate and representing it in the form of schematic and layout design. We can see the working of an nand gate with respect to the input applied and their output which can be represented in the form of waveforms. The design will utilize the models that are present in __skywater 130nm pdk__ and various open source tools such as, __Xschem__, __NGSPICE__, __MAGIC__, __Netgen__, etc.

Let's get right into it.

![gatenand](https://github.com/user-attachments/assets/0def82a9-9c16-455a-a6b2-86428f18377e)

---
## Contents
- [1. Schematic representation](#1-Schematic-representation)
- [2. Layout representation](#2-Layout-representation)

## 1. Schemactic representation

A CMOS NAND gate is a logic gate that implements the logical NAND operation. It has two inputs and one output. The output is high (logic 1) only when both inputs are low (logic 0) or either of the inputs are low (logic 0) or high (high 1). Otherwise, the output is low (logic 0).

A CMOS NAND gate is constructed using a network of NMOS and PMOS transistors. The NMOS transistor is connected between the power supply (VDD) and the output, while the PMOS transistor is connected between the ground (VSS) and the output. The inputs are connected to the gates of both transistors.

![col1](https://github.com/user-attachments/assets/5474ef6f-1792-474a-9a77-e0c8d29f46a3)

For our design we have used the components that was available in the sky130pdk:<br>
```nfet_01v8.sym``` - from xschem_sky130 library<br>
```pfet_01v8.sym``` - from xschem_sky130 library<br>
```parac_0.2pF.sym``` - xschem_sky130 library<br>
```vsource.sym``` - from xschem devices library<br>
```code_shown.sym``` - from xschem devices library<br>

Operation:
* Both inputs are low: The NMOS transistors is turned **OFF**, and the PMOS transistors is **ON**. This pulls the output to the high state (VDD).
* One of the inputs are high: Either of the nmos transistors gets turned **ON** depending upon which transistors get an input high (logic 1), this will not pull the output to the low state (VSS) since both the both nmos transitors are connected in series both needs to be turned **ON** for it to pull the output to low state (VSS). One of the nmos transitors will be turned **ON** due to the input low (logic 0) at the gate; this will pull the output to the high state (VDD). 
* Both inputs are high: The NMOS transistors are turned **ON**, pulling the output to the low state (VSS). The PMOS transistors will remains **OFF**.
The trutrh table representation is shown below:

| InputA  | InputB | Output | 
|---------|------- | ------ |
|    0    |    0   |    1   | 
|    0    |    1   |    1   |
|    1    |    0   |    1   |
|    1    |    1   |    0   |

Below is the waveforms that can re used to analyze the output logic values for differnt inputs

![vin_vout_ for_nand_gate](https://github.com/user-attachments/assets/37c9129e-d9ee-4f98-bc52-44cbfb283751)

From the above waveforms that is generated with the help of open source tool Ngspice we can observe the following logics. When the both the inputs are low (logic 0) and either of the inputs are low (logic 0) or high (logic 1) we can observe the output to be high (logic 1) and only when both the inputs are high (logic 1) the output goes to low (logic 0).

There are advantages with the cmos nand gate design:
* In the off state, when both transistors are off, leads to minimal leakage current which helps in low static power consumption.
* The complementary structure of NMOS and PMOS transistors enables fast switching between high and low states.
* The complementary structure provides good noise immunity.
* CMOS technology is highly scalable, allowing for the fabrication of complex integrated circuits with millions of transistors.

An observation can be made from the schematic that we have designd; we have used the width ratio of the **pmos** in the pull network to be double ( _in our case it is 3.5 times bigger than **nmos**, since it is the ideal size which was proved from the previous analyis of our CMOS inverter_) than the width of **nmos** in pull down network. The primary reason for making the **PMOS** transistor in a CMOS inverter 2-3 times larger than the **NMOS** transistor is to **balance the rise and fall times** of the output signal.
When the input is high, the **NMOS** transistor turns on and pulls the output to ground. When the input is low, the **PMOS** transistor turns on and pulls the output to VDD. By making the PMOS transistor larger, it can drive the output to VDD more quickly, compensating for the NMOS transistor's slower pull-down speed. This balanced switching helps to ensure that the output transitions between high and low states in a symmetrical manner, which is important for proper circuit operation. And also one more parameter affecting the transistors is the mobility of the charge carries. The mobility of holes in **pmos** is less than the mobility of electrons **nmos**.

---

## 2. Layout representation

We have seen the representation of the CMOS nand gate in the form of the schematic from **xschem** and waveforms derived for the given inputs from **ngspice** in the above section. Now we can represent the same nand gate in the form of an layout. Layout design defines the physical arrangement of components and interconnections on the silicon substrate. It's the blueprint that guides the fabrication process. A schematic design alone cannot be directly used to manufacture a chip.
We have used the layout specification that was avaialble from the open source sky water sky130 PDK to design the layout of our nand gate. Here the ratio of the **pmos to nmos** is taken as **2:1**. Open source tool **magic** is used as layout editor to create our layout reprsentation of nand gate.

![col2](https://github.com/user-attachments/assets/5096747c-ce2e-4357-b5bb-c3d5ececb45c)



