# R[UN]PATH (Runtime Search Path)   

RPATH is a mechanism to include a list of directories in a binary where required shared libraries may be available. These locations are considered by the dynamic loader (ld* .so) to locate the libraries that are required by a particular binary.

RPATH designates the run-time search path hard-coded in an executable file or library. Dynamic linking loaders use the rpath to find required libraries. Specifically, it encodes a path to shared libraries into the header of an executable (or another shared library).

Both `RPATH` and `RUNPATH` are optional entries in the `.dynamic` section of ELF executables or shared libraries.  

Their goal is to allow programmers alter the behavior of the dynamic loader.  

When linking a shared library, the executable needs to know where to look for said library at runtime. In most cases the library would be placed in a common system library path and the executable would find it due to a predefined list of places to search. However, if you want to ship the shared library file with your executable or have multiple versions installed in parallel, you need to make sure that the library can be found at your custom location.  

With RPATH you can solve this issue by embedding additional search paths directly into the executable. 

In a lot of cases and for maximum portability, you don't want to specify an absolute path to the shared library, but have it relative to the executable. For that you get `$ORIGIN` on Linux.   

On Linux `$ORIGIN` represents at runtime the location of the executable and thus if set the RPATH to for example `$ORIGIN/lib/libmylib.so`, your executable will look for the needed shared library relative to the executable location.   

RPATH can also be useful during development, as you can link libraries within the build tree relative to the executable. 

* If `RUNPATH` isn't set, the loader looks for every library in the directories specified by `RPATH`.  
* If `RUNPATH` is set, the loader looks for direct dependency libraries in the directories specified by `RUNPATH`.  
* `RPATH` is deprecated, and the use of `RUNPATH` is encouraged instead.  

Given an ELF file, we can examine `R[UN]PATH` values using:  
` readelf -d <path-to-elf> | egrep "RPATH|RUNPATH" `  

We can manipulate an ELF in two different ways:   
1. Set at compile time. The GNU linker `ld` supports the `-rpath` option. All `-rpath` options are concatenated and added to the final executable.  
1. Manipulate an existing ELF file using `patchelf`:  
` # Clearing RPATH & RUNPATH `   
` patchelf --remove-rpath <path-to-elf> `  

` # Setting RPATH `  
` patchelf --force-rpath --set-rpath <desired-rpath> <path-to-elf> `  

` # Setting RUNPATH `  
` patchelf --set-rpath <desired-rpath> <path-to-elf> `   

....   

## $ORIGIN  

On Linux/Solaris, specify any RPATH setting one requires to look up the location of a package's private libraries via a relative expression, to not lose the capability to provide a fully relocatable package.  


https://youtube.com/watch?v=01fnuhjMwc0  

