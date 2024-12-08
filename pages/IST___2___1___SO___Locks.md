- References
	- ![Mem-Partilhada I 2024-25-lock-rwl-noimpl (1).pdf](../assets/Mem-Partilhada_I_2024-25-lock-rwl-noimpl_(1)_1733670341075_0.pdf)
- Notes
	- Mutex
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
				  
				  
				  pthread_rwlock_unlock(&rwl);
				  ```
	- Semaphores
		- Definition
		- Properties
		- Programming
	-