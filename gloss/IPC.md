# Inter-process communication  

Inter-process communication (IPC) is any mechanism which allows separate processes to communicate with each other, usually by sending messages. Shared memory is, strictly defined, also an inter-process communication mechanism, but the abbreviation IPC usually refers to message passing only, and it is the latter that is particularly relevant to microkernels. IPC allows the operating system to be built from a number of smaller programs called servers, which are used by other programs on the system, invoked via IPC. Most or all support for peripheral hardware is handled in this fashion, with servers for device drivers, network protocol stacks, file systems, graphics, etc.

IPC can be synchronous or asynchronous.
