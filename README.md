# C-study
Study C for embeded systems coding
## Include Headers

<> for standard libraries, "" for user defined. 

## Complier and temps files. 

main.c -->compiler--> main.i, preprocessing stage, preprocess directives, main, indludes ... all pre-processing directives will be resolved.

main.i -->complier-->main.s, code generation stage, higher level language code statements will be converted into processor architectural level mnemonics.

main.s -->complier-->main.o, assembly level mnemonics are converted into opcodes(machine codes for instructions) 

> adding extra compile flag `-save-temps` can save the intermediate generated code in these stages.

## Escape sequence

E.g. `\n` for prinf(); is moving the cursor to next line, `\"` is double quote, apply `\` before the escape sequence can counter the effect of the escape. 

## Format specifier
%d: integer, %f: float, %c: character, %s: string, %u:  unsigned integer, %ld: long integer </br>
%p: pointer, a memory address `printf("variable is stored in %p\n", &myVariable);`

## Data types in C

### Integer data types: integers
Integer data types(for signed data): data could be negative 
- char 
- Short int, also referred by short, and "int" is assumed. short int == short
- int
- long int, also referred by long, and "int" is assumed. long int == long
- long long int, also referred by long long, and "int" is assumed, long long int == long long

Integer data types(for unsigned data): data always be non-negative
- unsigned char
- unsigned short int
- unsigned int
- unsigned long int
- unsigned long long int

#### integer data types, storage size and value ranges

[Table](https://www.tutorialspoint.com/cprogramming/c_data_types.htm)

```
#include <stdio.h>
#include <stdlib.h>
#include <limits.h>
#include <float.h>

int main(int argc, char** argv) {

    printf("CHAR_BIT    :   %d\n", CHAR_BIT);
    printf("CHAR_MAX    :   %d\n", CHAR_MAX);
    printf("CHAR_MIN    :   %d\n", CHAR_MIN);
    printf("INT_MAX     :   %d\n", INT_MAX);
    printf("INT_MIN     :   %d\n", INT_MIN);
    printf("LONG_MAX    :   %ld\n", (long) LONG_MAX);
    printf("LONG_MIN    :   %ld\n", (long) LONG_MIN);
    printf("SCHAR_MAX   :   %d\n", SCHAR_MAX);
    printf("SCHAR_MIN   :   %d\n", SCHAR_MIN);
    printf("SHRT_MAX    :   %d\n", SHRT_MAX);
    printf("SHRT_MIN    :   %d\n", SHRT_MIN);
    printf("UCHAR_MAX   :   %d\n", UCHAR_MAX);
    printf("UINT_MAX    :   %u\n", (unsigned int) UINT_MAX);
    printf("ULONG_MAX   :   %lu\n", (unsigned long) ULONG_MAX);
    printf("USHRT_MAX   :   %d\n", (unsigned short) USHRT_MAX);

    return 0;
}
```
meaning of the memory size (Bytes): (Depends on the complier how to identify the types and allocate the memory)
(8bits is 1 Byte)

The compiler (e.g.GCC) will generate the code to allocate 64 bits(8 bytes of memory) for each long long variable.

**These data types will always be fixed size irrespective of compliers**</br>
char (singed or unsigned) is always 1 byte.</br>
short (signed or unsigned) is always 2 bytes. </br>
longlong (signed or unsigned) is always 8 bytes. </br>

- ***char***
It is an integer data type to store a single character (ASCII code) value or 1 byte of signed integer value (positive or negetive value), char variable consumes 1 byte of memory. It is the ***smallest*** integer data type of 1 byte.</br> char range: -128 - 127, char data type will be used to store 1 byte of signed data. unsigned char range: 0 - 255, unsigned char will be used to store 1 byte of unsigned data.



### floating data types: real number
[Table](https://www.tutorialspoint.com/cprogramming/c_data_types.htm)


---

### sizeof operator
**sizeof** operator of C is used to find out the size of a variable. The output of the sizeof operator maybe different on different machines because it is complier dependent. 

```
#include <stdio.h>

int main()
{
    //sizeof() operator called as keyword, operand can be variable name or data type
    printf("Size of char data tyope = %d\n", sizeof(char));
    printf("Size of char data tyope = %d\n", sizeof(short));
    printf("Size of char data tyope = %d\n", sizeof(int));
    printf("Size of char data tyope = %d\n", sizeof(long));
    printf("Size of char data tyope = %d\n", sizeof(long long));

    return 0;
}

