Chapter 8 - Exceptional Flow Control  

-   Know what interrupts are and how they behave in terms of a jump table, event, and an interrupt handler (slide 2).  Know what an interrupt handler is.  Know what happend when an interrupt handler finishes. 
**-The normal execution of your program, your processor can interrupt it and run other code. 
-When the processor detects that the event has occured, it makes an indirect procedure call (exception) through a jump table called an exception table, to an OS subroutine (exception handler) 
-Interrupt handler is a piece of a code in the OS 
-Whenever the handler finishes, one of three things can happen:
	- it returns control to the current instruction of the process which was the instruction that was executing when the event occured
	- it returns control to the instruction that would have executed next had the exception not occured
	- it aborts the interrupted program

-   Know the types of interrupts handlers described on slide 5 (hardware and system/service call)*Hardware interrupt handlers (divide by 0, seg fault), occurs when a device in your computer has a timer and when the timer ticks, runs an interrupt. System service call, which are assigned by the OS.*

-   Know what a exception table is and what it contains (as per slide 5) *an exception table is a jump table that is allocated and initialized by the OS at system boot. it contains entries that have the address of the handler for the exception of the entry*

-   Know the algorithm for invoking an interrupt handler as indicated on slide 6. *The processor fetches instructions from ram, seeing if there was interrupt, seeing what number it was, looking at the exception table, calls the handler, the handler does its job and then returns*

-   Know the characteristics of an interrupt handler as per slide 7. 
	*- the return address can either be the address of the instruction that caused the interrupt or the one after it
	-the return address is a far address so that it can return with a inter-segment jump which allows it to possibly jump from the OS kernel to the process
	-the processor also saves the program status word (a status word whose bits indicate the state of the processor)
	-typically run in kernel mode, which is a more priveleged mode than what a user level process use when they run*

-   Be able to describe how a device interrupt occurs. *Interrupts occur often asynchronously, signals a pin on the processor chip and places onto the system bus the exception number that identifies the device that caused the interrupt, and after the current instruction finishes, the processor notices that the interupt pin has gone high and reads the exception number from the system bus and calls the appropiate interrupt handler and when the handler returns, it returns control to the next instruction*

-   Know what a trap is and how it is used to provide system calls.  Know the differece between a trap and a normal function call. *Traps are intentional exceptions that occur as a result of executing an instruction and provides a procedure-like interface between user programs and the kernel known as a system call. They allow you to jump from your processor to the OS and causes a context switch into the kernel and enter a privileged mode.*

-   Know what a fault is.  Know what a page fault is. *Faults are error events that the OS may be able to correct. If it does correct it, it returns control to the faulting instruction and the CPU attempts the instruction again. Page faults are where an instruction referneces a virtual address whose correpsonding page is not resident in memory and must therefore be retrieved from disk.*

-   Know that to invoke a  Linux system call, you place the system call's number into a register and invoke a trap.  Also understand that  a system library wraps the invocation of a trap into a function call (for example, read(), write(), open(), ...)

-   Be able to define a process and identify its characteristics. *Processes are instances of a program ine execution. It is an independent logical control flow that provides the illusion that our program has exclusive use of the processor. Contains data and code. One process can't read the memory of another. Has a private address space that provides the illusion that our program has exclusive use of the memory system.*

-   Be able to describe the notion of concurrency and multitasking.  Be able to compare and contrast multitasking with parallelism. *Mustitasking is having multiple programs in memory at the same time allowing the processor to switch from one to another. Concurrency is having two process running at the same time. Parallelism is two processes running and simultaniously running instructions at the same time.*

-   Be able to, if given an example similar to what is on slide 15, identify is one or more processes are concurrent. 

-   Know what logical addressing is.  Know how logical addressing works (as per slide 15). *A logical address is generated by CPU while a program is running. Since a logical address does not physically exists it is also known as a virtual address. This address is used as a reference by the CPU to access the actual physical memory location.*

-   Be able to describe and use the fork() Linux system call.  Know how fork() behaves, and how it is used to determine the code that the child needs to execute and the code that the parent needs to execute.  Know what is meant by call once, return twice. Be able to describe and use the getpid() system call. *fork() creates a new process and is a child process. it has a unique process ID. it is used to determine which code that the child and parent needs to execute by an if statment with the return value of getpid(). call once return twice means the fork function is called once by the parent and returns twice from the parent and the newly created child.*

-   Know how to reap child processes using the wait() and waitpid() system calls.  know what a zombie is.  Know what it means that reaping a child process is non-deterministic (as far as ordering is concerned). *A process waits for its children to terminate or stop by calling wait() or waitpid(). A zombie is a terminated proces that has not yet been reaped. The reaping of a child is non-deterministic meaning that the parent does not know in what order the children will finish*

-   Be able to use the Unix execve function and know how it behaves.  Be able to use fork() and execve() together to run an program as a child process.  Know how to set up the argv[] structure.  Know the basics of how the shell works on Linux. *The execve function loads and runs a new program in the context of the current process. Returns to the calling program ony if there is an error. Unlike fork, execve is called once and never returns. It replaces the code and data from calling process with the code and data from the indicated program file. Arguments are the full path to the executable and the argv array which should be a list of strings of commands to run. and ends with 0.*

-   Know what a Unix signal is.   Know what a pending signal is, and know how many signals can be pending for a particular signal type.  Know that a process can block the receiving a signal for a particular type.  *Unix signals are higher level software form of exceptional control flow that allows processes and the kernel to interrupt other processes. A pending signal is a signal that has been sent but not recieved. There can be **at most one** pending signsal of a particular type. A process can selectively block the receipt of certain signals which means it gets delivered but the process will not respond to the pending signal until it is unblocked.*

-   Know how Unix uses process groups and understand how they are useful (see slide 34).  *Every process belongs to exactly one process group which is identified by a positive integer process group ID. The getpgrp function returns the process group ID of the current process. *

-   Know the kill command (shell command line) and what it does 

-   Know what a pipe is *a pipe `|` is a way for processes to communicate to each other by creating a job that uses two processes. the command `ls | sort` creates a foreground job consisting of two processes. The process will run ls, and sort. The shell creates a separate process job for each job. 

-   Know how to use the kill() system call *If the pid passed is greater than 0, the kill function sends the signal number to the process. If it is 0, it sends the kill signal to every process in the group of the calling process. If it’s less than 0, then it sends the signal to every process in the process group using the absolute value.*

-   Know how to register a handler with the signal() system call.  Know that SIGSTOP and SIGKILL can't be changed/caught. Know what SIG_IGN and SIG_DFL are.  Know that signal handling can be nested and how the flow of control occurs. *You can use the signal() system call to make your own signal calls. If you want to ignore the signals of type signum call SIG_IGN, if you want to use default, call SIG_DFL and the action for signals of type signum reverts to the default action. Signal handlers can be interrupted by other handlers which creates nesting of signal handling. *

-   Know the rules for safe signal handling.  You do NOT have the know the list of async safe calls. 
*1. Ensure that (a) the signal handler calls only async-signal-safe functions, and (b) the signal handler itself is reentrant with respect to global variables in the main program.
2 Block signal delivery in the main program when calling functions that are unsafe or operating on global data that is also accessed by the signal handler.