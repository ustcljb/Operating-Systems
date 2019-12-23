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
![diagram_of_process_state]()
- Context switch
   - When CPU switches to another process, the system must save the state of the old process and load the saved state for the new process via a context switch
   
- Independent process vs cooperating process
   - Cooperating processes need interposes communication (IPC)
   - Two models of IPC: **shared memory** and **message passing**
   ![shared_memory_message_passing]()
   - Synchronization
