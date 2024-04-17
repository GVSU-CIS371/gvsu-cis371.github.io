# Exam Review Exercises

---

You are not require to include any import statements of the libraries used, but you are required to include the type of every variable used in lambda expressions (i.e. "fat arrow functions").

## Question 1

Alice and Emma are using a movie app connected to Firebase Cloud Firestore.

```{image} ../assets/img/firestore.jpg
:alt: dom
:width: 750px
:align: center
```

**(a)** Alice has given a thumbs up to a movie, and this action needs to be reflected in the Firestore database. Create the `addThumbsUp` function in doc-update.ts to increment the thumbsUpCount for a movie identified by its movieId in the `movies` collection. Each Movie document includes `id: string`, `title: string`, `synopsis: string`, and `thumbsUpCount: number` fields.

<!-- prettier-ignore -->
::::{grid} 
:gutter: 3

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

:::{grid-item-card} doc-update.ts

<!-- prettier-ignore -->
```ts
const app: FirebaseApp = initializeApp(firebaseConfig);
const db: Firestore = getFirestore(app);
function addThumbsUp(movieId: string) {
  // Implement the logic to increment the thumbsUpCount 
  // for a movie with the given id




}
```

````{admonition} Answer
:class: dropdown
```javascript
const app: FirebaseApp = initializeApp(firebaseConfig);
const db: Firestore = getFirestore(app);
function addThumbsUp(movieId: string) {
  // Implement the logic to increment the thumbsUpCount
  // for a movie with the given id
  const movieRef = doc(db, "movies", movieId);
  updateDoc(movieRef, {
     thumbsUpCount: increment(1),
   });
 }
```
````

:::

::::

---

**(b)** Since Alice has recently made changes to a movie's information in the movies collection on Firebase Firestore. Emma should see these updates in the app on her smartphone in real-time. Implement the listen_item function in the doc-update.ts file to enable real-time updates on Emma's smartphone whenever a specific movie's data is modified in the Firestore database.

<!-- prettier-ignore -->
::::{grid} 
:gutter: 2

:::{grid-item-card} doc-update.ts

<!-- prettier-ignore -->
```ts
function listen_item(movieId: string,
callback: (m: Movie | null) => void
) {
  // Implement the logic to listen to changes on a movie with the given id







  
}
```

````{admonition} Answer
:class: dropdown
```ts
function listen_item(movieId: string,
callback: (m: Movie | null) => void
) {
  // Implement the logic to listen to changes on a movie with the given id
  const movie = doc(db, "movies", movieId);
  return onSnapshot(movie, (ds: DocumentSnapshot) => {
   if (ds.exists()) {
     console.log("Movie has been updated.");
     callback(ds.data() as Movie);
   } else {
     console.log("Movie document does not exist.");
     callback(null);
   }
  });
}
```
````

:::

:::{grid-item-card} Movie.vue

<!-- prettier-ignore -->
```ts
<script lang="ts" setup>
import { ref, Ref, onMounted, onUnmounted } from "vue";
import { Movie } from "../data-types";
import { listen_item } from "../doc-update";

const { movie } = defineProps<{ movie: Movie }>();
const m_movie: Ref<Movie> = ref(movie);

let unsubscribe: () => void;

// Add your code implementation here







  

```

````{admonition} Answer
:class: dropdown
```ts
<script lang="ts" setup>
import { ref, Ref, onMounted, onUnmounted } from "vue";
import { Movie } from "../data-types";
import { listen_item } from "../doc-update";

const { movie } = defineProps<{ movie: Movie }>();
const m_movie: Ref<Movie> = ref(movie);

let unsubscribe: () => void;
onMounted(() => {
  unsubscribe = listen_item(movie.id, (m: Movie | null) => {
    if (m) {
      m_movie.value = m;
    }
  });
});

onUnmounted(() => {
  if (unsubscribe) {
    unsubscribe();
  }
});
</script>
```
````

:::

::::

## Quesion 2

Assume a hypothetical web service at <http://petpics.io> provides an endpoint /search that returns image files of particular animal types. This API endpoint accepts a query parameter pet to request specific pet types. The following URL is an example of a request to this web service: <http://petpics.io/search?pet=bird,cat> to which the service responds with a JSON data in the following format:

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

::::

Demonstrate your knowledge of using the axios library to fetch data from the above web service.

**(a)** Define the appropriate TypeScript type(s) to model the response data from this API.

<!-- prettier-ignore -->
```ts
// Add your code implementation here







  

```

````{admonition} Answer
:class: dropdown
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
````

---

**(b)** Demonstrate your knowledge of using **axios** and **Promise** `then()` function to fetch dog images and then store the **URLs** in an array of strings. Be sure all your variables are properly typed. Include error handling for the request.

<!-- prettier-ignore -->
```ts
// Add your code implementation here







  

```

````{admonition} Answer
:class: dropdown
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
````

---

**(c)** Repeat the above task (2), but this time use async-await syntax. Pay attention to proper error handling.

<!-- prettier-ignore -->
```ts
// Add your code implementation here







  

```

````{admonition} Answer
:class: dropdown
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
````

## Question 3

