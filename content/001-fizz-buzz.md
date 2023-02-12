::Post

#prompt
Write a function that takes a number as input and returns "Fizz" if it is divisible
by 3, "Buzz" if it is divisible by 5, and "FizzBuzz" if it is divisible by both.

#default

```ts [001-fizz-buzz.ts] {}
function fizzBuzz(num: number) {
  return (
    (num % 3 ? '' : 'Fizz') + (num % 5 ? '' : 'Buzz') ||
    'Not divisible by 3 or 5.'
  );
}
```

::
