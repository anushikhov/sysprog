# What does the loader load?  

When loading a static executable, there is no need for the dynamic loader, as all the required libs were integrated into the executable during link-time.  
When loading a dynamic executable, the system depends on the loader to do the heavy lifting.  

The loader always starts by loading:  
* All the libraries specified by the envar `LD_PRELOAD`  
* All the libraries listed in `/etc/ld.so.preload`  

Then, it tries to satisfy each direct dependency (library) string specified as `NEEDED` in the ELF's `.dynamic` section.  

If one of these libraries requires an additional library, not required by the executable, this library is referred to as an 'indirect dependency'. After loading all the direct dependencies, the loader loads the indirect ones.  

For each dependency, the loader follows this decision making process:  

If the dependency string contains a slash, it is interpreted as a pathname and loaded from there and no further lookup is required.  

Otherwise, the loader follows these steps (the step is skipped if the condition is not satisfied):  
1. Using the directories in `DT_RPATH`  -- condition: `DT_RUNPAPTH` attribute does not found, note: `DT_RPATH` is deprecated   
1. Using the envar `LD_LIBRARY_PATH` -- condition: the executable is not being run in secure-execution mode (formally, when `AT_SECURE` has a nonzero value. Informally, this happens e.g. when we set the file's SUID bit, e.g. when the `SETUID` bit is set, and the process's real and effective UIDs differ, the loader will ignore it, note: `LD_LIBRARY_PATH` can be overridden by executing the dynamic linker directly with the option `--library-path` , e.g.  
` /lib64/ld-linux-x86-64.so.2 --library-path "/my/libs:/my/other/libs" myapp `  
1. Using the directories in `DT_RUNPAPTH` -- condition: the loader is loading a direct dependency, e.g. if a binary needs a single library a.so, and a.so requires b.so, when looking for b.so (which is not a direct dependency), the loader will skip this step. Note that this is different from `DT_RPATH`, which is always applied.  
1. From the `/etc/ld.so.cache` cache file -- condition: the ELF doesn't contain the `NODEFLIB` flag.  
1. In the default path `/lib[64]`, and then `/usr/lib[64]` -- condition: the ELF doesn't contain the NODEFLIB flag.  

If the loader goes through all five steps and still it cannot find a library, the load process fails with an error message.  


