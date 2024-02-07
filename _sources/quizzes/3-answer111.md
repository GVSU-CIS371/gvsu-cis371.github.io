# Quize 3 TypeScript Basics

Given the following array,

```javascript
let books = [
  { title: "1984", author: "George Orwell", pages: 328 },
  { title: "The Great Gatsby", author: "F. Scott Fitzgerald", pages: 180 },
  { title: "To Kill a Mockingbird", author: "Harper Lee", pages: 281 },
  { title: "Brave New World", author: "Aldous Huxley", pages: 264 },
  { title: "The Catcher in the Rye", author: "J.D. Salinger", pages: 234 },
];
```

Complete the following tasks in TypeScript:

1. Typing an Object

   Create a TypeScript interface or type named `Book` to describe the structure of the objects within the `books` array.

2. Copy Elements with `slice()`

   Copy the last 2 objects from the array `books` using `slice()`, and `console.log` the result.

3. Replace Elements with `splice()`

   In the books array, replace the 3th object with two new objects `{ title: "The Hobbit", author: "J.R.R. Tolkien", pages: 310}` and `{title: "Pride and rejudice", author: "Jane Austen", pages: 432};` using `splice()`, and `console.log` the updated `books`.

4. Iterate Over Object Properties

   Use for-loop (`for-in` or `for-of`) to `console.log` all properties names and values of all objects in `books`.

5. Splitting an Array into Two Parts with Destructuring and the Spread Operator

   Write a function `splitIt` that takes a `Book` array as input, splits it into two parts: the first two elements and the rest, and returns both parts.

   ```javascript
   const [firstTwo, theRest] = splitIt(books);
   console.log("First Two Books:", firstTwo);
   console.log("The Rest of the Books:", theRest);
   ```

Test your solutions on [typescriptlang.org](https://www.typescriptlang.org/play?#code/MYewdgzgLgBARiEBrCMC8MDaBYAUDGAbxigEsoAbAUwC4YAiARgE4AOAFnoBoYBDAVygALEACc69AOJUxAcyowA8qIDuVChW4wADr3kQ6AZgBMrGAF8ueAsTKVaDACpCFk0VV6xJniHACeWgLCYhIAYgB0MADKoFCwoeQAXvKivBQAJlq6+nSMrAAMFlb4RCTk1BKOIDAA0qQafDAAsiDASKRgsnCkopk8QSLiDAASvKLaVKIwADJUVFl6VAYwpoxF1qV2FQwAQqkAbgoAclQqMADqYhmBgoMSAIIZIPyow-wAHtQBPNlLdMYANnY6xKtnKDnozgUAGFPMAXFMOiQXDAAEp+eb9W4hBgAKXCABFIlE0h0UgscitDMDLHgALoAbiAA):

1.  ```js
    type Book = {
      title: string,
      author: string,
      pages: number,
    };
    ```

2.  ```js
    console.log(books.slice(-2));
    ```

3.  ```js
    books.splice(
      2,
      1,
      { title: "The Hobbit", author: "J.R.R. Tolkien", pages: 310 },
      { title: "Pride and rejudice", author: "Jane Austen", pages: 432 }
    );
    console.log(books);
    ```

4.  ```js
    for(let k of books){
      console.log(`##Book: ${k}##`);
      let temp = k as any;
      for(let j in k){
         console.log(j+":"+temp[j]);
      }
    }
    ```

5.  ```js
    function splitIt([first, second, ...rest]: Book[]): [Book[], Book[]] {
      return [[first, second], rest];
    }
    ```
