# Quiz 4 High-order Functions

Given the following array,

```javascript
type Book = {
  title: string,
  author: string,
  year: number,
  genres: string[],
};
const books: Book[] = [
  {
    title: "1984",
    author: "George Orwell",
    year: 1949,
    genres: ["Fiction", "Dystopia"],
  },
  {
    title: "The Great Gatsby",
    author: "F. Scott Fitzgerald",
    year: 1925,
    genres: ["Fiction", "Tragedy"],
  },
  {
    title: "To Kill a Mockingbird",
    author: "Harper Lee",
    year: 1960,
    genres: ["Fiction", "Drama"],
  },
  {
    title: "Brave New World",
    author: "Aldous Huxley",
    year: 1932,
    genres: ["Fiction", "Dystopia"],
  },
  {
    title: "Moby Dick",
    author: "Herman Melville",
    year: 1851,
    genres: ["Fiction", "Adventure"],
  },
];
```

- Your task is to implement the following functions using only high-order functions such as `.sort()`, `.some()`, `.filter()`, `.flatMap()`, `.map()`, and `.reduce()`.
- Solutions utilizing traditional for-loops or `.forEach()` will not be accepted.

1. **Sort** the books based on their publication year in descending order (newest first).

   ```javacript
   const sortedBooks = books.sort((a, b) => b.year - a.year);
   ```

2. Use **Array.some()** to check if any book has been published after the year 1950.

   ```javacript
   const hasPost1950 = books.some(book => book.year > 1950);
   ```

3. Use **Array.filter()** and **string.includes()** to create a new array containing only the books that belong to the "Dystopia" genre.

   ```javacript
   const dystopiaBooks = books.filter(book => book.genres.includes("Dystopia"));
   ```

4. Use **Array.flatMap()** to create a flat list of all genres across all books.

   ```javacript
   const genres = books.flatMap((book) => book.genres);
   ```

5. **Create a new array of strings** for books that are of the genre "Dystopia" and were published after the year 1940. The strings should be in the format: "The book {title} by {author}, published in {year}, is a post-1940 work of Dystopia."

   ```javacript
   const post1940DystopiaDescriptions = books
     .filter((book) => book.genres.includes("Dystopia") && book.year > 1940)
     .map(
       (book) =>
         `The book ${book.title} by ${book.author}, published in ${book.year}, is a post-1940 work of Dystopia.`
     );
   ```

6. Use **Array.reduce()** to calculate the total number of books published before 1950.

   ```javacript
   const totalBooksBefore1950 = books.reduce((count, book) => book.year < 1950 ? count + 1 : count, 0);

   ```

Test your solutions on [typescriptlang.org](https://www.typescriptlang.org/play?#code/C4TwDgpgBAQg9nA1lAvFA3gWAFBSsAS2ABsIAuKAZ2ACcCA7AcwBoc8BDAV2AAs4aK1Ok1a4oICOwFR6nALYAjCDVF5GEejQiVBtBowDaAXVEBfANw4AxnHrUoChIh2wnx1FANsM3vIRLkUABEAIwAnAAcACxBqnhQXLz8FEEA4hD86lAA8jQA7hDExLG+4pLS4VFhcWoaWi4GQQBiBFaEtrHBACIg1HBgBOxBJt6mcVhifkSkKQAqPNCpWuzAUKkrlAogJZMJ3HzSzQB0UADKNsCrLcAAXuo07MQAJjvxZVIU4QBMAKw1UOpNNoKI0Wm0CB1mMFZg91E9tiMxGNvBM3v4ZtC4FAANIEIoJKAAWTgVkQ+gUBBoL3+iQOKQAElJIDQoAAZCAQV7xCQfKDhABsAAZ-oD6iDmq12vROkEug85ENEXhkWJUfF0YEgjAHgA3aAAOQgeSgAHV+M8uRx9slggBBZ5wTiUKD0zgAD1I23+PIqYQAzF8RXVgZ4JeDId1esB+oNhnEVXg1VMAiliVsoF1WohLXskod6coFfQiYUdXjSDmfZ8Ij8QkGgQ0w1KZbannr6MBOFo46NREZzEA):