```
---
## Variables 

- local variable: </br>
'Local variable' exists (memory claimed) for the time the function is executed. Once the function exits , local variable die.(memory reclaimed). They do not sit permanently on the data memory. </br>
can be seen as bounded within the scope of definition bracket `{}`. </br>
***uninitialized local variable default value :*** unpredictable, can be some random values. dangerous! so make sure you need to declare it. </br>

- global variable: </br>
'Global variable' exists on the memory permenantly. </br>
***uninitialized global variable default value :*** 0. </br>
---
## Address of variables:
E.g.  Use `&myVariable`, `&` ampersand, to give the memory location address of `myVaribale` variable.

pointer type usually 8 bytes. 

we can use **typeCasting** to convert pointer type to the datatype we want. 

E.g. 
```
#include <stdio.h>
int main(){
    //define and declare char type a1 variable. 
    char a1 = 'A';

    //start a variable named addressOfa1, type is 8 byte unsigned long long int to match the pointer data type size, 

    unsigned long long int addressOfa1 = ( unsigned long long int ) &a1;

    // ( unsigned long long int ) is typecasting, convert the output of &a1 datatype to the unsigned long long int. 

    printf("address of variable a1 = %I64X\n", addressOfa1);
    //%I64,means integer 64 bits, X means hexagon. 

    return 0;
}
```
## Storage Classes

### storage classes in c :
- static : restrict the visibility of the variable/functions only within the scope. (protect) 
- extern : extend the visibility to other files/scope. 

### ASCII codes
The American National Standards Institute (ANSI), which developed ANSI C, also developed the ASCII codes. 
ASCII stands for "American Standard Code for Information Interchange'. </br>
Encode 128 different characters. Refer to the ASCII table. (0-127)


## Typecasting:
Typecasting is a way of converting a variable or data from one data type to another data type. 

**Data will be truncated when higher data type is converted into lower. **

- Implicit casting (Complier does this, assume casting)

- Explicit casting (Overwrite what complier does, programmer does this)

Warning may cause trouble, because they maybe related to implicit casting... which actually truncated information. 


---
---

## Embedded Microcontroller:
For coding, all microcontroller needs to have a start file. (given in the STM32CubeIDE tho, may need to write yourself)

Using printf outpus on ARM Cortex M3/M4/M7 or higher based MCUs. printf works over SWO pin (Serial Wire Output of SWD interface)

[processor] ---SWO pin --- [debug module]

### SWD
SWD(Serial Wire Debug) is a two-wire protocol for accessing the ARM debug interface. It is part of the ARM Debug interface Specification v5 and is an alternative to JTAG.

The physical layer of SWD consists of two lines:

- SWDIO: a bidirectional data line
- SWCLK: a clock driven by the host

By using SWD interface, should be able to program MCUs internal flash, you can access memory regions, add breakpoints, stop/run CPU. 

The other good thing about SWD is you can use the serial wire viewer for your printf statements for debugging. 
 
## Embeded system notes:

An embeded application never ends </br> If the application has got nothing to do, it will put the processor to sleep or executes the infinite loop. 
```
for(;;);
```
A statement like this in the main function is an implementatiion of an infinite loop that does nothing but keeps the processor  busy. 

### What is Microcontroller?

MCU is a small computer system on a single chip, but its resources and capalibilities such as memory, speed, external interfaces are very much limited than of a desktop computer, because of MCU targets embeded applications.</br>

A typical microcontroller includes a processor, volatile and non-volatile memories, inpuit/output(I/O) pins, peripherals, clock, bus interfaces on a single chip.
![Anatomy of a Typical Small Microcontroller](/README_IMAGES/p1.png)

CPU execute instructions, the instructions are from the program memory, usually non-volatile. It means once stored the programs into the program memory, cant erase it, or write programs, even plugged out the power, the program memory will not be corrupted. </br>

How fast the cpu can decode the instructions depends on the clock speed. </br>

Data memory: volatile, and it is used to store data of the program and also used as a scratchpad. Usually it is consumed during the run-time of the program.

Code Memory (program memory) :

The purpose of the code memory is to store instructions and constant data of the program, there are different types of code memory: </br>
- ROM (read only memory)
    - MPROM (mask programmable read only memory)
    - EPROM (ultraviolet erasable programmable ROM)
    - EEPROM (electrially erasable programmable ROM)
- OTP (on time programmable)
- Flash (erasable, easy to use, dominant in most MCUs)
- FRAM (Ferroelectric Random Access Memory, costly but fast)

### Question
**when doing embeded, downloaded the program to the code memory (non-volatile, flash), the initial data is with the program and stored there, how the data be used or later in data memory (volatile, SRAM as e.g.)?**

To analyze this, we should analyze the ELF file, using the GNU tools, or check the .list file for `.data` </br>

LMA: load memory address (source in FLASH)

VMA: virtual memory address (destination in SRAM)

By examining, we can observe that when loading the program, the source and destination address have been assigned, who did this? **the start up code**

![Reset of Processor](/README_IMAGES/p2.png)
