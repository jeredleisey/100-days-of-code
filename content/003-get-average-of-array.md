::Post

#prompt
Write a function that takes an array of numbers as input and returns the average of all the numbers.

#default

```ts [003-get-average-of-array.ts]
const getAverageOfArray = (set: number[]) => set.reduce((a, b) => a + b) / set.length;
```

::
