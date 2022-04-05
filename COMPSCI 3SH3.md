# Chapter 1

### Operating System

* Operating System is a program that acts as an intermediary between a user of a computer and the computer hardware
  * They vary dramatically in accomplishing this:
    * Mainframes - primary function is to optimize CPU utilization
    * Smart phones - Ease of use
    * PC - Everything

* Operating system goals:
  * Efficient use: Ensure efficient use of a computer's resources
  * User convenience: Provide convenient methods of using a computer system
  * Non interference: Prevent interference in the activities of its users

### Computer System Structure

* Computer system can be divided into four component:

  * **Hardware** - provides basic computing resources
    * CPU, memory, I/O devices

  * Operating system
    * Controls and coordinates use of hardware among various applications and users

  * Application programs
    * Define the ways in which the system resources are used to solve the computing problems of the users
      * Word processors, compliers, web browsers, database system

  * Users
    * People, machines, other computers

### What Operating Systems do?

* OS is a **resource allocator**
  * Manage all resources(such as memory, CPU, I/O devices)
  * Decides between conflicting requests for efficient and fair resource use

* OS is a **control program**
  * Controls execution of programs to prevent errors and improper use of the computer

### What is an OS?

* Primarily an OS consists of the:
  * **Kernel**
    * Part that stays in main memory (the one program always running on the computer)
    * Controls the execution of all other programs
      * other programs(system or user) interact with it through **System calls** (are routines mostly written in a high level language.)

### Computer System Organization

* One or more CPUs, device controllers connect through common bus providing access to shared memory
* Concurrent execution of CPUs and devices competing for memory.



### I/O Structure I

* A general-purpose computer system consists of CPUs and multiple device controllers that are connected through a common bus.
* Each **device controller** is in charge of a specific type of devices. Depending on the controller, more than one device may be attached.
* A device controller maintains some local buffers storage and a set of special-purpose register.
* The device controller is responsible for moving the data between the peripheral devices that it controls and its local buffer storage.
* Typically, in OS there is a device driver for each device controller.
* This device driver provides the operating system with a uniform interface to the device.

### I/O Structure II

* To start an I/O operation
  * The device driver loads the appropriate registers within the device controller.
  * The device controller, in turn, examines the contents of these registers to determine what action to take (read a character from the keyboard)
  * The controller starts the transfer of data from the device to its local buffer.
  * Once the transfer of data is complete, the device controller sends an interrupt signal to CPU.
  * CPU transfers control to ISR which handles this request.

### Computer System Operation - Computer Startup

* When a computer system is switched on or rebooted
  * It automatically loads a program (**bootstrap program**) stored on a reserved part of an I/O device typically a disk and starts executing the program.
  * The bootstrap program then
    * Loads the Operating system kernal
    * and system programs (system daemons)
  * The kernal and system programs run all the time on the computer provide services.
  * After the system is fully booted it waits for an **event** to occur.

### Computer System Operation - Interrupts

* An operating system is **event driven** and events occur by interrupts. Therefore, OS is **interrupt driven**.
* Interrupt requires the operating system stop and figure out what to do next.
* **Interrupt**: A mechanism that enables a device/software to notify CPU that it needs attention.
* An interrupt is caused by:
  * Signal to CPU from a device attached to a computer via system bus
  * An executing program within the computer through system calls.
* A **trap** or **exception** is a software-generated interrupt caused either by an error or a user request.

### Interrupt Handling I

* When an interrupt occurs:
  * CPU stops executing current task
  * The operating system preserves the stat of the CPU by storing registers and the program counter
  * Transfers execution to a fixed location, which has the starting address of **Interrupt Service Routine (ISR)**
  * ISR handles the interrupt, after which
  * Interrupted process resumes its execution

### Interrupt Handling II

* Implementing ISR as a routine is slow and therefore inefficient.
* Since only predefined interrupt exist, a table of pointers to the various interrupt routines is used instead.
* This table of addresses is called **Interrupt vector**

### Storage Structure

* CPU can access only main memory (**RAM - Random access memory**)
  * For programs to run, they must be stored in main memory.
  * Main memory is volatile (lost data with loss of power)
  * Need secondary storage (Hard disk drives) to store data permanently and in large quantities
* All forms of memory provides an array of bytes, and each byes as its own address

### Caching

* **Cache** is a faster storage system than main memory and is located very closer ot CPU
* When CPU needs a particular piece of information it first checks in cache, if it finds it, it is called a 'HIT'
* If the information is not in the cache it called a 'Miss'
* CPU then gets information from main memory and places a copy of it in the Cache.
* Careful selection of cache size and replacement policy greatly increase the system's    performance.
* other caches implemented into the hardware

### Computer System Architecture

* A **Single processor** system has
  * One general purpose CPU
  * Possibly more than one special purposes CPUs
* Multi-processors
  * More than one general purpose CPUs
  * Advantages include: increased throughput, economy of scale, increased reliability.

### Computer-System Architecture

