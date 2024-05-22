# The-Ultimate-React-Course


## 📌Review of Essential JavaScript for React

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
- Promises are used for asynchronous operations.
- Example:
  ```javascript
  fetch("https://jsonplaceholder.typicode.com/todos")
    .then((res) => res.json())
    .then((data) => console.log(data));
  ```
  (`fetch` returns a promise, and `.then()` handles the resolved value.)

#### Async/Await
- `Async/Await` provides a way to work with asynchronous code in a synchronous manner.
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
  (`await` pauses the execution until the promise resolves.)

                                                                               | React Fundamentals |
                                                                               |---------------------|

## 📌 Working with Components, Props, and JSX


#### Rendering the Root Component and Strict Mode
- In React v18, we use `ReactDOM.createRoot` to render the root component:
  ```js
  const root = ReactDOM.createRoot(document.getElementById("root"));
  root.render(
    <React.StrictMode>
      <App />
    </React.StrictMode>
  );
  ```

#### Components as Building Blocks
- React applications are made of components.
- Components are the building blocks of user interfaces in React.
- Each component handles its own data, logic, and appearance.
- Components can be reused and nested within each other.

#### Creating and Reusing a Component
- Components are reusable pieces of UI.
- Example of a component:
  ```js
  function Header() {
    return <h1>Fast React Pizza Co.</h1>;
  }
  ```

#### What is JSX?
- JSX is a syntax extension of JavaScript that looks similar to HTML.
- It allows us to write HTML elements in JavaScript and place them in the DOM.
- Each JSX element is converted to a `React.createElement` function call.

#### Creating More Components
- Break down the UI into smaller components.
- Example of creating a `Menu` component:
  ```js
  function Menu() {
    return (
      <main>
        <h2>Our Menu</h2>
      </main>
    );
  }
  ```

#### JavaScript Logic in Component
- We can use JavaScript expressions inside JSX using `{}`.
- Example:
  ```js
  const isOpen = true;
  return <div>{isOpen ? "Open" : "Closed"}</div>;
  ```

#### Separation of Concerns
- React combines HTML, CSS, and JavaScript into components.
- Each component manages its own data, appearance, and logic.

#### Styling React Applications
- Inline styles are written as objects:
  ```js
  const style = { color: "red", fontSize: "48px" };
  ```

#### Passing and Receiving Props
- Props are used to pass data from parent components to child components.
- Example:
  ```js
  function Pizza({ pizzaObj }) {
    return <h3>{pizzaObj.name}</h3>;
  }
  ```

#### Props, Immutability, and One-Way Data
- Props are read-only and cannot be modified by the child component.
- This ensures one-way data flow, making the application predictable and easier to debug.

#### The Rule of JSX
- `className` instead of HTML’s `class`
- `htmlFor` instead of HTML’s `for`
- Every tag needs to be closed.
- Event handlers and properties need to be camelCased.

#### Rendering Lists
- Use the `.map()` method to render lists of components.
- Example:
  ```js
  const pizzas = pizzaData.map(pizza => <Pizza key={pizza.name} pizzaObj={pizza} />);
  ```

#### Conditional Rendering with &&
- Render components conditionally using `&&`.
- Example:
  ```js
  return <div>{isOpen && <p>We are open!</p>}</div>;
  ```

#### Conditional Rendering with Ternaries
- Use the ternary operator for conditional rendering.
- Example:
  ```js
  return <div>{isOpen ? <p>We are open!</p> : <p>We are closed.</p>}</div>;
  ```

#### Conditional Rendering with Multiple Returns
- Use multiple return statements to conditionally render components.
- Example:
  ```js
  if (!isOpen) return <p>We are closed.</p>;
  return <p>We are open!</p>;
  ```

#### Extracting JSX Into New Component
- Extract repeated JSX into a new component for reusability.
- Example:
  ```js
  function PizzaList({ pizzas }) {
    return (
      <ul>
        {pizzas.map(pizza => (
          <Pizza key={pizza.name} pizzaObj={pizza} />
        ))}
      </ul>
    );
  }
  ```

#### Destructuring Props
- Destructure props for cleaner code.
- (Props ko directly function parameter me destructure karte hai, taaki code clean rahe)
- Example:
  ```js
  function Pizza({ pizzaObj: { name, ingredients, price, photoName, soldOut } }) {
    return <h3>{name}</h3>;
  }
  ```

#### React Fragments
- Use `<React.Fragment>` or `<>` to group multiple elements without adding extra nodes to the DOM.
- Multiple elements ko group karne ka tareeka without extra nodes in DOM.
- Example:
```js
<React.Fragment>
  <Header />
  <Menu />
</React.Fragment>
```

#### Setting Classes and Text Conditionally
- Set classes conditionally using template literals.
- Example:
  ```js
  <li className={`pizza ${soldOut ? "sold-out" : ""}`}></li>
  ```
