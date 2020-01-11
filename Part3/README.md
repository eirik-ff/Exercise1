# Reasons for concurrency and parallelism


To complete this exercise you will have to use git. Create one or several commits that adds answers to the following questions and push it to your groups repository to complete the task.

When answering the questions, remember to use all the resources at your disposal. Asking the internet isn't a form of "cheating", it's a way of learning.

 ### What is concurrency? What is parallelism? What's the difference?
 > Concurrency is multiple computers (CPUs) running at the same time, but can work on different tasks. It is used in networks as well as multiple cores in a single computer. Concurrency is a form of multitasking. A concurrent program can be run with a single or with multiple cores, where the latter will help with a speed increase. 
 > Parallelism is splitting a certain task into smaller subtasks that are solved simultaneously and combined later to provide an answer to the task. 
 > For later reference: 
 > * https://wiki.haskell.org/Parallelism_vs._Concurrency 
 > * https://web.mit.edu/6.005/www/fa14/classes/17-concurrency/ 
 
 ### Why have machines become increasingly multicore in the past decade?
 > It gets progressively harder to increase the clock speed on a CPU, so to make applications run faster more cores are added. A downside to adding more cores is that programs have to be specifically programmed to make use of the extra cores. 
 
 ### What kinds of problems motivates the need for concurrent execution?
 (Or phrased differently: What problems do concurrency help in solving?)
 > 
 
 ### Does creating concurrent programs make the programmer's life easier? Harder? Maybe both?
 (Come back to this after you have worked on part 4 of this exercise)
 > Making concurrent programs are harder and introduces new types of bugs such as race conditions which are notoriously hard to debug. 
 
 ### What are the differences between processes, threads, green threads, and coroutines?
 > A _process_ can be seen as running on a virtual computer, with it's own private memory space. 

 > A _thread_ runs in a process and can share memory between threads. Threads are controlled by the OS scheduler and can be interrupted in the middle of running. This can lead to race conditions. 
 
 > A _green thread_ is scheduled by a VM or library instead of by the OS scheduler. This adds the ability to use multithreading where it is otherwise not supported. 
 
 > A _coroutine_ is a subroutine which yields when it is done and is not interrupted by the scheduler. This means it can finish its task and then yield for another coroutine to run. 

 > For future reference: 
 > * https://stackoverflow.com/questions/3324643/processes-threads-green-threads-protothreads-fibers-coroutines-whats-the 
 
 ### Which one of these do `pthread_create()` (C/POSIX), `threading.Thread()` (Python), `go` (Go) create?
 > * `pthread_create()`: Threads
 > * `threading.Thread()`: Threads
 > * `go`: Green threads
 
 ### How does pythons Global Interpreter Lock (GIL) influence the way a python Thread behaves?
 > The GIL makes it so only one thread can run the Python interpreter at the time, so it effectivly blocks Python applications from running multi threaded. 
 
 ### With this in mind: What is the workaround for the GIL (Hint: it's another module)?
 > A workaround for the GIL is to use the `multiprocessing` module instead of `threading`. This creates two Python processes instead of two threads, meaning they have their own Python interpreter and thus their own memory space. Performance is somewhat better, but switching between two processes have more overhead than switching between two threads. 
 > For later reference: https://realpython.com/python-gil/ 
 
 ### What does `func GOMAXPROCS(n int) int` change? 
 > The function limits the number of operating system threads the Go process can use. 
