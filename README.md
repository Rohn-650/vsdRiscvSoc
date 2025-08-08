# RISC-V Unique Test for VSD SoC
# vsdRiscvSoc
# 🧠 VSD RISC-V Toolchain Task 1 Submission

This repository contains my complete submission for **Task 1** of the VSD RISC-V SoC Design Program. The objective was to verify a working RISC-V toolchain by writing and running a test program, and demonstrating uniqueness of the compiled output based on the user and host machine.

---

## 📋 Task Breakdown

### ✅ Task 1.1 — Setup the RISC-V Toolchain

- **Goal**: Download, extract, and configure the RISC-V toolchain including:
  - `riscv64-unknown-elf-gcc` (cross compiler)
  - `spike` (RISC-V ISA simulator)
  - `pk` (proxy kernel)

- **Steps Taken**:
  - Extracted toolchain tarball
  - Added the toolchain `bin` directory to `$PATH` using:
    ```bash
    export PATH=$HOME/riscv_toolchain/riscv64-unknown-elf-gcc*/bin:$PATH
    ```
  - Verified tool availability:
    ```bash
    which riscv64-unknown-elf-gcc
    which spike
    ```

---

### ✅ Task 1.2 — Write the C Test Program (`unique_test.c`)

- **Goal**: Write a C program that:
  - Prints a greeting
  - Displays the user and host at compile time
  - Computes a hash (`UniqueID`) based on user and host
  - Shows compiler configuration details (like GCC VLEN)

- **Source File**: `unique_test.c`

- **Key Features**:
  - Uses FNV-1a 64-bit hashing
  - Reads compile-time values using macros (`USERNAME`, `HOSTNAME`)

---

### ✅ Task 1.3 — Compile for RISC-V Architecture

- **Compiler Command**:
  ```bash
  riscv64-unknown-elf-gcc -O2 -Wall -march=rv64imac -mabi=lp64 \
  -DUSERNAME="$(id -un)" -DHOSTNAME="$(hostname -s)" \
  unique_test.c -o unique_test
<img width="924" height="152" alt="image" src="https://github.com/user-attachments/assets/92e84bd2-d1de-4b1e-b7af-1ce665bab0ed" />
