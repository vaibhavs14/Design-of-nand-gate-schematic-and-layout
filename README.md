# Design-of-nand-gate-schematic-and-layout
---
This project contains the design of an CMOS nand gate with representing it the form of schematic and layout design. We can see the working of an nand gate with respect to the input applied and their output which can be represented in the form of an waveforms. The design will utilize the models that are present in under the __skywater 130nm pdk__ and various open source tools such as, __Xschem__, __NGSPICE__, __MAGIC__, __Netgen__, etc.

Let's get right into it.

...image...

---
## Contents
- [1. Schemactic representation](#1-Schemactic-representation)
- [2. Layout representation](#2-Layout-representation)
-

## 1. Schemactic representation

A CMOS NAND gate is a logic gate that implements the logical NAND operation. It has two inputs and one output. The output is high (logic 1) only when both inputs are low (logic 0). Otherwise, the output is low (logic 0).

A CMOS NAND gate is constructed using a network of NMOS and PMOS transistors. The NMOS transistor is connected between the power supply (VDD) and the output, while the PMOS transistor is connected between the ground (VSS) and the output. The inputs are connected to the gates of both transistors.

![col1](https://github.com/user-attachments/assets/5474ef6f-1792-474a-9a77-e0c8d29f46a3)

Operation:
* Both inputs are low: The NMOS transistor is off, and the PMOS transistor is on. This pulls the output to the high state (VDD).
* One or both inputs are high: The NMOS transistor turns on, pulling the output to the low state (VSS). The PMOS transistor remains off.
The trutrh table representation is shown below:

| InputA  | InputB | Output | 
|---------|------- | ------ |
|    0    |    0   |    1   | 
|    0    |    1   |    1   |
|    1    |    0   |    1   |
|    1    |    1   |    0   |

