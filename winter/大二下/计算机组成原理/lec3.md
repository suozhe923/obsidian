
##### Conditional Operations
>Branch to a labeled instruction if a condition is _true_, otherwise, continue sequentially
- beq rs1, rs2, L1
	- if ($rs1==rs2$) branch to instruction labeled L1
- bne rs1, rs2, L1
	- if ($rs1 !=rs2$) branch to instruction labeled L1
Unconditional branch
- beq x0, x0, L1
	- 直接跳转到L1
```c
if (i == j) f = g+h;
else f = g-h;
```

```risc-v
	bne x22, x23, Else
	add x19, x20, x21
	beq x0, x0, Exit
Else: sub x19, x20, x21
Exit:
```

- Signed comparison
	- blt rs1, rs2, L1
		- if (rs1 < rs2) brance to L1
	- bge rs1, rs2, L1
		- if (rs1 >= rs2) L1
> blt: branch if less than
> bge: branch if greater than or equal
- Unsigned comparison
	- bltu,bgeu

The assembler defines __pseudo-instructions(伪命令)__ for your convenience:
bgt x2, x3, foo (pseudo)    will become
blt x3, x2, foo (basic)

##### Basic Blocks
- A basic block is a sequence of instructions with
	- No embedded branches (except at end)
	- No branch targets (except at beginning)
	- A compiler identifies basic blocks for optimization
	- An advanced processor can accelerate execution of basic blocks

- C to RISC-V example:
```C
int A[20];
int sum = 0;
for (int i = 0; i < 20; i++)
	sum += A[i];
```
Assume x8 holds pointer to A
Assign x10=sum, x11=i
- origin:
1.	add x10, x0, x0 # sum=0
2.	add x11, x0, x0 # i=0
3.	addi x12,x0,20 # x12=20
4. ==loop==:
	bge x11, x12, ==exit==
5. slli x13, x11, 2 # i * 4
6. add x13, x13, x8 # A + i
7. lw x13, 0(x13) # *(A + i)
8. add x10, x10, x13 # increment sum
9. addi x11, x11, 1 # i++
10. beq x0, x0, loop # iterate
11. ==exit==:
- Optimized(优化版)
1. add x10, x0, x0 # sum=0
2. add x11, x0, x0 # i=0
3. addi x12,x0,80 # x12=20x4
4. ==loop==:
	bge x11, x12, exit
5. add x13, x11, x8 # A + i
6. lw x13, 0(x13) # *(A + i)
7. add x10, x10, x13 # increment sum
8. addi x11, x11, 4 # i++
9. beq x0, x0, loop # iterate
10. exit: