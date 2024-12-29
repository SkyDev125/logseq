- References
	- ![Mem-Partilhada I 2024-25-lock-rwl-noimpl (1).pdf](../assets/Mem-Partilhada_I_2024-25-lock-rwl-noimpl_(1)_1733670341075_0.pdf)
	- ![10 - Semaforos  - Cooperacao entre actividades (1).pdf](../assets/10_-_Semaforos_-_Cooperacao_entre_actividades_(1)_1735447570157_0.pdf)
	- ![11 - Variaveis de condicao - 2.pdf](../assets/11_-_Variaveis_de_condicao_-_2_1735447573321_0.pdf)
- Notes
	- Mutex
	  collapsed:: true
		- Definition
			- Protects parts of memory from being tampered with by other threads while one thread works on it.
		- Properties
			- Can be locked or Unlocked
			- Once closed, the other threads need to wait for it to unlock.
			- Only to be used in extremely necessary situations as it can affect performance greatly.
		- Programming
			- Initialize
				- ```cpp
				  #include <pthread.h>
				  
				  pthread_mutex_t mutex = PTHREAD_MUTEX_INITIALIZER;
				  ```
				- Initializes the mutex ready to be locked or unlocked.
			- Lock
				- ```cpp
				  #include <pthread.h>
				  
				  int pthread_mutex_lock(pthread_mutex_t *mutex);
				  ```
				- Locks making all other threads waiting for this lock, stop and wait for until it is unlocked.
			- Unlock
				- ```cpp
				  #include <pthread.h>
				  
				  int pthread_mutex_unlock(pthread_mutex_t *mutex);
				  ```
				- Unlocks Allowing the other threads to lock it again and process.
	- Read Write Lock
	  collapsed:: true
		- Definition
			- Abstraction of Mutexes that allows for the protection of specific read only or write only operations.
		- Properties
			- Write locks will block anything from writing or reading
			- Read locks will only block writing.
			- Writers will wait for all reads to end.
			- Allows for a more optimized management of memory.
		- Programming
			- Initialize
				- ```cpp
				  #include <pthread.h>
				  
				  pthread_rwlock_t rwl = PTHREAD_RWLOCK_INITIALIZER;
				  ```
				- Initializes the read write lock to be used
			- Read Lock
				- ```cpp
				  #include <pthread.h>
				  
				  pthread_rwlock_rdlock(&rwl); //Activates the read lock
				  ```
			- Write Lock
				- ```cpp
				  #include <pthread.h>
				  
				  pthread_rwlock_wrlock(&rwl); //Activates the write lock
				  ```
			- Unlock
				- ```cpp
				  #include <pthread.h>
				  
				  pthread_rwlock_unlock(&rwl);
				  ```
				- When read locks occur, it keeps an internal counter, to then unlock until it reaches 0 again, finally letting writes occur.
				- When a write occurs, it just waits for it to unlock, allowing for the rest to continue.
				- For this reason it doesn't require a specific implementation for each "write or read" unlock.
	- Semaphores
	  collapsed:: true
		- Definition
			- A counter that is protected by the kernel and that works similar to a Mutex.
		- Properties
			- Can be incremented
			- Can be decremented
			- Locks when == 0
		- Programming
			- Initialize
				- ```cpp
				  sem_t sem;
				  
				  int sem_init(sem_t *sem, int pshared, unsigned value);
				  ```
				- Can be accessed by all threads of the same process if pshared == 0
				- Any thread of any process can access it if pshared != 0
				- Value defines the starting value of the counter.
			- Decrement & Wait
				- ```cpp
				  #include <semaphore.h>
				  
				  int sem_wait(sem_t *sem); // Decrement sem by 1
				  ```
				- Allows you to keep decrementing until reaching 0 where it then blocks all calls until it can be decremented again.
			- Increment
				- ```cpp
				  #include <semaphore.h>
				  
				  int sem_post(sem_t *sem); // Increment sem by 1
				  ```
	- Condition Variables
		- Definition
			- Connected to a Mutex and related to a condition
			- Is often used when a specific condition is to be checked, to either lock or unlock certain threads.
		- Properties
			- Can be waited for a signal or a broadcast.
			- Signal unlocks one of the waits.
			- Broadcast unlocks all waits.
		-
	- Deadlocks
	  collapsed:: true
		- Definition
			- Two threads or more get locked indefinitely with no way to free themselves.
		- Handling
			- When locking things, always make sure that the logic will allow for a thread to always free itself and not be stuck forever.
			- Use of try_lock()
			- Force a specific condition to fix Cyclical deadlocks
			- Free the locks for the operation if one of them fails. To allow others to finish their job and then try again
	-