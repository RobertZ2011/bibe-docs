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

## Arithemetic flags
These bits are only set by cc instructions.

### V - Overflow flag
RO

### C - Carry flag
RO

### Z - Zero flag
RO

### P - Positive flag
RO

### ee - Interrupt control and status flags
These bits contain control and status information for
interrupt handling.

#### e[0]: In interrupt mode flag
RO
This bit is set while handling an exception

#### e[1]: IRQ disable flag
RW
When this bit is set the processor does not respond to IRQs