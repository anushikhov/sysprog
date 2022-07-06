# NODEFLIB  

NODEFLIB flag can be found in an option .dynamic seciton called `FLAGS_1`. It tells the loader to avoid loading libraries from the loader cache file and default system locations.  

To check if the flag is set:  
` readelf -d <path-to-elf> | grep NODEFLIB `  

We can manipulate it during compile time, by passing the `-z nodefaultlib` flag to the GNU linker. To manipulate an existing ELF we can use patchelf:  
` patchelf --no-default-lib <path-to-elf> `  

 
