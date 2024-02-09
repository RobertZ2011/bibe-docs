# Types

### o - Integer Operation
| Value | Operation |
| ----- | --------- |
| 0x0   | Add       |
| 0x1   | Sub       |
| 0x2   | Mul^1     |
| 0x3   | Div^1     |
| 0x4   | Mod^1     |
| 0x5   | And       |
| 0x6   | Or        |
| 0x7   | Xor       |
| 0x8   | Shl       |
| 0x9   | Shr       |
| 0xa   | Asl       |
| 0xb   | Asr       |
| 0xc   | Rol       |
| 0xd   | Ror       |
| 0xe   | Not       |
| 0xf   | Neg       |
| 0x10  | Addcc     |
| 0x11  | Subcc     |

1. Requires integer multiplication extension

### c - Condition
| Value | Condition    |
| ----- | ---------    |
| 0x0   | Always       |
| 0x1   | Overflow     |
| 0x2   | Carry        |
| 0x3   | Zero(Eq)     |
| 0x4   | Negative(Lt) |
| 0x5   | !Z(Ne)       |
| 0x6   | !N(Ge)       |
| 0x7   | !(N || Z)(Gt)|

### l - Load Store
| Value | Operation  |
| ----- | ---------- |
| 0x0   | Load B     |
| 0x1   | Load S     |
| 0x2   | Load W     |

| 0x4   | Store B    |
| 0x5   | Store S    |
| 0x6   | Store W    |

### d, r, q - Registers
Registers, d is Rd, R is Rs, and q is Rq

### t - Bit shift type
| Value  | Operation |
| -----  | --------- |
| 0x0    | Shl       |
| 0x1    | Shr       |
| 0x2    | Asl       |
| 0x3    | Asr       |
| 0x4    | Rol       |
| 0x5    | Ror       |

### s - Bit shift amount
Unsigned

## RRR
00 00 ooooo ddddd rrrrr qqqqq ttt sssss

Perform reg[d] = reg[r] op (reg[q] shift(t) s)
If op is unary reg[d] = op (reg[r] + reg[q] shift(t) s)

## Memory RR
00 01 0 llll ddddd rrrrr qqqqq ttt sssss
Memory operation involving the address reg[r] + (reg[q] shift(t) s)

## CSR
00 01 1 llll rrrrr uuu uuuu uuuu uuuu uuuu
Read/Write the CSR named by u

The immediate space is divided as follows:
0x00000-0x3ffff: Reserved
0x40000-0x7ffff: Implementation defined

## Reserved0010
0010 xxxxxxxxxxxxxxxxxxxxxxxxxxxx

## Reserved0011
0011 xxxxxxxxxxxxxxxxxxxxxxxxxxxx

## RRI
01 ooooo ddddd rrrrr ccc iiiiiiiiiiii

Conditionally perform reg[d] = reg[r] op i
If op is unary reg[d] = op (reg[r] + i)

## Memory RI
10 llll ddddd rrrrr iiiiiiiiiiiiiiii
Memory operation involving the address reg[r] + i

## Jump
11 ii iiii iiii iiii iiii iiii iiii iiii iiii
Perform pc = pc + i