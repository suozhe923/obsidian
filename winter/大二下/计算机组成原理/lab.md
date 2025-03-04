- Assembly Program Structure
	- Data Declarations
		- .data(placed in section of program identified with assembler directive(汇编说明/汇编器指示符)
		- declare variable names used in program; storage allocated in main memory (RAM)
	- Program Code
		- .text
	- Comments
		- `#` on a line

- RARS
	- System Call
![ecall](Pic/ecall.png)

li a7, [Number]
ecall
调用上述function



机器码占4个字节