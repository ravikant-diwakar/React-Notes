# The-Ultimate-React-Course

## Review of Essential JavaScript for React

#### Destructuring
- Destructuring allows us to extract values from arrays or properties from objects and assign them to variables.
- Example:
  ```javascript
  const book = getBook(3);
  const { title, author, pages, publicationDate, genres, hasMovieAdaptation } = book;
  console.log(author, title, genres);
  ```

#### Array Destructuring
- Extract elements from an array.
- Example:
  ```javascript
  const [primaryGenre, secondaryGenre, ...otherGenres] = genres;
  console.log(primaryGenre, secondaryGenre, otherGenres);
  ```

#### Spread Operator
- The spread operator (`...`) allows us to spread elements of an array or object properties.
- Example:
  ```javascript
  const newGenres = ["epic fantasy", ...genres];
  const updatedBook = {
    ...book,
    moviePublicationDate: "2001-12-19",
    pages: 1210,
  };
  ```
  (Here, ...genres spreads out the genres array, and { ...book } spreads out the book object properties.)

#### Template Literals
- Template literals provide an easy way to create strings. They allow embedded expressions, which can be multi-line.
- Example:
  ```javascript
  const summary = `${title}, a ${pages}-page long book, was written by ${author} and published in ${getYear(publicationDate)}.`;
  console.log(summary);
  ```

#### Ternary Operator
- The ternary operator is a shorthand for an `if-else` statement.
- Example:
  ```javascript
  const pagesRange = pages > 1000 ? "over a thousand" : "less than 1000";
  console.log(`The book has ${pagesRange} pages`);
  ```
  (This checks if pages is greater than 1000, then assigns the appropriate string.)

#### Logical Operators
- Logical AND (`&&`) and OR (`||`) operators can be used for short-circuit evaluation.
- Example:
  ```javascript
  console.log(hasMovieAdaptation && "This book has a movie");
  const spanishTranslation = book.translations.spanish || "NOT TRANSLATED";
  ```

#### Nullish Coalescing Operator (`??`)
- Provides a default value when dealing with `null` or `undefined`.
- Example:
  ```javascript
  const count = book.reviews.librarything.reviewsCount ?? "no data";
  console.log(count);
  ```

#### Optional Chaining (`?.`)
- Allows us to safely access deeply nested properties.
- Example:
  ```javascript
  function getTotalReviewCount(book) {
    const goodreads = book.reviews?.goodreads?.reviewsCount;
    const librarything = book.reviews?.librarything?.reviewsCount ?? 0;
    return goodreads + librarything;
  }
  ```

#### Array Methods
- `map()`: Transforms elements of an array.
- Example:
  ```javascript
  const titles = books.map((book) => book.title);
  ```
  (Array ke har element pe operation perform karke naya array create karta hai)

- `filter()`: Filters elements of an array based on a condition.
- Example:
  ```javascript
  const longBooksWithMovie = books.filter((book) => book.pages > 500 && book.hasMovieAdaptation);
  ```
  (Array ke elements ko condition ke basis pe filter karta hai)

- `reduce()`: Reduces the array to a single value.
- Example:
  ```javascript
  const pagesAllBooks = books.reduce((sum, book) => sum + book.pages, 0);
  ```
  (Array ke elements ko ek single value mein reduce karta hai, jaise sum calculate karna.)

- `sort()`: Sorts elements of an array.
- Example:
  ```javascript
  const sortedByPages = books.slice().sort((a, b) => a.pages - b.pages);
  ```
  (Array ko sort karta hai, jaise yaha books ko pages ke basis pe ascending order me sort kiya)

#### Adding, Deleting, Updating Objects in an Array
- Adding:
  ```javascript
  const newBook = { id: 6, title: "Harry Potter and the Chamber of Secrets", author: "J. K. Rowling" };
  const booksAfterAdd = [...books, newBook];
  ```

- Deleting:
  ```javascript
  const booksAfterDelete = booksAfterAdd.filter((book) => book.id !== 3);
  ```

- Updating:
  ```javascript
  const booksAfterUpdate = booksAfterDelete.map((book) =>
    book.id === 1 ? { ...book, pages: 1210 } : book
  );
  ```

#### Promises
- A `Promise` is an object representing the eventual completion or failure of an asynchronous operation.
- Example:
  ```javascript
  fetch("https://jsonplaceholder.typicode.com/todos")
    .then((res) => res.json())
    .then((data) => console.log(data));
  ```

#### Async/Await
- `async` functions and `await` keywords are used to work with Promises more comfortably.
- Example:
  ```javascript
  async function getTodos() {
    const res = await fetch("https://jsonplaceholder.typicode.com/todos");
    const data = await res.json();
    console.log(data);
    return data;
  }
  const todos = getTodos();
  console.log(todos);
  ```
