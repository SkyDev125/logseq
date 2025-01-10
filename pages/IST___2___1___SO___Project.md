- Part2
	- Server
		- TODO Start-up format
			- ```shell
			  ./kvs dir_jobs  max_threads  backups_max  nome_do_FIFO_de_registo
			  ```
			- New thread
				- Manages connection requests.
			- Producer-Consumer queue for client commands
				- Creation of threads for consumption
		-
	- Client
		- TODO Start-up format
			- ```shell
			  ./client id_do_cliente nome_do_FIFO_de_registo
			  ```
			- Connect
				- Send a connect request with 3 "requested names"
					- "command+clientid"
					- "ack+clientid"
					- "notification+clientid"
			-
			-