# Exam Review Exercises I

---

**You are not require to include any import statements of the libraries used, but you are required to include the type of every variable used in lambda expressions (i.e. "fat arrow functions").**

1. Given the following type declarations.

   <!-- prettier-ignore -->
   ::::{grid}
   :gutter: 3

   :::{grid-item}

   ```javascript
   type Product = {
     name: string,
     price: number,
   };
   ```

   :::

   :::{grid-item}

   ```javascript
   type Order = {
     products: Array<Product>,
     isDelivered: boolean,
   };
   ```

   :::

   :::{grid-item}

   ```javascript
   type Customer = {
     name: string,
     city: string,
     orders: Array<Order>,
   };
   ```

   :::

   Your task is to implement the following functions using only Java|Type Script Array functions: `.every()`,`.map()`, `.flatMap()`,`.some()`,`.sort()`, etc.

   **Note**

   - Your answer should not require additional data storage (local/global variables) beyond what are provided as function input arguments of each function below.
   - Answers using traditional `for-loop` or `.forEach` will not be accepted.

   **(a) Collect all undelivered products ordered by a particular customer**

   <!-- prettier-ignore -->
   ::::{grid}
   :gutter: 1

   <!-- prettier-ignore -->
   :::{grid-item}

   ```ts
   function undeliveredProductsOf(cust: Customer): Array<Product> {
     // Implement the logic to return an array of all undelivered products ordered by the given customer
     return cust.orders
       .filter((order) => !order.isDelivered)
       .flatMap((order) => order.products);
   }
   ```

   :::

   &nbsp;

   &nbsp;

   &nbsp;

   &nbsp;

   **(b) Find the most expensive product ordered in a city**

   <!-- prettier-ignore -->
   ::::{grid}
   :gutter: 1

   :::{grid-item}

   ```ts
   function mostExpensiveProduct(db: Array<Customer>, city: string): Product {
     // Implement the logic to find and return the most expensive product ordered in the specified city
     return db
       .filter((customer) => customer.city === city)
       .flatMap((customer) => customer.orders)
       .flatMap((order) => order.products)
       .sort((a, b) => b.price - a.price)[0];
   }
   ```

   &nbsp;

   &nbsp;

   &nbsp;

   &nbsp;

2. Amy and Beth, using a browser and a smartphone respectively, both connect to Firebase Cloud Firestore for an initial data load. This data is cached locally on their devices for quick access and offline support. As Amy updates data on her app, these changes are instantly reflected locally and then sent to Firebase. Firebase, in turn, notifies other clients like Beth's device, updating their local views with the new changes.

   ```{image} ./images/firestore.jpg
   :alt: dom
   :width: 750px
   :align: center
   ```

   <!-- prettier-ignore -->
   ::::{grid}
   :gutter: 1

   :::{grid-item-card} data-types.ts

   ```ts
   export type Movie = {
     id: string;
     title: string;
     synopsis: string;
     thumbsUpCount: number;
   };
   ```

   :::

   Alice has just given a thumbs up to a movie. This action needs to be reflected in the Firebase Firestore database by incrementing the thumbsUpCount field of the specific movie. Implement the addThumbsUp function in the doc-update.ts file. This function should increase the thumbsUpCount for a movie, identified by its movieId. The movie data is stored in the Firestore database within the `movies` collection.

   <!-- prettier-ignore -->
   ::::{grid}
   :gutter: 1

   :::{grid-item-card} doc-update.ts

   ```ts
   import { Movie } from "./data-types";
   const app: FirebaseApp = initializeApp(firebaseConfig);
   const db: Firestore = getFirestore(app);
   function addThumbsUp(movieId: string) {
     // Implement the logic to increment the thumbsUpCount for a movie with the given id
     const movieRef = doc(db, "movies", movieId);
     updateDoc(movieRef, {
       thumbsUpCount: increment(1),
     });
   }
   ```

   :::

   &nbsp;

   &nbsp;

   &nbsp;

   &nbsp;

   Since Alice has recently made changes to a movie's information in the movies collection on Firebase Firestore. Emma should see these updates in the app on her smartphone in real-time. Implement the listen_item function in the doc-update.ts file to enable real-time updates on Emma's smartphone whenever a specific movie's data is modified in the Firestore database.

   <!-- prettier-ignore -->
   ::::{grid}
   :gutter: 1

   :::{grid-item-card} doc-update.ts

   ```ts
   import { Movie } from "./data-types";
   const app: FirebaseApp = initializeApp(firebaseConfig);
   const db: Firestore = getFirestore(app);

   function listen_item(movieId: string) {
     // Implement the logic to listen to changes on a movie with the given id
     const movie = doc(db, "movies", movieId);
     onSnapshot(movie, (ds: DocumentSnapshot) => {
       console.log("Doc updated", ds.data());
     });
   }
   ```

   :::

