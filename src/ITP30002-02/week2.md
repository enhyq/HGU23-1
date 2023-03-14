# Process

## 3/9 (Thur)
![Lecture Note](img/23-03-10-14-25-59.png)

### Lecture Summary
 - What kind of problems appear when sharing a computer?
    - How to decide who should use the computer at a specific time
    - How to manage time of sharing
    - A process taking over entire space
    - A process corrupting the entire system
    - many other..
 - OS is created to solve the problems that arise when sharing a common resource (CPU and memory)

 > Time Sharing

 - Time Sharing is the concept that is used in OS to share resources among multiple processes
    - It is divided into 2 smaller concepts
        1. Mechanism
        2. Policies



## Notes from video
 - Process
   - a running instance of a program
      - program vs process
      - static / dynamic
   
 - Constitution of Program Execution Content
   - What kind of information are needed to be stored to resume process after pausing?
   1. Memory states
      - address space
      - this just stays in the memory space
   2. CPU states
      - this must be copied over to memory space to be safely stored
      - registers: general-purpose and special-purpose
      - cache: they are for performance of the CPU computation
         - When doing timesharing, cache can not be utilized most efficiently
         - performance of the cache will be degraded
      - Recent computer architecture provide some functionality to utilize cache when performin context switching
   3. I/O information
   - Above 3 informations are needed
      - They are taken **snapshot**
   
 - Life Cycle of a Process
   - Process creation
      - resource allocation
         - independent space: memory space, 
         - every process open some basic files (stdin, stdout, stderr) -> basic file resources
         - under kernel, it manages some datastructure that manages currently running process. A new object must be created
      - loading : brining binary code (program) to address space of process (from disk storage)
         - eagle(?) (eagerly) manner
         - lazy manner
            - Instead of taking the whole snapshot of the program, only part of it is taken snapshot
            - binary code
            - executable code
               - initial part of the code
            
            - **decode the metadata of the program allignment**
               - **decode**
               - **metadata**
               - **program allignment**
            
            - Questions: does the programmer have to provide the initial instruction that can be loaded in lazy manner?

 - Process
   - a running instance of an application program
   - a process is an object of OS to represent a status of a program execution
   - a process progresses in an instruction-by-instruction fashion
   - a program is a pssive entity resided in a storage (e.g. an executable file) whereas a process is an active entity of the CPU and memory status
      - a process starts when executable file loaded into memory
      - multiple users may run multiple processes for a single program
      - program -> initial memory status of a process

 - A process is an object to hold all entities to represent the running status of a program
   - CPU snapshot (kernel space)
      - Program counter
      - Registers
   - Memory snapshot (user space)
      - program code (also called text section)
      - Stack section: Function parameters, return addresses, local variables
      - Data section: memory for containing global variables
      - Heap section: memory for dynamically allocated during run time
   - **State** (kernel space)
 - An OS can make multiple processes run at the same time by **time-sharing** a processor and **space-sharing** main memory


 - Process Creation
   - A process is identified and managed via a process identifier (pid)
   - A parent process can **spawn** a child process to **delegate** a subtask
      - A process can spawn multiple children proceses
      - A parent process can run concurrently with its children processes

   - init d, system d -> usually pid = 1
      - every processor is essentially a child of init d
      - this is a **good design**
         - why?
         - Parent process - Child process
         - Caller function - Callee function
         - Multi-processing is basically to parallelize the task
            - 