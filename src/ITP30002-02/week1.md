# Introduction

## What is Computer?
 - Computer vs Calculator

 - Fundamental contructing units of a computer
    - CPU - memory

 - What is OS?
   - "a body of **software** that enable various programs to run effectively and efficiently on computer with different hardware devices"
   - suit of differnet kinds of program
   - work as a **platform** for application program and hardware devices
      - **platform** where various parts come to gether and communicate together... (???)
   - means a **suite of system programs** which support construction and operation of application programs


 - Motivation
   - sophiscated calculator?
   - What is computer?
      - Processor + Memory (Von Neumann)
      - Memory is just a storage of array of bytes
      - Processor -> **PC**
      - What happens? 
         - processor "fetch" the code from memory
         - "decode"
         - execute
         - store
   - Constructing a software system by combining existing ones
   - importing progrmas from other systems
   - managing a diversity and variety of hardware devices
   - providing interactive features in software system (eg. networking)
      - to run things simultaneously the definition of computer was not enough (processor + memory)
   - Problems
      - portability issue (hardware-dependency)
      - interoperatability issue
      - scheduling issues
      - reourse management issue (efficiency and scalability)
      - safety & security issues
         - some program could access some sensitive data on stored on my computer

 - Approach -> solution to addressed problems
   1. **Virtualize a computer system**
      - provide a conistent and simple view to application and programmers (for *portability*)
      - provide *common interfaces* for an application program to communicate with hardware units and other application programs (for *interoperatability*)
      - distribute hardware resources to efficiently serve request from application programs (for *concurrency*, *efficiency* and *scalability*)
      - forbid an application to access the critical control and internals of a computer system and the other programs (for safety and *security*)
   2. Divise different policies of coordinating application programs and then use a suitable one at a specific context

 - Realizing those two concepts is the key to understanding of what is OS


 - Solution -> OS Kernel
   - Have **library** programs that provide "helper" function with common interfaces to application programs
      - for accessing HW components and for communicating with other programs
   - Let these helper functions take th econtrol of and execution form its caller to do sensitive operations under protection from the caller application
      - It's more like "officer" than just "helper" 
      - Extends a computer architecture to provide a special instruction to call these officer functions (requires HW support)
      - system call
   - When they work. officer functions not only serve request, but also regulate and manage the resources that the application uses, especiallly in consideration with other application programs in the system
      - Then it's more like "governor" than "officer"

 - Solution -> System Progrmas
   - To make a human user and an application easily interact each other, there exists parts of operating systems running upon kernel called *system programs*
      - e.g. compiler, linker, loader, shell, service daemons , ...

 - Solution -> Abstraction
   - 3 models
      1. Process
         - an abstract object representing a running instance of a program and all resources that it uses
      2. Virtual memory
         - an abstraction of memory locations (address space)
      3. File system
         - an abstract object for communication channel (streams)
            - to storage devices (i.e. permanent memory)
            - to other programs
            - to other systms via network


 - Concurrency
   - each program making continuous progress

 - When program is running, memory translation is always happening
   - by frame pointer (FP)
   - and the FP is managed by the OS

# Ch2 Introduction to Operating Systems

 - Running Program
    - fetch - decode - execute -> repeat (Von Neumann model)
 - OS
    - primary goal: make system **easy to use**
    - method: **virtualization**
    - virtualization
        - OS referred to virtual machine
        - physical resource -> virtual form
        - OS exports few hundred **system call**s for application to use
            - can also say that the OS provides a **standard library** to applications
    - resource manager
        - resource: CPU, memory, disk 

 - CRUX OF THE PROBLEM
 - "how does the operating system virtualize resources?"
    - OS implements **mechanisms** and **policies**

## 2.1 Virtualizing the CPU
 - Creating an illusion that the system has a large number of virtual CPUs
    - run many programs at once -> virtualizing the CPU
    - how to decide which should run at specific time?
        - **policy**

    - resource manager
## 2.2 Virtualizing Memory
 - model of physical memory
    - simply just an array of bytes
 - virtualizing memory
    - private virtual address space

## 2.3 Concurrency
 - Problems that arise when working with many thigs at once
    - OS, modern multi-threded programs
    - **Thread**:
        - function running within the same memory space as other functions
        - more than one of them active at a time
        - Q: What does it mean by active?
 - CRUX OF THE PROBLEM
    - "How can we use primitives and mechanisms to solve the problems of concurrency?"
 - problems occur when reading file at the same time
    - because load, update, write instructions are not executed **atomically**

## 2.4 Persistence
 - DRAM is volatile
 - I/O device
    - hard drive, solid-state drives
 - OS -> manage disk using program -> file system
 - disk space is shared (not virtualized like CPU and memory)
 - when creating and writing to file
    - open(), write(), close(); these **system calls** are routed to **file system** which handles the request and return result