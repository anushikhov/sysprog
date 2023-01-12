# The difference between cross compiling and native compiling  

Cross compiling is compiling something for different CPU type than the one you are running on. An example is compiling ARM binaries under an i386 system, or compiling 64-bit executables under a 32-bit system.

You normally won't be able to run what you've just compiled when you cross compile it, until you ship the binaries to the system they belong to.

Native compiling is when you compile for the same architecture you're running under, which is the normal situation.

Cross compiling is building for a platform (roughly, a combination of OS, CPU family and ABI) other than the one you are running on. That means having a compiler that runs on one platform but targets another platform. It generally (there are exceptions to this because some platforms have compatibility layers) means you can't just run the binaries you have just built.


