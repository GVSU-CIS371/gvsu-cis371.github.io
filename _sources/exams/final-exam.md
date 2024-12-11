# Final Exam

---

## Coding Questions

1. Alice and Emma are exploring a movie app that is connected to Firebase Cloud Firestore. The app allows users to interact with the movies in various ways.

   - a. Alice wants to add a new review for a movie in the Firestore database. Create the `addMovieReview` function in `review-update.ts` to add a new review for a movie identified by its `movieId` in the `reviews` collection. Each review document should include `id: string`, `movieId: string`, `content: string`, and `rating: number` fields.

   ```javascript
   // data-types.ts
   type Review = {
     id: string,
     movieId: string,
     content: string,
     rating: number,
   };
   ```

   ```javascript
   // review-update.ts
   const app: FirebaseApp = initializeApp(firebaseConfig);
   const db: Firestore = getFirestore(app);
   function addMovieReview(
     movieId: string,
     reviewContent: string,
     rating: number
   ) {
     // Implement the logic to add a new review
     // for a movie with the given movieId, reviewContent, and rating
   }
   ```

   - b. Emma is interested in getting notifications on her smartphone whenever a new review is added for her favorite movie. Implement the `listenToNewReviews` function in`review-update.ts` to enable real-time notifications on Emma's smartphone. Additionally, complete the implementation in `Movie.vue` to display these reviews as they are added.

     ```javascript
     // review-update.ts
     function listenToNewReviews(
       movieId: string,
       callback: (review: Review) => void
     ) {
       // Implement the logic to listen to new reviews for a movie with the given id
     }
     ```

     ```javascript
     // Movie.vue
     <script lang="ts" setup>
     import { ref, Ref, onMounted, onUnmounted } from "vue";
     import { Review } from "../data-types";
     import { listenToNewReviews } from "../review-update";

     const { movieId } = defineProps<{ movieId: string }>();
     const reviews: Ref<Array<Review>> = ref([]);

     let unsubscribe: () => void;
     // Add your code implementation here

     </script>
     ```

2. Assume a hypothetical web service at <http://foodinfo.io> provides an endpoint `/recipes` that returns recipe details for various cuisines. This API endpoint accepts a query parameter `cuisine` to request specific types of cuisines. The following URL is an example of a request to this web service:

   <http://foodinfo.io/recipes?cuisine=italian,mexican> to which the service responds with JSON data in the following format:

   ```javascript
   [
     {
       cuisineType: "italian",
       recipes: [
         { name: "Spaghetti Carbonara", prepTime: 30, difficulty: "Medium" },
         { name: "Margherita Pizza", prepTime: 45, difficulty: "Hard" },
       ],
     },
     {
       cuisineType: "mexican",
       recipes: [
         /* more data here */
       ],
     },
   ];
   ```

   Showcase your skills in using the axios library to interact with the above web service.

   - a. Define appropriate TypeScript type(s) to model the response data from this API.

     ```javascript
     // TypeScript types for the response data
     // Add your code implementation here
     ```

   - b. Use axios and the Promise `then()` function to fetch Italian recipes and store the recipe names in an array. Ensure correct typing and include error handling.

     ```javascript
     import axios from "axios";
     // Add your code implementation here
     ```

   - c. Repeat the previous task using async-await syntax, with attention to error handling.

     ```javascript
     import axios from "axios";
     // Add your code implementation here
     ```

3. Consider a simple game "Word Unscramble" where the player must unscramble 10 words (one word at a time) to earn 10 points for each correct word. The game will be implemented as a Vue 3.x component using Vuetify.

   - The left screenshot shows a scrambled "catalyst", but the player incorrectly guessed "analyst" in the input text box.
   - The middle screenshot shows the player's current score (10, guessed only one correct word so far), and in the middle of attempting to solve the fourth word, a scrambled "earthquake"
   - The right screenshot illustrates the scenario where, upon completing 10 words and clicking the Skip button, the final score is displayed. At each step of the game, the player may guess the correct word as many times as desired by pressing the Check button, or skip to the next random word without earning points by pressing the Skip button.

   ![Word Unscramble Game](../assets/img/unscramble.jpg)

   You are to implement the game as a Vue 3.x component assuming the following are available to use:

   1. A string array `stockWords` holds 10 selected words (unscrambled) to use in the game.
   2. A function `shuffle()` which takes a string and returns a scrambled copy of the string.

   - a. Show a snippet of code demonstrating how the following variables are used in the UI with Vuetify | HTML components. You don't need to design the entire UI, just the relevant components where the variables are used.

     ```javascript
     <script setup lang="ts">
       const wordIndex = ref(0); // Current word index
       const userInput = ref(""); // Player's input
       const score = ref(0); // Player's score
       const result = ref(""); // Game feedback for final grade
     </script>
     <template>
       // Add your code implementation here
     </template>
     ```

   - b. Complete the doSkip and doCheck functions for the "Word Unscramble" game. These functions should handle the following scenarios:

     - doSkip: Handle the behavior when the Skip button is pressed. If there are more words left in the game, move to the next word and reset the user input. If all words are completed, display the final result with the score.
     - doCheck: Handle the behavior when the Check button is pressed. If the user's input matches the current word, award points, and proceed to the next word with appropriate logic.

     ```javascript
     function doSkip() {
       // when the Skip button is pressed
     }

     function doCheck() {
       // when the Check button is pressed
     }
     ```
