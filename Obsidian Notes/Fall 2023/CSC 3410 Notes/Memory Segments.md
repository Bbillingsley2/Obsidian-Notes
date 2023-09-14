
- The three sections of an assembly program (.text, .data, .bss) represent various memory segments as well
	- If you replace the section keyword with segments, you will get the same result 

- A segmented memory model divides the system's memory into groups of independent segments
	- These are referenced by pointers (addresses) located in the segment registers 

- Each segment is used to contain a specific type of data 
	- Types of segments:
		- One segment is used to contain instruction codes
		- Another segment stores the data elements 
		- A third segment keeps the program stack

- We can specify various memory segments as:
	- Data segments
		- represented by .data section and the .bss
		- The .data section is used to declare the memory region, where data elements are stored for the program
			- This section cannot be expanded after the data elements are declared, and it remains static throughout the program
		- the .bss segment is also a static memory section
			- contains uninitialized data, variables and constants 
			- the .bss memory is zero-filled
	- Code segments
		- represented by .text section 
		- defines an area in memory that stores the instruction codes. 
			- this is also a fixed area
	- Stack
		- this segment contains data values passed to functions and procedures within the program 


### Registers 

- Big four registers:
	- eax
	- ebx
	- ecx
	- edx

- Registers speed up the processor operations by being included by the processor for internal memory storage locations
	- very fast compared to RAM because they are on the processor 
	- no memory bus to traverse 
	- small in size 

- Registers store data elements for processing without having to access the memory 
	- A limited number of registers are built into the processor chip 

### 32-bit Intel Processor Family Registers

- There are ten 32-bit and six 16-bit registers in IA-32 architecture 

- The registers are grouped into three categories:
	- general registers
	- control registers 
	- segment registers 

- the general registers are further divided into the following groups:
	- data registers
	- pointer registers
	- index registers 


#### Data registers 

- 4 32-bit data registers are used for arithmetic, logical, and other operations 

- These 32-bit registers can be used in three ways:
	- complete 32-bit data registers: EAX, EBX, ECX, EDX
	- 16-bit lower halves of the 32-bit registers: AX, BX, CX, DX. 
	- 8-bit lower and higher halves of the above-mentioned 16-bit registers: AH, AL, BH, BL, CH, CL, DH, DL

- ![[Screenshot 2023-08-30 at 11.19.29 AM.png]]


- Some data registers have specific use in arithmetical operations:

	- EAX is the primary accumulator
		- used in input/output and most arithmetic instructions
			- Example: in multiplication operation, one operand is stored in EAX or AX or AL register according to the size of the operand 


	- EBX is known as the base register (mostly traditional)
		- can be used in indexed addressing (but so can the others)

	- ECX is known as the count register 
		- stores the loop count in iterative operations 


	- EDX is known as the data register 
		- also used in input/output operations
		- also used with EAX register along with EDX for multiply and divide operations involving large values 



#### Pointer Registers 


- Pointer registers are 32-bit EIP, ESP, EBP
- There are 3 categories of pointer registers:
	- Instruction Pointer
		- the EIP register stores the offset address of the next instruction to be executed 
		- EIP in association with the CS register (CS:EIP)
			- together, they give the complete address of the current instruction in the code segment 
	- Stack Pointer
	- Base Pointer 