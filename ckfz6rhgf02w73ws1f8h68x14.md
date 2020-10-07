## How to use Functions in JavaScript?

**Functions **are the fundamental part of JavaScript programming language. It is a block of code that is reusable, i.e. the function can be called anywhere in the code and perform the required task as many times as you need it.

In this article, we are gonna take look at various ways/methods of using JavaScript Function


- ** Function statement** :- 
In this method, we simply declared the function using the `function` keyword along with the name of the function. We passed the arguments (if any) in the round`()` bracket and the write the code what you want the function to perform when it is called or invoked inside parenthesis `{}`.


In the function statement, the function gets hoisted, that is you can access or invoke the function even before it is declared. You can learn more about hoisting where I have briefly discussed it in my [previous article](https://sarveshkadam.tech/learn-var-const-and-let-javascript-in-6-minutes)

```
square(4) //Output: 16

function square(a){
    console.log(a * a);
}

square(2)

//Output : 4
```


- **Function expressions** :- 
An anonymous function is created, which does not have its name and therefore we create an expression by assigning to a variable using the equal `=` operator.

```
var square = function(a){
    console.log(a * a);
}

square(2)

//Output : 4
```
The `square` variable is not the name of the function, it just points towards the address of the function in the memory space.

*Note*:- In function expression, we cannot access the function before it is declared as it will return the variable `square` as `undefined`

- **Immediately Invoked function expression**: -
In this, we simply declared an anonymous function as we discussed in the function expression above, but instead of assigning it to a variable, we wrapped it inside the parenthesis `()` and we can immediately invoke or called the function.

```
(function(a){
    console.log(a * a);
})(2)
//Output : 4

```

As you can see above example we create an anonymous function passed an argument `a` and it returns the square of the argument, we can also invoke the function immediately after the curly brackets `{}` as shown below

```
(function(a){
    console.log(a * a);
}(2))

//Output : 4
```

- **Arrow Functions**:- Arrow functions are a concise and neat way to write JavaScript functions. It was introduced in ES6, in this way we don't need to explicitly mention the `function` keyword while declaring the functions instead we use arrow `=>`.

```
var square = (a)=>{
    console.log(a * a);
}
square(2)

//Output : 4
```

Since in the above code we are passing only one argument `a` and returning only one value i.e. the square of the number we can make the code more concise by removing the argument brackets and parentheses `{}` the curly braces

```
var square = a => console.log(a * a);
square(2)

//Output : 4
```
Before, moving forward let us discuss the about `this` keyword, The `this` in normal function points towards the Object where it is placed in, whereas in the arrow function it points toward the Global Object.

```
var a = {
    square1 : ()=> {
        console.log(this);
    },
    square2 : function(){
        console.log(this);
    }
}

a.square1() //Output: Window {parent: Window, opener: null, top: Window, length: 0, frames: Window, …}
a.square2() //Output: {square1: ƒ, square2: ƒ}
```

- **Callback function**:- A callback function is a function you passed as an argument to another function. Sounds Confusing!
Let's look at the below example.

```
var square = (callback)=>{
    callback(2);
}

square((a)=>{
    console.log(a * a); 
})
```
So in the above example, we create a square function where we pass the "callback" function as an argument, which itself has an argument which is declared as "2".
During the invocation of the `square` function, we pass the 'callback' function with the argument as `a` and it prints the square of `a` on the console.

There is also another function called `async` which we will discuss it in upcoming blogs since it also requires the concept of `promise`

**Conclusion **:- 

- In the function statement, we declared using the `function` keyword and `this` point towards the object it is located in.

- In function expression, we assign the function to a variable using the `=` equal operator.
- Immediately Invoked function expression is wrapped around the parenthesis `()` and it is invoked immediately after the declaration.

- Arrow function which was introduced in ES6 is a concise way to write functions and the `this` keyword inside arrow functions point towards Global Object irrespective of where it is located.

- Callback functions are the functions that are passed as arguments in another function.

>Thank you for your time for reading the article, please, give a follow on my [twitter](https://twitter.com/kadamsarvesh10) as I document my learning