* Tow types of Multi-processing:
  * Asymmetric Multiprocessing:
    * Boss processor controls system
    * Each processor is assigned a special task
    * Boss process schedules/allocates processes
  * Symmetric Multiprocessing
    * Each processor perform all tasks.
    * All modern system provides support for SMP

### Multi-core Design

* Multi-processor systems can be Multi-chip or **multicore**
* Multi-core systems are efficient as on chip communication is faster and consumes less power

### Operating System Structure I

* An operating system provides the environment within which programs are executed
* **Multiprogramming:** organize jobs so CPU always has one to execute
  * A subset of total jobs in system is kept in memory
  * One job selected and run via **job scheduling**
  * When it has to wait (for I/O), OS switches to another job

### Operating System Structure II

* Timesharing (multitasking) is logical extension of multiprogramming
  * CPU switches jobs so frequently that users can interact with each job while it is running, creating **interactive** computing
  * Respond time should be <1 second
  * Each user has at least one program executing in memory -> process
  * If several jobs ready to run at the same time -> CPU scheduling

### Operating-System Operations

* Dual-mode operation allows OS to protect itself and other system components
  * User mode and kernel mode
  * **Mode bit** provided by hardware
    * Provides ability to distinguish when system is running user code or kernel code
    * Kernel mode bit = 0 and User mode bit = 1 
    * Some instructions designated as privileged, only executable in kernel mode
    * System call changed mode to kernel, return from call resets it to user
* Increasingly CPUs support multi-mode operations
  * Virtual machine manager mode for guest VMs

### Operating-System Operations - Timer

* Timer: is a hardware component that can be set to interrupt the computer after a specified period.
* Timer helps to prevent infinite loop/ process hogging resources
* To set the time period the operating system maintains a counter and sets its value, which is decremented by the physical clock.
* When counter reaches zero generate an interrupt
* Set up before scheduling process to regain control or terminate program that exceeds allotted time.

### Key functionality of an OS

* Process Management
* Memory Management
* Storage and File management
* Protection and Security

### Process

* Process is a program in execution
* Program is passive entity stored on disk (**executable file**), process is active
  * Program becomes process when executable file loaded into memory

### Kernel Data Structures

* Many similar to standard programming data structures
  * Linked lists
  * Binary search tree
  * Hash Tables
* Bitmap - string of n binary digits representing the status of n items

### Computing Environments - Virtualization

* **Virtualization**  is a technology that creates abstraction of the computer hardware, thereby creating an illusion that all its operating systems are running on it own private computer.
  * VMM provides virtualization 

* Virtualization belongs to the Emulation class of software



# Chapter 2



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
* **Swapping**: is the term used for removing a process from main memory store on disk and later bring it back in from disk to continue execution.
* **Medium - term scheduler**: used to queue swapped jobs
  * can be added if degree of multiple programming needs to decrease

### Interprocess Communication

* Processes within a system may be:
  * ***Independent***
  * ***Cooperating*** (It can affect or be affected by other processes, including sharing data)

* Reasons for cooperating processes:
  * Information sharing, computation speedup, modularity and convenience.

* Cooperating processes need **interprocess communication** (IPC)

* Two models of IPC
  * Shared memory
  * Message passing

### IPC - Shared Memory

* An area of memory shared among the processes that wish to communicate
* The communication is under the **control of the user** processes not the operating system.
* It is more complicated to set up and doesn't work as well across multiple computers.
* Used for sharing large amount of data.
* Major issues - synchronize process actions when accessing shared memory.

### IPC - Message Passing

* Operating system provides message passing capability.
* As a result, Message Passing requires system calls for every message transfer, and is therefore slower.
* However, it is simpler to set up and works well across multiple computers.

## Chapter 4

### Threads

* A traditional process has a single thread of control.
* **Multi-threaded applications** have multiple threads within a single process.
* **Thread** is a basic unit of CPU utilization.
* Process creation is many times heavy-weight while thread creation is light-weight.

### Threads in Single and Multi-threaded Processes

* Each thread consists of:
  * Thread ID
  * Program Counter
  * Set of registers
  * Stack

* They share
  * code
  * data
  * file

### Multi-threading example

* Editing word document
  * One thread can interpret the key strokes.
  * Second thread display images.
  * Third thread checks spelling and grammer.
  * Fourth thread does periodic automatic backups of the file being edited.

* Most operating system kernels are multi-threaded
  * Many threads operate in the kernel process, where each thread performs a specific task.
    * Managing devides
    * Managing memory
    * Interrupt handling

### Advantages

* **Responsiveness** - may allow continued execution if part of process is blocked, especially important for user interfaces.
* **Resources Sharing** - threads share resources by default.
* **Economy** - cheaper than process creation, thread switching lower overhead than context switching.
* **Scalability** - A single process can take advantages  of multiprocessor architectures.
* Threads enable concurrent programming and on multiple processor systems, true parallelism.

### Parallelism

* **Parallelism** implies a system can perform more than one task simultaneously

### Concurrency

Concurrency supports more than one task making progress.

### Multi-core Programming

* ***Multi-core*** or **Multiprocessor** systems puts pressure on programmers.
