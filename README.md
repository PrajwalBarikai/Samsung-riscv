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

