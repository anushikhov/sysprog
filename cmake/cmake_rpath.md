# cmake rpath  

CMake offers quite a few options to refine the behavior during build tree linking and install linking:   

By default, RPATH will be used in the build tree, but cleared when installing the targets, leaving an empty RPATH. 

### Variables  

` CMAKE_INSTALL_RPATH` -- a semicolon-separated list specifying the RPATH to use in installed targets  
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


