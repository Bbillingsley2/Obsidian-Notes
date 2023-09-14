
- ![[Screenshot 2023-08-28 at 11.02.58 AM.png]]

- An assembly program can be divided into three sections:
	- the data section
		- used for declaring initialized data or constants 
			- this data does not change at runtime 
		- This section declares constant values, file names, buffer size etc.
		- The syntax for declaring data section is:
			- SECTION .data 
	- the bss section
		- used for declaring variables 
		- syntax for declaring bss section is:
			- SECTION .bss
	- the text section
		- used for keeping the actual code
		- must begin with the declaration *global main*
			- this tells the kernel where the program execution begins
		- the syntax for declaring text section is:
			- SECTION .text
			- GLOBAL main
			- main:


# Assembly Language Statements

- Assembly language programs consist of three types of statements:
	- executable instructions 
		- tells the processor what to do
		- each instruction consists of an operation code (opcode)
		- each executable instruction generates one machine language instruction 
	- assembler directives or pseudo-ops
		- tells the assembler about the various aspects of the assembly process
		- these are non-executable and do not generate machine language instructions
	- macros
		- a text substitution mechanism (like C pre-processor macros)

### Syntax of Language Statements

- They are entered one statement per line
- each one follows the following format:
	- [label] mnemonic operands ;comment

- Example: 
	- ![[Screenshot 2023-08-28 at 11.21.10 AM.png]]


# Labels or Identifiers 

- Valid characters in labels are letters, numbers, _ , $, #, @, ~, . , and ?
- Of the special characters, you should only use underscores
- An identifier may not begin with a digit and may have up to 4095 characters (do not make them that big)
- You cannot use identifiers that are the same as the names of instructions, directives, registers, and other words that have a special meaning to the assembler 
	- You can in NASM by using the $, but dont do it


# Program Format 

- indent for readability 
	- start labels in column 1
	- align mnemonics and trailing comments where possible

- Assembler code is not case-sensitive, but it is common practice to:
	- Use lowercase letters for instructions
	- Use uppercase letters for directives 


# Compiling and Linking an Assembly Program in NASM

- Type the above code using a text editor and save it as hello.asm
- Make sure that you are in the same directory as where you saved hello.asm
- To assemble the program, type
	- nasm -f elf32 -o hello.o hello.asm
- if there are any errors, fix them and recompile.
	- Add -g to the above command to include debugging symbols for GDB
- Otherwise, an object file of your program named hello.o will be created 
- To link the object file and create an executable file named hello, type 
	- ld hello.o -m elf_i386 -o hello
- execute the program by typing ./hello