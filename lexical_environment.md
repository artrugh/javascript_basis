## Lexical environments or scopes

(Lexical environments in ECMAScript)[https://262.ecma-international.org/6.0/#sec-lexical-environments]

**Lexical environments or scopes** are environment records, or state components, in which the variables are stored, creating variable indetifier. Everytime an execution context is created, a new lexical environment is created as well.

It is a structure that holds identifier-variable mapping and the region of code over which an identifier is valid.

Identifier refers to the name of variables or functions, and the variable is the reference to actual object -including function object and array object- or primitive value.

```javascript
const a = 20;
const b = 40;
function foo() {
  console.log("bar");
}
```

```javascript
lexicalEnvironment = {
  a: undefiend,
  b: undefiend,
  foo: <ref. to foo function>
}
```

Each lexical environment or scope, has three components:

- environment record
- reference to the outer environment
- _this_ binding.

### Environment record

The environment record is the place where the variable and function declarations are stored inside the lexical environment.

There are also two types of environment record:

#### declarative environment record

As its name suggests stores variable and function declarations. The lexical environment for function code contains a declarative environment record.

For function, the environment record also contains an arguments object that contains the mapping between indexes and arguments passed to the function and the length(number) of the arguments passed into the function.

#### object environment record

The lexical environment for global code contains a **objective environment record**.

Apart from variable and function declarations, the object environment record also stores a global binding object (window object in browsers). So for each of binding object’s property (in case of browsers, it contains properties and methods provided by browser to the window object), a new entry is created in the record.

### Reference to the outer environment - Scope Chain

The reference to the outer environment means it has access to its outer lexical environment. That means that the JavaScript engine can look for variables inside the outer environment if they are not found in the current lexical environment.

so it is used to resolve identifiers outside the current Execution Context.

### _This_ Binding

The value of _this_ is set in the lexical environment.

In the global execution context, the value of this refers to the global object. (in browsers, this refers to the Window Object).

In the function execution context, the value of this depends on how the function is called.

- If it is called by an object reference, then the value of this is set to that object
- Otherwise, the value of this is set to the global object or undefined(in strict mode).

Example:

```javascript
const person = {
  name: "peter",
  birthYear: 1994,
  calcAge: function () {
    console.log(2018 - this.birthYear);
  },
};

// 1. FIRST INVOCATION
person.calcAge();
// 'this' refers to 'person', because 'calcAge' was called with //'person' object reference
const calculateAge = person.calcAge;

// 2. SECOND INVOCATION
calculateAge();
// 'this' refers to the global window object, because no object reference was given
```

Scopes:

- Block:
  - calculateAge:
    **after invocation**
    - calcAge:
      - arguments: {}
      - length
      - name
      - ...
  - person
  - this: Window
- Window: Global

FIRST INVOCATION
person.calcAge()

- calcAge:
  - this: {
    - name
    - birthYear
    - calcAge:
      - arguments: { - callee: calcAge()
        }
      - callee: null
      - length
      - name
      - ...
        }

SECOND INVOCATION
calculateAge()

- calcAge:

  - this: Window
  - arguments: {

    - callee: calcAge()
    - length: 0
    - ...
      }

Each time a function is invoked, a new execution context and a new lexical environment is created.

```javascript
GlobalExecutionContext = {
    LexicalEnvironment: {
        EnvironmentRecord: {
            Type: "Object",
            // Identifier bindings go here
            person: < uninitialized >,
            calculateAge: < func >
            }
        outer: <null>,
        this: <global object>
    }
}

FunctionExecutionContext = {
    LexicalEnvironment: {
        EnvironmentRecord: {
            Type: "Declarative",
            // Identifier bindings go here
            }
        outer: <Global or outer function environment reference>,
        this: <depends on how function is called>
    }
}
```

Usually a lexical environment is associated with some specific syntactic structure of ECMAScript code such as a FunctionDeclaration, a BlockStatement, or a Catch clause of a TryStatement and a new lexical environment is created each time such code is evaluated.

The four lexical environments are:

    1. Global lexical environment or global scope - visible by everything
    2. Local lexical environment or local scope
        1. Function lexical environment or global scope - visible within a function (and its sub-functions and blocks)
        2. Block lexical environment or block scope - visible within a block (and its sub-blocks)
        - let and const:
         They have block scope, apart from when they are declared directly in the global context, in which case they have global scope
        - If
        - { block statement }
        - try | catch
        - Function declarations
            Function declarations have block scope in strict mode and function scope in non-strict mode.

        3. Module lexical environment or Module scope - visible within a module

There are three pertinent factors in deciding the scope of an identifier in javascript:

- How a indetifier was declared
- Where a indetifier was declared
- Strict mode or non-strict mode

Some of the ways identifiers can be declared:

- var, let and const
- Function parameters
- Catch block parameter
- Function declarations
- Named function expressions
- Implicitly defined properties on the global object (i.e., missing out var in non-strict mode)
- import statements
- eval

Some of the locations identifiers can be declared:

- Global context
- Function body
- Ordinary block
- The top of a control structure (e.g., loop, if, while, etc.)
- Control structure body
- Modules

### Closure

In JavaScript, every function-object has a hidden [[Environment]] reference that is a reference to the lexical environment of the execution context (stack frame) within which it was created.

When you invoke a function, the hidden [[Call]] method is called. This method creates a new execution context and establishes a link between the new execution context and the lexical environment of the function-object. It does this by copying the [[Environment]] value on the function-object, into an outer reference field on the lexical environment of the new execution context.

Note that this link between the new execution context and the lexical environment of the function object is called a closure.

Thus, in JavaScript, scope is implemented via lexical environments linked together in a "chain" by outer references. This chain of lexical environments is called the scope chain, and identifier resolution occurs by searching up the chain for a matching identifier.
