## Call Stack

The **call stack** or **execution stack** is a region in memory that helps the interpreter or compiler, keeping track of the invoked (called) functions.

Basically, the call stack tracks:

- what function is currently being run, or in other words, which **execution context** is currently executed.

- what functions are called from within that function.

### How does the call stack store and manage function invocation or function call?

When the code is loaded, the JavaScript engine first creates a **global execution context**.

Then, during execution, when a function is invoked, a **new execution context** is created and pushed to the **top** of the **call stack**, creating a new **stack frame**.

The engine executes the function which is at the top of the call stack, in other words, the last **stack frame**. Once the function is completed, the **stack frame** is removed from the call stack.

This data structure is known as LIPO / LastIn-FirstOut.

**LastIn-FirstOut**

The last function that gets pushed or added **-LastIn-** into the call stack, is the first to be pop out or removed **-FristOut-** from it, only after the function is completly executed.

### Summary

1. When a script calls a function, the interpreter adds it to the call stack and then starts carrying out the function.

   - Each entry in the stack is called a **stack frame**.
   - The **stack frame** contains the information of the called function, such as arguments, locals variables of the function, return address (where the return value will be consumed), and other information.

2. Any functions that are called by that function are added to the call stack further up, and run where their calls are reached.

3. When the current function is finished, **the interpreter** takes it off the call stack and resumes execution where it left off in the last code listing.

4. If the stack takes up more space than it had assigned to it, it results in a **stack overflow** error.
