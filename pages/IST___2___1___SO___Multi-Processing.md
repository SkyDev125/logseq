- References
	- ![Programacao com Processos e Tarefas 2024-25.pdf](../assets/Programacao_com_Processos_e_Tarefas_2024-25_1733609965851_0.pdf)
- Notes
	- Pseudo-Concurrency
	  collapsed:: true
		- Definition
			- Apparent multitasking through rapid switching
		- Operation
			- The operating system can only have as many Threads as there are cpu cores* running simultaneously.
				- * Certain CPU's while only having an X number of cores, can actually have an Y number of Virtual Cores (CPU Threads). So for example if a cpu has 8 cores and 16 threads, in reality the OS will consider the 16 as the total number of cores.
			- This means, that even if we create thousands of processes, the Operating System can still allow them to work, by scheduling them to operate at different time intervals (switching between processes/threads very quickly), based on their priority and user needs. 
			  id:: 6754cb9e-aca5-478f-93aa-448d2491cfb1
			- (e.g. the window on the foreground is more important than one in the background).
	- Process
	  collapsed:: true
		- Definition
			- Operating System Abstraction that allows for the execution of programs.
		- Properties
			- Similar to a Virtual Machine
			- Virtual Memory space
			- CPU User Mode
			- There's always a Parent Process except for the Process 1
			- Stores all the memory needed to continue the execution of a certain program.
			- Other info is stored... (e.g. Parent process, priority, etc..)
		- Operation
			- Can create new Threads and Child Processes
			- Exact copy of Parent's memory (Ensured by the Operating System).
				- Usually means that whenever a certain variable gets changed, either by the parent or the child, the variable is duplicated on-time. Instead of the entire memory being copied which could be very resource intensive.
			- Zombie
				- Occurs when the Process exits, making it no longer active, but still occupying a tiny portion of the memory with it's return status and PID for the parent to retrieve with wait().
		- Reserved
			- Process 0
				- Memory Management
			- Process 1
				- System Initialization
				- Adopts all Child Processes that lost their Parent.
		- Programming
			- Create new Child Process
				- ```cpp
				  #include <sys/types.h>
				  #include <unistd.h>
				  
				  pid_t fork(void); // Returns 0 to child, Child PID to Parent, -1 on ERR.
				  ```
				- Continues the execution of the program from the exact point where fork is called.
			- Close the process
				- ```cpp
				  #include <stdlib.h>
				  
				  void exit(int status); # Same as return value on int main().
				  ```
				- Finishes the process's Execution of the Calling process and returns a status to the parent (negative values usually mean an error occurred).
			- Wait for a child
				- ```cpp
				  #include <sys/types.h>
				  #include <sys/wait.h>
				  
				  pid_t wait(int *wstatus); # wstatus is the return value of the child.
				  pid_t waitpid(pid_t pid, int *wstatus, int options); # Specific child.
				  ```
				- Pauses the current Thread until a child finishes.
				- Returns Instantly if child already finished.
			- Exec
				- ```cpp
				  #include <unistd.h>
				  
				  int execl(const char *pathname, const char *arg, ...
				                         /* (char  *) NULL */)
				  ```
				- Allows for the execution of a completely different binary. With a new memory space.
				- Changes the UID/GUID to the owner of the file
	-