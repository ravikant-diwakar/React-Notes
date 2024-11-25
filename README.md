![180px-React_Logo_SVG svg](https://github.com/ravikant-diwakar/React-Notes/assets/110620635/00634298-b1a0-45e4-9228-15f8fa03d4f8)


# 📖 REACT NOTES


**Creating and Running React App**
```bash
npx create-react-app@5 my-app
```
```bash
dir my-app
```
```bash
npm start
```

## 📌 Review of Essential JavaScript for React

#### Destructuring
- Destructuring allows us to extract values from arrays or properties from objects and assign them to variables.
- Example :
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

# 📌React Fundamentals


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


#### What is JSX?
- JSX (JavaScript XML) is a syntax extension of JavaScript that looks similar to HTML.
- It allows us to write HTML elements in JavaScript and place them in the DOM.
- Each JSX element is converted to a `React.createElement` function call.

Syntax:

```js
const element = <h1>JavaScript XML</h1>;
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
  console.log(pizzaObj);

  // if (pizzaObj.soldOut) return null;

  return (
    <li className={`pizza ${pizzaObj.soldOut ? "sold-out" : ""}`}>
      <img src={pizzaObj.photoName} alt={pizzaObj.name} />
      <div>
        <h3>{pizzaObj.name}</h3>
        <p>{pizzaObj.ingredients}</p>

        {/* {pizzaObj.soldOut ? (
          <span>SOLD OUT</span>
        ) : (
          <span>{pizzaObj.price}</span>
        )} */}
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
  <ul className="pizzas">
            {pizzas.map((pizza) => (
              <Pizza pizzaObj={pizza} key={pizza.name} />
            ))}
          </ul>
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

## 📌 State, Events, and Forms in React

#### Building a Steps Component
- Steps component manage karte hai navigation through different steps using state variables.

  - `step`: Tracks the current step
  - (track karta hai ki user kaun se step pe hai, starting from 1)
  - `isOpen`: Tracks if the steps section is open or closed
  - (control karta hai ki steps UI mein dikh rahe hain ya nahi, basically open ya close state ko handle karta hai)

  ```javascript
  function Steps() {
  const [step, setStep] = useState(1);
  const [isOpen, setIsOpen] = useState(true);
  ```
 
- **Event Handlers :**
  - `handlePrevious`: Decreases step by 1 if not already at the first step
  - ( user "Previous" button press karta hai to call hota hai, aur ye check karta hai ki agar current step 1 se zyada hai to ek step kam kar do)
  - `handleNext`: Increases step by 1 if not already at the last step
  - (user "Next" button press karta hai to call hota hai, aur ye check karta hai ki agar current step 3 se kam hai to ek step badha do.)
  ```javascript
  function handlePrevious() {
    if (step > 1) setStep((s) => s - 1);
  }

  function handleNext() {
    if (step < 3) setStep((s) => s + 1);
  }
  ```
  | Current Step: 1                | Current Step: 2                | Current Step: 3                |
  |--------------------------------|--------------------------------|--------------------------------|
  | User presses "Next"            | User presses "Next"            | User presses "Next"            |
  | `handleNext` check: `if (step < 3)` (1 < 3, true) | `handleNext` check: `if (step < 3)` (2 < 3, true) | `handleNext` check: `if (step < 3)` (3 < 3, false) |
  | Step becomes 2                 | Step becomes 3                 | Step remains 3                 |

  | Current Step: 3                | Current Step: 2                | Current Step: 1                |
  |--------------------------------|--------------------------------|--------------------------------|
  | User presses "Previous"        | User presses "Previous"        | User presses "Previous"        |
  | `handlePrevious` check: `if (step > 1)` (3 > 1, true) | `handlePrevious` check: `if (step > 1)` (2 > 1, true) | `handlePrevious` check: `if (step > 1)` (1 > 1, false) |
  | Step becomes 2                 | Step becomes 1                 | Step remains 1                 |

#### Handling Events the React Way
- Events are bound using JSX syntax.
- **Example:** Handling a button click to toggle `isOpen` state.
  ```javascript
  <button className="close" onClick={() => setIsOpen((is) => !is)}>
    &times;
  </button>
  ```

#### What is State in React?
- Data that a component holds over time, necessary for information it needs to remember throughout the app’s lifecycle. Updating state triggers a re-render of the component.
- **Example Usage:**
  ```javascript
  const [step, setStep] = useState(1);
  ```

#### Creating a State Variable with useState
- `useState` hook se functional components me state add kar sakte hai
- **Syntax:** `const [stateVariable, setStateFunction] = useState(initialValue);`
- **Example:**
  ```javascript
  const [step, setStep] = useState(1);
  ```

#### Don't Set State Manually
- Directly modifying state variables.
  ```javascript
  // Incorrect
  test.name = "Fred";
  setTest({ name: "Fred" });
  ```
- Using state functions.
  ```javascript
  // Correct
  setStep((s) => s + 1);
  ```
  State ko hamesha state function (like `setStep`) se update kare

#### Adding Another Piece of State
- Use multiple `useState` hooks for managing different pieces of state.
- **Example:**
  ```javascript
  const [isOpen, setIsOpen] = useState(true);
  ```

```javascript
return (
  <div>
    <button className="close" onClick={() => setIsOpen((is) => !is)}>
      &times;
    </button>
```

- **Close Button:**
  - Yeh button steps section ko toggle karta hai (open/close). 
  - `onClick` event handler use karke `setIsOpen` function call kiya gaya hai jo `isOpen` state ko true/false karta hai.

```javascript
    {isOpen && (
      <div className="steps">
```

- **Conditional Rendering :**
  - Agar `isOpen` true hai toh steps section render hoga, warna nahi.

```javascript
        <div className="numbers">
          <div className={step >= 1 ? "active" : ""}>1</div>
          <div className={step >= 2 ? "active" : ""}>2</div>
          <div className={step >= 3 ? "active" : ""}>3</div>
        </div>
```
  - `step` value ke hisaab se "active" class conditionally apply hoti hai, jo current step ko highlight karti hai.

```javascript
        <StepMessage step={step}>
          {messages[step - 1]}
          <div className="buttons">
            <Button
              bgColor="#e7e7e7"
              textColor="#333"
              onClick={() => alert(`Learn how to ${messages[step - 1]}`)}
            >
              Learn how
            </Button>
          </div>
        </StepMessage>
```

  - `StepMessage` component current step ka message aur ek button display karta hai.
  - `messages` array mein step-wise messages hain. `messages[step - 1]` se current step ka message milta hai.
  - "Learn how" button click karne se ek alert trigger hota hai jo current step ka message show karta hai.

## 📌 New Project: The "Far Away" Travel List

   | Project |
   |---------|
   | https://github.com/ravikant-diwakar/The-Far-Away-Travel-List |

#### State vs. Props
- State (`useState`) is used within components to manage local data.
- Props are used to pass data and functions between components.







## 📌 Components, Composition, and More

### Component Categories

**Stateless/Presentational Components:**
- No state management, only present data.
- Examples: Logo, NumResults.

**Stateful Components:**
- Manage their own state.
- Examples: Search, MovieDetails.

**Structural Components:**
- Provide the structure or layout of the app.
- Examples: App, NavBar.

### Fixing Prop Drilling with Composition

**Technique :**
- Use children to directly pass components where needed.

**Example:**
```jsx
function NavBar({ children }) {
  return <nav className="nav-bar">{children}</nav>;
}
```

### Props as a Component API

**Define Props :**
- `maxRating`, `color`, `size`, `onSetRating`

**Example :**
```jsx
function StarRating({ maxRating = 5, color = "#fcc419", size = 48, onSetRating }) {
  // Component logic
}
```

### Library vs. Framework

|    Framework    |        Library         |
|-----------------|------------------------|
| - All-in-one solution with pre-included tools. | - Freedom to choose the best tools. |
| - Complete structure for large-scale applications. | - Pieces of code shared for specific tasks. |
| - Includes routing, styling, HTTP management, etc. | - React is a view library, focuses on UI rendering. |
| - Batteries included, but less flexible. | - Needs external libraries for routing, styling, etc. |
| - Example: Angular, Vue, Svelte. | - More flexibility, tailor-made solutions. |
|   |   - Example: React. |

#### React's Ecosystem
- Large third-party library ecosystem.
- Popular libraries: React Router, React Query, Redux, Styled Components, Tailwind.


## 📌 7 React Hooks

#### 1. **useState**

`useState` adds state to functional components.

It returns the current state and a function to update it.

```javascript
import React, { useState } from 'react';

function Counter() {

  const [count, setCount] = useState(0);

  // more code
}
```

Here, `count` starts at `0`, and `setCount` updates it.


#### 2. **useEffect**

`useEffect` handles side effects like data fetching or updating the DOM.

It runs after every render, but you can control when it runs by passing dependencies.

```javascript
import React, { useState, useEffect } from 'react';

function TitleUpdater() {

  const [count, setCount] = useState(0);

  useEffect(() => {
    document.title = `You clicked ${count} times`;
  }, [count]);

  // more code
}
```

This updates the document title whenever `count` changes.

#### 3. **useContext**

`useContext` accesses global data or shared state directly, without the need for prop drilling.

```javascript
import React, { useContext } from 'react';

const MyContext = React.createContext();

function DisplayValue() {

  const value = useContext(MyContext);

  // more code
}
```

`useContext` retrieves the value provided by `MyContext` and displays it.

#### 4. **useReducer**

`useReducer` is used for managing complex state logic. It returns the current state and a dispatch function.

```javascript
import React, { useReducer } from 'react';

const initialState = { count: 0 };

function reducer(state, action) {
  switch (action.type) {
    case 'increment':
      return { count: state.count + 1 };
    default:
      return state;
  }
}

function Counter() {

  const [state, dispatch] = useReducer(reducer, initialState);

  // more code
}
```

This setup helps handle state transitions in a structured way.

