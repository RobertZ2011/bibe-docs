# Types

### o - Operation
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

### d, r, q - Registers
Registers, d is Rd, R is Rs, and q is Rq

### m - instruction specific operation

### s - Bit shift amount

### t - Bit shift type

## RRR
00 00 ooooo ddddd rrrrr qqqqq ttt sssss

Perform reg[d] = reg[r] op (reg[q] shift(t) s)
If op is unary reg[d] = op (reg[r] + reg[q] shift(t) s)

## Memory
| Value | Operation |
| ----- | --------- |
| 0x0   | ldrb.rr   |
| 0x1   | strb.rr   |
| 0x2   | ldrs.rr   |
| 0x3   | strs.rr   |
| 0x4   | ldrw.rr   |
| 0x5   | strw.rr   |

| 0x10  | ldrb.ri   |
| 0x11  | strb.ri   |
| 0x12  | ldrs.ri   |
| 0x13  | strs.ri   |
| 0x14  | ldrw.ri   |
| 0x15  | strw.ri   |

### RR
00 01 mmmmm ddddd rrrrr qqqqq ttt sssss
Memory operation involving the address reg[r] + (reg[q] shift(t) s)

## RI
00 01 mmmmm ddddd rrrrr iiiiiiiiiiiii
Memory operation involving the address reg[r] + i

## CSR
00 10 mmmmm rrrrr uuu uuuu uuuu uuuu uuuu
| Value | Operation |
| ----- | --------- |
| 0x0   | csrb      |
| 0x1   | csrs      |
| 0x2   | csrw      |

| 0x10  | cswb      |
| 0x11  | csws      |
| 0x12  | csww      |

csrr reads the model-specific register named by the immediate u into the register r
csrw writes the value of the register r into the model-spcific register named by the immediate u

The immediate space is divided as follows:
0x00000-0x3ffff: Reserved
0x40000-0x7ffff: Implementation defined

Reserved0011
0011 xxxxxxxxxxxxxxxxxxxxxxxxxxxx

## RRI
01 ooooo ddddd rrrrr ccc iiiiiiiiiiii

Conditionally perform reg[d] = reg[r] op i
If op is unary reg[d] = op (reg[r] + i)

## Reserved10
10 xxxxxxxxxxxxxxxxxxxxxxxxxxxxxx

## Implemntation defined
11 xxxxxxxxxxxxxxxxxxxxxxxxxxxxxx