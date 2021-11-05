# JavaScript

The basis of javascript is covered here. A deep comprehension of how javascript works and what happens under the hood.

However, we really recommend u to search yourself in the browser and keep learning more and deeper about Js.

```diff
+ This is just a guide.
+ Feel free to improve this wiki, pull requests are welcome 😀.
```

## Js characteristics

- **high-level programming lenguage** \*
- **interpreted or just-in-time (JIT) compiled** \*
- single-threaded
- multi-paradigm
- dynamic typing
- prototype-based object orientation
- first class functions

All those topics are covered in different branches. So, feel free to `git checkout "name_of_the_branch"` and lern more and deeper about those topics.

```diff
! * topics which are covered on branches
```

### What does high-level mean?\*

Before covering high-level and low-level programming languages meanings, let's clarify some concepts.

#### Which lenguage does the computer understand?

**Machine code**

Machine code is the only language a computer can process directly without a previous transformation and it is a stream of raw, usually binary, data.

##### Machine code

Machine code is any low-level programming language, consisting of machine language instructions, which is used to control a computer's central processing unit (CPU).

Each instruction causes the CPU to perform a very specific task, such as a load, a store, a jump, or an arithmetic logic unit (ALU) operation on one or more units of data in the CPU's registers or memory.

##### What is a low-level language?

Low-level languages can be converted to machine code without a compiler or interpreter

Second-generation programming languages use a simpler processor called an assembler – and the resulting code runs directly on the processor.

A program written in a low-level language can be made to run very quickly, with a small memory footprint.

##### How can a developer code in Machine Code.

Currently, programmers almost never write programs directly in machine code, because it requires attention to numerous details that a high-level language handles automatically. Furthermore, it requires memorizing or looking up numerical codes for every instruction, and is extremely difficult to modify.

A programmer coding in "machine code" normally codes instructions and data in a more readable form such as decimal, octal, or hexadecimal which is translated to internal format by a program called a loader or toggled into the computer's memory from a front panel.

```diff
# Example: A function in hexadecimal representation of 32-bit x86 machine code to calculate the nth Fibonacci number
```

8B542408 83FA0077 06B80000 0000C383
FA027706 B8010000 00C353BB 01000000
B9010000 008D0419 83FA0376 078BD989
C14AEBF1 5BC3

#### High-level language

It refers to the higher level of abstraction from machine language.

Rather than dealing with:

- registers
- memory addresses
- call stacks

high-level languages deal with:

- variables
- arrays
- objects
- complex arithmetic
- boolean expressions
- subroutines
- functions
- loops
- threads
- locks

and other abstract computer science concepts, with a focus on **usability** over optimal program efficiency.

One thing to note about high-level programming languages is that these languages allow the programmer to be detached and separated from the machine.

A high-level language is easy for programmers to write as well as to understand.

However high-level language can not be executed by the computer.

##### How can the computer execute a high-level lenguage?

There are three general modes of execution for modern high-level languages:

- Interpreted
- Compiled
- Source to source translated or transcompiled

However, note that languages are not strictly interpreted languages or compiled languages.

###### Interpreted

The code syntax is read and then executed directly, with **no compilation stage**.

A program called an interpreter which reads each program statement, following the program flow, then decides what to do, and does it.

###### Compiled

The code syntax is transformed into an executable form before running.

There are two types of compilation:

- Machine code generation

Some compilers compile source code directly into machine code.

This is the original mode of compilation, and languages that are directly and completely transformed to machine-native code in this way may be called truly compiled languages. See assembly language.

- Intermediate representations

When code written in a language is compiled to an intermediate representation, that representation can be optimized or saved for later execution without the need to re-read the source file.

When the intermediate representation is saved, it may be in a form such as bytecode. The intermediate representation must then be interpreted or further compiled to execute it.

###### Source-to-source translated or transcompiled

Code written in a high-level language is translated into terms of a lower-level language for which native code compilers are already common.

**Docu**

