# Make building with cmake verbose  

### Through CMakeLists.txt  

Update CMakeLists.txt to include the following config line:  
`set(CMAKE_VERBOSE_MAKEFILE ON) `   

The configuration is not passed on to other CMakeLists.txt file that are included to the build using the command `add_subdirectory()`  from the master CMakeLists.  
Thus, you need to copy the config line to each file you want to make verbose.  

### Through the make command  

After `cmake`, execute `make`  uwint the `VERBOSE=1` variable as follows:  
`make VERBOSE=1`   

### cmake -DCMAKE_VERBOSE_MAKEFILE:BOOL=ON  

https://bytefreaks.net/programming-2/make-building-with-cmake-verbose  
