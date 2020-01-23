# C-study
Study C for embeded systems coding

## Complier and temps files. 

main.c -->compiler--> main.i, preprocessing stage, preprocess directives, main, indludes ... all pre-processing directives will be resolved.

main.i -->complier-->main.s, code generation stage, higher level language code statements will be converted into processor architectural level mnemonics.

main.s -->complier-->main.o, assembly level mnemonics are converted into opcodes(machine codes for instructions) 

> adding extra compile flag `-save-temps` can save the intermediate generated code in these stages.

## Escape sequence

E.g. `\n` for prinf(); is moving the cursor to next line, `\"` is double quote, apply `\` before the escape sequence can counter the effect of the escape. 

## Format specifier
%d: integer, %f: float, %c: character, %s: string, %u:  unsigned integer, %ld: long integer </br>
%p: a memory address

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
