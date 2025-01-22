public:: true

- References
	- ![Intro 2- Organizacao dos Sistemas Operativos.pdf](../assets/Intro_2-_Organizacao_dos_Sistemas_Operativos_1737552007505_0.pdf)
	- ![14 - Organizacao-sistemas-operativos e despacho.pdf](../assets/14_-_Organizacao-sistemas-operativos_e_despacho_1735458139693_0.pdf)
	-
- Notes
	- Security Modes
		- User
			- Only a sub-set of the instructions is allowed, direct memory access restricted through virtual memory.
		- Kernel
			- Full unrestricted Access
	- SO Structures
	  collapsed:: true
		- Monolith
			- Uses Device drivers to be able to handle evolution like new peripherals.
			- Is a single system organized in modules
		- Layers
			- Easy to modify the code of a single layer.
			- More security
		- Micro-Kernel
			- Only has the very essentials.
	- Boot Cycle
	  collapsed:: true
		- Turn On
		- Bios
			- Copies the execution of the bootloader to memory and runs it.
		- Bootloader
			- Loads the kernel in the Disk to the memory, and starts it.
		- Kernel Initialization
			- Starts base data structures
			- Copies Memory and interrupt treating routines
			- Fills Interrupts
			- Starts other processes. Like login.
		-
	- Process Manager
	  collapsed:: true
		- Transfer of control
		  collapsed:: true
			- Interruption Treatment
				- Changes stack pointer to kernel's stack
				- Saves information needed to go back to User's stack
	- Process
	  collapsed:: true
		- Hardware
			- Processor Registries
			- Memory Registries
		- Software
			- IDs
			- Priority
			- Status
			- Other infos... (open descriptors.. etc)