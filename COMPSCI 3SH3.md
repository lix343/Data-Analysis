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

