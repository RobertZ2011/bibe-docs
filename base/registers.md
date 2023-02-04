# Registers

## General Purpose

### r1 - r27

### Zero

### pc

### lr

### fp

### sp

# Processor Status Register
The processor status register contains flags and values on the
current execution state of the processor.
xxxx xxxx xxxx xxxx xxxx xxxx xxxx xxcc

x - Reserved
c - Last `cmp` result
| Value | Result |
| ----- | -------|
| 0x0   | Equal  |
| 0x1   | Lt     |
| 0x2   | Gt     |
| 0x3   | Res    |

# Model Specific Registers