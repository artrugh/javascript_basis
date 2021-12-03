## Execution context

Whenever a javascript code is run, a **execution context** is created.

_An **execution context** is a specification device that is used to track the runtime evaluation of code by an ECMAScript implementation.
At any point in time, there is at most one execution context that is actually executing code. This is known as the running execution context._

An **execution context** is an environment where the javascript code is evaluated and executed.

There are two types of execution context in javascript.

1. **Global Execution Context**

   This is the initial or default execution context, which is created when the code is loaded for first time in the browser.

   It is always at the bottom of the **call stack**.

   There can only be one global execution context in a program. This global context is accesible from any other execution context.

   It performs two things:

   - it creates a global object which is a window object (in the case of browsers) stored into the **global lexical environment** or **global scope**
   - it sets the value of **this** to equal to the global object.

2. **Functional Execution Context**

   Each function has its own execution context.

   Every time a function is invoked, a new execution context is created for that function.

   This context creates a **local lexical environment** or **local scope** which is attached to this **execution context**. The execution context has access to its **local scope**. (check the lexical_environment file)

- Each time an execution context is created, it is pushed or added to the **call stack**.
- Each time a function completes, the corresponding execution context is popped or removed from the **call stack**

### How an execution context is created?

The execution context is created in two phases:

- Creation Phase
- Execution Phase

#### Creating Phase

Before the execution of the code, the interpreter or the compiler, goes through the code, line by line, and whenever a variable or a function is encountered, it allocates memory for it.

**Lexical environments** and **variable environments** are created during the **creating phase**.

So, the execution context contains references to the lexical environments.
(check the lexical_environment file)

```
ExecutionContext = {
  LexicalEnvironment = <ref. to LexicalEnvironment in memory>,
  VariableEnvironment = <ref. to VariableEnvironment in  memory>,
}
```

Only, once the memory allocation is done, the **code execution phase** starts. Javascript runs through the code again.

#### Execution Phase
