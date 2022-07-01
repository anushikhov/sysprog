# Position-independent code  

PIC or PIE(Position-independent executable) is a body of machine code that, being placed somewhere in the primary memory, executes properly regardless of its absolute address.   

PIC is commonly used for shared libraries, so that the same library code can be loaded in a location in each program address space where it does not overlap with other memory in use (e.g. other shared libraries). 
