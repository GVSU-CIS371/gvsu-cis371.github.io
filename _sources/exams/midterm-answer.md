# Midterm Exam Answer

---

1. Consider the `index.html` and `style.css` provided below. Due to the cascading nature of CSS, what color will "Hello World" be rendered as?

   - [ ] black
   - [ ] red
   - [ ] green
   - [x] blue

   **style.css**

   ```css
   #sample {
     color: red;
   }
   ```

   **index.html**

   ```html
   <html lang="en">
     <head>
       <link rel="stylesheet" href="style.css" />
       <style>
         #sample {
           color: green;
         }
       </style>
     </head>
     <body>
       <span id="sample" style="color: blue">Hello World.</span>
     </body>
   </html>
   ```

2. Given the following DOM structure, which elements are directly targeted by the `div > span`?

   - [ ] "one"
   - [ ] "one", "two", and "three"
   - [ ] "four"
   - [x] "one" and "three"

   **DOM Structure:**

   ```
   body
   |-- div
   |   |-- span
   |   |   |-- "one"
   |   |-- p
   |   |   |-- span
   |   |       |-- "two"
   |   |-- span
   |       |-- "three"
   |-- span
       |-- "four"
   ```

3. The `:nth-child()` pseudo-class

   - [ ] Targets a child based on its type
   - [ ] Targets the nth child of a specific type
   - [ ] Targets the nth last child a specific type
   - [x] Targets a child based on its order in the DOM

4. In TypeScript, the purpose of unions is to

   - [ ] Join multiple arrays
   - [x] Allow a variable to be of multiple types
   - [ ] Merge multiple objects
   - [ ] Concatenate strings

5. Which of the following methods can be used to delete elements from an array in TypeScript?

   - [ ] `.push()`
   - [ ] `.pop()`
   - [ ] `.slice()`
   - [x] `.splice()`

6. Given the object and array

   ```js
   const obj1 = { name: "John" };
   const arr = [1, 2, 3];
   const obj2 = { ...obj1, arr };
   ```

   The resulting obj2 will be

   - [ ] `{ obj1: {name: "John"}, arr: [1, 2, 3] }`
   - [x] `{ name: "John", arr: [1, 2, 3] }`
   - [ ] `{ name: "John", 0: 1, 1: 2, 2: 3 }`
   - [ ] `{ obj1: {name: "John"}, 0: 1, 1: 2, 2: 3 }`

7. The `:last-child` pseudo-class targets the last child of a parent element

   - [x] True
   - [ ] False

8. In TypeScript, == checks both type and value whereas === only checks value

   - [ ] True
   - [x] False

9. `.splice()` in arrays creates a new array and doesn't modify the original one

   - [ ] True
   - [x] False

10. Given the following DOM,

    **HTML**

    ```html
    <h2>Title</h2>
    <ul>
      <li><a href="#">Link 1</a></li>
      <li><a href="#">Link 2</a></li>
      <li><a href="#">Link 3</a></li>
      <li><a href="#">Link 4</a></li>
    </ul>
    <ul>
      <li>Item 1</li>
      <li>Item 2</li>
      <li>Item 3</li>
    </ul>
    ```

    a. Write the Emmet abbreviation used to generate this DOM.

    ````{admonition} Answer
    ```js
    h2{Title}>(ul>li*4>a[href=#]{Link $})+ul>li*3{Ltem $}
    ```
    ````

    b. Write the CSS selector to target the `<li>Item 2</li>`.

    ````{admonition} Answer
    ```js
    ul:nth-of-type(2)>li:nth-child(2){
      color:red;
    }
    ```
    ````

    c. Suppose the list item `Item 3` is bound to the function clickme as `<li onclick="clickme(this)">Item 3</li>`. Implement the clickme function so that upon clicking, the text content of `Item 3` updates to “Updated Item 3”.

    ````{admonition} Answer
    ```js
    function clickme(element) {
        element.textContent ="Updated Item 3";
    }
    ```
    ````

