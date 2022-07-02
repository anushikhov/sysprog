# Microkernel  

A microkernel (often abbreviated as μ-kernel) is the near-minimum amount of software that can provide the mechanisms needed to implement an operating system (OS). These mechanisms include low-level address space management, thread management, and inter-process communication (IPC).  

If the hardware provides multiple rings or CPU modes, the microkernel may be the only software executing at the most privileged level, which is generally referred to as supervisor or kernel mode. Traditional operating system functions, such as device drivers, protocol stacks and file systems, are typically removed from the microkernel itself and are instead run in user space.  

In terms of the source code size, microkernels are often smaller than monolithic kernels. The MINIX 3 microkernel, for example, has only approximately 12,000 lines of code.  
