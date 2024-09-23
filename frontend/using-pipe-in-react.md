# Using pipe in FP with HOCs and context provider

Pipes are a powerful concept in functional programming. They allow you to compose functions in a way that is easy to read and understand. In this article, we will explore how to use pipes with higher-order components (HOCs) and context providers in React.

## What is a pipe?

A pipe is a function that takes a list of functions as arguments and returns a new function that applies each function in the list to the input in sequence. For example, given the following functions:

```ts
const removeUnderscores = (str: string) => str.replace(/_/g, ' ');
const removeDash = (str: string) => str.replace(/-/g, ' ');
const removeNumbers = (str: string) => str.replace(/[0-9]/g, '');
const capitalize = (str: string) => str.charAt(0).toUpperCase() + str.slice(1);
const capitalizeAll = (str: string) => str.split(' ').map(capitalize).join(' ');
```

We can create a pipe that applies these functions in sequence like this:

```ts
const pipe =
  (...fns: Function[]) =>
  (x: any) =>
    fns.reduce((v, f) => f(v), x);
```

Now we can create a new function that applies these functions in sequence:

```ts
const transform = pipe(
  removeUnderscores,
  removeDash,
  removeNumbers,
  capitalizeAll
);
console.log(transform('hello_world-123')); // Hello World
```

## Using pipes with HOCs

Higher-order components (HOCs) are functions that take a component and return a new component with additional functionality. We can use pipes to compose HOCs in a way that is easy to read and understand. For example, given the following HOCs:

```ts
const withAuth = (Component: React.ComponentType) => (props: any) => {
  // Add authentication logic here
  return <Component {...props} />;
};

const withPermissions =
  (permissions: 'edit' | 'view') =>
  (Component: React.ComponentType) =>
  (props: any) => {
    if (permissions === 'edit') {
      // Add edit permissions logic here
    } else {
      // Add view permissions logic here
    }
    return <Component {...props} />;
  };
```

We can create a pipe that composes these HOCs like this:

```ts
const withProtection = pipe(withAuth, withPermissions('edit'));
```

Now we can use this pipe to enhance a component with logging and error handling:

```ts
const ProtectedComponent = withProtection(Component);
```

## Conclusion

In this article, we explored how to use the pipe function to compose higher-order components (HOCs) in React. By leveraging the power of function composition, we can create reusable and modular HOCs that enhance our components with additional functionality such as authentication, permissions. This approach not only makes our code more readable and maintainable but also promotes the separation of concerns, making it easier to manage and scale our React applications.

Happy coding!
