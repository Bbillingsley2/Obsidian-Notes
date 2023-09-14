
### Chapter 1

- How is it actually stored in RAM? In one byte numbers (1s and 0s) 
- How is it representeed to the user? It is fed through a representation of the ASCII table and match the value with a character and then output the character
- Difference between a binary file and a text file?
- What are bits and bytes? 
		-  8 bits = 1 byte
- How is memory addressed in a computer? 
- What is machine language? The language that the computer processor can execute the code. Opcodes and Operands
- What is an executable file? A file consisting of machine code and data and directives of how to load the data. Composed of instructions that can be executed by the processor
- What are the steps to compilation? source code being processed and put in a compiler 
- What is a command shell and how does it behave? (Slide 8)
- How does the computer treat types? 
- Type sizes sizes on a 64-bit x86 machine for shorts, ints, longs (Linux,OS X, Windows)
		- shorts =  
		- ints =
		- longs =
- What is the program counter? A special register in the hardware that has the address of the next instruction it needs to execute
- What is the basic fetch-and-execute cycle? 
- What is an instruction set architecture? The ISA is the set of machine instructions that the machine knows
- What is the ALU? Arthimetic and Logic Unit that does the decoding and running of the instruction
- What is the basic instructions found in an ISA? The jump, group of adding and delete instructions, mode instructions, store instructions, basic operations that are in registers
- Steps to executing a Program:
		- here
- Define caching: It takes data from slow memory and puts it in fast memory and work on them while they are in fast memory
- What is the purpose of an OS? What are the beautification and resource management principles?
- Describe concurrency: the idea of having multiple programs running and not necessarily running instructions at the same time, if they are running instructions at the same time, they are parallel
- Define context switching: Where you have programs in memory but not enough processors to run them all so you hop between which programs to run for a little while
- What is a thread? 
- How does a thread compare to a process? Processes dont share memory. Processes can have multiple threads. 
- What is virtual and logical memory? 
		- Logical memory: addresses you can use of a program when they are logical when they do not directly map to a location, they go through a mapping function
		- Virtual memory: 
- Basic memory organization of a process (slide 22)
- Basics of how a file is represented on most computer systems today: as a collection of bytes: 



### Chapter 2

- Why can overflow occur when munipulating numbers? Sometimes in binary math, you have to carry and that causes overflow because you need more bits to represent the number
		- Integer math is associative, floating point math is not
- Know how to represent a number in binary and hexadecimal. We represent the numbers with the MSB (Most significant bit) first and the LSB (Least significant bit) last.
- Be able to convert from binary to base 10 and vice versa. Be able to convert from hex to base 10 and vice versa. Be able to convert from binary to hexadecimal and vice versa.
- Know how to add binary numbers. Know how to represent a negative number in two's complement to represent the negative version before adding them.
- Be able to add and subtract hexadecimal numbers. Be able to carry and borrow.
- Know the size of each data type depicted on slide 26.
- Know what little endian and big endian byte ordering is. Know how data would be represented in memory if the byte ordering is little endian.
- How are strings represented in memory and how are they displayed to the user via their ASCII representation?
- Be able to apply the bitwise operators to bytes of memory.


### Chapter 6

- What is locality of reference, temporal locality, and spatial locality? Give examples
		- Reference of memory can be clustered. They can also cluster in space. Examples: iterating through an array (spatial locality)
- What is the difference between DRAM and SRAM and what memories use them?
		- One is more expensive than the other
- What is persistent storage is and what is the devices that implement this form or storage? NVMe SSDs 
- How does a hard drive work? Metal platters that spin around and another motor slides back and forth and has cylinders
- What is access time, seek time, rotational latency, and transfer time? 
- What is a solid state drive (the technology it is based on) and the positive and negative characteristics when compared to hard drives?
- Processor speed increases have been outpacing memory speed increases.
- How does a web browser, OS, or database server exploit temporal and spatial locality?
- What is a stride-k reference patter?
- Memory Hiararchy (Slide 18) 
- Cache hit and cache miss and how to calculate the cache hit and miss as a percentage
- Know the issues with caching and writing. Know what a write through cache is. Know what a delayed cache is. Know the advantages and disadvantages of each.
- Know what hit time and miss penalty are.





