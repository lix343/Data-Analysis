# Chapter 3

### Types of Processes

* Processes can be describe as either:
  * I/O-bound process - spends more time doing I/O than computations, many short CPU bursts
  * CPU-bound process - spends more time doing computations ; few very long CPU bursts

### Threads

* Modern systems allow a process to have multiple threads associated with it.
* These threads can execute concurrently.

### Context Switch

* ***Context*** of a process is represented in the PCB(value of CPU registers, the process state etc.)
* When CPU switches to another process, the system must ***save the context*** of the old process and load the ***saved context*** for the new process. The process is called ***context switching***.
* Context-switch is an overhead; the system does no useful work while switching
  * The more complex the OS and the PCB -> the longer the text switch

* Time dependent on hardware support
  * Some hardware provides multiple sets of registers per CPU -> multiple contexts loaded at once

### CPU Switch From Process to Process

### Operations On Processes

* System must provide mechanism for:
  * Process creation
  * Process termination

#### Process Creation

* Every process is given an integer identifier called the ***Process identifier(pid)*** 
* A process ***parent process***  can create another process ***child process***
* In addition to PID of a process, its PPID is also stored as well

### Parent - Child Sharing

* Resources sharing options
  * Parent and children share all resources
  * Children share subset of parent's resources
  * Parent and child share no resources

* Execution options
  * Parent and children execute concurrently
  * Parent waits until children terminate

* Address space sharing options:
  * Child is a duplicate of parent (has the same program and data as the parent)
  * Child has a new program loaded into it

### Creating Processes in Linux/Unix

* **fork()** system call is used to create a new process
* **fork()** takes no arguments and return a process ID (in the parent)
* The new process created by fork becomes the child process of the calling process
* This child process has the same environment as its parent; that is, it is an exact copy of the parent with only a different process ID.
* After a new child process is created, both the parent and child will execute the next instruction following the **fork()** system call. 
