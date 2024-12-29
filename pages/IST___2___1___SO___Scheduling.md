- References
	- ![15 - Escalonamento - introducao.pdf](../assets/15_-_Escalonamento_-_introducao_1735459487251_0.pdf)
	- ![16 - Escalonamento - unix e linux.pdf](../assets/16_-_Escalonamento_-_unix_e_linux_1735459490265_0.pdf)
- Notes
	- Scheduling Policies
		- Interactive Users in Shared time (Most Common)
		  collapsed:: true
			- Properties
			  collapsed:: true
				- Time slices
					- Defines a max time for each process, going through them in FIFO, moving to the next either through sys calls that wait or end of max time.
				- Dynamic Priorities
					- Allows to allocate different time slices for each process. based on how important it is. (more important get smaller slices of time as they need to be more responsive.)
				- Preemption
					- Switches to a more important process to make sure it's response time is reduced.
			- Good
			  collapsed:: true
				- Response Time based on user interaction.
		- Batch
		  collapsed:: true
			- Good
				- Productivity - Throughput
				- Turn around time
				- High Processor Usage
		- Real Time
		  collapsed:: true
			- Good
				- Deadlines
				- Predictable performance and workloads.
	- Proc Struct
		- Information for scheduling and signals.
		-