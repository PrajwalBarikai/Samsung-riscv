# Samsung RISC-V Program  

**RISC-V Talent Development Program**, powered by **Samsung Semiconductor India Research (SSIR)** in collaboration with **VLSI System Design (VSD)**.  

## Basic Details  
Name: Prajwal Hanamatraya Barikai 
College: Vidyavardhaka College of Engineering  
Email: prajwalhb26@gmail.com  

## Task 1: RISC-V Toolchain Installation 
- Installation of RISC-V toolchain using the VDI link provided.
- The program demonstrates basic operations in C and their equivalent implementation in RISC-V assembly language.


  ## Task 2: spike simulation and compiling c prigramming using RISC-V GCC 
1. Spike (RISC-V Instruction Set Architecture Simulator)
Spike is an emulator for the RISC-V ISA, often used to simulate and test RISC-V programs. It mimics the behavior of a RISC-V processor, allowing programs to run in a virtualized and controlled environment for development and debugging purposes.
2. -d Option (Debug Mode)
The -d option in Spike activates debug mode. This mode facilitates detailed program execution by enabling step-by-step inspection of the processor's state, including registers and memory, to help diagnose and resolve issues.
3. Proxy Kernel (pk)
The proxy kernel (pk) functions as a lightweight operating system within the RISC-V simulation. It manages system calls and supports the execution of programs in the simulated environment provided by Spike.
4. RISC-V Assembly Commands
addi sp, sp, -16 (Add Immediate):
This command subtracts 16 from the current value of the stack pointer (sp), effectively adjusting the stack pointer downwards.
lui a0, 0x21 (Load Upper Immediate):
This instruction loads the immediate value 0x31, shifted left by 12 bits, into the upper part of register a2


