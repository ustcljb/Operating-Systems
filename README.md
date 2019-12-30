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

- CPU scheduling decisions may take place when a process:
   - Switches from running state to waiting state
   - Switches from running state to ready state
   - Switches from waiting state to ready state
   - When a process terminates
- Nonpreemptive scheduling: Once the CPU has been allocated to a process, the process keeps the CPU until it releases the CPU
   - either by terminating
   - or by switching to the waiting state. 
- Preemptive scheduling can result in race conditions when data are shared among several processes.
- Dispatcher module gives control of the CPU to the process selected by the CPU scheduler. It involves:
   - Switching context
   - Switching to user mode
   - Jumping to the proper location in the user program to restart that program
- CPU scheduling criteria
   - **CPU utilization** - keep CPU as busy as possible
   - **Throughput** - number of processes that complete their execution per time unit
   - **Turnaround time** - amount of time to execute a particular process
   - **Waiting time** - total amount of time a process has been waiting in the ready queue
   - **Response time** - amount of time it takes from when a request was submitted until the first response is produced
- Common scheduling algorithms
   - **First –come, First-serve** (FCFS)
      - Convoy effect - short process behind long process
   - **Shortest-Job-First** Scheduling (SJF)
      - Can only estimate the time of next CPU burst
      - Preemptive version of SJF is called **shortest-remaining-time-first**
      - ![Example 1](https://github.com/ustcljb/operating-systems/blob/master/figures/Shortest_remaining_time_first.png)
   - **Round-Robin** Scheduling (RR)
      - ![Example 2](https://github.com/ustcljb/operating-systems/blob/master/figures/Round_robin.png)
   - **Priority** Scheduling
      - Problem is **starvation** - low priority processes may never execute
      - Solution is **aging** - as time progresses increase the priority of the process
   - **Multilevel Queue** Scheduling: Ready queue is partitioned into separate queues, eg
      - foreground (interactive)
      - background (batch)
      - ![Example 3](https://github.com/ustcljb/operating-systems/blob/master/figures/Multilevel_feedback_queue.png)
- Thread scheduling
   - user-level: process contention scope (PCS)
   - kernel-level: system contention scope (SCS)
- Multiprocessor CPU scheduling
   - Asymmetric multiprocessing: all scheduling decisions, I/O processing, and other system activities are handled by a single processor—the master server. The other processors execute only user code
   - Symmetric multiprocessing: each processor is self-scheduling, all processes in common ready queue, or each has its own private queue of ready processes (Most common currently)
      - Load balancing
      - Push migration
      - Pull migration
- Real-time CPU scheduling
   - Soft real-time systems: no guarantee as to when critical real-time process will be scheduled
   - Hard real-time systems: task must be serviced by its deadline
   

