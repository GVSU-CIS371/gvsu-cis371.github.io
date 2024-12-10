# Final Exam Review and Practice

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

**Your Answer**: [Online Playground](https://play.vuejs.org/#eNp9UctOwzAQ/JWVT0WCcoBTEAeoQAKJh3jccnGTbWpwbMu7LoUq/8466YNKqMolOzO7np1dqasQxouEqlDqWDFV3s1MM/4g7wRalQ6gVJVvg7EYnwIb76hUBfRM5rS1/uu+xzgmPN7g1Ryrz3/wD1pmrFTPEQnjAku15VjHBnmgb14fcSn/W7L1dbKiPkC+IHmbssdBdp1cLbb/6Hq3d23wkY1r3uhmyehos1Q2mpVdry+V5DI5sPrO7tn4vO8rXScp1pr1CX8HpDGTpIjL/B5kBB78wiBcDkNMXQBxFCcXuWTDFvcQ+nY+kKF92Ty1U3oPE58cF+CkwihMd5Hf9tVJCuIAh7flnsSgQyjg1kScakK5uBgwzrDR1vzkejRbc5P+/EcybWisp0MfsY/Ztuy7LUcyNStnyVU5HNB1/bb2Nmrznnfb/Y6GhU9PQcK32KKTPOYI1jemAvZip4o7eG9FWHfOfAQN/WD4MjzvlY1ZoJMgS7f5OtX9Ajn09qI=)

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

**Your Answer**: [Online Playground](https://play.vuejs.org/#eNqFU11r2zAU/SsXP6WQJg/bk5sEutBBB91K174ZiiNfx2plSegjTZb5v+9KcpxklBaB0f2QdM65x/vsWuvJxmOWZ9k4c5YpWfP15MUqSal9IQGKjKlWc4Hml3ZcSVtkOcRKqJVCqLcfMeeMx/Ehzxpkr+/kX+w25Irs3qBFs8EiG2quNGt0qXzz+yduaT8UW1V5Qd0fFB/QKuEDxtT2zcuKYJ/0RbS3rVbGcbl+tDdbh9IeSAWgobOL/UVGuiw/oH6E+2XyNZ4rZEcqVqUrL91Oo504SyriNrwHIQN3asMR5ukSXuVgnSEkVyF03Ak8y9idVNpye97W+HZln/RSeelykBShoUp3Fd5W7NJrQoDpbZqndVBqncN3bnBVWqSJEwAuueOl4H9CPKr72jKO/4JuSwerVTpnnTIBNvEdwhHdGjprL1kQB8qqeuyxjdrA83bgd5EIT6dA4gtsUZIeDYJQa87AKYLDzDF9RhH6k7UyUEK8GN64a2Lnmm9QkpCFPCwaQloDLsEtTfmZO2z/x0WDZuSJVclecxi1eT+fv6SqEBcwX8BGhcs/xZ/eCDvWlHKNFoIgn6NNi9wUnRNf73/HmWWGaweCrpuT2ch7YNF5vSgkjw6GPRisx/AQPkreBbGwCtsn2aYAOqiNapOXi4ymNRxNTIf6ZDI9+va880S/8/7Ba7H/4Jl9z7ojv1RYc4n3hlw86/MHjbvF6Oiz9rmvEZdZrC/oNLFLAwuNhRTowEvrV0GZFTWPhgnFOk3nuqpgp7wBpioEYpBmVUYfNGjo9z5ds2kSmSSlgPhpQWwomk1Pgqz7B8bGyLE=)

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

**Your Answer**: [Online Playground](https://www.typescriptlang.org/play/?#code/PTAEEkFsAcBsFNLwHYBdSoBb1ARQK7wDOAlgPbKgBMoAhgLABQTLzbrH7jIEMCSaDNjyFSFaqABGnGV1k8ocRCnRYcBYuUo0AxrP2MgA)

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


function checkAnswerAndGoNext() {
// Add your code implementation here

}


```

**Your Answer**: [Online Playground](https://play.vuetifyjs.com/#eNqNkk9PGzEQxb/KyBdahLptDz2koVWo1Ept+SMQcGBzsLwT1mJ3bMY2EKJ8d8brJQKJSFzWY7+Z559X72qlAptq5v2nu4RqoqYRe9/piD9gWm3qmmqaBsPWRwgYk4dO0/V+rWKolagAtveOI6yAcQFrWLDrYUcsd/IogHEUItwmDNFKCftwlY8BVmWBjTaBWl22OoINEFsEo72NugNj4xLcAn6zJoM/a7X3POn84DkRS3WA3FkSUVz+O2rcWJ9otoKay0PdsG1qNd8YaAr3yPni57airMd1C6M1LcjvIRxYb8jdE+gCfYoNnAzSNtBDzSPP3yQPRC6bMx0Tj8wXSEl63uIcp9+NaVyiyEtoXYiClhG/fv7yDc5S3yPDcbfsvTVhG+yv1pIuUAesH21X6nMS8Ab+WbpuXF/OTlMIVnrfot7MvuaudqF3jC/S0aJsd6ssz7+XAC0SmSyCadHczAbPGTV/3BE+xA8f8+Nz21pyWpWgSizlArXeo9R1w2f+BGBY8AU=)

[**Answer**](https://play.vuetifyjs.com/#eNqNVmtv2zYU/SsXwoAkTWTZ+7ABjp0tHdCh27J1SR8oIgNlKNoiTJEqSTlxDf/3XpJ6OZXR5oNF3cfhuYeXV7nfRUbT5LosR5uKRdNoZllRCmLZVSoBZpuYEp0BFcSYeRoVTzGprEojKMhT/Mgzm6P11/E4jXx8mxGb6sFyKwKMd5iSyOYF4Or/ihnLlZzCbge00ppJ29hey4w9wTlMYL9P0P25tpuRYHJlczS3sInDPdzlCu6o0swjG7fC+MPAWTJMs2EfbP2d74coLkaNH3doMQcB2ZPtSG5iTTKu4pVWVQmbuFAZEyikYYJRy7JraR6ZbjXt53QWwMSl0ph2qkrH4QK4I3WGj+/yDhkmjfp40zXbIpxHeeYR5MEzDHnPnBsiKjbovHKieN5d8Y0lVN/ZS9T7c8W/3DJTCev0bJydsp2KjbCE+kL62j5YCb9TwekaOdGc0XXQ81pmf6p/EQKFdQ8Hi7HPN+kjNkZ8mSW9m4GvhmpeWjDM4hEKIle4mUVBfR4vSqUt7ECzJexhqVUBJ3jBTlwqAEV8250RzOE+kNg1ZTS+KaTRh5xY4AZszoCSklsigHK7BbWEV5pIyn5Lo4smsz7ZKUJGL5kWHA/kAlH+UTJzh+PWb4jmSNUtb0imeZZGixaAeLHcxk1Y8Ozr5xGOnOaA8kjmua6lepRAAulblsEb7zpG9Iboms9fFRboet+93BFb6ZrzeyYrjBniWWf/ME2qKmn1FnJl8LJ5ij+PJ7/AXVUUTMN/YluUnJpjZP/IuSSB1EtNvnAR1u8kEs/gby5XmSqC7bYyhmPsEOs295B38gIKN7K67sgZvr5InHtx2bXP4Mycu447HZ9dQpLAW03oOhyBv9OuYXwThcx2iw7zcADVaGkUT9IoQN5Z5DYA2STW9V1CPIHHnEmQqja5rmiiehv68XyMNfbTlukTTHRh/ZvTjImWIhIMd2tZSX+BYaXe+tveCHR61vQEX8LpkHojP8hg9u33JoZJm40kjuaen/sDcn+HUtbQczx3J6YvFCvAy4IjHCTSPDgNbAdgwrB+Fzclt1CfPqoKllxyk9dd7IJG8ArbUwTJpvDTzi9C0v5TTc9/PvHnQLChUXko2nBN8/l3PjchcDEKjdATskcNzucwGXtdXkuqWeEaNHSHUwgXGreue6lXBAycs0e5URsGVn2rLabh/wJ+euOsxlsX7S9kJYT/WXwFWSn6KQ==)