3. Assume a hypothetical web service at <http://petpics.io> provides an endpoint /search that returns image files of particular animal types. This API endpoint accepts a query parameter pet to request specific pet types. The following URL is an example of a request to this web service: <http://petpics.io/search?pet=bird,cat> to which the service responds with a JSON data in the following format:

   <!-- prettier-ignore -->
   ::::{grid}
   :gutter: 1

   :::{grid-item-card} JSON

   ```json
   [
     {
       "pet": "bird",
       "images": [
         { "url": "http://bit.ly/987123.png", "width": 1078, "height": 876 },
         { "url": "http://bit.ly/411344.jpg", "width": 761, "height": 413 },
         { "url": "http://bit.ly/713287.jpg", "width": 512, "height": 512 }
       ]
     },
     {
       "pet": "cat",
       "images": [
         /* more data here */
       ]
     }
   ]
   ```

   :::

   Demonstrate your knowledge of using the axios library to fetch data from the above web service.

   **(a) Define TypeScript Types:** Define the appropriate TypeScript type(s) to model the response data from this API.

   ```ts
   type Image = {
     url: string;
     width: number;
     height: number;
   };

   type Pet = {
     pet: string;
     images: Image[];
   };
   ```

   &nbsp;

   &nbsp;

   &nbsp;

   &nbsp;

   **(b) Fetch Dog Images Using Axios and Promise then():** Demonstrate your knowledge of using **axios** and **Promise** `then()` function to fetch dog images and then store the **URLs** in an array of strings. Be sure all your variables are properly typed. Include error handling for the request.

   ```ts
   import axios from "axios";

   function fetchDogImages(): Promise<string[]> {
     return axios
       .get<Pet[]>("http://petpics.io/search?pet=dog")
       .then((response: AxiosResponse) => {
         if (!response.data) {
           throw new Error("No dog images found");
         }
         return response.data.flatMap((pet: Pet) =>
           pet.images.map((image: Image) => image.url)
         );
       })
       .catch((error) => {
         console.error("Error fetching dog images:", error);
         return [];
       });
   }
   ```

   &nbsp;

   &nbsp;

   &nbsp;

   &nbsp;

   **c. Fetch Dog Images Using Async-Await:** Repeat the above task (2), but this time use async-await syntax. Pay attention to proper error handling.

   ```ts
   import axios from "axios";
   async function fetchDogImagesAsync(): Promise<string[]> {
     try {
       const response: AxiosResponse = await axios.get<Pet[]>(
         "http://petpics.io/search?pet=dog"
       );
       if (!response.data) {
         throw new Error("No dog images found");
       }
       return response.data.flatMap((pet: Pet) =>
         pet.images.map((image: Image) => image.url)
       );
     } catch (error) {
       console.error("Error fetching dog images:", error);
       return [];
     }
   }
   ```

   &nbsp;

   &nbsp;

   &nbsp;

   &nbsp;

4. Create a clone of the Pet Picture web service in the previous question using ExpressJS. Unlike petpics.io which accepts multiple pet types (i.e. ?pet=cat,bird,dog), your clone can only accept a single pet type (i.e. ?pet=something) in its URL.

   Assume the following snippet has been provided.

   ```ts
   import express, { Application, Request, Response } from "express";
   const app: Application = express();
   const PORT = 1234;
   /* missing code here to be completed in your answer below */
   app.listen(PORT);
   ```

   (a) Define the type needed to parse the query parameter in the URL

   ```ts
   type Query = { pet: string };
   ```

   &nbsp;

   &nbsp;

   &nbsp;

   &nbsp;

   (b) Add the missing code to handle the /search endpoint. Your code should demonstrate your understanding of

   - Parsing the incoming pet type
   - Sending a JSON response in the exact format specified in the previous question (it is acceptable to hardcode some part of the JSON response).

   ```ts
   const petData = [
     {
       pet: "bird",
       images: [
         { url: "http://bit.ly/987123.png", width: 1078, height: 876 },
         { url: "http://bit.ly/411344.jpg", width: 761, height: 413 },
         { url: "http://bit.ly/713287.jpg", width: 512, height: 512 },
       ],
     },
     {
       pet: "cat",
       images: [
         /* more data here */
       ],
     },
   ];

   app.get("/search", (req: Request<any, any, any, Query>, res: Response) => {
     const petRequested = req.query.pet;
     const resData = petData.find((pet) => pet.pet === petRequested);

     if (!resData) {
       res.status(404).json({ error: "Pet type not found" });
       return;
     }

     res.json(resData);
   });
   ```

   &nbsp;

   &nbsp;

   &nbsp;

   &nbsp;
