

# RISC-V Toolchain Setup and Verification Tasks

## Table of Contents
- [Task 1: RISC-V Toolchain Setup](#task-1-risc-v-toolchain-setup)
- [Task 2: Local RISC-V Verification](#task-2-local-risc-v-verification)
- [GitHub Repository](#github-repository)
- [Instruction Decoding](#instruction-decoding)
- [Program Outputs](#program-outputs)

## Task 1: RISC-V Toolchain Setup

### Overview
Successfully set up complete RISC-V development environment including:
- Base developer tools
- RISC-V GCC toolchain (v8.3.0)
- Spike simulator (v1.1.0-dev)
- Proxy kernel (riscv-pk)
- Verification through unique test program

### Setup Verification
![Toolchain Verification](Screenshot%20from%202025-08-02%2023-50-51.png)
*Successful execution of unique test program showing:*
- *Username: rohn*
- *Hostname: rohn-VirtualBox*
- *UniqueID: 0xaca4dab8327313e6*
- *GCC version length: 5*

### Key Commands
```bash
# Toolchain installation
wget "https://static.dev.sifive.com/dev-tools/riscv64-unknown-elf-gcc-8.3.0-2019.08.0-x86_64-linux-ubuntu14.tar.gz"
tar -xvzf riscv64-unknown-elf-gcc-8.3.0-2019.08.0-x86_64-linux-ubuntu14.tar.gz

# Unique test compilation
riscv64-unknown-elf-gcc -O2 -Wall -march=rv64imac -mabi=lp64 \
-DUSERNAME="$(id -un)" -DHOSTNAME="$(hostname -s)" \
unique_test.c -o unique_test

# Execution
spike pk ./unique_test
```

## Task 2: Local RISC-V Verification

### Programs Implemented
1. **factorial.c** - Recursive factorial calculation
2. **max_array.c** - Array maximum value finder
3. **bitops.c** - Bitwise operations demonstration
4. **bubble_sort.c** - Bubble sort implementation

### Assembly Generation Examples
![factorial.s](out1.png)
*Disassembled main function from factorial.c showing RISC-V instructions*

![max_array.s](out2.png)
*Disassembled main function from max_array.c*

![bitops.s](out3.png)
*Disassembled main function from bitops.c*

![bubble_sort.s](out4.png)
*Disassembled main function from bubble_sort.c*

### Program Outputs
![Factorial Output](factorial.png)
*Factorial program output showing ProofID: 0x56f548c1345da29a*

![Max Array Output](max_array.png)
*Max array program output showing RunID: 0xcd608e734299ce23*

![Bitops Output](bitops.png)
*Bitwise operations program output*

![Bubble Sort Output](bubble_sort.png)
*Bubble sort program output showing sorted array*

## GitHub Repository
![GitHub Activity](Screenshot%20from%202025-08-08%2022-27-20.png)
*Repository activity showing commits for both tasks*

### Repository Structure
```
vsdRiscvSoc/
├── Task1/
│   ├── unique_test.c
│   └── unique_test_output.png
├── Task2/
│   ├── unique.h
│   ├── factorial.*
│   ├── max_array.*
│   ├── bitops.*
│   ├── bubble_sort.*
│   └── instruction_decoding.md
└── README.md
```

## Instruction Decoding

Decoded instructions from factorial.s:

| Instruction | Opcode  | rd  | rs1 | rs2 | funct3 | funct7 | Binary | Description |
|-------------|---------|-----|-----|-----|--------|--------|--------|-------------|
| addi sp,sp,-32 | 0010011 | sp | sp | N/A | 000 | N/A | 111111100000_00010_000_00010_0010011 | Adjust stack pointer |
| sd ra,24(sp) | 0100011 | N/A | sp | ra | 011 | N/A | 000110_00010_00001_011_11000_0100011 | Store return address |
| lui a5,0x66 | 0110111 | a5 | N/A | N/A | N/A | N/A | 0000000001100110_00101_0110111 | Load upper immediate |
| jal ra,101ce | 1101111 | ra | N/A | N/A | N/A | N/A | 0_11000111001111_0_00001_1101111 | Jump and link |
| lw a5,-20(s0) | 0000011 | a5 | s0 | N/A | 010 | N/A | 111111101100_01000_010_00101_0000011 | Load word from memory |

## Toolchain Information
```
$ spike --version
Spike RISC-V ISA Simulator 1.1.0-dev

$ riscv64-unknown-elf-gcc -v
gcc version 8.3.0 (riscv64-unknown-elf)
```

## Conclusion
Both tasks were successfully completed with:
- Verified unique toolchain installation
- Four functional RISC-V programs
- Complete instruction decoding
- Machine-specific identification in all outputs
- Proper GitHub repository organization
