# C-study
Study C for embeded systems coding

## Complier and temps files. 

main.c -->compiler--> main.i, preprocessing stage, preprocess directives, main, indludes ... all pre-processing directives will be resolved.

main.i -->complier-->main.s, code generation stage, higher level language code statements will be converted into processor architectural level mnemonics.

main.s -->complier-->main.o, assembly level mnemonics are converted into opcodes(machine codes for instructions) 

> adding extra compile flag `-save-temps` can save the intermediate generated code in these stages.

## Escape sequence

E.g. `\n` for prinf(); is moving the cursor to next line, `\"` is double quote, apply `\` before the escape sequence can counter the effect of the escape. 

## Data types in C

