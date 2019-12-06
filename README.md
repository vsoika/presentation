# presentation

## ASYNC JAVASCRIPT

### Sync vs Async

When you execute something synchronously, you wait for it to finish before moving on to another task. When you execute something asynchronously, you can move on to another task before it finishes. Synchronous code is also called “blocking” because it halts the program until all the resources are available. However, asynchronous code is also known as “non-blocking” because the program continues 
executing and doesn’t wait for external resources (I/O) to be available. Asynchronous interaction with the database means that a single parallel function instance can handle many requests concurrently and receive the responses concurrently. That way, the waiting time can be overlayed with sending other requests and receiving responses. At the very least, the waiting time is amortized over multiple requests. This leads in most cased to much higher streaming throughput. 

Asynchronous programming successfully solves many problems. One of the most important is the availability of the user interface.
If the application works synchronously, then the user will not be able to interact with the pages until the result is received.
In a world where no one likes to wait, you just can't write code synchronously!

### ASYNC EXAMPLES

DOM Event
API Query
setTimeout/setInterval

### Callbacks

Callbacks are simple functions which are used to notify the calling instance when an asynchronous code block has been executed and the result is available. Using callbacks is simple as we only need to deal with functions.

The getData function is defined, so that it takes the callback function as a parameter. Inside getData we’re using two setTimeout functions to delay the execution of code for 1 and 2 seconds respectively. Then we’re again calling the callback function. As an argument we’re passing in the object which should be returned.
When calling getData we now need to make sure to pass in a callback function as a parameter.In this example the callback function is passed with two parameters (error, data). After first setTimeout the result of the function execution will be data, and after second setTimeout the result of the callback function execution will be error, because an error was passed as the first parameter.

Callback functions are useful for short asynchronous operations. 

Common Problem: Callback Hell
Sometimes you have a series of tasks where each step depends on the results of the previous step. A common problem where you have callback functions deeply nested inside of each other. It's easy to run into callback hell, the code is difficult to read, and will become worse when error-handling logic is added.

### Promises

The alternative to callbacks is a promises.
We can convert callbacks into promises using the Promise constructor. The Promise constructor takes a callback with two arguments resolve and reject. Resolve: is a callback that should be invoked when the async operation is completed. Reject: is a callback function to be invoked when an error occurs. The constructor returns an object immediately, the promise instance. You can get notified when the promise is “done” using the method .then in the promise instance. 

When calling the getTodo function we’re now able to chain a call of then. Then is expecting to get handed over a function which is executed once the Promise is being resolved. As a parameter this function gets what is passed into the call of resolve. In the example from above we’re using the function body to print the content of text property to the console once again.
To simulate the occurrence of an error lets set the error variable to true. By making this change we’re now making sure that instead of the resolve function the reject function is called. 

Chaining

A common need is to perform two or more asynchronous operations one after another, and each next one starts when the previous one is successfully completed and uses the result of its execution. We do this by creating a promise chain. The function  'then' returns a new promise different from the original. Every promise you invoke means you have successfully completed the previous steps in the chain.

Promises can improve code order and give us flexibility. Promise solve the main problem of the callback hell, handling all errors.
We can call 'then' as many times as we want. This is the basis for the functional construction of asynchronous operations.

### Async/await

Async/Await introduces in ES7  language specification. Async/Await is the next version of Promise. The new async/await syntax allows you to still use Promises. Async keyword defines an asynchronous function. Await indicates that you want to resolve the Promise.

Inside of fetchTodo we’re calling the getTodo method by using the keyword await. This indicates that getTodo is returning a Promise and we have to wait for the Promise to be resolved (or rejected). The result of what is being returned from the promise is stored in todo.
We can to handle erros by using try/catch block. In case of an error, the control jumps from try block to the catch block. 

When we’re outside of any async function, we can not use "await".
In this case, we can use .then/catch to handle the final result or errors.

### WHY ASYNC/AWAIT IS BETTER?
Concise and clean code
Errors handling
Debugging
Error stacks



