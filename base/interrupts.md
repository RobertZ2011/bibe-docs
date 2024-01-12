# Interrupts

## Interrupt Table
The interrupt table is located at the memory address `csr[ISR_BASE]`
and contains one 32-bit entry for each supported interrupt.

## Entering Interrupt Mode
When an interrupt occurs the processor enters interrupt mode by
performing the following steps:
* The interrupt mode flag is set in the PSR
* The interrupt disable flag is set in the PSR
* `csr[ISR_ERR1]` is set
* `csr[ISR_ERR2]` is set
* SP is set to the value of `csr[ISR_SP]`
* The processor jumps to the address `csr[ISR_BASE] + word n`
* Registers banks are swapped

These steps are atomic to the application layer

## Exiting Interrupt Mode
When interrupt handling is finished, interrupt mode can be exited by
writing to `csr[ISR_EXIT]`. Upon exiting interrupt mode, the following happens:
* The interrupt mode flag is cleared in the PSR
* The interrupt disable flag is cleared in the PSR
* Register banks are swapped

## Interrupts

### Software
#### Reset
Triggered by the reset of the processor

### NMI
Non-maskable interrupt indicating hardware fault

### Breakpoint

### Alignment Fault (#AL)
Attempted unaligned access

### Memory Fault (#ME)
General memory access fault

### Opcode Fault (#OP)
General failure of an instruction.

### Double Fault (#DF)
A fault occuring while handling an interrupt results in a double fault
`csr[ISR_ERR1]` will contain the faulting PC vaule and `csr[ISR_ERR2]`
the faulting SP value. All general-purpose registers retain their values
from before the double fault. A subsequent fault before exiting interrupt mode
results in a reset.

### Software Interrupt (SWI)
Triggered by writing to csr[ISR_SWI] or the alias instruction `swi`

### Reserved 0-7

### IRQ
External IRQ

## Interrupt CSRs
ISR_R1 - 0x0
...
ISR_PC - 4 * 31
ISR_ERR1
RO/0
ISR_ERR2
RO/0

ISR_BASE
R/O/I

ISR_ENTER
R/W/0 - Writing a one to any bit will trigger a software interrupt

ISR_EXIT
R/W/0 - Writing a one to any bit will exit interrupt mode

## ISR Table
Reset
NMI
Breakpoint
#AL
#ME
#OP
#DF
SWI
Reserved0-7
IRQ0
...
IRQn