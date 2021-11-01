# JavaScript

**This is just a guide**

The basis of javascript is covered here. A deep comprehension of how javascript works and what happens under the hood.

However, we really recommend u to search yourself in the browser and keep learning more and deeper about Js.

**Feel free to improve this wiki, pull requests are welcome 😀.**

## Js characteristics

* **high-level programming lenguage** \*
* **just-in-time (JIT) compiled** \*
* multi-paradigm
* single-threaded
* dynamic typing
* prototype-based object orientation
* first class functions

All those topics are covered in different branches. So, feel free to `git checkout "name_of_the_branch"` and lern more and deeper about those topics.

\* topics which are covered on branches

### What does high-level mean?*

Before covering high-level and low-level programming languages meanings, let's clarify some concepts.

#### Which lenguage does the computer understand?

**Machine code**

Machine code is the only language a computer can process directly without a previous transformation and it is a stream of raw, usually binary, data.

##### Machine code

Machine code is any low-level programming language, consisting of machine language instructions, which is used to control a computer's central processing unit (CPU).

Each instruction causes the CPU to perform a very specific task, such as a load, a store, a jump, or an arithmetic logic unit (ALU) operation on one or more units of data in the CPU's registers or memory.

##### What is a low-level language?

Low-level languages can convert to machine code without a compiler or interpreter

Second-generation programming languages use a simpler processor called an assembler – and the resulting code runs directly on the processor.

A program written in a low-level language can be made to run very quickly, with a small memory footprint. 

##### How can a developer code in Machine Code.

Currently, programmers almost never write programs directly in machine code, because it requires attention to numerous details that a high-level language handles automatically. Furthermore, it requires memorizing or looking up numerical codes for every instruction, and is extremely difficult to modify.

A programmer coding in "machine code" normally codes instructions and data in a more readable form such as decimal, octal, or hexadecimal which is translated to internal format by a program called a loader or toggled into the computer's memory from a front panel.

*Example: A function in hexadecimal representation of 32-bit x86 machine code to calculate the nth Fibonacci number*

`8B542408 83FA0077 06B80000 0000C383
FA027706 B8010000 00C353BB 01000000
B9010000 008D0419 83FA0376 078BD989
C14AEBF1 5BC3`

#### High-level language

It refers to the higher level of abstraction from machine language.

Rather than dealing with:

* registers
* memory addresses
* call stacks

high-level languages deal with: 

* variables
* arrays
* objects
* complex arithmetic
* boolean expressions
* subroutines
* functions
* loops
* threads
* locks

and other abstract computer science concepts, with a focus on **usability** over optimal program efficiency.

One thing to note about high-level programming languages is that these languages allow the programmer to be detached and separated from the machine.

A high-level language is easy for programmers to write as well as to understand.

However high-level language can not be executed by the computer.

##### How can the computer execute a high-level lenguage?

There are three general modes of execution for modern high-level languages:

* Interpreted
* Compiled
* Source to source translated or transcompiled

However, note that languages are not strictly interpreted languages or compiled languages.

###### Interpreted

The code syntax is read and then executed directly, with **no compilation stage**.

A program called an interpreter which reads each program statement, following the program flow, then decides what to do, and does it.

###### Compiled

The code syntax is transformed into an executable form before running.

There are two types of compilation:

* Machine code generation

Some compilers compile source code directly into machine code.

This is the original mode of compilation, and languages that are directly and completely transformed to machine-native code in this way may be called truly compiled languages. See assembly language.

* Intermediate representations

When code written in a language is compiled to an intermediate representation, that representation can be optimized or saved for later execution without the need to re-read the source file.

When the intermediate representation is saved, it may be in a form such as bytecode. The intermediate representation must then be interpreted or further compiled to execute it.

###### Source-to-source translated or transcompiled

Code written in a high-level language is translated into terms of a lower-level language for which native code compilers are already common.

**Docu**

* [wiki high-level](https://en.wikipedia.org/wiki/High-level_programming_language)
* [wiki low-level](https://en.wikipedia.org/wiki/Low-level_programming_language)
* [machine-code low-level high-level](https://www.educba.com/assembly-language-vs-machine-language/)

