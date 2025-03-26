# multithreading-with-locks
To create and initialize a lock, you have 2 ways:

- Way 1: declare and initialize at the same time:

pthread_mutex_t lock = PTHREAD_MUTEX_INITIALIZER;

- Way 2: Declare first and initialize it later at run time (recommended):

pthread_mutex_t lock;

int rc = pthread_mutex_init(&lock, NULL);
assert(rc == 0); // always check success!

To request and release a lock:
pthread_mutex_lock(&lock);
x = x + 1; // or whatever your critical section is
pthread_mutex_unlock(&lock);

You should also destroy lock after done:

pthread_mutex_destroy()

Problem 1: Write a program that has a counter as a global variable. Spawn 10 threads in the program, and let each thread increment the counter 10000 times in a loop. Print the final value of the counter after all the threads finish—the expected value of the counter is 100000. Run this program first without using locking across threads, and observe the incorrect updation of the counter due to race conditions (the final value will be slightly less than 100000). Next, use locks when accessing the shared counter and verify that the counter is now updated correctly. Submit screenshots to Canvas showing results without and with using lock.

Problem 2: Write a program where the main default thread spawns N threads. Thread i should print the message “I am thread i” to screen and exit. The main thread should wait for all N threads to f inish, then print the message “I am the main thread”, and exit. Note that you must learn how to pass arguments (say, thread number) to the thread start function in order to solve this lab. When you pass a variable as an argument, care should be taken to ensure that the value of the variable is retained until the thread actually runs. So, you must use different variables for different threads, and not reuse the same variable to store different values for different threads.
