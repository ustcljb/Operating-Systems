# Operating-Systems
## Processes
- Program vs process
   - Program is passive entity stored on disk (executable file)
   - Process is active
   - Program becomes process when executable file loaded into memory
- A process includes
   - the program code (the **text** section)
   - the current activity (the value of the **program counter** and the contents of the **processor's registers**)
   - **stack** (storing temporary data)
   - **data section** (storing global variables)
   - **heap** (storing dynamically allocated data)
- Diagram of process state
![diagram_of_process_state](https://github.com/ustcljb/operating-systems/blob/master/figures/diagram_of_process_state.png)
- Context switch
   - When CPU switches to another process, the system must save the state of the old process and load the saved state for the new process via a context switch
   
- Independent process vs cooperating process
   - Cooperating processes need interposes communication (IPC)
   - Two models of IPC: **shared memory** and **message passing**
   ![shared_memory_message_passing](https://github.com/ustcljb/operating-systems/blob/master/figures/shared_memory_message_passing.png)
   - Synchronization
   
## Threads
- Process vs thread
   - Each process provides the resources needed to execute a program. A process has `a virtual address space, executable code, open handles to system objects, a security context, a unique process identifier, environment variables, a priority class, minimum and maximum working set sizes, and at least one thread of execution`. Each process is started with a single thread, often called the primary thread, but can create additional threads from any of its threads.
   - A thread is an entity within a process that can be scheduled for execution. All threads of a process share its virtual address space and system resources.
   - A thread is an independent set of values for the processor registers (for a single core).
- Single-threaded vs multi-threaded processes
![single_vs_multi-threaded](https://github.com/ustcljb/operating-systems/blob/master/figures/single_vs_multi-threaded_processes.png)
- Concurrency vs parallelism
   - **Concurrency** is when two or more tasks can start, run, and complete in overlapping time periods. It doesn't necessarily mean they'll ever both be running at the same instant. For example, multitasking on a single-core machine.
   - **Parallelism** is when tasks literally run at the same time, e.g., on a multicore processor.
   - It is possible to have concurrency without parallelism.
   ![concurrency_vs_parallelism](https://github.com/ustcljb/operating-systems/blob/master/figures/concurrency_vs_parallelism.png)
   
## CPU scheduling
