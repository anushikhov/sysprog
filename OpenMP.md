# Open Multi-Processing (OpenMP)  

An API that supports multi-platform shared-memory multiprocessing programming in C, C++, and Fortran.

It consists of a set of compiler directives, library routines, and env vars that influence run-time behavior.  

An app built with the hybrid model of parallel programming can run on a computer cluster using both OpenMP and Message Passing Interface (MPI) such that OpenMP is used for parallelism within a (multi-core) node while MPI is used for parallelism between nodes.  

OpenMP is an implementation of multithreading, a method of parallelizing whereby a primary thread forks a specified number of sub-threads and the system divides a task among them. The threads then run concurrently, with the runtime environment allocating threads to different processors.  

The section of code that is meant to run in parallel is marked with a compiler directive that will cause the threads to form before the section is executed. Each thread has an id attached to it, which can be obtained using the function `omp_get_thread_num()`. The original thread is the primary thread and will be denoted as master thread with thread ID 0. After the execution of the parallelized code, the threads join back into the primary thread, which continues onward to the end of the program.  

Work-sharing constructs can be used to divide a task among the threads so that each thread exectues its allocated part of the code independently. Both task parallelism and data parallelism can be achieved using OpenMP in this way.  
The runtime environment allocates threads to processors depending on usage, machien load and other factors. The runtime environment can assign the number of threads based on environment variables, or the code can do so using functions. The OpenMP functions are included in the omp.h header file.  

The core elements of OpenMP are the constructs for thread creation, workload distribution, data-environment management, thread synchronization, user-level runtime routines and environment variables.  

In C/C++, OpenMP uses #pragmas.  

https://www.openmp.org/wp-content/uploads/OpenMP-API-Specification-5.0.pdf  

https://www3.nd.edu/~zxu2/acms60212-40212/Lec-12-OpenMP.pdf   

https://riptotorial.com/openmp  

https://www.intel.com/content/dam/develop/external/us/en/documents/gdma-2-165938.pdf  

Threading methods - OpenMP, POSIX threads (pthreads), Win32 threading API

With OpenMP, much of the fine control over threads is lost. Among other things, OpenMP does not give the programmer a way to set thread priorities or perform event-based or inter-process synchronization. OpenMP is fork-join threading model with an explicit master-worker relationship among threads. These characteristics narrow the range of problems for which OpenMP is suited. In general, OpenMP is best suited for data parallelism, while explicit threading API methods are best suited for functional decomposition.  

