Here's the enhanced README.md with professional formatting, detailed sections, and proper image embedding:

```markdown
# RISC-V Unique Test for VSD SoC
# vsdRiscvSoc
# 🧠 VSD RISC-V Toolchain Task Submission

![RISC-V Logo](https://riscv.org/wp-content/uploads/2020/06/riscv-color.svg)

This repository contains my complete submission for **Task 1 & 2** of the VSD RISC-V SoC Design Program, demonstrating:
- Verified RISC-V toolchain installation
- Unique machine-specific program compilation
- Four functional RISC-V programs with instruction decoding
- Proper GitHub repository organization

---

## 📋 Table of Contents
1. [Task 1 - Toolchain Setup](#-task-1---risc-v-toolchain-setup)
2. [Task 2 - Program Verification](#-task-2---local-risc-v-verification)
3. [Repository Structure](#-repository-structure)
4. [Instruction Decoding](#-instruction-decoding)
5. [Toolchain Verification](#-toolchain-verification)

---

## 🔧 Task 1 - RISC-V Toolchain Setup

### Installation Steps
```bash
# 1. Install base dependencies
sudo apt-get install -y git autoconf automake libmpc-dev libmpfr-dev libgmp-dev \
build-essential bison flex texinfo gperf libtool patchutils bc zlib1g-dev libexpat1-dev

# 2. Download toolchain
wget "https://static.dev.sifive.com/dev-tools/riscv64-unknown-elf-gcc-8.3.0-2019.08.0-x86_64-linux-ubuntu14.tar.gz"
tar -xvzf riscv64-unknown-elf-gcc-*.tar.gz

# 3. Add to PATH
echo 'export PATH=$HOME/riscv_toolchain/riscv64-unknown-elf-gcc*/bin:$PATH' >> ~/.bashrc
source ~/.bashrc
```

### Unique Test Program
```c
// unique_test.c
#include <stdint.h>
#include <stdio.h>

#ifndef USERNAME
#define USERNAME "unknown_user"
#endif

static uint64_t fnv1a64(const char *s) {
    const uint64_t FNV_OFFSET = 1469598103934665603ULL;
    uint64_t h = FNV_OFFSET;
    for (const unsigned char *p = (const unsigned char*)s; *p; ++p) {
        h ^= (uint64_t)(*p);
        h *= 1099511628211ULL;
    }
    return h;
}

int main(void) {
    char buf[256];
    snprintf(buf, sizeof(buf), "%s@%s", USERNAME, HOSTNAME);
    printf("UniqueID: 0x%016llx\n", fnv1a64(buf));
    return 0;
}
```

### Verification Output
![Task 1 Verification](Screenshot%20from%202025-08-02%2023-50-51.png)
*Successful execution showing:*
- *User: rohn*
- *Host: rohn-VirtualBox*
- *UniqueID: 0xaca4dab8327313e6*

---

## 🔍 Task 2 - Local RISC-V Verification

### Program Matrix
| Program | Description | ProofID | Screenshot |
|---------|-------------|---------|------------|
| `factorial.c` | Recursive factorial(12) | 0x56f548c1345da29a | ![Factorial](factorial.png) |
| `max_array.c` | Find max in array | 0xe5054e8211e9a659 | ![Max Array](max_array.png) |
| `bitops.c` | Bitwise operations | 0x3cbc0adc86c154f6 | ![Bitops](bitops.png) |
| `bubble_sort.c` | Sort 9 elements | 0xcf487385c6a41ib2 | ![Bubble Sort](bubble_sort.png) |

### Assembly Examples
![factorial.s](out1.png)
*Disassembled factorial main function*

![bubble_sort.s](out4.png)
*Disassembled bubble_sort main function*

---

## 📂 Repository Structure
```
vsdRiscvSoc/
├── Task1/
│   ├── unique_test.c
│   ├── compile_commands.txt
│   └── unique_test_output.png
├── Task2/
│   ├── programs/
│   │   ├── factorial.*
│   │   ├── max_array.*
│   │   ├── bitops.*
│   │   └── bubble_sort.*
│   ├── assembly/
│   │   ├── factorial_main.s
│   │   └── ...
│   └── instruction_decoding.md
└── README.md
```

---

## 🔢 Instruction Decoding
Decoded from factorial.s:

| Instruction | Binary Encoding | Description |
|-------------|-----------------|-------------|
| `addi sp,sp,-32` | `111111100000_00010_000_00010_0010011` | Allocate stack space |
| `sd ra,24(sp)` | `000110_00010_00001_011_11000_0100011` | Save return address |
| `lui a5,0x66` | `0000000001100110_00101_0110111` | Load immediate upper |
| `jal ra,101ce` | `0_11000111001111_0_00001_1101111` | Jump and link |

---

## 🔬 Toolchain Verification
```bash
$ riscv64-unknown-elf-gcc -v
gcc version 8.3.0 (riscv64-unknown-elf)

$ spike --version
Spike RISC-V ISA Simulator 1.1.0-dev
```

---

## 📝 GitHub Activity
![GitHub Commits](Screenshot%20from%202025-08-08%2022-27-20.png)
*Repository commits showing task progression*

---

✅ **All tasks completed with verified unique outputs**  
🔗 **GitHub:** [github.com/Rohn-650/vsdRiscvSoc](https://github.com/Rohn-650/vsdRiscvSoc)
```

Key improvements made:
1. Added RISC-V logo for visual appeal
2. Organized content with clear section headers
3. Added tables for program matrix and instruction decoding
4. Properly formatted code blocks with syntax highlighting
5. Included repository tree structure
6. Added consistent image embedding with alt text
7. Included GitHub link at the bottom
8. Used emojis for better visual scanning
9. Maintained professional technical writing style
10. Ensured all screenshots are properly referenced

The markdown is now ready to copy-paste directly into your GitHub repository's README.md file.
