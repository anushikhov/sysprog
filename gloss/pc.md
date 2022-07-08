# PC  

A PC file is a metadata file used by pkg-config, a helper tool used when compiling applications and libraries. It contains information about a code library, such as the library's name, description, URL, version, and dependencies.  

PC files are also referred to as pkg-config files.  

Pkg-config is a free tool that helps developers check for the existence of requisite libraries while compiling applications. 

If the library exists, developers can use pkg-config to include the library in the compiled application. Developers can also use pkg-config to retrieve information about the library.   

The information pkg-config retrieves is stored in PC files. These files are plaintext files that are saved alongside the library they describe. Packages that contain multiple libraries include multiple PC files, one for each library.  

Each PC file may contain information about a library's name, description, URL, version, dependencies (both public and private), conflicts, compiler flags, and link flags (both public and private). May also include freeform variables, which most commonly define installation paths.  

PC files are typically named for their corresponding code library. For example, a library named Magma.so would use a PC file named Magma.pc.  

To use a PC file with pkg-config (cross-platform) reference the file as part of the `pkg-config` command. E.g., to retrieve version information stored in Magma.pc, run `pkg-config --modversion Magma`.  
