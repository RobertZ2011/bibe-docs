# Types

### o - Operation
| Value | Operation |
| ----- | --------- |
| 0x0   | Add       |
| 0x1   | Sub       |
| 0x2   | Mul^1     |
| 0x3   | Div^1     |
| 0x4   | And       |
| 0x5   | Or        |
| 0x6   | Xor       |
| 0x7   | Shl       |
| 0x8   | Shr       |
| 0x9   | Asl       |
| 0xa   | Asr       |
| 0xb   | Rol       |
| 0xc   | Ror       |
| 0xd   | Not       |
| 0xe   | Neg       |
| 0xf   | Cmp       |

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
00 00 oooo ddddd rrrrr qqqqq ttt ssssss

Perform reg[d] = reg[r] op (reg[q] shift sssssssss)
If op is unary reg[d] = op (reg[r] + (reg[q] shift sssssssss))

## Memory
00 01 mmmm ddddd rrrrr kkk iiiiiiiiiii
| Value | Operation |
| ----- | --------- |
| 0x0   | ldrb      |
| 0x1   | strb      |
| 0x2   | ldrs      |
| 0x3   | strs      |
| 0x4   | ldrw      |
| 0x5   | strw      |
| Rest  | Reserved  |
Load/store byte/short/word to/from memory address (reg[r] << k) + i and register reg[d]

## Model specific
00 10 mmmm rrrrr uuuuuuuuuuuuuuuuuuuu
| Value | Operation |
| ----- | --------- |
| 0x0   | rms       |
| 0x1   | wms       |
| Rest  | Reserved  |

## RRI
01 oooo ddddd rrrrr ccc iiiiiiiiiiiii

Conditionally perform reg[d] = reg[r] op iiiiiiiiiiiii
If op is unary reg[d] = op (reg[r] + iiiiiiiiiiiii)

## Implemntation defined
11 0xxxxxxxxxxxxxxxxxxxxxxxxxxxxx