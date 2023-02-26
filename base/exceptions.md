# Exceptions

## Exception Table
The exception table is located at the memory address `msr[ISR_BASE]`
and contains one 32-bit entry for each exception. An implementation
of the exception table is required to contain an entry for every exception
even if it does not implement the associated behavior. E.g. a
microcontroller that doesn't implement the `div` instruction is
required to have a #DZ entry in its exception table.

## Entering Exception Mode
When an exception occurs the processor enters exception mode by
performing the following steps:
* The exception mode flag is set in the PSR
* The exception disable flag is set in the PSR
* `msr[ISR_OLD_SP] = SP`
* `msr[ISR_OLD_PC] = PC`
* `msr[ISR_ERR1]` is set
* `msr[ISR_ERR2]` is set
* SP is set to the value of `msr[ISR_SP]`
* The processor jumps to the address `msr[ISR_BASE] + word n`

These steps are atomic to the application layer

## Exiting Exception Mode
When exception handling is finished, exception mode can be exited by
writing to `msr[ISR_EXIT]`. Upon exiting exception mode, the following happens:
* `SP = msr[ISR_OLD_SP]`
* `msr[ISR_OLD_SP] = 0`
* The exception mode flag is cleared in the PSR
* The exception disable flag is cleared in the PSR
* The processor jumps to `msr[ISR_OLD_PC]`

## Reset
Triggered by the reset of the processor

## Division by Zero (#DZ)
Triggered when an attempt to divide by zero is made

## Opcode (#OP)
Triggered by a general failure of an instruction.

## Memory Fault (#ME)
Triggered by a memory error, including:
* Unaligned access
* Attempt to access an invalid address

## SWI
Triggered by writing to msr[ISR_SWI] or the alias instruction `swi`

## IRQ
External IRQ

## NMI
Non-maskable interrupt indicating hardware fault