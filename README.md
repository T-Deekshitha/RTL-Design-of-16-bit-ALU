This project presents the design and implementation of a 16-bit Arithmetic Logic Unit (ALU) in Verilog.
Verilog is a hardware description language(HDL) used for modeling electronic systems. 
The design involves creating individual modules for logical, arithmetic, and multiplication operations and integrating them into a single ALU module.
Simulation and synthesis demonstrate the functionality and correctness of the ALU design.

BLOCK DIAGRAM:

![ALU_schematic](https://github.com/user-attachments/assets/98f1abc7-be93-4a5d-a0cc-89b580f1cb3c)

A and B are 16 bit inputs (operands). OP is the input which represents operator. There are 3 combinational logic units for logical, arithmetic and multiplication operations.
Demuxes are used to route the input given to these units taking "OP" input as select line. A multiplexer is used to choose correct output from these blocks. In erilog code, mux and demux are written using case statement.

LOGICAL:
A behavioural code is used to perform logical operations like inverting, AND, OR, XOR, shifting and rotating etc using a case statement.

ARITHMETIC:
Four 4-bit ripple carry adders are used which run almost simultaneously. Four 4-bit carry look ahead adders are used to generate carry for these ripple carry adders. 
Ripple carry adders save area and Carry look ahead adders save time. As CLA is used only to generate carry, not much area is used here. And it saves much time by not keeping the ripple carry adders waiting for carry_in. 

First RCA gives 4-bit sum and first CLA generates carry_out (carry_in for next RCA). Then second RCA takes this carry as input and generates next 4 bit sum. In the same way second CLA generates carry_in for third RCA. Third and fourth RCAs and CLAs too work in this way. Hence delay and area are balanced.

MULTIPLIER:
A behavioural code is used with a for loop for multiplication.
