# Registers

## General Purpose

### r1 - r27

### Zero

### pc

### lr

### fp

### sp

# Model Specific Registers

## Processor Status Register (0)
The processor status register contains flags and values on the
current execution state of the processor. This is an architectural
register that must be implemented.

xxxx xxxx xxxx xxxx xxxx xxxx xxee mmcc

x - Reserved

### c - Last `cmp` result
RO
These bits store the result of the last `cmp` instruction

| Value | Result |
| ----- | -------|
| 0x0   | Equal  |
| 0x1   | Lt     |
| 0x2   | Gt     |
| 0x3   | Res    |

### m - Model control and status flags
RW
These bits contain control and status information for msr
instructions.

#### m[0]: Quiet flag
When set this bit causes msr instructions that operate on an invalid
register index to not trigger and exception. The instructions set the error
flag as their only effect.

#### m[1]: Error flag
When set indicates that an msr instruction attempted to access an invalid register

### ee - Exception control and status flags
These bits contain control and status information for
exception handling.

#### e[0]: In exception mode flag
RO
This bit is set while handling an exception

#### e[1]: IRQ disable flag
RW
When this bit is set the processor does not respond to IRQs