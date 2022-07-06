# Executable and Linkable Format (ELF)  

Is a common standard file format for executable files, object code, shared libraries, and core dumps.  

It supports different endiannesses and address sizes so it does not exclude any particular CPU or instruction set architecture.  

Each ELF file is made up of one ELF header, followed by file data.  

The specification does not clarify the filename extension for ELF files.  

https://linuxhint.com/understanding_elf_file_format/   

https://linux-audit.com/elf-binaries-on-linux-understanding-and-analysis/  

https://www.opensourceforu.com/2020/02/understanding-elf-the-executable-and-linkable-format/ 

The three main uses of ELF: executable, shared library, object file.  

Each ELF file can contain zero or more segments and sections.  

Segments are exclusively used during runtime, sections are almost exclusively used at link time.  

You can, therefore have an ELF executable that only contains segments and an object file that only contains sections.  


