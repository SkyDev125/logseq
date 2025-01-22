public:: true

- References
	- ![15 - Escalonamento - introducao.pdf](../assets/15_-_Escalonamento_-_introducao_1735459487251_0.pdf)
	- ![16 - Escalonamento - unix e linux.pdf](../assets/16_-_Escalonamento_-_unix_e_linux_1735459490265_0.pdf)
- Notes
	- Scheduling Policies
	  collapsed:: true
		- Interactive Users in Shared time (Most Common)
			- Properties
			  collapsed:: true
				- Time slices
					- Defines a max time for each process, going through them in FIFO, moving to the next either through sys calls that wait or end of max time.
				- Dynamic Priorities
					- Allows to allocate different time slices for each process. based on how important it is. (more important get smaller slices of time as they need to be more responsive.)
					- FIFO per Min priority queue. (0 - High priority, N - Low priority).
					- Negative values are special, when processes got blocked in the kernel level. need to be processed asap.
				- Preemption
					- Switches to a Higher priority process  when it appears to make sure it's response time is reduced.
			- Good
			  collapsed:: true
				- Response Time based on user interaction.
		- Batch
		  collapsed:: true
			- Good
			  collapsed:: true
				- Productivity - Throughput
				- Turn around time
				- High Processor Usage
		- Real Time
		  collapsed:: true
			- Good
				- Deadlines
				- Predictable performance and workloads.
	- Process Struct (Unix)
	  collapsed:: true
		- Info
			- Information for scheduling and signals.
			- Needs to always be in memory.
		- Properties
			- Status
			- Priority
			- Signals sent
			- Time in memory
			- Time in CPU
			- Process ID
			- Parent Process ID
	- User Struct (Unix)
		- Info
			- Only needed while process is in Execution
			- Can be stored to disk in the meantime.
		- Properties
			- Processor Registries
			- Kernel Stack
			- UID, GID
			- Current Directory
			- Open file descriptors
			- Function Parameters.
		-