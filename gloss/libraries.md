# Libraries  

Libraries allow programmers to pack code into reusable modules.  Then, every program that requires the same functionality can simply use the already-existing library. There are two kinds of libraries:  

* Static libraries(.a files): become part of the execurable during linking. This means that once the executable is ready it does not require any additional files.  
* Dynamic libraries(.so files): are shipped separately from the execurable, and are required to be present at run-time. We can use this libraries in two different ways, and the difference is mainly whether or not the libraries are present during compile-time:  
1. The executable links with the library at compile time. The executable can call methods defined in the library as if both shared their code-base. There is no need to explicitly load the library. A classic example is any C program that links and uses glibc.  
1. The executable doesn't link with the library at compile time, it loads and possibly unloads the library during execution-time only. The executable uses the library's API during run-time using functionality provided by the dynamic loader. This is accomplished using `dlopen` A classic example is an application that loads plug-ins during runtime.  

**Static executables** don't depend on any libraries.  
**Dynamic executables** depend on other libraries.  

We can use the `file` command to find out if an exectuable is static or dynamic.  

Static executables are statically linked. Dynamically linked executables require dynamic libraries.  

When we compile a C/C++ application with gcc the compiler is programmed to automatically use the standard libraries; glibc.so for C and additionally libstdc++.so for C++.  

When compiling an app, we tell the linker to add libraries using the `-l` flag. Required libraries are specified only by their basename, whereas the lookup directories are defined using additional parameters such as `-L` or system default paths. 

## Static enumeration of needed libraries  

Using the `patchelf` tool's `--print-needed` option, we can print a list of libraries (basenames) required by an executable.  

`patchelf --print-needed myapp`  

We can accomplish the same by directly examining the ELF dynamic sections. Each needed library is represented by an entry in the `.dynamic` section, so we can simply print the entire `.dynamic` section using the `readelf -d <path-to-elf>` command, and look for the keyword `NEEDED`:  
` $ readelf -d myapp | grep NEEDED `  

## Dynamic enumeration of needed libraries  

Using `ldd` (List Dynamic Dependencies), we can get the full pth of the libraries we are going to use. 
`<lib-basename> => <lib-full-path> (lib-load-addr)`  
We can see the actual instance to be loaded and the load address.  

`ldd` loads the application without executing it and traces the loader's actions. If we run it using Bash's trace mode enabled, we'll see that the entire script evaluates to a single line:  
`bash -x $(which ldd) myapp`  

The dynamic loader is a single static executable ELF file that goes by a name usually reserved by libraries.  

It can be run either indirectly by running some dynamically linked program or shared object, or directly.  

The default loader (on 64-bit machines) can be found at `/lib64/ld-linux.so.2` and is actually a symbolic link to the real loader file `/lib/x86_64-linux-gnu/ld-<version>.so`.   

Using `file` we can find out which loader an ELF "expects".  
` $ file myapp `  

To change the loader for a specific ELF, we can use `patchelf` and specify the interpreter and the ELF to patch.  
` $ patchelf --set-interpreter <path-to-interpreter> <path-to-elf> `  

When shipping such a package, make sure the loader loads the libraries shipped with instead of system defaults. 


