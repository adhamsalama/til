In TypeScript, you can define function overloads to provide different function signatures for the same function name. This can be useful when you have a function that can accept multiple argument types or return types.

Here's an example of how to define function overloads for a pure function:

```ts
function add(a: number, b: number): number;
function add(a: string, b: string): string;
function add(a: any, b: any): any {
  return a + b;
}
```

In this example, we define three function signatures for the `add` function. The first signature accepts two `number` arguments and returns a `number`. The second signature accepts two `string` arguments and returns a `string`. The third signature accepts any two arguments of any type and returns a value of the same type as the arguments.

The third signature is the implementation signature, which defines the actual function logic. The first two signatures are the overload signatures, which define the different function signatures that the `add` function can be called with.

When you call the `add` function with arguments, TypeScript will choose the correct overload based on the types of the arguments. Here are some examples:

```ts
const result1 = add(1, 2); // result1 is inferred as number
const result2 = add("Hello, ", "world!"); // result2 is inferred as string
```

In this example, the first call to `add` matches the first overload signature, so the return type is inferred as `number`. The second call matches the second overload signature, so the return type is inferred as `string`.

By using function overloads, you can provide multiple function signatures for the same function name, which can make your code more readable and easier to use.
