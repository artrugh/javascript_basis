## TypeScript

JavaScript is **dynamic typing language**, which means, that it verifies its type safety at runtime.

The other process to verify type safety is called **static type checking**.

This process allows to detect errors before runing the code, before executing it, on other words, at compilation time.

An **static type checking** determines what is an error and what is not, based on the kinds and type of values being operated on.

Basically, it describes the shapes and behaviors of what our values will be when we run our programs.

An as u can imagine, TypeScript is a **static type checker** used in JavaScript.

### What is exactly TypeScript?

- TypeScript is a **typed superset**, which adds rules about how different kinds of values can be used
- TypeScript is JavaScript’s runtime with a compile-time type checker. it checkes the JavaScript code before execution, based of kind of values.

TypeScript **never** changes the runtime behaviour of JavaScript code, neither when it inferred an error. That guarantes:

- that the code is always run in the same way it was written.
- The type errors during compilation has not influence on how the program works when it runs.

### How does TypeScript work?

TypeScript offers all of JavaScript’s features, and an additional layer on top of these: TypeScript’s **type system**.

That allows Typescript to heighlight unexpected behaviour in the code, lowering the chance of bugs.

JavaScript infers types automatically, but it is difficult to it when some design patterns are used.

```javascript
const letters = {
  a: "a",
  b: "b",
};

console.log(object.c); // undefined
```

TypeScript supports an extension of the JavaScript language, which offers places for tell TypeScript what the types should be.

In that case, an interface can use to describe the shape type of the object.

```typescript
interface Letters {
  a: string;
  b: string;
}

const letters: Letters = {
  a: "a",
  b: "b",
};
```

### Types in TypeScript

#### Simple types

There is already a small set of primitive types available in JavaScript: **boolean, bigint, null, number, string, symbol, and undefined**, which you can use in an interface.

TypeScript extends this list with a few more, such as **any** (allow anything), [**unknown**](https://mariusschulz.com/blog/the-unknown-type-in-typescript) (ensure someone using this type declares what the type is), **never** (it’s not possible that this type could happen), and **void** (a function which returns undefined or has no return value).

#### Composition types

Compining simple types, **complex types** can be created.

With TypeScript, you can create complex types by combining simple ones. There are two types:

- unions
  multiple specific types
- generics
  Generics provide variables to types. A common example is an array. An array without generics could contain anything. An array with generics can describe the values that the array contains.

[learn more about type](https://github.com/artrugh/typescript)
