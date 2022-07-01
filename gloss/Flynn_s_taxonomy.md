# Flynn's taxonomy  

Flynn's taxonomy is a classification of computer architectures, proposed by Michael J. Flynn in 1966 and extended in 1972. The system has been used as a tool in design of modern processors and their functionalities. Since the rise of multiprocessing CPUs, a multiprogramming context has evolved as an extension of the classification system. Vector processing, covered by Duncan's taxonomy, is missing from Flynn's work because the Cray-1 supercomputer was released in 1977.  

The four initial classifications defined by Flynn are based upon the number of concurrent instruction (or control) streams and data streams available in the architecture. Flynn later defined three additional sub-categories of SIMD in 1972.  

Flynn's taxonomy  

Single data stream - SISD, MISD  
Multiple data streams - SIMD, MIMD  
SIMD Subcategories - Array processing(SIMT), Pipelined processing(packed SIMD), Associative processing(predicated/masked SIMD)  

(SPMD, MPMD)   


## Single instruction stream, single data stream (SISD)  

A sequential computer which expoits no parallelism in either the instruction or data streams. Single control unit (CU) fetches a single instruction stream (IS) from memory. The CU then generates appropriate control signals to direct single processing element (PE) to operate on a single data stream (DS) i.e., one operation at a time. Examples of SISD architectures are the traditional uniprocessor machines like older PCs and mainframe computers, by 2010, many PCs had multiple cores.  

## Single instruction stream, multiple data streams (SIMD)  

A single instruction is simultaneously applied to multiple different data streams. Instructions can be executed sequentially, such as by pipelining, or in parallel by multiple functional units. Flynn's 1972 paper subdivided SIMD down into three further categories.  
* Array processor  
* Pipelined processor  
* Associative processor  

## Multiple instruction streams, single data stream (MISD)  

Multiple instructions operate on one data stream. This is an uncommon architecture which is generally used for fault tolerance. Heterogeneous systems operate on the same data stream and must agree on the result.   

## Multiple instruction streams, multiple data streams (MIMD)  

Multiple autonomous processors simultaneously executing different instructions on different data. MIMD architectures include multi-core superscalar processors, and distributed systems, using either one shared memory space or a distributed memory space.  

