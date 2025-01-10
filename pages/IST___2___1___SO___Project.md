- Part2
	- Server
		- TODO Start-up format
			- ```shell
			  ./kvs dir_jobs  max_threads  backups_max  nome_do_FIFO_de_registo
			  ```
			- New thread for
				- Manages connection requests.
			- Producer queue for client commands
		-
	- Client
		- TODO Start-up format
			- ```shell
			  ./client id_do_cliente nome_do_FIFO_de_registo
			  ```
			- Connect
				- Send a connect request with 3 "requested names"
					- Commands
					- Replies
					- Notifications
			-
			-