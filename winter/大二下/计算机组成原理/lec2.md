__concept__
• Application software
	• Written in high-level language
• System software
	• Compiler: translates HLL code to machine code
• Operating System:
	• Handling input/output
	• Managing memory and storage
	• Scheduling tasks & sharing resources
• Hardware
	• Processor, memory, I/O controllers

__Instruction(指令) Set Architecture (ISA)__
• A set of assembly language instructions (ISA) provides a link between
software and hardware.
• Given an instruction set, software programmers and hardware engineers
work more or less independently.
• Common types of ISA: RISC, CISC

• Instructions: CPU’s primitive operations
	• Instructions performed one after another in sequence
	• Each instruction does a small amount of work (a tiny part of a larger program).
	• Each instruction has an operation applied to operands,
	• and might be used to change the sequence of instructions.
• CPUs belong to “families,” each implementing its own set of instructions
• CPU’s particular set of instructions implements an Instruction Set
Architecture (ISA)
	• Examples: ARM, Intel x86, MIPS, RISC-V, PowerPC...

##### CISC vs RISC
CISC:
• Complex Instruction Set Computer
• Variable instruction length
• Much more powerful instructions
• Hardware intensive instructions (more transistors
• e.g. x86

RISC:
• Reduced Instruction Set Computer
• Fixed instruction size
• Simple instructions (load/store)
• Emphasizes more on software (compiler)
• e.g. MIPS, ARM, PowerPC, RISC-V

CISC: wintel(windows + intel)
RISA: 
- AA(ARM + Apple)
- RISC-V

**Translate the following C code into assembly code**:
a = b + c + d + e;
add a, b, c add a, b, c
add a, a, d or add f, d, e
add a, a, e add a, a, f
• Instructions are simple: fixed number of operands (unlike C)
• A single line of C code is converted into multiple lines of assembly code
• Some sequences are better than others… the second sequence needs one more
(temporary) variable f

All arithmetic operations have this form: add a, b, c(a = b + c)
==Design Principle 1: Simplicity favors regularity==
Design Principle 2: Smaller is faster


##### RISC-V Registers
`本课程使用32bit`

Register x0
> x0 is special, always holds the value zero and can't be changed

- Copy a value from one register to another(add x3, x4, x0 same as f = g )
- whenever a value is produced and we want to throw it away, write to x0
- By convention RISC-V has a specific no-op instruction
add x0,x0,x0
- sed later with “jump-and-link” instruction

In RISC-V immediates are "sign extended"

Register vs Memory
Using Load Word (lw) in RISC-V:
```risc-v
lw x10,32(x13) # reg x10 gets A[8]
add x11,x12,x10 # g = h + A[8]
```
偏移量(32) = 数组序列数(8) x word字节数(4)
lb 1byte; 1h 2 byte; 1d 8 byte
