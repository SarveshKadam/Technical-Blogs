## How to use Modular patterns in NodeJS?

Modular Pattern is one of the fundamental features of Node.

When building an application, as our application/code becomes complex we cannot put our entire code in one single file.

As this becomes unmanageable, we use node modular pattern to write different files and export them(which includes functions, objects, and methods) to the main files.

Now you might ask what exactly is a `module`?

In simple terms, a `module` is nothing but a JavaScript file. That's It.

With the node modular functionality, we can import your own external files, core node modules, and npm modules.


> #### Importing your own files :

In this article, we are going to discuss, how we can export and import our own files.
Basically, there are two files `calculate.js` from where we will export and import them into the `main.js` file. 


![mduleexport.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1603082860893/xGgR903x4.png)


We have both the files in the same folder for simplification purposes.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1603015526076/cwIgq_IuU.png)


- 
**Importing a function: ** 

```
//---- Exported file [calculate.js] ----
const add = (a,b)=>{
    return a + b
}

module.exports = add
```
Here we export a function called `add` using `module.exports`. Then this function gets imported to a different file using the `require` method.

In node, each file is referred to as a `module` and `exports` is a property of the module Object.

We can now invoke the function in the different files i.e `main.js` by passing the arguments as shown below.

```
//------ Main File[main.js] ----

const add = require('./calculate') //name of the desired file
const result = add(2,4)
console.log(result); //Output : 6

```

- **Importing an Object: ** We can also export an entire object and access the different methods in it.

```
//---- Exported file [calculate.js]  ----
const add = {
    result : (a,b)=>{
        return a + b
    }
}
module.exports = add

```
As we exported object add and imported to our main file using the `require` method. 

We can now access the `result` method of the `add` object using the `.` dot operator


```
//---- Main file[main.js] ----
const add = require('./calculate')

const result = add.result(5,8)

console.log(result) //Output : 13

```
Another way we can do the above Object exportations is by only exporting the method which you require rather than the entire object.

```
//---- Exported file [calculate.js]  ----
const add = {
    result : (a,b)=>{
        return a + b
    }
}

module.exports = add.result
```
As you can see we are importing the `result` method in the `add` Object, So this method can be directly invoked in the main file.

This is good practice if you don't need the entire object but only require some methods/functions of it and also make our code more secure.

```
//---- Main file[main.js] ----

const add = require('./calculate')
const result = add(5,8)
console.log(result) //Output : 13

```


- **Importing a Function Constructor: **

Function constructor is basically used to create a new instance of an Object which possesses the same properties as that of the main object/function.

You can learn more about Function Constructor [here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Function#Constructor)

In the below case, we create a new instance of the 'Add' Object using the `new` keyword. This process where we create an instance of an object is called 'instantiation'.

Then we export this instance using `module.exports`


```
//---- Exported file [calculate.js]  ----

function Add (){
    this.result = (a,b)=>{
        return a + b
    }
}

module.exports = new Add()

```
Now we can import it into our main file and access the 'result' method inside it, to get our calculated value.

```
//---- Main file[main.js] ----

const add = require('./calculate2')
const result = add.result(1,3)
console.log(result); //Output : 4

```
This way we can export and import a function constructor.

There is another way we can do this, which is by creating our new instance in the main file rather than in the exported file as shown above `module.exports = new Add()`.

We'll see that while exporting ES6 Classes which works similar to Function constructors.


- **Importing ES6 Classes: **

`class` is a special type of function where the `class` keyword helps to initialize it and uses the `constructor` method to store the properties. You can learn more ES6 classes [here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes)

Now we are going to export the entire `class` using `module.exports`

```
//---- Exported file [calculate.js]  ----

const Add = class{
    constructor(a,b){
        this.a = a;
        this.b = b;
    }

    result(){
        return this.a + this.b
    }
}

module.exports = Add;

```

Now in our main file, we create a new instance using the `new` keyword and access the `result` method to get our calculated value.

```

//---- Main file[main.js] ----

const add = require('./calculate')

const result = new add(2,5)

console.log(result.result()); //Output : 7

```

#### Conclusion :

In this article, we discussed how we can import our own files.

We looked into a few ways how we can do this, such as

* Importing Functions
* Importing an Object
* Importing a Function Constructor
* Importing ES6 Classes

There are n number of ways in which you can export and import your own files.

The other things which we did not discuss in this article are importing npm modules and importing node core modules which we'll look into in an upcoming article.

>Thank you for your time for reading the article, please, give a follow on my [Twitter](https://twitter.com/kadamsarvesh10) as I document my learning



