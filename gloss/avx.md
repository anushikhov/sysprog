# Advanced Vector Extensions  

AVX are extensions to the x86 instruction set architecture for microprocessors from Intel and Advanced Micro Devices (AMD). AVX provide new features, new instructions and a new coding scheme.  

AVX2 (aka Haswell New Instructions) expands most integer commands to 256 bits and introduces new instructions. They were first supported by Intel with the Haswell processor, which shipped in 2013.  

AVX-512 expands AVX to 512-bit support using a new EVEX prefix encoding proposed by Intel in 2013 and first supported by Intel with the Knights Landing co-processor, which shipped in 2016.

AVX uses 16 YMM registers to perform a single instruction on multiple pieces of data (SIMD). 

Each YMM register can hold and do simultaneous operations (math) on:  
* 8 32-bit single-precision floating point numbers or  
* 4 64-bit double-precision floating point numbers  

AVX-512 is disabled by default in Alder Lake(Intel Xeon, Core, Pentium, Celeron) processors. On some motherboards with some BIOS versions, AVX-512 can be enabled in the BIOS, but this requires disabling E-cores.  
