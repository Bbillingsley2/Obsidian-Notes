#CSC2770

### Computer Systems
- A computer system consists of hardware and systems software thta work together to run apps and/or programs
- Systems programming is the study of the operation of such systems and gaining the ability to program such systems. The best programmers are the ones that know whats going on under the hood
- The program "Hello World" is an example of how important it is to understand computer systems

### Representation of Hello World
- The hello world source code is represented in memory (and stored on disk) as a sequence of bytes,  where bytes are just numbers. Each byte represents one character which is encoded according to the ASCII table. Each line is terminated by a special invisible character called the newline character which is number 10 on the ASCII table. The files that hold this data are called text files. All other files are called binary files.

### How Programs Are Translated
- The text file that contains the "hello world" program cannot be executed by a computer
- Before the computer can run the program, the textfile must be convertes into the representation that the computer understands
- The only representation that the computer can read is called machine langauge and it is made up of machine language instructions. The file that contains this is called an executable file.

![[Screenshot 2023-01-30 at 2.52.08 PM.png]]

- Undertanding compilation can help us:
	- Optimize program performance
	- Understanding link-time erros
	- Avoiding security holes
	- Write mixed langauge programs (in C, C++, Java, Python)
	- Understand how scoping works and take advantage of it
	- etc.

### How Processors Read and Interpret Instructions
- Once a source code file has been turned into an executable file, you can run it by either the command line or double clicking its icon.
- If the first word of the command line does not correspond to a built in shell command, then the shell assumes that it is the name of an executable file that it should load and run.
- The shell then prints a prompt and waits for the next input of the command line.

![[Screenshot 2023-01-30 at 2.58.01 PM.png]]

### Main Memory
- The main memory  is a temporary storage device that holds both a program and the data it manipulates while the processor is executing the program
	- The main memory holds both the data and code
- Physically, the main memory consists of a collection of dynamic random access memory (DRAM) chips
- Logically, memory is organzied into a linear array of bytes, each with its own unique address (array index) starting at 0
- The sizes of data items that correspond to C program varibales vary according to type
	- On a X86-64, a short is 2 bytes, an int is 4 bytes, a long is 8 bytes, a long long is 8 bytes, a float is 4 bytes, and a double is 8 bytes
	- A long on windows is 4 bytes because windows sucks

### Processors
- The central processing unit (CPU) or simply processor, is the engine that interprets instructions stored in main memory
- It has a word-size register called the program-counter (PC) that points at (contains the address of) some machine langauge instruction in main memory
- The processor repeadly runs the instructions that the program counter is pointing at. After executing an instruction, the processor updates the program counter to point at the next instruction
- A processer operates according to a very simple instruction execution model, defined by its instruction set architecture. Instructions execute in strict sequence.
- Each instruction execution requires a number of steps, called the fetch-and-execute cycle which consists of the following:
	- The processor reads the instruction from memory pointed at by the PC
	- Then it interprets the bits in the instruction and performs some simple operation dictated by the instruction
	- Then it updates the PC to point at the next instruction
- These instructions manipulate main memory, registers, or I/O ports (special device memeory addresses used to manipulate off-chip I/O devices such as SSDs and USB devices)
- The arithmetic/logic unit (ALU), which is part of the processor, computes new data and address values
- Some examples of the simple operations that the CPU might carry out are:
	- Load: Copy a byte or a word from main memory into a register, overwriting the previous contents of the register
	- Store: Copy a byte or a word from a register to a location in main memory, overwriting the contents of that location.
	- Add, Subtract, Divide, Multiply, and other operations: Copy the contents of two registers to the ALU, perform an arthimetic operation on the two words, and store the result in a register, overwriting the previous contents of that register
	- Jump: Extract a word from the instruction itself and copy that word into the program pounter (PC), overwriting the previous value of the PC.

- Various models of CPUs that implement the same instruction set may have different implementations of that instruction set (with different optimizations). This is called having different microarchitectures

### Caching

- As can be seen from the example above, a lot of a program's time can be spent moving data around.
- To spped things up, the OS will do a bulk read from the slow disk device into faster memory called a cache.
- Then each subsequent access to the file reads the requested bytes from the last cache instead of the slow device

### Memory Hierarchy

![[Screenshot 2023-02-01 at 3.04.36 PM.png]]