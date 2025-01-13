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


