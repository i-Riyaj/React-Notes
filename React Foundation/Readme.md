# JSX 

JSX stands for **JavaScript XML**. It's a syntax extension for JavaScript, often used with React, a popular JavaScript library for building user interfaces.

Imagine you're building a web page using HTML and JavaScript. **JSX is like a mix of JavaScript and HTML**. It allows you to write HTML-like code directly within your JavaScript code.

### Here's a simple example:
` const element = <h1>Hello, world!</h1>; `

In the example above, **Hello, world!** looks like HTML, but it's actually JSX. **Under the hood, JSX gets transformed into regular JavaScript code** that React can understand and work with.

JSX makes it easier to write and understand code, especially when you're building user interfaces with React. It lets you write HTML-like code directly in your JavaScript files, which helps keep your code organized and makes it more readable.

# Component
In React, a component is a reusable and independent piece of code that encapsulates a part of a user interface. Components are the building blocks of React applications, and they allow you to split the UI into small, reusable pieces, making your code more modular and easier to manage.

### There are two main types of components in React:

- Functional Components: These are simple JavaScript functions that accept props (short for properties) as arguments and return React elements (usually JSX) to describe what should be rendered on the screen. Functional components are primarily used for simpler UI elements.

***Example of a functional component:***
`
function Welcome(props) {
  return <h1>Hello, {props.name}!</h1>;
}
`
- Class Components: These are JavaScript ES6 classes that extend the React.Component class. They have a render() method that returns a React element, and they can maintain their own private data, called state.

***Example of a class component:***
`
class Welcome extends React.Component {
  render() {
    return <h1>Hello, {this.props.name}!</h1>;
  }
}
`
Components can be composed together to build complex UIs. They can also accept inputs called props, which allow the parent component to pass data down to its children.

In summary, components in React are reusable, modular pieces of code that represent parts of a user interface, and they play a central role in building React applications.

# Reconciliation

In easy terms, **reconciliation** in React is like a smart system that figures out what parts of a webpage need to change and updates only those parts. Imagine you have a puzzle on your table, and someone gives you a new piece. Instead of rearranging the whole puzzle, you just find where the new piece fits and put it there.

### Here's how reconciliation works in React:

- Virtual Representation: React keeps a virtual representation of your webpage's structure in memory. It's like a blueprint of how your webpage should look.

- Changes Detection: When something changes in your webpage, like user input or new data coming in, React checks the virtual representation against the actual webpage to see what's different.

- Smart Updates: React is smart about figuring out what parts of the webpage need to change. It doesn't repaint the whole webpage every time. Instead, it identifies the specific parts that need updating and only changes those parts.

- Efficient Rendering: By updating only the necessary parts, React makes rendering your webpage faster and more efficient. It saves resources and makes your webpage feel responsive to users.

In essence, reconciliation is like having a handy assistant who quickly scans your webpage for changes and efficiently updates only what's needed, without wasting time or effort. It's one of the reasons why React is so popular for building dynamic and fast web applications.

# React Fibre

React Fiber is an **internal reimplementation of the React core algorithm**, introduced in React version 16. It's not something developers directly interact with, but it significantly impacts how **React manages updates**, **handles asynchronous rendering**, and **maintains performance**.

### Here are key points about React Fiber:

- Reconciliation Algorithm: Fiber is primarily focused on the **reconciliation algorithm**, which is the process of determining what parts of the user interface need to be updated based on changes in state or props. **Fiber introduces a new, more efficient reconciliation algorithm that can be paused, aborted, or resumed**. This enables React to prioritize and manage updates more effectively, especially in complex user interfaces.

- Asynchronous Rendering: Fiber allows React to perform work **asynchronously**, meaning it can break down rendering work into smaller chunks and **prioritize high-priority updates while deferring lower-priority tasks**. As a result, React can maintain a smooth and responsive user interface, even when dealing with heavy computation or rendering tasks.

- Incremental Rendering: Fiber enables incremental rendering, which means React can update the UI gradually as it completes work on each chunk of the render tree. This incremental approach helps to improve perceived performance and responsiveness, especially in applications with large component trees or complex rendering logic.

- Better User Experience: By leveraging Fiber's capabilities, React can handle interactions, animations, and updates more efficiently, resulting in a smoother and more responsive user experience. Fiber's ability to pause and resume work also helps to prevent UI jank or stuttering, even under heavy load.

- Under the Hood Optimization: While Fiber doesn't change the public API of React, it represents a significant improvement in how React manages rendering and updates internally. It allows React to be more adaptable to different environments, prioritize rendering work more effectively, and handle complex component trees with greater efficiency.

In summary, React Fiber is an internal reimplementation of React's core algorithm that introduces features like asynchronous rendering, incremental updates, and improved performance optimizations. While developers may not interact directly with Fiber, it plays a crucial role in making React more efficient, responsive, and capable of handling modern web application requirements.

# Memoization

Memoization is an optimization technique used in programming to speed up certain functions. It works by storing the results of function calls along with the inputs used, and then retrieving those stored results instead of recomputing the function if the same inputs are encountered again.

### Here's a breakdown of how memoization works:

- **Cache**: A cache is created to store the previously computed results. This cache can be a simple object or a more sophisticated data structure depending on the implementation.

- **Function Call**: When a memoized function is called with a specific set of inputs, the function first checks the cache.

- **Cache Lookup**: If the cache contains an entry for the exact combination of inputs used in the current function call, the function retrieves the pre-computed result from the cache and returns it immediately.

- **Computation**: If the cache doesn't have a result for the specific inputs, the function performs its usual computation and stores the result in the cache along with the corresponding inputs. The computed result is then returned.

## Benefits of Memoization:

- **Improved Performance**: By avoiding redundant computations, memoization can significantly improve the performance of functions, especially those that involve complex calculations or repetitive tasks.

- **Reduced Redundancy**: Memoization eliminates the need to recalculate the same results for the same inputs, making your code more efficient.

### Trade-offs of Memoization:

- **Memory Usage**: Since memoization involves storing computed results, it can increase memory usage. This might be a concern for applications with limited memory resources.

- **Invalidation**: If the function's output depends on external factors that can change, the cached results may become invalid.  You'll need a mechanism to invalidate the cache when necessary.

Overall, memoization is a valuable technique for optimizing functions that perform expensive computations or have repetitive calculations. It's important to consider the trade-offs between performance gains and memory usage when deciding whether to use memoization in your code.




