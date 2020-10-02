## Learn var, const, and let [JavaScript] in 6 minutes

If you have started learning JavaScript and even if you are in the early stages you must have come across `var`, `const`, and `let` variable declaration.

The `const` and `let` were introduced in ES6 but before that only `var` was the only way of variable declaration. Each one of them has its properties, scopes, and uses. 

Let us understand each one of them, the main differences between these ways of declaring variables

### var : 
Variable declared with `var` are **mutable** i.e. they can be reassigned or even declare first and initialize in another step
```
var num  //num declared -- > value of num is undefined 
num = 1  //num initialize/assigned-- > value of num is 1
num = 3 //num reassigned -- > value of num is 3

```

`var` is Global scoped and functional scoped.</br>
A variable has global scope when it is declared outside the function and that variable is accessible anywhere in the code

```
var firstName = "Sarvesh"
var lastName = "Kadam"
function greet(){
       console.log(firstName+" "+lastName)
}
greet() //*Output*: Sarvesh Kadam

```

Now the functional scoped says that if  a variable is declared with the `var` keyword inside a function, it cannot be accessed outside it

```
function hello(){
       var firstName = 'Sarvesh'
      }
console.log(firstName) //Will throw an error as firstName is not defined
```

We cannot access the `firstName` variable outside the function lexical scope. 



### const and let: 
`const` and `let` are blocked scoped(we will this understand in a second). But first, let's look at the difference between them.

`let` is mutable (as seen in `var`) whereas `const` is immutable.

As we can see in the below example, we can declare the variable at one instance and assigned a value to the "item" variable later or even reassign a new value to it.


```

let item //declaration
item = "food" //item is assigned a value -- > value of item is food
item = "clothes" //item variable declared -- > value of num is clothes

```

Let's look at `const`

```
const item ; //the value must be assigned while declaring
item = "food"  //error

const item2 = "pen"
item2 = "eraser" //error : value cannot be reassigned to constant variable
 
```
So in `const`, we need to declare and initialize the variable at one instance only and we cannot reassign/change the value.

Now both `const` and `let` are blocked scope i.e. we cannot access the variables outside parenthesis{} whether the block is a function or conditional statement

```
if(true){
    let number1 = 2
    const number2 = 4
}
console.log(number1) //will throw an error as number1 is not defined
console.log(number2) //will throw an error as number2 is not defined
```
As the variables "number1" and "number2" are declared inside the if statement block we cannot access them, whereas in the case of `var` we can access it as it is function scoped not block scoped.

```
if(true){
   var number = 5
}
console.log(number) //Output = 5

```
Now let us discuss a scenario where an object is declared with `const`

```
const player = {
    name : "Eden Hazard",
    team : "Read Madrid",
    position : "forward"
}

player.name = "Karim Benzema" //will re-assign the Value successfully

player = {
    name : "Modric",
    team : "Read Madrid",
    position : "forward"
}   //will throw an error 

```
As you can see in the above example we can change the properties of the object variable declared with `const` but cannot reassign the entire object.

#### Some peculiar behavior :


- In `var` we can **declare** a single variable multiple times and it will not throw an error. 
**Note:** We don't use this property in any circumstances, just wanted to make you aware of it

```
     var name = "sarvesh"
     console.log(name)  //Output: sarvesh
     var name = "rihan"
     console.log(name) //Output : rihan
    
```

- In `let` we can use the same name for declaring variables for different blocks and it will not affect the value of the global variables

```
     let a = 5
     if(true){
          let a = 8
          console.log(a) //Output : 8 
     }

     console.log(a) //Output : 5 

```
As we have used a similar name "a" to declare and initialize the variable. Inside the block, the value of "a" is 8 and outside the block i.e. on the global object the value is 5.


- In `var` the variable gets **hoisted** i.e. (the `var` variable is available even before any function/code is executed).

```
     console.log(name) //Output : undefined

     var name = "sarvesh"

     console.log(name) //Output : sarvesh

```

In the above code, the variable "name" is accessible even before its value is declared or initialize.
As the JavaScript is parsed, before executing any function/code, the parser searches for any variable or function declarations and it sets a memory space for them with value as `undefined`.

So here before execution, the variable "name" is stored in the memory space with the value of 'undefined' before any of the `log` functions are executed.

This entire phenomenon is called **Hoisting** .( will explain in detail with another blog)

This scenario will throw an error if we used `let` or `const` instead of `var`, as these variables do not get hoisted.

### Conclusion : 
 

-  `var` is functional scoped

- `const` and `let` are blocked scoped

- `var` and `let` are mutable

- `const` is immutable


It's a common practice to use `let`,`const` instead of `var`, as the former two are blocked scope and not accessible outside the block,  as it makes the code more secured so if anybody changes the value outside the block it will bot affect the functionality of the entire code.

Even in between `const` and `let`, use `const` wherever possible as it makes the code more readable as we understand if the value of the variable will be updated or not further down the code

The above-mentioned points are good enough to get you started with `var`, `let`, and `const`.


>Thank you for your time for reading the article, please leave a review and share it if it >helped you. Also, give a follow on my twitter(twitter.com/kadamsarvesh10)