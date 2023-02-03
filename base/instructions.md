# Types

### b - Binary operation
| Value | Operation |
| ----- | --------- |
| 0x0   | Add       |
| 0x1   | Sub       |
| 0x2   | Reserved  |
| 0x3   | Reserved  |
| 0x4   | And       |
| 0x5   | Or        |
| 0x6   | Xor       |
| 0x7   | Asl       |
| 0x8   | Asr       |

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


### s - Bit shift


## RRR
00 00 bbbb ccc ddddd rrrrr qqqqq ssssss

## Memory
00 01 mmmm ddddd rrrrr ssssss iiiiiiii

## State Related
00 10 oooo xxxxxxxxxxxxxxxxxxxxxxxx
TODO: model specific registers and processor state

## Implementation Defined
00 11 xxxxxxxxxxxxxxxxxxxxxxxxxxxx

## RRI
01 bbbb ddddd rrrrr iiiiiiiiiiiiiiii

## RRI C
10 bbbb ddddd rrrrr ccc iiiiiiiiiiiii

## Unary
11 0000000000 oooo ddddd rrrrr ssssss