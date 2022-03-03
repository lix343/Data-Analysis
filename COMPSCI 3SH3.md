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

### Exec() System call

* The ***exec()*** system call used right after ***fork()*** enables the child process to execute a different program than the one it inherits from its parent process
* This act is also referred to as an **overlay**
* There is a family of ***exec()*** functions, all of which have slightly different characteristics. 

### Process Termination

* After executing the last statement, a process is terminated.
  * Implicitly - using the return statement
  * Explicitly - using the **exit()** system call

* Process resources are deallocated by operating system.
* Parent may terminate the execution of children processes using the **abort()** system call. Some reasons for doing so:
  * Child has exceeded allocated resources.
  * Task assigned to child is no longer required.
  * The parent is exiting and the operating system does not allow a child to continue if its parent terminates.

* Some operating systems do not allow child to exist if its parent has terminated. If a process terminates, then all its children must also be terminated.
  * **Cascading termination**. All children, grandchildren, etc. are terminated
  * The termination is initiated by the operating system.

### Child Process - Termination status

* When a child process terminates, the parent can know the child's exit status using the **wait()** system call.

* The call returns status information and the pid of the terminated process.

  ``` c
  pid = wait(&status)
  ```

* Unix maintains the tale of processes. This table contains the list of all processes running and includes the process status.

* If a parent process terminates, its entry is removed from the table.

* If a child process terminates, its entry is removed from the table only after the parent process invokes a **wait()**.

* If no parent waiting (did not invoke **wait()**) process is a **zombie**.

* if parent terminated without invoking **wait()**, process is an **orphan**.

### Process Scheduling

* Goal: Maximize CPU use, quickly switch processes onto CPU for time sharing.
* Process scheduler must meet the above objectives by implementing suitable scheduling policies.
* Operating system maintains **Scheduling queues** of processes.
  * **Job queue** - set of all processes in the system
  * **Ready queue** - set of all processes residing in main memory, ready and waiting to execute.
  * **Device queues** - set of processes waiting for a I/O device. Usually a separate device queue for each device

* Processes migrate among the various queues.
* Scheduler:  selected a process from a queue. 

### Schedulers

* **Short-term scheduler** or we called it **CPU scheduler** - selects processes should be executed next and allocates CPU.
  * Sometimes the only scheduler in a system.
  * Short-term scheduler is invoked frequently

* **Long-term scheduler** or we called it **Job scheduler** - selects which process should be brought into the ready queue.
  * 
