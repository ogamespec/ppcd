PPCD is very accurate disassembler for PowerPC-based processors. Current supported models are:

  * Generic POWERPC-32
  * Generic POWERPC-64
  * Gekko

For each model standalone compiled executable is provided. To disassemble binary file, use:

ppcd-**model** binary

Output will go to stdout.

Credits: This program was written by org between 2006-2007 for Gekko debugger. PPCD is free opensource. You can use it in your applications without mention.

Let me know, if you made support for more processors in PPCD.

How to use sourcecode:

You need to add ppcd.cpp/ppcd.h and Commondefs (data types) to your project. Call PPCDisasm and pass it PPCD\_CB structure with filled "pc" and "instr" parameters. At minimum you can use "mnemonic" and "operands" as output parameters, but if you need more detailed information about disassembled instruction, use "icalss", "immed", "target" and "r":

iclass: Combination of flags which specify instruction "class" or category. See ppcd.h for list of flags. Note, many flags can be combined, for example FPU + LDST.
immed: Immediate value for integer instructions or address displacement for load/store.
target: "Cooked" absolute branch address (calculated from input "pc" parameter) OR mask for rlwinm-like instructions.
r: Index list for register operands in appropriate order.

As option there is PPCDisasmSimple call for quick use. Just call PPCDisasmSimple(pc, instr) and it will return formatted string.

ppcd.cpp compilation tips:

If you need uppercase: define UPPERCASE
If you need another hexademical numbers representation: See HEX1 and HEX2
If you dont need spaces between commas: redefine COMMA as ","
If you dont need simplified mnemonics (highly not recommended :)): undefine SIMPLIFIED

CHANGELOG:

  * 0.01    Initial release. Generic 32/64-bit ISA is implemented and extensively tested.
  * 0.02    Added support for Gekko.
  * 0.03    Fixed some typos. (SVN [r1](https://code.google.com/p/ppcd/source/detail?r=1))

**This project is completed.**

**If you're experience weird .cpp errors, use static type casting in problem places. Things may change in time in CPP world.**