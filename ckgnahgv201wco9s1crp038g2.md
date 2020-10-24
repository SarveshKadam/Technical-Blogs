## How to use the NodeJS Core (Native) modules?

In the last [article](https://sarveshkadam.tech/how-to-use-modular-patterns-in-nodejs), we discussed how to import our own files in NodeJS which included function, Objects, function constructor, and ES6 classes.
You can find that article over [here](https://sarveshkadam.tech/how-to-use-modular-patterns-in-nodejs).

Today we are going to discuss how we can import and use Node Core(Native) modules into our own files.

#### Importing Node Core (Native) modules:

Rather than creating our own custom modules every time, Node provides a set of modules to make our lives easier.

We are going to discuss some of the modules, but you can find the entire list on the official node API document over [here](https://nodejs.org/dist/latest-v15.x/docs/api/)

Importing Node modules is similar to that of importing your own modules we use the same `require()` function to access it in our own file.

But there are some modules which you may have used knowingly unknowingly which do not need to be imported. For eg. `console.log()`, we have used the `console` module many times without fetching it in our own local file as these methods are available **globally**.

Let us look at one of the Core Native Modules which is **File System** (`fs`).
There are n number of operations we can perform with the file system module such as reading a file, writing a file, and updating it to name a few.

We are going to use the `fs` module to read a file, even in that there are two ways we can perform this one by using the synchronous function `fs.readFileSync()` and the other by asynchronous function `fs.readFile()`, we'll discuss synchronous-asynchronous Node functions in future posts.

Today, we'll use the asynchronous version i.e. `fs.readFile()`

For this example, we have created two files one `main.js` where we are going to perform file reading operation and `file.txt` which is the file we are going to read.


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1603442034534/DRk8tK6B8.png)

The`file.txt`contains some text in it.

%[https://gist.github.com/SarveshKadam/ae8443ec11abf919c6c28e9c1821e5ba]

Now, if we use the `fs` module to read the file, without importing it as shown below

%[https://gist.github.com/SarveshKadam/17dc243be300a9ca1c9f625b288583ea]

It will throw an error as `fs` is not defined that is because the file system `fs` module is not available globally as the `console` module is.

```
ReferenceError: fs is not defined
    at Object.<anonymous> (C:\Users\Sarvesh Kadam\Desktop\Training\blog\code snippets\Node Modular Pattern\main.js:3:1)
    at Module._compile (internal/modules/cjs/loader.js:1256:30)
    at Object.Module._extensions..js (internal/modules/cjs/loader.js:1277:10)
    at Module.load (internal/modules/cjs/loader.js:1105:32)
    at Function.Module._load (internal/modules/cjs/loader.js:967:14)
    at Function.executeUserEntryPoint [as runMain] (internal/modules/run_main.js:60:12)
    at internal/main/run_main_module.js:17:47
```
Therefore, we need to import all the data from the file system module using the `require()` function and store all that data in a variable `fs`.

%[https://gist.github.com/SarveshKadam/ed9b09bd8597037f22b0498fbb43c2e6]

Now you can name that variable anything, we named it `fs` for readability and it's the standard which most developers follow.

Using the `fs` variable we can access the `readFile()` method where we passed three arguments which are file path, character encoding `utf-8`, and the callback function to give an output.

You might ask why are we passing `utf-8` as our argument in the `readFile()`?

The reason is, it encodes the value and gives the text as an output rather than giving a buffer as shown below

`<Buffer 48 65 6c 6c 6f 20 57 6f 72 6c 64 21 21>`

The callback function, in turn, has two arguments an error (`err`)and the actual content in the file (`data`), and then we print that `data` in the console.

```
//Output:
Hello World!

```
#### Conclusion :

- Node has it's own set of Core (Native) Modules which we can use.

- Some of them are available globally, some of them need to be imported locally in your project/folder.

- `require()` function is used to fetch the particular module data and we stored all that data in a variable to access it.

>Thank you for your time for reading the article, please, give a follow on my [Twitter](https://twitter.com/kadamsarvesh10) as I document my learning







