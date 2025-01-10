- Part2
	- Server
		- TODO Start-up format
			- ```shell
			  ./kvs dir_jobs  max_threads  backups_max  nome_do_FIFO_de_registo
			  ```
			- New thread
				- Manages connection requests.
			- Producer-Consumer queue for client commands
				- Threads will be created to consume this queue
				- Handle these commands:
					- Connect
					-
					-
		-
	- Client
		- TODO Start-up format
			- ```shell
			  ./client id_do_cliente nome_do_FIFO_de_registo
			  ```
			- Connect
				- Create Named Pipes
					- "commands+clientid" (Write)
					- "replies+clientid" (Read)
					- "notifications+clientid" (Read)
				- Send the Name of the pipes to server
					- Through connections_pipe
				- Wait for ACK reply from server on "replies+clientid" pipe
			-
			-