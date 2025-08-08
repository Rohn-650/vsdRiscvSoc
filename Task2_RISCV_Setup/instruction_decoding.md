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

