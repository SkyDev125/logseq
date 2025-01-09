public:: true

- References
	- ![13 - IPC (1).pdf](../assets/13_-_IPC_(1)_1735449996620_0.pdf)
- Notes
	- Pipes
	  collapsed:: true
		- Definition
			- A FIFO (First in first out) of bytes that is connected between 2 processes.
		- Properties
			- The pipe descriptors are internal to a process
			- Can be transmitted to the child processes.
			- Can be used just like a normal file descriptor.
			- Waits when writing to a full pipe or reading from an empty pipe.
			- Can be used to redirect outputs to different inputs or the sort. Exactly how the | operator works in linux.
		- Programming
			- ```cpp
			  #include <unistd.h>
			  
			  int pipefd[2];
			  int pipe(pipefd);
			  ```
			- In each pair of pipes, one will be for reading the other for writing, it's recommended to always close one of the pipes (on each side of the 2 processes) since there's a limit to how many file descriptors a process can have open.
	- Named Pipes
	  collapsed:: true
		- Definition
			- A pipe with a name, allowing for communication for non-affiliated processes.
		- Properties
			- Behaves exactly like a normal file.
			- Can be opened and used by processes without any affiliation.
			- Works very similarly to a normal pipe. But has a name in the filesystem.
		- Programming
		  collapsed:: true
			- Initialize
				- ```cpp
				  #include <sys/types.h>
				  #include <sys/stat.h>
				  
				  int mkfifo(const char *pathname, mode_t mode);
				  ```
			- Open
				- Works like the normal Open for file descriptors, however it will wait until the other side of the pipe is opened.
			- Unlink
				- Same function for file Descriptors. Others also apply like write, read, etc.
	- Signals
	  collapsed:: true
		- Definition
			- A message sent directly to a process that triggle a specific handling.
		- Properties
			- A process can have multiple signals pending, when it wakes up they all get treated in an order defined by the kernel.
			- If many of the same signal get sent, some signals may be considered as one.. making it unreliable to assume that a process receives exactly all signals.
			- Can't receive new signals while treating signals.
			- While treating the signal, only specific functions can be used. Called "async-signal-safe".
		- Programming
		  collapsed:: true
			- ```cpp
			  #include <signal.h>
			  
			  int sigaction(int signum, const struct sigaction *act,
			                struct sigaction *oldact)
			  
			  // Example
			  struct sigaction sa;
			  
			  // Assign the signal handler function
			  sa.sa_handler = my_signal_handler;
			  
			  // define Flags here
			  sa.sa_flags = SA_RESTART;
			  
			  // Block SIGTERM while handling SIGINT
			  sigemptyset(&sa.sa_mask);
			  sigaddset(&sa.sa_mask, SIGTERM);
			  
			  // Set the handler for SIGINT
			  if (sigaction(SIGINT, &sa, NULL) == -1) {
			    perror("sigaction failed");
			    return 1;
			  }
			  ```