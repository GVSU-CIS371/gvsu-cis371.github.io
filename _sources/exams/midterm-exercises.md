# Midterm Review and Practice

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

**Your Answer:**

1. Write the Emmet abbreviation used to generate this html.

   ```HTML
     <body>
       <header id="header">
         <h1>Welcome to My Site</h1>
       </header>
       <nav>
         <ul>
           <li class="menu-item">Home</li>
           <li class="menu-item">About</li>
           <li class="menu-item">Contact</li>
         </ul>
       </nav>
       <div class="content">
         <p>This is a sample paragraph in the content section.</p>
       </div>
       <footer>
         <p>Thank you for visiting!</p>
       </footer>
     </body>
   ```

2. Write a CSS selector that specifically targets and selects only the paragraph containing the text "This is a sample paragraph in the content section.

   **Your Answer:**

3. Using the following CSS style on the DOM, which style (color) will be rendered for "About".

   ```css
   .menu-item {
     color: blue;
   }
   li.menu-item {
     color: green;
   }
   .menu-item[class] {
     color: purple;
   }
   li:nth-child(2) {
     color: red;
   }
   ```

   **Your Answer:**

4. ```typescript
   const students = [
     { id: 1, name: "Alice" },
     { id: 2, name: "Bob" },
     { id: 3, name: "Charlie" },
     { id: 4, name: "Tom" },
     { id: 5, name: "Jack" },
   ];
   ```

   - Copy the last 3 objects from the array `students` using `slice()`.

   **Your Answer:**

   - Split `students` into `first-student` and `rest` using the Spread Operator.

   **Your Answer:**

5. Convert the following `getFullName` function to a lambda/fat arrow function using single-line return contraction, and ensure that it properly handles null and undefined values:

   ```typescript
   function getFullName(
     firstName?: string | null,
     lastName?: string | null
   ): string {
     if (firstName && lastName) {
       return `${firstName} ${lastName}`;
     } else if (firstName) {
       return firstName;
     } else if (lastName) {
       return lastName;
     } else {
       return "No name provided";
     }
   }
   ```

   **Your Answer:**

   ```typescript
   type Student = {
     id: number;
     name: string;
     grade: number;
   };

   const students: Student[] = [
     { id: 1, name: "Alice", grade: 85 },
     { id: 2, name: "Bob", grade: 90 },
     { id: 3, name: "Charlie", grade: 78 },
     { id: 4, name: "Dana", grade: 88 },
     { id: 5, name: "Eve", grade: 92 },
   ];
   ```

6. Use `.sort()` to sort students according to their grades in ascending order (highest last).

   **Your Answer:**

7. Use `.reduce()` to calculate the sum of students' grades.

   **Your Answer:**

Test your solutions on

- [CodePen](https://codepen.io/Yong-Zhuang/pen/yLdwRLP)
- [typescriptlang.org](https://www.typescriptlang.org/play?#code/Q)
