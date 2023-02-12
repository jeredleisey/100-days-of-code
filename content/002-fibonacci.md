::Post

#prompt
Create a function that returns the first n Fibonacci numbers and returns them in an array.

#default

```ts [002-fibonacci.ts]
const createFibonacci = (size: number) => {
  let fibonacciSequence = [0];

  if (size < 1) return 'Size must be greater than zero.';
  else if (size == 1) return fibonacciSequence;
  else fibonacciSequence.push(1);

  for (let i = 1; i < size; i++) {
    fibonacciSequence.push(fibonacciSequence[i - 1] + fibonacciSequence[i]);
  }

  return fibonacciSequence;
};
```

::
