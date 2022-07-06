# Using the ILP64 interface vs LP64 interface  

The Intel(R) MKL ILP64 libraries use the 64-bit integer type (necessary for indexing large arrays, with more than (2^31)-1 elements), whereas the LP64 libraries index arrays with the 32-bit integer type.   



The difference between them is integer type length.  

ILP64 interface uses the 64-bit integer type, while LP64 use the 32-bit integer.  

By defualt, the compilers take integers ('int' for C or C++ /'INTEGER' for Fortran) as 32-bit lenght. So most applications need link with LP64 MKL libraries.  


