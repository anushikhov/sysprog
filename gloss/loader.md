# What does the loader load?  

When loading a static executable, there is no need for the dynamic loader, as all the required libs were integrated into the executable during link-time.  
When loading a dynamic executable, the system depends on the loader to do the heavy lifting.  

The loader always starts by loading:  
* All the libraries specified by the envar `LD_PRELOAD`  
* All the libraries listed in `/etc/ld.so.preload`  

Then, it tries to satisfy each direct dependency (library) string specified as `NEEDED` in the ELF's `.dynamic` section.  

If one of these libraries requires an additional library, not required by the executable, this library is referred to as an 'indirect dependency'. After loading all the direct dependencies, the loader loads the indirect ones.  