11. In the provided TypeScript code, our goal is to calculate the student's average grade. Your task is to implement logic to calculate the sum of their grades.

    **Main.ts**

    ```js
    type Student = {
      id: number,
      name: string,
      grade: number,
    };

    const students: Student[] = [
      { id: 1, name: "Alice", grade: 85 },
      { id: 2, name: "Bob", grade: 90 },
      { id: 3, name: "Charlie", grade: 78 },
      { id: 4, name: "Dana", grade: 88 },
      { id: 5, name: "Eve", grade: 92 },
    ];
    ```

    - Your task is to implement the following functions using only high-order functions such as .sort(), .some(), .filter(), .flatMap(), .map(), and .reduce().
    - Solutions utilizing traditional for-loops or .forEach() will not be accepted.

    a. Use `.sort()` to sort students according to their grades in ascending order (highest last).

    ````{admonition} Answer
    ```js
    students.sort((a,b)=>a.grade-b.grade);
    ```
    ````

    b. Create a new array of strings for students whose grades are greater than or equal to 90. Each string should be formatted as follows: "The student {name} has a grade of {grade}."

    ````{admonition} Answer
    ```js
    const strs = students.filter((s)=>s.grade>=90).map((s)=>`The student ${s.name} has a grade of ${s.grade}.`);
    ```
    ````

    c. Use `.reduce()` to calculate the sum of students' grades.

    ````{admonition} Answer
    ```js
    console.log(students.reduce((s,cur)=>s+cur.grade,0));
    ```
    ````

   <!-- 5. In TypeScript, what does the `??` operator do?

      - [ ] Compares values.
      - [ ] Acts as a logical AND operator.
      - [x] Acts as a coalesce operator, returning the right-hand operand if the left-hand operand is null or undefined.
      - [ ] Tells the compiler to trust that the preceding value is not null or undefined.

   1. In Vue.js, the `v-model` directive is used for

      - [x] Two-way data binding
      - [ ] Event handling
      - [ ] Conditional rendering
      - [ ] Looping through arrays

   2. Which of the following is NOT a Vue.js 3 lifecycle function?

      - [ ] `onMounted()`
      - [ ] `onUpdated()`
      - [ ] `onBeforeMount()`
      - [x] `onBeforeCreate()`

   3. **(bonus)**Examine the provided DOM structure. Without any Event Modifier, the events originating from "one" propagate in the order: $span > p > div$. Now, if we add the `.capture` modifier to the `@click` event on the second paragraph, in which order will the events originating from "two” propagate

      - [ ] $span > p > div$
      - [x] $p > span > div$
      - [ ] $span > p$
      - [ ] $p > span$

      **DOM Structure:**

      ```
      div
      |-- p
      |   |-- span
      |       |-- "one"
      |-- p @click.capture
          |-- span
              |-- "two"
      ```

   4. Web Client/Server Architecture only supports static read-only web apps

      - [ ] True
      - [x] False

   5. The CSS property position: relative takes an element out of the normal document flow and positions it based on its closest positioned parent

      - [ ] True
      - [x] False-->

   <!-- 1. Vue.js 3.x allows only one-way data binding

      - [ ] True
      - [x] False

   6.  Examine the provided Vue component code in App.vue

       **App.vue**

       ```js
       <template>
         <h1>{{ who }} is {{ age }}</h1>
         <p>Enter your name: <input id="name" type="text" v-bind:value="who" /></p>
         <p>
           Pick an age:
           <input id="age" type="range" v-model.number="age" min="1" max="100" />
         </p>
       </template>
       <script setup lang="ts">
       import { ref } from "vue";
       const who = "Alice";
       const age = 21;
       </script>
       ```

       a. How can you implement two-way binding for the text input element with the ID "name"?

       ````{admonition} Answer
       ```js
       <input id="name" type="text" v-model="who" />
       ```
       ````

       b. How can you apply Vue's Reactive Reference to the variables `who` and `age`?

       ````{admonition} Answer
       ```js
       const who = ref("Alice");
       const age = ref(21);
       ```
       ````

       c.**(bonus)** The initial setup uses one-way binding for the text input element with the ID "name". What problems might arise in this situation?

       ```{admonition} Answer
       When we change the name in the textbox "name", the variable `who` won't change, so the displayed name in the `<h1>{{ who }} is {{ age }}</h1>` won't be updated.
       ```

       d.**(bonus)** What potential issues might arise if we don't utilize Vue's Reactive Reference for the variables `who` and `age`?

       ```{admonition} Answer
       When we change the name in the textbox "name" or the age using the input range. the variables `who` and `age` cannot be changed, because they are const.
       Without using Vue's reactivity system (like ref or reactive), the variables `who` and `age` won't trigger updates in the DOM when their values change. This means the user interface won't reflect the current state of these variables, leading to a stale or misleading display. Additionally, when we change the name in the textbox "name" or the age in the input range, it attempts to reassign the const variables, which will result in a runtime error since const variables cannot be reassigned.
       ``` -->
