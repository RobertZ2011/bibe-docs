# Types

### b - Binary operation
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
| 0x7   | Reserved  |

### d, r, q - Registers
Registers, d is Rd, R is Rs, and q is Rq

### o - instruction specific operation

### s - Bit shift

## RRR
00 00 bbbb ccc ddddd rrrrr qqqqq ssssss

## Memory
00 01 mmmm ddddd rrrrr ssssss iiiiiiii

## State Related
00 10 oooo ddddd uuuuuuuuuuuuuuuuuuuu
| Value | Operation |
| ----- | --------- |
| 0x0   | rms       |
| 0x1   | wms       |
| Rest  | Reserved  |

## Unary
00 11 oooo ccc ddddd 00000 rrrrr ssssss
| Value | Operation |
| ----- | --------- |
| 0x0   | Not       |
| 0x1   | Neg       |
| 0x2   | Sxt       |
| Rest  | Reserved  |

## RRI
01 bbbb ddddd rrrrr iiiiiiiiiiiiiiii

## RRI C
10 bbbb ddddd rrrrr ccc iiiiiiiiiiiii

## Implemntation defined
11 0xxxxxxxxxxxxxxxxxxxxxxxxxxxxx

## Reserved
11 1xxxxxxxxxxxxxxxxxxxxxxxxxxxxx