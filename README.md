

# RISC-V Toolchain Setup and Verification Tasks
by Rohn Eldho
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

## 📌 Additional Proof

This section addresses the review feedback and adds the missing elements.

### 1. Toolchain Version Proof
As per the review, screenshots and outputs of `riscv64-unknown-elf-gcc -v` and `spike` version are added.

```bash
$ riscv64-unknown-elf-gcc -v
Using built-in specs.
COLLECT_GCC=riscv64-unknown-elf-gcc
COLLECT_LTO_WRAPPER=/path/to/riscv64-unknown-elf-gcc/libexec/gcc/riscv64-unknown-elf/8.3.0/lto-wrapper
Target: riscv64-unknown-elf
Configured with: ...
Thread model: single
gcc version 8.3.0 (GCC)


$ spike
Spike RISC-V ISA Simulator 1.1.1-dev



### Setup Verification


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
spike ~/riscv_toolchain/riscv-pk/build/pk ./unique_test

```
### Task 1 : Screenshots-
<img width="1199" height="334" alt="task1_gcc_version" src="https://github.com/user-attachments/assets/8277a764-8e21-49e1-8df6-e7e2f49bd6fa" />
<img width="646" height="94" alt="task1_spike_version" src="https://github.com/user-attachments/assets/f76af669-c211-4409-b9be-f8b7a0e27bbb" />
<img width="924" height="152" alt="task1out" src="https://github.com/user-attachments/assets/ab2f0d59-34be-4a54-9b94-2043e53efa6c" />

## Task 2: Local RISC-V Verification

### Programs Implemented
1. **factorial.c** - Recursive factorial calculation
2. **max_array.c** - Array maximum value finder
3. **bitops.c** - Bitwise operations demonstration
4. **bubble_sort.c** - Bubble sort implementation

### Assembly Generation Examples
<img width="536" height="300" alt="out1" src="https://github.com/user-attachments/assets/f60ec2ce-c23b-41c8-9f85-c7aff3c2a023" />

*Disassembled main function from factorial.c showing RISC-V instructions*
<img width="536" height="703" alt="out2" src="https://github.com/user-attachments/assets/809fe445-8213-4d93-a5ab-b1d609c721fa" />

*Disassembled main function from max_array.c*

<img width="536" height="662" alt="out3" src="https://github.com/user-attachments/assets/e9cf760d-4848-4342-9136-3c974e127919" />

*Disassembled main function from bitops.c*

<img width="536" height="662" alt="out4" src="https://github.com/user-attachments/assets/fcd8894b-792b-4a28-946a-a073dbd6af4f" />

*Disassembled main function from bubble_sort.c*

### Task 2 – Main Assembly Screenshots

The <main> assembly has now been extracted for all four programs using:

riscv64-unknown-elf-objdump -d <program> | grep -A30 "<main>:" > <program>_main_objdump.txt

Factorial Main Assembly:
<img width="903" height="658" alt="Screenshot from 2025-08-10 12-08-04" src="https://github.com/user-attachments/assets/2ac2fb2f-bd0a-44e9-9616-3297b439b0da" />

Max Array Main Assembly:
<img width="903" height="658" alt="Screenshot from 2025-08-10 12-08-21" src="https://github.com/user-attachments/assets/7ee67ef0-0f43-4f81-90f9-fee494b43988" />

Bitops Main Assembly:
<img width="903" height="658" alt="Screenshot from 2025-08-10 12-08-30" src="https://github.com/user-attachments/assets/29518a9e-afac-4955-b3e4-0754dd787ec5" />

Bubble Sort Main Assembly:
<img width="903" height="658" alt="Screenshot from 2025-08-10 12-09-51" src="https://github.com/user-attachments/assets/c4954af7-c5d7-468d-9d18-9c4883c34b57" />

### Program Outputs
<img width="348" height="322" alt="factorial" src="https://github.com/user-attachments/assets/a65ddb9b-e0b4-4b50-a3f1-a6fb9b201d1a" />

*Factorial program output showing ProofID: 0x56f548c1345da29a*

<img width="348" height="315" alt="max_array" src="https://github.com/user-attachments/assets/2c87d34c-7627-4fc5-bcbf-8f2044b72346" />

*Max array program output showing RunID: 0xcd608e734299ce23*

<img width="348" height="404" alt="bitops" src="https://github.com/user-attachments/assets/7b63d332-a307-4879-8062-65e6693cefc2" />

*Bitwise operations program output*

<img width="348" height="317" alt="bubble_sort" src="https://github.com/user-attachments/assets/58dec4c2-7681-4d69-bc66-706688b91aca" />

*Bubble sort program output showing sorted array*


```

## Instruction Decoding


# RISC-V Instruction Decoding Table

| Assembly Instruction | Hex Source   | Opcode | rd  | rs1 | rs2/imm | funct3 | funct7 | 32-bit Binary Representation       | Description                          |
|----------------------|--------------|--------|-----|-----|---------|--------|--------|------------------------------------|--------------------------------------|
| `addi sp, sp, -32`   | 1101         | 0010011 | sp (x2) | sp (x2) | -32     | 000    | N/A    | 0000001 00000 00010 000 00010 0010011 | Adds immediate -32 to stack pointer  |
| `addi s0, sp, 64`    | 0008         | 0010011 | s0 (x8) | sp (x2) | 64      | 000    | N/A    | 0000000 00000 00010 000 01000 0010011 | Adds immediate 64 to sp, stores in s0|
| `addw a5, a5, a4`    | 97ba         | 0111011 | a5 (x15)| a5 (x15)| a4 (x14)| 000    | 0000000| 0000000 01110 01111 000 01111 0111011 | Adds 32-bit words (W-extension)      |
| `lui a5, 0x6`        | 677d         | 0110111 | a5 (x15)| N/A    | 0x6     | N/A    | N/A    | 000000000110 00000 000 01111 0110111 | Loads upper immediate 0x6 into a5    |
| `sltu a5, a4, a5`    | 00e7b7b3     | 0110011 | a5 (x15)| a4 (x14)| a5 (x15)| 011    | 0000000| 0000000 01111 01110 011 01111 0110011 | Sets a5=1 if a4 < a5 (unsigned)      |

## Key
- **rd**: Destination register
- **rs1/rs2**: Source registers
- **imm**: Immediate value (I-type)
- **funct3/funct7**: Function codes defining operation variants
- W-extension: 32-bit variant in RV64


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
