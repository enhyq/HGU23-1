# Introduction

## What is Computer?
 - Computer vs Calculator

 - Fundamental contructing units of a computer
    - CPU - memory
    - 

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