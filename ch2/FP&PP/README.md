
<p align = "center"><img src="https://cloud.netlifyusercontent.com/assets/344dbf88-fdf9-42bb-adb4-46f01eedd629/004935cd-848e-4eb4-aefe-252ce0cfc041/fp-preview.png"></p>

# Functional Programming and Functional Paradigms

## Intro

Here, I will introduce you to functional programming and some of its paradigms. A new and learning programmer may be relucant to learn a different method to achieve the same result, especially when the functional approach can be a difficult approach to understand. However, Functional Programming and its paradigms are best served when software **evolves** over its lifetime, as it was so eloquently put here on [StackOverflow](https://stackoverflow.com/questions/2078978/functional-programming-vs-object-oriented-programming):

> Object-oriented languages are good when you have a fixed set of operations on things, and as your code evolves, you primarily add new things. This can be accomplished by adding new classes which implement existing methods, and the existing classes are left alone. 
> 
> Functional languages are good when you have a fixed set of things, and as your code evolves, you primarily add new operations on existing things. This can be accomplished by adding new functions which compute with existing data types, and the existing functions are left alone.
> 
> Norman Ramsey

As noted here, object oriented programming addresses software evolution by creating more content to accomplish the task at hand, often by creating new classes which can bloat the software and scales poorly. Functional programming on the other hand would minimize the amount of new code added, solving complex problems in a simpler way with the use of lambda operators, improving modularity, and code maintainabilty by use of nested functions. This isn't to say that OOP and Functional Programming are mutually exclusive; though being able to recognize where a developer is able to use functional programming is beneficial to development as a whole.

**_What is Functional Programming?_**
 
 Functional programming is best understood as an approach towards coding-- using functions most effectively to create concise and rectifiable code. This is what is meant to be a paradigm, a pattern, model, or methodology for how something is done or accomplished.
 
 ## Functional Tools
 
  Here, I will cover some methods that are used in functional programming, particularily the most common ones such as **map**, **reduce**, **flatmap**, and **sort**. JavaScript will be the language used in the following examples.
 
 ### map()
 
 The functional map() method **takes a given array** and modifies the elements within its indexes to **output a new array**. Below are a few examples on applications of the method, albeit rather simple.
 
 A use of .map() that takes the numberArray and creates a new array of the modified numbers.
 ```javascript
const numberArray = [9, 16, 81];
const numberRoots = numbers.map((num) => Math.sqrt(num));
// A new array numberRoots with the content of [3, 4, 9] is created.
 ```
  This use of .map() takes an array of objects and modifies them to a new array of objects.
 ```javascript
 const kvArray = [{ key: 1, value: 10 },
                 { key: 2, value: 20 },
                 { key: 3, value: 30 }];

const reformattedArray = kvArray.map(({ key, value}) => ({ [key]: value }));

// A new array reformattedArray with the content of [{1: 10}, {2: 20}, {3: 30}]
 ```
  This code snippet uses map() on a String to create an array representing the character values ASCII bytes.
 ```javascript
const map = Array.prototype.map;
const charCodes = map.call('Hello World', (x) => x.charCodeAt(0));

// charCodes now equals [72, 101, 108, 108, 111, 32, 87, 111, 114, 108, 100]
 ```
 
 ### reduce()
 
  The simplist way of thinking of functional method reduce(), adds the sum of all values in an array, but that isn't quite right. What the reducer does is takes two arguements, which can be an object, array, or function, and returns only a single value. The termninology of these arguments are known as the reducer and accumulator; the latter of which is thhe value we end with, and the reducer the action we will perform on the two arguments. Let's take a look at what some reducer examples can perform:
  
  This use of reduce() simply adds and then returns the sum of all the values in the array.
  ```javascript
  //this is our initial value i.e. the starting point
  const initialValue = 0;
  
  //numbers array
  const numbers = [5, 10, 15];
  
  //reducer method that takes in the accumulator and next item
  const reducer = (accumulator, item) => {
  return accumulator + item;
  };
  
  //we give the reduce method our reducer function and our initial value
  const total = numbers.reduce(reducer, initialValue)
  ```
  This use of reduce() takes an array of arrays, and concatinates all of the indexes of the sub-arrays into a new single array. 
  ```javascript
  function flattenArray(data) {
    // our initial value this time is a blank array
    const initialValue = [];

    // call reduce on our data
    return data.reduce((total, value) => {
        // if the value is an array then recursively call reduce
        // if the value is not an array then just concat our value
        return total.concat(Array.isArray(value) ? flattenArray(value) : value);
      }, initialValue);
    }
  )
  // flattened is [2, 4, 6, 8, 10, 12]
  ```
  Finally, let's do an example where we have some objects with a pair of defined variables, and we want to display the information in a particular way, as shown in the code below:
  ```javascript
  //We have an array of objects that looks like this:
  const person = [
  { name: "Alice", Age: "8" },
  { name: "Steve", Age: "21" },
  { name: "Belmont", Age: "32" }
  ]
  
  //And we want it to look like this:
  const pokemonModified = {
  Alice: { Age: "8" },
  Steve: { Age: "21" },
  Belmont: { Age: "32" }
  };
  
  //To do so, we make use of reduce():
  const simpleObjects = info =>
  info.reduce((acc, item) => {
    // add object key to our object i.e. Alice: { Age: '8' }
    acc[item.name] = { type: item.type };
    return acc;
  }, {});
  ```
  
 ### FlatMap
 
 ### Sort

# Platform Programming

# References

- https://towardsdatascience.com/why-developers-are-falling-in-love-with-functional-programming-13514df4048e
- https://www.freecodecamp.org/news/how-and-why-to-use-functional-programming-in-modern-javascript-fda2df86ad1b/#:~:text=Advantages%20Of%20Functional%20Programming,improve%20maintainability%20of%20the%20code.
- https://www.infoworld.com/article/3613715/what-is-functional-programming-a-practical-guide.html
- https://www.joelonsoftware.com/2006/08/01/can-your-programming-language-do-this/
- https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/map
- https://enlear.academy/reducers-in-javascript-f5317b34cba2
- https://www.digitalocean.com/community/tutorials/js-finally-understand-reduce
