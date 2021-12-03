# JavaScript

The basis of javascript is covered here. A deep comprehension of how javascript works and what happens under the hood.

However, we really recommend u to search yourself in the browser and keep learning more and deeper about Js.

- [wiki](https://en.wikipedia.org/wiki/JavaScript)
- [mdn](https://developer.mozilla.org/en-US/docs/Web/JavaScript)
- [javascript.info](https://javascript.info/intro)

```diff
+ This is just a guide.
+ Feel free to improve this wiki, pull requests are welcome 😀.
```

## Js characteristics

- high-level programming lenguage \*
- interpreted or just-in-time (JIT) compiled \*
- single-threaded \*
- multi-paradigm
- dynamic typing
- prototype-based object orientation
- first class functions

All those topics are covered in different branches. So, feel free to `git checkout "name_of_the_branch"` and lern more and deeper about those topics.

```diff
! * topics which are covered on branches
```

### Single-threaded

Javascript is known as a single-threaded language at runtime.

That means, the code execution is done one piece at a time, on other words, it is done **synchronously**, from top to bottom.

Thanks to modern browsers, as not all open browser tabs rely on single JavaScript thread. Instead, they use separate JavaScript thread per tab or per domain.

Any tab having page opened from the same domain / same website, shares the same thread. Browsers implement one-process-per-site policy and a process uses the same javascript execution thread.

(Click here) to learn more about how browsers manage the thread[http://hassansin.github.io/shared-event-loop-among-same-origin-windows]

#### Code Execution in javascript

There are three essencial linked concepts that explains how the interpreter or compiler runs code in javascript.

1. execution context
2. call stack
3. scope or lexical environment

A briefly introduction to them.

1. The **execution contexts** are environments where the javascript code is evaluated and executed.

The first time a code is loaded into the javascript engine, a **global execution context** is created, and pushed to the **call stack**.

But also, each time a function is invoked, a new execution context is created and pushed to the **call stack**, which will create a new **stack frame**.

Once the function is totally executed, the corresponding execution context is popped from the stack.

2. The **call stack** is a region in memory, that helps the interpreter, keeping track of its place in a script that functions are invoked (called).

In other words, it keeps track of the current execution contexts, creating a new **stack frame**. The **stack frame** is nothing but the pushed execution context.

3. The **execution contexts** contain references to the lexical environments.

   **Lexical environments or scopes** are environment records in which the variables are stored, creating variable indetifier.

   Lexical environments also have a reference to their parent environment (Scope Chain), building a tree structure.


However, inside the JavaScript interpreter, every call to an execution context has two phases:

1. the memory creation or allocation phase
2. code execution phase

Let's go deeper over those topics.

It is recommended to take some minutes before and read this (well written article)[https://newbedev.com/what-is-the-difference-and-relationship-between-execution-context-and-lexical-environment]