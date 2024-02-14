# Exam Review Exercises

Given the following HTML,

```html
<body>
  <div id="content">
    <h1>Welcome</h1>
    <p class="description"></p>
    <ul>
      <li>Item 1</li>
      <li>Item 2</li>
      <li>Item 3</li>
    </ul>
  </div>
</body>
```

1. Write the Emmet abbreviation used to generate this html.

2. Use `addEventListener` or `onclick` to set an onclick event for the second `<li>` element, and when it is clicked, change its text content to "Updated Item 2".

   To verify your answer, use the following CSS code on the online platform CodePen at [https://codepen.io/Yong-Zhuang/pen/VwRqbLv](https://codepen.io/Yong-Zhuang/pen/VwRqbLv):

3. ```HTML
   const students = [
     { id: 1, name: "Alice" },
     { id: 2, name: "Bob" },
     { id: 3, name: "Charlie" },
     { id: 4, name: "Tom" },
     { id: 5, name: "Jack" },
   ];
   ```

   - Copy the last 3 objects from the array `students` using `slice()`.
   - Split `students` into `first-student` and `rest` using the Spread Operator.

4. Write the **Lambda/Fat Arrow Function** version of the following `add` function.

   ```typescript
   function add(a: number, b: number): number {
     return a + b;
   }
   ```

5. Write the **Lambda/Fat Arrow Function with implicit return(typeless)** version of the following `isEven` function.

   ```typescript
   function isEven(num: number): boolean {
     if (num % 2 === 0) {
       return true;
     } else {
       return false;
     }
   }
   ```

   Test your solutions on [typescriptlang.org](https://www.typescriptlang.org/play?#code/Q):
