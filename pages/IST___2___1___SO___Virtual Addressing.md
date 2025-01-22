- References
	- ![18 - MV2 - Funcioamento enderecamento virtual.pdf](../assets/18_-_MV2_-_Funcioamento_enderecamento_virtual_1737552094522_0.pdf)
	- ![19 - MV3 - Eficiencia no enderecamento virtual.pdf](../assets/19_-_MV3_-_Eficiencia_no_enderecamento_virtual_1737552097124_0.pdf)
	- ![20 - MV4 - Algoritmos 2024-25.pdf](../assets/20_-_MV4_-_Algoritmos_2024-25_1737552099487_0.pdf)
- Notes
	- Memory Management Unit
		- Redirects "virtual addresses" to actual addresses in memory.
		- Segmentation
		  collapsed:: true
			- Cons
				- High fragmentation
				- Replaces the current block with an equal or smaller block from swap
				- the process wont use all the memory allocated for it. internal fragmentation too.
		- Pagination
		  collapsed:: true
			- Properties
				- Split in multiple small pages
				- Each process thinks it has the entire memory for itself.
				- Page table converts the Process memory to real memory
				- Unused Pages go to swap.
				- Presence Bit lets us know if the page is in primary or secondary memory
			- Pros
				- Programmer doesnt need to worry about any virtual memory
				- Better use of Real Memory
			- Cons
				- Fragmented Processes are slower
				- Instructions need to be restartable due to fragmentation of processes.
			- Calculating physical address
				- Virtual Address + Offset
		- TBL - Translation Lookaside Buffer
		  collapsed:: true
			- Stores most commonly used page addresses so it doesnt waste time going to the table and waiting for conversion
			- Small buffer (size changes based on quantum)
			- Operating system updates it each time it fails to access a specific page.
		- Memory Management Algorithms
			- Memory Allocation
			  collapsed:: true
				- Pagination
				  collapsed:: true
					- Simple
					- Finds the first free Page
					- Free Pages list
				- Segmentation
				  collapsed:: true
					- Complex
					- Recompacts Segments on frees
				- Finding Free blocks
					- Best-Fit (smallest)
					  collapsed:: true
						- List sorted by size
						- Finds the smallest that still allows for segment to fit
					- Worst-Fit (largest)
					  collapsed:: true
						- List sorted by size
						- finds the largest possible.
						- Makes it nearly impossible to get large segments
					- First-fit
					  collapsed:: true
						- Memory fragments easily
						- finds the first block available
					- Next-fit
					  collapsed:: true
						- finds the one right after the last found
						- spreads tiny blocks across the memory (bad fragmentation)
						-
			- Memory Transfer
			  collapsed:: true
				- Properties
				  collapsed:: true
					- Each process needs to have at least
					  collapsed:: true
						- A code segment
						- data segment
						- and stack in memory
					- Swapping occurs if primary memory runs out.
					- pages/segments that aren't currently in use get moved to secondary memory.
					- if all segments of a process get transferred, its called "swapped out"
				- Swapping
				  collapsed:: true
					- Focuses on low priority processes, or blocked processes
					- Has a minimum ammount of time it gives a process before swapping it again to disk.
					- Process size (many pages make it harder to swap)
				- Trashing
				  collapsed:: true
					- Occurs when multi-processing is elevated
					- And memory runs out.
					- Many processes with tiny pages.
					- Multiple swaps occuring all at once.
					- Most of the time is wasted in moving in and out of the disk..
				- Working-sets
				  collapsed:: true
					- Helps prevent trashing
					- A process usually is working in a very tiny amount of its total memory.
					- A process will only be swapped into primary memory, if the minimum size of its working set can be moved all at once
				- Transfer types
				  collapsed:: true
					- On request
					  collapsed:: true
						- Used in segmented memory
						- OS determines when to load the block into primary memory
					- On demand
					  collapsed:: true
						- Used in paginated memory
						- A fault is generated when trying to access and OS receives it, loading to primary memory
					- Prefetching
					  collapsed:: true
						- The OS thinks this will be needed soon, so it loads it early hoping it will be helpful.
				-
				-
				-
				-
			- Memory Substitution
				- FIFO
					- Uses time to define when to move it out of memory
					- LRU - Least Recently Used
					  collapsed:: true
						- Efficient due to reference locality
						- Expensive in latency
					- Aproximation
					  collapsed:: true
						- Bit R
						  collapsed:: true
							- Set by MMU when page is accessed
							- 1 when accessed
							- 0 after finished use
						- R = 0 -> Increase age group
						- R = 1, Reset age group
						- Sent to "free blocks list" after reaching max age group.
						-
					- NRU - Not Recently Used
						- Bit R and M in Page table
							- R = 1 when read
							- M = 1 when written
							- Constantly reset R to 0.
						- 0: R=0 M=0
						- 1: R=0 M=1
						- 2: R=1 M=0
						- 3: R=1 M=1
						- Free pages in smallest group