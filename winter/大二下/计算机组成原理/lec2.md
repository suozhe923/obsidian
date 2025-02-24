#### concept
• Application software
	• Written in high-level language
• System software
	• Compiler: translates HLL(hight-level language) code to machine code
• Operating System:
	• Handling input/output
	• Managing memory and storage
	• Scheduling tasks & sharing resources(调度任务和共享资源)
• Hardware
	• Processor(处理器), memory, I/O controllers

#### Levels of Program Code
- high-level language
- Assembly language(汇编语言)
- Machine language
#### Abstraction(抽象)
__Instruction(指令) Set Architecture (ISA,指令集架构)__
• _A set of assembly language instructions_ (ISA) provides a link between software and hardware.
• Common types of ISA: RISC, CISC
	• IBM370/X86 (CISC)
	• RISC-V (RISC)
	• MIPS (RISC)
	• ARM (RISC)
##### ISA
• Instructions: CPU’s primitive(原始) operations
	• Instructions performed one after another in sequence
	• Each instruction does a **small** amount of work (a tiny part of a larger program).
	• Each instruction has an operation applied to operands(操作数), and might be used to change the sequence of instructions.
• CPUs belong to “families,” each implementing its own set of instructions
• CPU’s particular set of instructions implements an Instruction Set
Architecture (ISA)
	• Examples: ARM, Intel x86, MIPS, RISC-V, PowerPC...

##### CISC vs RISC
- CISC:
	- Complex Instruction Set Computer
	- Variable instruction length
	- Much more powerful instructions
	- Hardware intensive(密集) instructions (more transistors(晶体管)
	- e.g. x86

- RISC:
	-  Reduced Instruction Set Computer
	-  Fixed instruction size
	-  Simple instructions (load/store)
	-  Emphasizes(强调) more on software (compiler)
	-  e.g. MIPS, ARM, PowerPC, RISC-V

>CISC: wintel(windows + intel)
>RISA: 
>	AA(ARM + Apple)
>	RISC-V

#### Basic Assembly instruction
**Translate the following C code into assembly code**:
- C:
	a = b + c + d + e;
- Assembly:
	add a, b, c             add a, b, c
	add a, a, d     __or__    add f, d, e
	add a, a, e             add a, a, f

All arithmetic operations have this form: add a, b, c(a = b + c)
- C code: f = (g + h) - (i + j)
- Assembly:
	add t0, g, h # 这是一个注释
	add t1, i, j
	sub f, t0, t1

#### Assembly Variables: Registers
汇编语言没有variables, Assembly language operands are objects called registers
>RISC-V Registers
>`本课程使用32bit`
>Each RISC-V register is 32 bits wide called a “word”
>Registers have __no type__
>Operation determines how register contents are interpreted

![Register](../../Pictures/Register.png)
Instructions have an opcode and opeands
例: add x1, x2, x3
- add: Operation code(opcode)
- x1: Destination register
- x2: First operand register
- x3: Second operand register
##### Register x0
> x0 is special, always holds the value zero and can't be changed
- Copy a value from one register to another(add x3, x4, x0 same as f = g )
- whenever a value is produced and we want to throw it away, write to x0
- By convention RISC-V has a specific no-op instruction
add x0,x0,x0
- sed later with “jump-and-link” instruction

##### Immediates
> Immediates are used to provide numerical constants, 即时数用于提供数值常数, 语法和add instruction 类似但是最后一个参数是 number 而不是 register

addi x3, x4, 10
same as f = g + 10

##### Numeric Representations

- unsigned:
$$x=x_{n-1}2^{n-1} + x_{n-2}2^{n-2 } + ...+x_12^1+x_02^0$$
- signed:
$$x=-x_{n-1}2^{n-1}+x_{n-2}2^{n-2}+...+x_12^1+x_02^0$$
- Complement(取反)
$$ x + \overline{x} = -1$$
$$ \overline{x} +1 = -x$$
##### Immediates & Sign Extension
> Immediates are necessarily small
 
In RISC-V immediates are "sign extended"
	the upper bits are the same as the top bit
e:
- +2:***0***000 0010 => ***0000 0000 0***000 0010
- -2 ***1***111 1110 => ***1111 1111 1***111 1110

Register vs Memory
Using Load Word (lw) in RISC-V:
```risc-v
lw x10,32(x13) # reg x10 gets A[8]
add x11,x12,x10 # g = h + A[8]
```
偏移量(32) = 数组序列数(8) x word字节数(4)
lb 1byte; 1h 2 byte; 1d 8 byte

##### Data transfer Operations
- Registers vs. Memory
	- Arithmetic operations can only be performed on registers
	- Thus, the only memory actions are loads & stores
- Given that 
	- Registers: 32 words (128 Bytes)
	- Memory (DRAM): Billions of bytes (2 GB to 16 GB on laptop)






P32选C
P33选D




Q1: addi 和 add区别
Q2:0x meaning
Q3:sub的计算是不是相当于add后一个数补码

