# VERILOG-IMPLEMENTATION-OF-BASIC-RISC-V-32-I-SINGLE-CYCLE
Verilog implementation of a basic RV32I single-cycle processor based on the RISC-V International ISA. Implements core instruction types (R, I, S, B, U, J) with modular datapath and control unit design. Designed for FPGA synthesis and educational CPU architecture learning.
The processor is organized in a modular hierarchical structure:
top
 └── data_path
      ├── pc_gen
      ├── ins_mem
      ├── imm_gen
      ├── control_unit
      ├── register_file
      ├── alu_control
      ├── alu
      └── data_mem
🔹 1. top.v

Top-level module

Instantiates the data_path

Connects clock and reset

🔹 2. data_path.v

Core processor integration module

Connects PC, IMEM, Register File, ALU, Control Unit, and Data Memory

Handles instruction execution flow

🔹 3. pc_gen.v

Program Counter generator

Handles:

Sequential PC increment (PC + 4)

Branch instructions (BEQ, BNE, BLT, BGE)

Jump instructions (JAL)

🔹 4. ins_mem.v

Instruction Memory (ROM)

Stores program instructions

Addressed using PC

🔹 5. imm_gen.v

Immediate Generator

Extracts and sign-extends:

I-type

S-type

B-type

U-type

J-type immediates

🔹 6. control_unit.v

Main Control Unit

Decodes opcode

Generates control signals:

RegWrite

MemRead

MemWrite

ALUSrc

MemtoReg

Branch

Jump

🔹 7. register_file.v

32 × 32-bit register file

2 read ports

1 write port

x0 is hardwired to 0

🔹 8. alu_control.v

Generates ALU control signals

Uses funct3, funct7, and ALUOp from control unit

🔹 9. alu.v

32-bit Arithmetic Logic Unit

Performs:

ADD / SUB

AND / OR / XOR

SLT

Shift operations

🔹 10. data_mem.v

Data Memory (RAM)

Used for:

Load (LW)

Store (SW)

✅ Supported RV32I Instructions

R-Type: ADD, SUB, AND, OR, XOR, SLT

I-Type: ADDI, ANDI, ORI, LW

S-Type: SW

B-Type: BEQ, BNE, BLT, BGE

U-Type: LUI, AUIPC

J-Type: JAL

🎯 Key Learning Outcomes

Understanding RISC-V datapath design

Instruction decoding logic

ALU and memory interfacing

Branch and jump control flow

Single-cycle CPU architecture design

🔮 Future Improvements

5-stage pipeline implementation

Hazard detection and forwarding

RV32M extension

CSR support

Cache integration
