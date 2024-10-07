# Midterm Exam

1. Given the following HTML,

   ```html
   <body>
     <section class="product">
       <h3>Product Details</h3>
       <div class="info">
         <ul>
           <li>Name: UltraPhone X</li>
           <li>Stock: 22</li>
         </ul>
         <p>Latest model with advanced features</p>
       </div>
     </section>
   </body>
   ```

   Write the Emmet abbreviation used to generate this html.

   **Your Answer:**

2. Given the following HTML,

   ```HTML
   <body>
      <div id="main">
       <h3>Product List</h3>
       <p class="content">Details of the products:</p>
       <table>
         <tr class="headers">
           <th>Product Name</th>
           <th>Stock</th>
         </tr>
         <tr>
           <td>UltraPhone X</td>
           <td>22</td>
         </tr>
         <tr>
           <td>SmartTablet Pro</td>
           <td>35</td>
         </tr>
         <tr>
           <td>SmartTV</td>
           <td>27</td>
         </tr>
       </table>
      </div>
   </body>

   ```

   Write a CSS selector that specifically(only) targets the first row of the table (excluding the headers).

   **Your Answer:**

3. You have the following CSS styles applied to the table:

   ```css
   table tr {
     background-color: yellow;
   }
   tr:nth-child(even) {
     background-color: gray;
   }
   td:nth-child(2) {
     background-color: red;
   }

   .headers ~ tr:last-child {
     background-color: green;
   }
   ```

   What background color will be applied to the number 27(stock for smart TV)?

   **Your Answer:**

4. Convert the following `getGreeting` function to a lambda/fat arrow function using single-line return contraction, and ensure that it properly handles null and undefined values:

   ```typescript
   function getGreeting(
     name?: string | null,
     greeting?: string | null
   ): string {
     if (greeting && name) {
       return `${greeting}, ${name}!`;
     } else if (greeting) {
       return `${greeting}, Guest!`;
     } else if (name) {
       return `Hello, ${name}!`;
     } else {
       return "Hello, Guest!";
     }
   }
   ```

   **Your Answer:**

5. Write a function sumEvenNumbers that accepts an array of integers and returns the sum of all even numbers in the array. For example, sumEvenNumbers([1, 2, 3, 4, 5]) should return 6.

   **Your Answer:**

6. Given the following products array, complete questions 6 - 8.

   ```typescript
   type Product = {
     id: number;
     name: string;
     category: string;
     price: number;
     inStock: boolean;
   };

   const products: Product[] = [
     {
       id: 1,
       name: "Laptop",
       category: "Electronics",
       price: 1000,
       inStock: true,
     },
     {
       id: 2,
       name: "Headphones",
       category: "Electronics",
       price: 100,
       inStock: false,
     },
     {
       id: 3,
       name: "Coffee Maker",
       category: "Home Appliances",
       price: 75,
       inStock: true,
     },
     {
       id: 4,
       name: "Blender",
       category: "Home Appliances",
       price: 50,
       inStock: false,
     },
     {
       id: 5,
       name: "Smartphone",
       category: "Electronics",
       price: 800,
       inStock: true,
     },
   ];
   ```

   Calculates how many kinds of products are currently in stock?

   **Your Answer:**

7. Create a new array containing only the products that belong to the **"Electronics"** category and are **in stock**.

   **Your Answer:**

8. Find the product in the **"Home Appliances"** category with the **highest price**.

   **Your Answer:**

Test your solutions on

- [CodePen](https://codepen.io/Yong-Zhuang/pen/yLdwRLP)
- [typescriptlang.org](https://www.typescriptlang.org/play?#code/Q)
