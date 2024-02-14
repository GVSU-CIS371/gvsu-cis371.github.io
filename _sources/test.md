# TypeScript Exercises I

---

## Variations of Function Declarations

1. **Named Function Declaration:** A traditional function declaration with a specific name.

   ```typescript
   function greet(name: string): string {
     return `Hello, ${name}!`;
   }
   ```

2. **Anonymous Function:** A function without a name, usually assigned to a variable.

   ```typescript
   const greet = function (name: string): string {
     return `Hello, ${name}!`;
   };
   ```

3. **Lambda/Fat Arrow Function:** A modern way to express functions using the "fat arrow" (`=>`) syntax.

   ```typescript
   const greet = (name: string): string => {
     return `Hello, ${name}!`;
   };
   ```

4. **Lambda/Fat Arrow Function (implicit return, typeless):** An arrow function where the return is implicit, no need for the return keyword.

   ```typescript
   const greet = (name) => `Hello, ${name}!`;
   ```

5. **Lambda/Fat Arrow Function with default parameter(implicit return, typeless):** An arrow function with a default parameter, used when no argument is provided.

   ```typescript
   const greet = (name = "Alice") => `Hello, ${name}!`;
   ```

### Exercise 1

```typescript
function add(a: number, b: number): number {
  return a + b;
}
```

**Tasks:**

1. Write the **Anonymous Function** version of the `add` function.

   ````{admonition} Answer
   :class: dropdown
      ```typescript
      const add = function(a: number, b: number): number {
       return a + b;
      }
      ```
   ````

2. Write the **Lambda/Fat Arrow Function** version of the `add` function.

   ````{admonition} Answer
   :class: dropdown
      ```typescript
      const add = (a: number, b: number): number => {
       return a + b;
      }
   ````

3. Write the **Lambda/Fat Arrow Function with implicit return(typeless)** version of the `add` function.

   ````{admonition} Answer
   :class: dropdown
      ```typescript
      const add = (a, b) => a + b;
   ````

---

### Exercise 2

```typescript
function isEven(num: number): boolean {
  if (num % 2 === 0) {
    return true;
  } else {
    return false;
  }
}
```

**Tasks:**

1. Write the **Anonymous Function** version of the `isEven` function.

   ````{admonition} Answer
   :class: dropdown
      ```typescript
      const isEven = function(num: number): boolean {
          return num % 2 === 0;
      }
   ````

2. Write the **Lambda/Arrow Function** version of the `isEven` function.

   ````{admonition} Answer
   :class: dropdown
      ```typescript
      const isEven = (num: number): boolean => {
       return num % 2 === 0;
      }
   ````

3. Write the **Lambda/Fat Arrow Function with implicit return(typeless)** version of the `isEven` function.

   ```{admonition} Answer
   :class: dropdown
      const isEven = (num) => num % 2 === 0;
   ```
