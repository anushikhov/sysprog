# Single instruction, multiple data  

SIMD is a type of parallel processing in Flynn's taxonomy. 

SIMD can be internal (part of the hardware design) and it can be directly accessible through an instruction set architecture (ISA), but it should not be confused with an ISA.  

SIMD describes computers with multiple processing elements that perform the same operation on multiple data points simultaneously.  

Such machines exploit data level parallelism, but not concurrency: there are simultaneous (parallel) computations, but each unit performs the exact same instruction at any given moment (just with different data). 
