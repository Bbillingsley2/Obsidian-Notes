
- Each family of processors has its own set of instructions
	- Getting input from the keyboard, displaying information on screen, etc.
- The processor understands only machine language instructions which are strings of 1s and 0s
- Machine language is too obscure and complex
	- Assembly is symbolic and thus easier to program
		- It allows the same fine-grained control to the machine as machine language 
		- More fine-grained control than any high level language 


Advantages of Assembly 

- Having an understanding of assembly makes one aware of:
	- How programs interface with OS, processor, and BIOS
	- Requires less memory and possibly the execution time
	- Allows a programmer to take advantage of hardware-specific instructions and devices 
	- Suitable for time-critical jobs 
	- Most suitable for writing interrupt service routines, device drivers, and other operating systems code
		- Java, Phyton, etc. are incapable of doing this
		- C/C++ compilers allow embedded assembly 


Basic Features of PC Hardware

- A bit is the most basic unit of information in a computer
	- Often represents "on" and "off" by 1s and 0s
- A byte is a group of 8 bits 
	- Smallest possible addressable 

Processor Data Sizes

- The processor supports the following data sizes:
	- Word: a 2 byte data item
	- Doubleword: a 4 byte data item
	- Quadword: a 8 byte data item
	- Paragraph: a 16 byte data area
	- Kilobyte: 1024 bytes (NOT 1000)
	- Megabyte: 1,048,576 bytes

Number Representation

- All numbers in a computer are represented as bits
- We represent a bit in base 2 (binary)
- Base 10 uses 0-9 while base 2 uses 0 and 1

	Binary Numbers 

	- Base 2, using bits (binary digits) 0 and 1
	- 10111 = 1 x 1 + 1 x 2 + 1 x 2^2 + 0 x 2^3 + 1 x 2^4

	- Digits are 1 and 0 
		- 1 is true
		- 0 is false
	
	- MSB = Most significant bit 
	- LSB = least significant bit 

		Binary Addition 

		- Starting with the LSB, add each pair of digits, include the carry if present 


Hexadecimal Numbers 

- Base 16 
		Digits:
		0-9 same as decimal 
		A for 10
		B for 11
		C for 12 
		D for 13
		E for 14
		F for 15

	- 5CB = 11 x 16^0 (1) + 12 x 16 + 5 x 16^2 = 11 x 1 + 12 x 16 + 5 x 16^2

Translating Binary to Hexadecimal 

- Each hexadecimal digit corresponds to 4 binary digits

Hexadecimal Addition



Hexadecimal Subtraction 



Integer Storage Sizes

- Standard sizes:
	- byte = 8
	- word = 16
	- doubleword = 32
	- quadword = 64

- Ranges of Unsigned Integers:
	- Unsigned byte
		- Range (low-high) = 0 to 255
	- Unsigned word 
		- Range (low-high) = 0 to 65,535
	- Unsigned doubleword 
		- Range (low-high) = 0 to 4,294,967,295
	- Unsigned quadword 
		- Range (low-high) = 0 to a lot 

- Signed Integers
	- The highest bit indicates the sign. 1 = negative, 0 = positive 
		- 11110110 - negative
		- 00001010 - Positive
	- If the highest digit of a hexadecimal integer is > 7, the value is negative.

- Two's Complement
	- Negative numbers are stored in two's complement notation
		- Represents the additive inverse 

	- Starting value = 00000001
	- Step 1: reverse the bits = 11111110
	- Step 2: add 1 to the value from Step 1 = 11111110 + 00000001
	- The sum is the two's complement representation = 11111111


- Addressing Data in Memory
	- The processor stores data in reverse-byte sequence
		- (the low-order byte is stored in low memory address and high-order memory address)
	- If the processor brings the value 0725H from register to memory, it will transfer 25 first to the lower memory address and 07 to the next memory address