![task_2_1](https://github.com/user-attachments/assets/4ad8f00a-a6ed-4570-be38-f2573c35ba35)
![task_2_2](https://github.com/user-attachments/assets/88183eb2-85ca-4587-8f3d-ddc8136b1171)
Program for printing numbers till n
![task_2_7](https://github.com/user-attachments/assets/6cb44b43-5be1-49b9-92e5-de83c1bd8cff)
compiling the program 

![task_2_3](https://github.com/user-attachments/assets/71bc3177-9a16-4f72-a63f-6ce163d918d2)
compiling the program using -O1 and -Ofast
![task_2_4](https://github.com/user-attachments/assets/b183a518-2f73-4c9d-aa55-5bbc7acb89a2)
using -O1
![task_2_5](https://github.com/user-attachments/assets/b57ea834-8f66-4aba-910e-f085503fa072)
using -Ofast
![task_2_6](https://github.com/user-attachments/assets/98bc8fe0-f0b7-46f6-adfc-9a298578ad2c)


## Task 3:Understanding RISC-V and Its Instruction Formats
# what is RISK-V

1. RISC-V is an open-source Instruction Set Architecture (ISA) rooted in RISC principles, designed to optimize processors for specific applications.
2. As the fifth generation of RISC-based ISAs, RISC-V offers a flexible, free alternative to proprietary processor technologies.
3. With its open and license-free nature, RISC-V empowers developers to create customized processors without the burden of licensing fees.
4. RISC-V’s open-source model fosters innovation and broadens the hardware development ecosystem, making it a compelling choice for modern processor design.

# RISC-V Instruction Formats

- R-format
- I-format
- S-format
- B-format
- U-format
- J-format


![image](https://github.com/user-attachments/assets/3ecbf2b9-196d-49fe-ae26-acea3b4fa43f)


# R-type Instruction

R-type (Register-type) instructions perform operations on registers instead of memory locations, primarily used for arithmetic and logical tasks. Each instruction is 32 bits long and divided into six fields.

### Instruction Structure:

| Field Name | Size   | Description                          |
|------------|--------|--------------------------------------|
| **Opcode** | 7 bits | Specifies the instruction type      |
| **rd**     | 5 bits | Destination register                |
| **func3**  | 3 bits | Defines the operation type          |
| **rs1**    | 5 bits | First source register               |
| **rs2**    | 5 bits | Second source register              |
| **func7**  | 7 bits | Further operation specification     |

![image](https://github.com/user-attachments/assets/966fc04b-82c4-4c3d-9b1f-16cf4c51684e)


---

### Example: `ADD r9, r2, r5`
Operation: Adds values from registers r2 and r5, placing the result in r9.

#### Field Breakdown:

| Field Name   | Value      |
|--------------|------------|
| **Opcode**   | `0110011`  |
| **rd**       | r9 → `01001`|
| **rs1**      | r2 → `00010`|
| **rs2**      | r5 → `00101`|
| **func3**    | `000`      |
| **func7**    | `0000000`  |

**32-bit Instruction**: `0000000_00101_00010_000_01001_0110011`

# I-type Instruction

I-type (Immediate-type) instructions operate on an immediate value and a register. These instructions are commonly used for arithmetic, logical, and load operations. Each I-type instruction is 32 bits long and divided into six fields.

### Instruction Structure:

| Field Name | Size   | Description                          |
|------------|--------|--------------------------------------|
| **Opcode** | 7 bits | Specifies the instruction type      |
| **rd**     | 5 bits | Destination register                |
| **func3**  | 3 bits | Defines the operation type          |
| **rs1**    | 5 bits | Source register                     |
| **imm**    | 12 bits| Immediate value                     |

![image](https://github.com/user-attachments/assets/c4b6beb7-adbb-4843-aa96-eedbe8442e53)


---

### Example: `ADDI r10, r1, 5`
Operation: Adds an immediate value of 5 to the value in register r1 and stores the result in r10.

#### Field Breakdown:

| Field Name   | Value      |
|--------------|------------|
| **Opcode**   | `0010011`  |
| **rd**       | r10 → `01010`|
| **rs1**      | r1 → `00001`|
| **imm**      | 5 → `000000000101`|
| **func3**    | `000`      |

**32-bit Instruction**: `000000000101_00001_000_01010_0010011`

# S-type Instruction

S-type (Store-type) instructions are used for storing data from a register to a memory location. Each S-type instruction is 32 bits long and divided into six fields.

### Instruction Structure:

| Field Name | Size   | Description                          |
|------------|--------|--------------------------------------|
| **Opcode** | 7 bits | Specifies the instruction type      |
| **imm[4:0]**| 5 bits | Lower 5 bits of the immediate value |
| **func3**  | 3 bits | Defines the operation type          |
| **rs1**    | 5 bits | Source register (base address)      |
| **rs2**    | 5 bits | Source register (data to store)     |
| **imm[11:5]**| 7 bits | Upper 7 bits of the immediate value|

![image](https://github.com/user-attachments/assets/1521feb4-b0ba-4773-bb6b-c863ac24a67d)


---

### Example: `SW r2, 8(r1)`
Operation: Stores the value from register r2 into the memory address calculated by adding 8 to the value in register r1.

#### Field Breakdown:

| Field Name       | Value      |
|------------------|------------|
| **Opcode**       | `0100011`  |
| **imm[11:5]**    | 8 → `0000000`|
| **rs1**          | r1 → `00001`|
| **rs2**          | r2 → `00010`|
| **imm[4:0]**     | 8 → `01000` |
| **func3**        | `010`      |

**32-bit Instruction**: `0000000_00010_00001_010_01000_0100011`

# B-type Instruction

B-type (Branch-type) instructions are used for conditional branching in the program flow based on comparisons. Each B-type instruction is 32 bits long and divided into six fields.

### Instruction Structure:

| Field Name   | Size   | Description                           |
|--------------|--------|---------------------------------------|
| **Opcode**   | 7 bits | Specifies the instruction type        |
| **imm[12]**  | 1 bit  | 12th bit of the immediate value       |
| **imm[10:5]**| 6 bits | Bits 10 to 5 of the immediate value   |
| **func3**    | 3 bits | Defines the branch condition          |
| **rs1**      | 5 bits | First source register for comparison  |
| **rs2**      | 5 bits | Second source register for comparison |
| **imm[4:1]** | 4 bits | Bits 4 to 1 of the immediate value    |
| **imm[11]**  | 1 bit  | 11th bit of the immediate value       |

![image](https://github.com/user-attachments/assets/efe1d5f4-a2aa-4074-b607-00e66397376d)


---

### Example: `BEQ r1, r2, 16`
Operation: Branches to the address offset by 16 if the values in registers r1 and r2 are equal.

#### Field Breakdown:

| Field Name       | Value       |
|------------------|-------------|
| **Opcode**       | `1100011`   |
| **imm[12]**      | 16 → `0`    |
| **imm[10:5]**    | 16 → `000001`|
| **rs1**          | r1 → `00001`|
| **rs2**          | r2 → `00010`|
| **imm[4:1]**     | 16 → `0000` |
| **imm[11]**      | 16 → `1`    |
| **func3**        | `000`       |

**32-bit Instruction**: `000001_00010_00001_000_0000_1_1100011`

# U-type Instruction

U-type (Upper immediate-type) instructions are used to build large constants by shifting an immediate value into the upper bits of a register. Each U-type instruction is 32 bits long and divided into three fields.

### Instruction Structure:

| Field Name | Size   | Description                           |
|------------|--------|---------------------------------------|
| **Opcode** | 7 bits | Specifies the instruction type        |
| **rd**     | 5 bits | Destination register                  |
| **imm**    | 20 bits| Immediate value shifted to the upper  |

![image](https://github.com/user-attachments/assets/056829bb-c8d2-4261-8798-3ea46eddacbb)

---

### Example: `LUI r10, 0x12345`
Operation: Loads the upper 20 bits of the immediate value `0x12345` into register r10, with the lower 12 bits set to zero.

#### Field Breakdown:

| Field Name   | Value          |
|--------------|----------------|
| **Opcode**   | `0110111`      |
| **rd**       | r10 → `01010`  |
| **imm**      | `0x12345` → `00010010001101000101` |

**32-bit Instruction**: `00010010001101000101_01010_0110111`

# J-type Instruction

J-type (Jump-type) instructions are used for jumping to a specific address within a program. Each J-type instruction is 32 bits long and divided into four fields.

### Instruction Structure:

| Field Name   | Size   | Description                             |
|--------------|--------|-----------------------------------------|
| **Opcode**   | 7 bits | Specifies the instruction type          |
| **rd**       | 5 bits | Destination register                    |
| **imm[20]**  | 1 bit  | 20th bit of the immediate value         |
| **imm[10:1]**| 10 bits| Bits 10 to 1 of the immediate value     |
| **imm[11]**  | 1 bit  | 11th bit of the immediate value         |
| **imm[19:12]**| 8 bits| Bits 19 to 12 of the immediate value    |

![image](https://github.com/user-attachments/assets/2b13c9dc-8283-4426-a3bd-a88673e143ea)


![image](https://github.com/user-attachments/assets/b1898d8a-ec4e-42b7-bf34-2835a5c7f4bd)

---

### Example: `JAL r1, 1024`
Operation: Jumps to the address offset by 1024 and stores the return address in register r1.

#### Field Breakdown:

| Field Name       | Value          |
|------------------|----------------|
| **Opcode**       | `1101111`      |
| **rd**           | r1 → `00001`   |
| **imm[20]**      | 1024 → `0`     |
| **imm[10:1]**    | 1024 → `0000000000`|
| **imm[11]**      | 1024 → `0`     |
| **imm[19:12]**   | 1024 → `00000100`|

**32-bit Instruction**: `00000100_0_0000000000_0_00001_1101111`

# RISC-V Instruction Breakdown

This repository contains a detailed analysis and breakdown of RISC-V assembly instructions extracted from a disassembled object file. The goal is to help understand the RISC-V instruction set and their corresponding machine codes.

## Overview

The project dissects a given object file and identifies unique RISC-V instructions used in the disassembly. For each instruction, the following details are provided:

- Opcode
- Instruction Format
- Machine Code
- Instruction Binary Representation

## Object File Disassembly

Below is a breakdown of 15 unique RISC-V instructions found in the provided object file. For each instruction, you'll find the opcode, instruction format, machine code, and the binary representation of the instruction.

![objdump_file](https://github.com/user-attachments/assets/ed9efde1-0004-47b1-9915-514954c6737c)

### 1. lui (Load Upper Immediate)
- **Opcode:** 0x37
- **Format:** U-type
- **Machine Code:** 00021537
- **Instruction Binary:** 000000000010 001000 000 10111 0110111

### 2. addi (Add Immediate)
- **Opcode:** 0x13
- **Format:** I-type
- **Machine Code:** ff010113
- **Instruction Binary:** 111111110000 0001 000 00001 0011011

### 3. li (Load Immediate)
- **Opcode:** 0x13
- **Format:** I-type
- **Machine Code:** 00f00613
- **Instruction Binary:** 000000000000 0000 000 00011 0011011

### 4. sd (Store Doubleword)
- **Opcode:** 0x23
- **Format:** S-type
- **Machine Code:** 00113423
- **Instruction Binary:** 000000000001 0001 000 11000 0100011

### 5. jal (Jump and Link)
- **Opcode:** 0x6F
- **Format:** J-type
- **Machine Code:** 340000ef
- **Instruction Binary:** 000000110100 0000 000 00000 0110111

### 6. ld (Load Doubleword)
- **Opcode:** 0x03
- **Format:** I-type
- **Machine Code:** 00813083
- **Instruction Binary:** 000000000000 0001 000 01100 0000011

### 7. ret (Return)
- **Opcode:** 0x67
- **Format:** I-type
- **Machine Code:** 00008067
- **Instruction Binary:** 000000000000 0000 000 00000 1100111

### 8. beqz (Branch if Equal Zero)
- **Opcode:** 0x63
- **Format:** B-type
- **Machine Code:** 00078863
- **Instruction Binary:** 000000000000 0000 000 00111 1100011

### 9. auipc (Add Upper Immediate to PC)
- **Opcode:** 0x17
- **Format:** U-type
- **Machine Code:** ffff0797
- **Instruction Binary:** 111111111111 0000 000 00000 0010111

### 10. sub (Subtract)
- **Opcode:** 0x33
- **Format:** R-type
- **Machine Code:** 40a60633
- **Instruction Binary:** 000000000100 0000 000 00111 0110011

### 11. j (Jump)
- **Opcode:** 0x6F
- **Format:** J-type
- **Machine Code:** 0c00006f
- **Instruction Binary:** 000000000000 0000 000 00000 0110111

### 12. memset (Memory Set) (Function call, typically not a single instruction)
- **Opcode:** Special function (not directly a RISC-V instruction)
- **Machine Code:** 1d4000ef
- **Instruction Binary:** 000000000001 1100 000 00000 0110111

### 13. lw (Load Word)
- **Opcode:** 0x03
- **Format:** I-type
- **Machine Code:** 00012503
- **Instruction Binary:** 000000000000 0001 000 00000 0000011

### 14. jalr (Jump and Link Register)
- **Opcode:** 0x67
- **Format:** I-type
- **Machine Code:** 00810593
- **Instruction Binary:** 000000000000 0001 000 00000 1100111

### 15. lw (Load Word) (Repeated instruction)
- **Opcode:** 0x03
- **Format:** I-type
- **Machine Code:** 00810593
- **Instruction Binary:** 000000000000 0001 000 00000 0000011

## Task-4:Function simulation of RISC-V core
### perform Perform a functional simulation of the given RISC-V Core Verilog netlist and testbench.

# Functional Simulation of RISC-V (RV32I)

This guide provides steps to perform the functional simulation of a RISC-V processor using iverilog and GTKWave.

## Prerequisites

Ensure you are using **Ubuntu** to follow these steps.

## Steps to Perform Simulation

### 1. Install Required Tools
Open the terminal and enter the following commands to install `iverilog` and `GTKWave`:
```bash
sudo apt-get update
sudo apt-get install iverilog gtkwave
```

### 2. Clone the Repository
Clone the GitHub repository containing the netlist files for simulation and navigate to the directory:
```bash
git clone https://github.com/vinayrayapati/iiitb_rv32i
cd iiitb_rv32i
```

### 3. Create Verilog and Testbench Files
Create two files:
- A **Verilog file** for the RISC-V design.
- A **Testbench file** for testing.

### 4. Add Code
Copy the Verilog and Testbench code from the [GitHub Repository](https://github.com/vinayrayapati/iiitb_rv32i) and paste it into your respective files.

### 5. Run the Simulation
To compile and simulate the Verilog code, use the following commands:
```bash
iverilog -o iiitb_rv32i iiitb_rv32i.v iiitb_rv32i_tb.v
./iiitb_rv32i
```

### 6. View the Simulation Waveform
To view the waveform in GTKWave, run:
```bash
gtkwave iiitb_rv32i.vcd
```

## Output
The waveform for the simulation will be displayed in GTKWave, showcasing the functionality of the RISC-V processor.

---

For more details, visit the [GitHub Repository](https://github.com/vinayrayapati/iiitb_rv32i).


### Differences Between Standard RISC-V ISA and Hardcoded ISA

| **Operation**      | **Standard RISC-V ISA** | **Hardcoded ISA** |
|---------------------|-------------------------|-------------------|
| ADD R6, R2, R1      | `32'h00110333`         | `32'h02208300`    |
| SUB R7, R1, R2      | `32'h402083b3`         | `32'h02209380`    |
| AND R8, R1, R3      | `32'h0030f433`         | `32'h0230a400`    |
| OR R9, R2, R5       | `32'h005164b3`         | `32'h02513480`    |
| XOR R10, R1, R4     | `32'h0040c533`         | `32'h0240c500`    |
| SLT R1, R2, R4      | `32'h0045a0b3`         | `32'h02415580`    |
| ADDI R12, R4, 5     | `32'h004120b3`         | `32'h00520600`    |
| BEQ R0, R0, 15      | `32'h00000f63`         | `32'h00f00002`    |
| SW R3, R1, 2        | `32'h0030a123`         | `32'h00209181`    |
| LW R13, R1, 2       | `32'h0020a683`         | `32'h00208681`    |
| SRL R16, R14, R2    | `32'h0030a123`         | `32'h00271803`    |
| SLL R15, R1, R2     | `32'h002097b3`         | `32'h00208783`    |

### Analysing the Output Waveform of various instructions

### Instruction 1: ADD R6, R2, R1
![add](https://github.com/user-attachments/assets/0e33e885-f23e-4696-ae38-0431b7a333df)

### Instruction 2: AND R8, R1, R3
![and](https://github.com/user-attachments/assets/ff2cb943-0892-4ac7-b333-1ecbfd7c31f0)

### Instruction 3: OR R9, R2, R5
![OR](https://github.com/user-attachments/assets/342a1035-e4c9-4b54-bf3c-4e3788272d5b)

### Instruction 4: XOR R10, R1, R4
![XOR](https://github.com/user-attachments/assets/e933e586-903e-4db1-a00f-1918e2b9733c)

### Instruction 5: SLT R1, R2, R4
![SLT](https://github.com/user-attachments/assets/f468e185-b819-4eb0-b655-6b831ac45497)

### Instruction 6: ADDI R12, R4, 5
![addi](https://github.com/user-attachments/assets/d3ba32c1-e82b-4625-aade-e11ca5e4b934)

### Instruction 7: BEQ R0, R0, 15
![BEQ](https://github.com/user-attachments/assets/95a0c61e-5b6a-401d-b32e-f7af5cb6a7d3)

### Instruction 8: BNE R0, R1, 20
![BEN](https://github.com/user-attachments/assets/7f0292e6-37e6-4a73-b5cc-ffd506725d75)

### Instruction 9: SLL R15, R1, R2
![SLL](https://github.com/user-attachments/assets/4c6a7e17-de68-4642-a45d-a5ea40fc3503)

### Instruction 10: SUB R7, R1, R2
![SUB](https://github.com/user-attachments/assets/3b7b7f57-a5dc-4771-84ca-e9c77a3b2825)

## Task-5: Smart Motion Detection Alarm  

### A compact and easy-to-install motion detection alarm using an ultrasonic radar sensor to detect trespassing and alert via a passive buzzer.  

## Features  
- **Easy Installation** – Simply place perpendicular to a solid surface.  
- **Auto-Adjust** – Calibrates detection range within 10 seconds.  
- **Adaptable Range** – Works between 0.1 – 4 meters.  
- **Low Power** – Operates on 5V DC via adapter or battery bank.  
- **Privacy-Friendly** – Suitable for private rooms.  

## Components Required  

| Component                  | Quantity | Description |
|----------------------------|----------|-------------|
| VSD Squadron Mini Board    | 1        | Development board |
| USB-C Cable                | 1        | For power supply |
| HC-SR04 Ultrasonic Sensor  | 1        | Distance measurement sensor |
| Breadboard                 | 1        | For circuit connections |
| Jumper Wires (Male-Male)   | 3        | For circuit connections |
| Jumper Wires (Male-Female) | 3        | For circuit connections |
| Red LED                    | 1        | Indicator light |
| Passive Buzzer             | 1        | Alarm alert |
| 220Ω Resistor              | 1        | For LED protection |
| Toggle Switch              | 1        | Power control |

## Installation  
1. Connect components as per the circuit diagram.  
2. Power with 5V DC (adapter or battery bank).  
3. Place perpendicular to a solid surface.  
4. Wait for auto-adjust (LED indicator).  
5. Alarm triggers when motion is detected.  

## How It Works  
- The **ultrasonic sensor** continuously monitors the distance to the surface.  
- On startup, it **auto-calibrates** to set a threshold distance.  
- Any object passing through its detection field triggers the **buzzer alarm**.  

---
![working circuit](https://github.com/user-attachments/assets/cb601e0c-0aed-472a-bf1c-c10d7fb9e70f)
![circuit photo 3](https://github.com/user-attachments/assets/5ee7f0cf-61ee-41ce-88e9-b2510ac77976)
![circuits photo 2](https://github.com/user-attachments/assets/34a4e35e-641d-4015-96c9-b1395268523a)
![circuit photo](https://github.com/user-attachments/assets/1aba05f7-fb41-4bc3-9fd3-d26bf8c6e3ff)

