However, inside the JavaScript interpreter, every call to an execution context has two phases:

1. the memory creation or allocation phase

   - Create the Scope Chain.
   - Create variables, functions and arguments.
   - Determine the value of "this".

2. code execution phase
   - The code is executed and variables values are assigned.

The memory allocation phase occurs first. Javascript goes through the code line by line, and whenever a variable or a function is encountered, it is created and it allocates memory for it.

Only once the **hoisting** process is complete the code will then be executed.

This process would allow to, in theory, call a function before declaring the function, and once it is run in the browser, since everything is created and stored before execution, it will be able to use the function and execute the call.

This will only work with **function declarations** and not with **function expressions**.

While function declarations are functions that are written out as a function, function expressions are functions that are written within a variable.

The same happens between var and const variable.

The reason is that function declarations and var variables are added to the **global scope** created by the **global execution context**, while function expressions and const, into the **function scope** and the **block scope**.

```javascript
getNumber(); // 1
getNumbers(); // ReferenceError: Cannot access 'getNumbers' before initialization
// function declaration
function getNumber() {
  console.log(1);
}
// function expression
const getNumbers = () => {
  console.log(2);
};
console.log(a); // undefiend
console.log(b); // ReferenceError: Cannot access 'b' before initialization
var a = "a";
const b = "b";
```

#### What is the scope?

**Memory life cycle** refers to how a programming language works with memory. Regardless of the language, memory life cycle is almost always the same. It is composed of three steps.

The memory life cycle consists on three phases:

- allocation memory
- use
- release.

1. **Allocate** in memory variable and functions.

   - **Value initialization**

   JavaScript will automatically **allocate memory** when values are initially declared.

   It is assign a unique identifier as a reference for each variable and function. These references are allocated in the stack as an address.

   So, each time a variable or function is created, the interpreter creates a new reference and allocates it, as an address, on the stack memory. The stack also stores the values of those variables when the code, but it also stores **static data**.

   What is static data?

   Data which is **inmmutable**. In javascript primitive data type or primitive values, are inmmutable, they cannot be altered.

   \*It is important not to confuse a primitive itself, with a variable assigned a primitive value. The variable may be reassigned a new value, but the existing value can not be changed in the ways that objects, arrays, and functions can be altered.

   Each time a variable which value is a primitive data type, changes its value, a new indetifier is allocated.

   Also, basic data type variable replication is to assign a new address, and the new value is a copy of the copied variable. Variables are independent and do not affect each other. \*

   ```javascript
   let number1 = 1;
   let number2 = number1;
   num1 = 4;

   console.log(num2); // 1
   ```

   Identifiers ---------------- Call Stack
   ------------------------- Address -- Value

   number1 -------------------- A001 -- undefiend
   number2 -------------------- A002 -- undefiend
   number1 -------------------- A003 -- undefiend

   And because primitive values are **inmmutable**, the engine knows the size at **compile time**. It can calculate ahead of time how much memory they will need. Since the engine knows that the size won't change, it will allocate a **fixed amount of memory** for each value.

   The process of allocating memory right before execution is known as **static memory allocation**.

   What happens with those variable which values are **dynamic data**?

   As you can already guees, **non primitive data type** are considered dinamic data, because they are mutable in javascript. Non primative are basically **objects and functions**.

   Functions are regular objects with the additional capability of being callable.

   And because non-primitive values are **mutable**, the engine cannot know the size at compile time, so it can't calculate ahead of time how much memory they will need.Otherwise, it can only know it at **run time**.

   In those cases, a reference is stored into the stack memory but those values are stored into the **heap memory**. The stack reference points to the refence which was stored into the heap. This process is known as **dynamic-memory-allocation**.

   The **heap**, which is also called "free store", is a large and single region in memory, which can be used to store arbitrary data in an unordered fashion.

   More about the heap in (mdn)[https://developer.mozilla.org/en-US/docs/Web/JavaScript/Memory_Management]

   So, basically the heaps and the stack are two data structures that the engine uses for different purposes.

   -------------------- Stack ------------------------------- Heap
   Primitive values and references ------------------ Objects and functions
   Size is known at compile time -------------------- Size is known at run time
   Allocates a fixed amount of memory --------------- No limit per object

2. **Use** the allocated memory (read, write).

   Using values basically means reading and writing in allocated memory. This can be done by reading or writing the value of a variable or an object property or even passing an argument to a function.

   E.g.

   ```javascript
   const number1 = 2;
   const number2 = 1;
   const name = "John";
   const arrayNames = [number1, number2];
   const objNames = { name: name };
   const newObj = { name: "Paul" };
   ```

   Allocation

   Identifiers ---------------- Call Stack ---------------- Heap
   ------------------------- Address -- Value -------- Address -- Value

   number1 -------------------- A001 -- undefiend
   number2 -------------------- A002 -- undefiend
   name ----------------------- A003 -- undefiend
   arrayNames ----------------- A005 -- B001 -------- B001 -- [ A001, A002 ]
   objNames ------------------- A006 -- B002 -------- B002 -- { name: A003 }
   newObj --------------------- A007 -- B003 -------- B003 -- { name: undefiend }

   Use

   Identifiers ---------------- Call Stack ---------------- Heap
   ------------------------- Address -- Value -------- Address -- Value
   number1 -------------------- A001 -- 2
   number2 -------------------- A002 -- 1
   name ----------------------- A003 -- John
   arrayNames ----------------- A005 -- B001 -------- B001 -- [ A001, A002 ]
   objNames ------------------- A006 -- B002 -------- B002 -- { name: A003 }
   newObj --------------------- A007 -- B003 -------- B003 -- { name: Paul }

   (More Info)[https://felixgerschau.com/javascript-memory-management/]

3. **Release** the allocated memory when it is not needed anymore.

   While the stack is automatically cleaned after the invoked function was already used, the heap memory is leaned up by the **garbage collector** when the data is not used anymore.

