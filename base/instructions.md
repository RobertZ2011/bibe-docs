# Types

### o - Operation
| Value | Operation |
| ----- | --------- |
| 0x0   | Add       |
| 0x1   | Sub       |
| 0x2   | Mul^1     |
| 0x3   | Div^1     |
| 0x4   | Mod^1
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
| 0x10  | Cmp       |

1. Requires integer multiplication extension

### c - Condition
| Value | Condition |
| ----- | --------- |
| 0x0   | Always    |
| 0x1   | Eq        |
| 0x2   | Ne        |
| 0x3   | Gt        |
| 0x4   | Ge        |
| 0x5   | Lt        |
| 0x6   | Le        |
| 0x7   | Never     |

### d, r, q - Registers
Registers, d is Rd, R is Rs, and q is Rq

### m - instruction specific operation

### s - Bit shift

## RRR
00 00 ooooo ddddd rrrrr qqqqq ttt sssss

Perform reg[d] = reg[r] op (reg[q] shift s)
If op is unary reg[d] = op (reg[r] + (reg[q] shift s))

## Memory
00 01 mmmmm ddddd rrrrr kkk iiiiiiiiii
| Value | Operation |
| ----- | --------- |
| 0x0   | ldrb.rr   |
| 0x1   | strb.rr   |
| 0x2   | ldrs.rr   |
| 0x3   | strs.rr   |
| 0x4   | ldrw.rr   |
| 0x5   | strw.rr   |
| 0x6   | Reserved  |
| 0x7   | Reserved  |
| 0x8   | Reserved  |
| 0x9   | Reserved  |
| 0xa   | Reserved  |
| 0xb   | Reserved  |
| 0xc   | Reserved  |
| 0xd   | Reserved  |
| 0xe   | Reserved  |
| 0xf   | Reserved  |
| 0x10  | ldrb.ri   |
| 0x11  | strb.ri   |
| 0x12  | ldrs.ri   |
| 0x13  | strs.ri   |
| 0x14  | ldrw.ri   |
| 0x15  | strw.ri   |
| 0x16  | Reserved  |
| 0x17  | Reserved  |
| 0x18  | Reserved  |
| 0x19  | Reserved  |
| 0x1a  | Reserved  |
| 0x1b  | Reserved  |
| 0x1c  | Reserved  |
| 0x1d  | Reserved  |
| 0x1e  | Reserved  |
| 0x1f  | Reserved  |

### RR
00 01 mmmmm 0000 ddddd rrrrr qqqqq ssss
Memory operation involving the address reg[r] + (reg[q] << s)

## RI
00 01 mmmmm ddddd rrrrr iiiiiiiiiiiii
Memory operation involving the address reg[r] + i

## Model specific
00 10 mmmmm rrrrr uuuuuuuuuuuuuuuuuuu
| Value | Operation |
| ----- | --------- |
| 0x0   | rms       |
| 0x1   | wms       |
| Rest  | Reserved  |

## RRI
01 ooooo ddddd rrrrr ccc iiiiiiiiiiii

Conditionally perform reg[d] = reg[r] op i
If op is unary reg[d] = op (reg[r] + i)

## Implemntation defined
11 xxxxxxxxxxxxxxxxxxxxxxxxxxxxxx