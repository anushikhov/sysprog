# cmake rpath  

CMake offers quite a few options to refine the behavior during build tree linking and install linking:   

By default, RPATH will be used in the build tree, but cleared when installing the targets, leaving an empty RPATH. 

### Variables  

` CMAKE_INSTALL_RPATH` -- a semicolon-separated list specifying the RPATH to use in installed targets, this is used to initialize the target property `INSTALL RPATH` for all targets.  
` CMAKE_SKIP_RPATH` -- if true, do not add run time path information  
` CMAKE_SKIP_BUILD_RPATH` -- do not include RPATHs in the build tree  
` CMAKE_BUILD_WITH_INSTALL_RPATH` -- use the install path for the RPATH  
` CMAKE_INSTALL_RPATH_USE_LINK_PATH` -- add paths to linker search and installed RPATH  

`# don't skip the full RPATH for the build tree  `
` set(CMAKE_SKIP_BUILD_RPATH FALSE) `  

`# use the install RPATH when installing  `
` set(CMAKE_BUILD_WITH_INSTALL_RPATH FALSE) `  
` set(CMAKE_INSTALL_RPATH "${CMAKE_INSTALL_PREFIX}/lib") `  

`# add the automatically determined parts of the RPATH which points to directories outside the build tree to the install RPATH `  
` set(CMAKE_INSTALL_RPATH_USE_LINK_PATH TRUE) `  

You can set `CMAKE_SKIP_RPATH` to ignore RPATH.  

`INSTALL_RPATH` -- the rpath to use for installed targets. A semicolon-separated list specifying the rpath to use in installed targets. This property is initialized by the value of the variable `CMAKE_INSTALL_RPATH` if it is set when a target is created.   

` CMAKE_BUILD_RPATH_USE_ORIGIN ` -- whether to use relative paths for the build `RPATH`  
` BUILD_RPATH_USE_ORIGIN ` -- whether to use relative paths for the build `RPATH` for all targets.  Setting this property to `TRUE` enables relative paths in the build `RPATH` for executables and shared libraries that point to shared libraries in the same build tree.  


https://linuxfixes.com/2021/11/solved-how-to-link-shared-library-with.html