- [wiki high-level](https://en.wikipedia.org/wiki/High-level_programming_language)
- [wiki low-level](https://en.wikipedia.org/wiki/Low-level_programming_language)
- [differences between machine-code/low-level/high-level](https://www.educba.com/assembly-language-vs-machine-language/)

### Is javascript an interpreted, compiled or a source-to-source translated or transcompiled lenguage?

Javascript is a interpreted or just-in-time ([JIT](https://hacks.mozilla.org/2017/02/a-crash-course-in-just-in-time-jit-compilers/)) compiled programming lenguage.

JIT compiled programming language? Wha'choo talkin' 'bout?.

Let's start from the beginning.

The computer needs a JS-engine to understand JS scripts, because as it was already explained, the computer only execute machine code, and js is a high-level programming lenguage.

So basically, the js-engine is a program that helps in converting your code of JavaScript into a lower level code or machine code.

#### What happens though inside the JS-engine?

The js-engine takes the code as an import and export machine code which can be understood by the CPU.

This process has three phases:

- Parsing
- Compiling
- Execution

##### Parsing

Before the code is passed to the interpreter, it has to first get parsed into Abstract Syntax Tree [(AST)](https://en.wikipedia.org/wiki/Abstract_syntax_tree), which is a tree-like structure of the code.

**[Try it here by yourself](astexplorer.net)**

##### Compiling

###### Interpreter role

It basically translates pretty much line-by-line, on the fly.

Interpreters are quite quick to get up and run, because it is not neccesary to go through the whole compilation before the code can start to be run.

But there is a con.

Our interpreter is amnesiac.

An interpreter translates line by line, which means that even if there is the same code in a script, the interpreter will take the time to translate it again an again, over and over.

The interpreter doesn't have time to optimized the executable code.

###### Compiler role

The compiler works ahead of time to create that translation and write it down.

It takes more time to start up, because it goes through the whole code before execution. But it runs faster when there is repeated code.

A compiler has the ability to optimized the code before run it.

_Some js-engines implements a just-in-time compiler stead of an interpreter. For instance, V8 -Chrome js-engine-, before 2017, implements full-codegen. A simple and very fast compiler that produced simple and relatively slow machine code, which removed the need for an interpreter.
In 2017 Google launched an improved V8 version, in which a Ignition Interpreter is implemented _

If your want to learn more and deeper about how V8 works, visit [this link](https://blog.sessionstack.com/how-javascript-works-inside-the-v8-engine-5-tips-on-how-to-write-optimized-code-ac089e62b12e) and [this one as well](https://medium.com/jspoint/how-javascript-works-in-browser-and-node-ab7d0d09ac2f).

###### Monitor role

Js-engine has another character who cares about translation. **The monitor.**

That monitor watches the code as it runs, and makes a note of how many times it is run and what types are used.

1. the monitor runs everything through the interpreter, and each segment of code is ranked by the frequency it is run (+ warm, ++ hot).

2. if the segment code gets warm

   1. it is sent off to be compiled.
   2. the compiler compiles that code to a indexed baseline stub (by number and variable type) where it is stored as Inline Caching.
      1. If a piece of code is monomorphic\*, it will get one stub.
      2. If it is polymorphic\*, then it will get a stub for each combination of types that has come through that operation.
   3. when the monitor sees that execution is hitting the same code again with the same variable types, it will just pull out its compiled indexed version.

3. if the segment code gets hot.

   1. it is sent off to the optimizing compiler.
   2. The optimizing compiler uses the information the monitor gatheres by watching code execution to make some type assumptions.
   3. the compiler creates another, even faster, version of the code based in those assumptions, that is also stored.
   4. because of dynamic type system in js, the compiled code needs to be checked before it runs. Those assumptions can be false.
      1. **optimization** if the assumption is true
      2. **deoptimization**:if it is not, the optimized code is trashed and execution goes back to the interpreter or compiled version.

4. The Garbage Collector is who cares about trashing and freeing space.

```diff
! * monomorphic (that is, always called with the same types)
! * polymorphic (called with different types from one pass through the code to another)
```

_Bonus Track_<br />
read about [monomorphism and polymorphism](https://mrale.ph/blog/2015/01/11/whats-up-with-monomorphism.html)<br />
V8-js-engine [tutorial](https://www.digitalocean.com/community/tutorials/js-v8-engine)<br/>
if u are a C# developer, maybe you can be interested in check [V8-github](https://github.com/v8/v8/blob/c736a452575f406c9a05a8c202b0708cb60d43e5/src/objects.h#L9368)