Consider designing a "Trivia Quiz" game where players answer 10 multiple-choice questions (one question at a time) to earn 10 points for each correct answer. The game will be implemented as a Vue 3.x component using Vuetify.

```{image} ../assets/img/trivia_quiz.jpg
:alt: dom
:width: 750px
:align: center
```

- The left screenshot displays the question "What is the capital city of France?", to which the player incorrectly answered "Berlin".
- On the right, the player's current score is shown as 10, indicating that they have correctly answered one question so far. They are currently attempting to answer the third question: "Which country hosted the 2016 Summer Olympics?". In each stage of the game, the player selects an option and clicks the "Next" button. The game then checks the answer, adding 10 points to the current score for a correct response, or leaving the score unchanged if the answer is incorrect. Subsequently, the game either presents the next question or, if all questions have been answered, displays the player's final score.

You are to implement the game as a Vue 3.x component assuming the following are available to use:

- An array questions containing objects of trivia questions. Each object includes a question, an array of possible answers, and the index of the correct answer.

```ts
const questions = [
  {
    question: "What is the capital city of France?",
    options: ["Berlin", "London", "Paris", "Madrid"],
    answer: "Paris",
  },
  {
    question: "Which planet is known as the Red Planet?",
    options: ["Mars", "Jupiter", "Saturn", "Venus"],
    answer: "Mars",
  },
  {
    question: "Which country hosted the 2016 Summer Olympics?",
    options: ["China", "Brazil", "United Kingdom", "Russia"],
    answer: "Brazil",
  },
  /* more questions here */
];
```

**(a)** Define all the variables and their initial value needed in the component. Be sure to identify whethter each variable is a ref or an ordinary TypeScript type.

<!-- prettier-ignore -->
```ts
// Add your code implementation here





  

```

**(b)** Show a snippet of code demonstrating how these variables are used in the UI with Vuetify components. You don’t need to design the entire UI, just the relevant Vuetify components where the variables are used.

<!-- prettier-ignore -->
```ts
<template>
// Add your code implementation here






</template>

```

**(c)** Complete the implementation of the following functions using Vuetify components:

<!-- prettier-ignore -->
```ts

function goToNextQuestion() {
// Add your code implementation here

}

function checkAnswerAndGoNext() {
// Add your code implementation here

}

  

```

[**Answer**](https://play.vuetifyjs.com/#eNqNVWFv2zYQ/SsHYUCSJpLirtgAx/aWDujQbdm6pNswRAbKUmeLsESqJOXUNfzfdyQlW0ZkdPkQUuTd47vHx/PjNjKap7d1nawbjMbRxGJVl8ziLJMAk9oPNDE1k8BLZsw0iz41aKxQMhZyobKojQH4s10fw3YLvNEape3W3socP8MljGC3S2m7wzBJiXJpC1qGSeqOCWgzf+QMHrjS6AGNmx3CAsE0MJysY850HlthS5z14R+HeMyTbp/wJulRcgunWS5UvNSqqWEdVyrHkio3WCK3mN9K84R6X3oX3wmxjhdKU/i5qt0hVyDcqRc0fJVYyDBZ1GGNV7ghKI/QWy3ZR88oxPc21qxs8NnGzFXpOba6HVXYXfZ2+6kRX+7RNKV1wuzF/Wgl/MhLwVeEzAvkq6DArcx/Vr/jZ0tSuMHhUiylTdKek+jTcC1qCwYtCVoyuSQgS2X6E0RVK21hCxoXsIOFVhWckSHPXCoAJ0HsQTmYwmOoattV3e2NIYv+KZgFYcAWCJzVwrISuLAbUAt4o5nk+EMWXXWZrd5jgoxeoy4FSXZFKL8pmTv53Pwd04Kouukdy7XIs2i+B2BeCHdwFxZ2du14gqPgBZA8Ej3XlVRPElggfY85vPNbp4jeMd3y+aWhAp0T3ccDs41uOf+NsqGYIZ5t9v+myVUjrd5AoQxZ31N8eT36Dh6aqkINf5SbqhbcnCL7UyEkC6Rea/ZFlGH+lyTiOfwq5DJXVVi7b4wRFDvEep97zDt9AZXrCwd3FEifL1K3Pb852GewH02d486vL24gTeG9ZnwVrsC/NmcYb6KQuT/igHncDlq0LIpHWRQgHyxxG4DsEtv6biAewVOBEqRql5wruqjegb4HnmJNftqgPqNEF9Z/Od2j3lMkguFtLRrJfSNcqvf+JXcCnV90nhALOB9SL/GtBibPe3kMo302kTiZe3npL8j9HUvZQk/p3p2YvlCqgB4LNVaQRPPoNsgOgKXBvou7kvdQH/5VDSyEFKZoXeyCEnhD9iyDZGP4ZusnIWn3oaW3cwP9OxJsqA0eizZc03T6lR+BEDhPghF6QvaoweUURtdel7eSa6ycQYM7nEI00XR066VeETBwzx7lTq0RrHquLaXRD67v3tSr6dVFu6vo2+Rl8ur7yE1GyehVNP8PMxfBpg==)
