## How to get started with NPM(Node Package Manager) Packages?

In this article, we are going to discuss how can we used NPM (Node Package Manager).

But before reading, I would suggest you to read my previous two articles of this [**Node Modules**](https://hashnode.com/series/node-modules-ckgn9w1n001uuo9s11k8e5cq2) series.

-  [How to use node modular pattern](https://sarveshkadam.tech/how-to-use-modular-patterns-in-nodejs)

- [How to use Node Core modules](https://sarveshkadam.tech/how-to-use-the-nodejs-core-native-modules)

#### NPM Overview:
So what exactly is Node Package Manager?<br>
The package is a piece of code that is managed by the Package Manager which is nothing but software that manages the installation and updating of packages.

NPM as per the official [document](https://docs.npmjs.com/)
>NPM is the world's largest software registry. Open-source developers from every continent use npm to share and borrow packages and many organizations use npm to manage private development as well.

So, in NPM we use somebody else's open-source code managed by NPM by importing into our project.<br>
NPM usually comes with Node JS when you download it.
You can check if npm is installed on your machine by simply running the command `npm -v` on your command-prompt.
if it returns some version number, it means NPM is successfully installed.

NPM has its registry at [npmjs.com](https://docs.npmjs.com/) where we can discover packages that we can use.

Let's look at one of the packages called [chalk](https://www.npmjs.com/package/chalk) which is basically used for terminal styling.


![chalknpm2.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1603909979665/T6w4cd8qR.jpeg)
>pic credit npmjs.com <br>

In the above figure, we can see the weekly downloads of the package which suggests how popular is it.<br>
Also, you can see this package dependencies in it. So this module which will serve as a dependency on our project is itself dependent on other modules.
So this entire management process is taken care of by the Package Manager.<br>
Even the source code is which is present on GitHub is given to us. We can navigate to it and verify if there are any open issues present.<br>
One more thing before moving forward, the NPM packages come in different versions. The pattern which the version follows is semantic versioning.<br>
As you can see, the latest version of the [chalk](https://www.npmjs.com/package/chalk) module as and when I wrote is article is **4.1.0**

It follows the semantic versioning as `Major_changes`**.**`Minor_changes`**.**`Patch`

`Major_changes` as the name stands, the significant changes made on the module which might affect your existing code.<br>
`Minor_changes` are a new enhancement or feature along with defect fixes been added which should not affect your existing code.<br>
`Patch` is the small bug fixes that will not crash your existing code.

You learn more about semantic versioning on [semver.org](https://semver.org/)

#### NPM Installation:
Now to import any package from NPM, you first need to initialize NPM on your local project folder by running the command on the command prompt

```
npm init
```
Once you run the above command, it will ask you for some data as shown below such as package name, version, and so on.
Much of this data can be kept as default as mention in the Round brackets **()**.
Also, the field such as `author` and `license` is for the folks who creating NPM packages.<br> On the other hand, we are just importing and using them to create our own application.

```
package name: (code_npm) code_npm
version: (1.0.0) 1.0.0
description: npm demo
entry point: (index.js) index.js
test command: test
git repository:
keywords: npm test
author: Sarvesh
license: (ISC)

```
Once you enter all the fields, it will create a JSON file with the values having the above properties and will ask you for confirmation as

```
Is this OK? (yes) yes
```

Once you confirmed `yes` it will create a `package.json` file with all the data you entered as illustrated below.
```
{
  "name": "code_npm",
  "version": "1.0.0",
  "description": "npm demo",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "keywords": [
    "npm",
    "test"
  ],
  "author": "Sarvesh",
  "license": "ISC"
}

```
Also, you can observe a `script` Object having a `test` property been added, which you can run using the `npm test` command and it will give back the desired output as 
```
"Error: no test specified"
```
Now instead of doing this elongated method of initializing NPM and entering the custom properties values, you can simply run the command  
```
npm init -y
```
Once you run this command, it will directly create a `package.json` file with the default values.

![pkgjson.PNG](https://cdn.hashnode.com/res/hashnode/image/upload/v1603968825440/3fcyAhRJG.png)
Now to install the latest version of the **chalk** package in your project you need to execute the command
```
npm install chalk
``` 
You can also install any specific version you need of chalk by just adding `@version number` as shown below and also instead of `install` you can simply put the short-hand `i` flag which stands for installation

```
npm i chalk@4.0.0
```
This will install two things, a `node_modules` folder, and a `package-lock.json` file.

![folderdir.PNG](https://cdn.hashnode.com/res/hashnode/image/upload/v1603968346848/EAws9k06a.png)
Also, it will add a new property called `dependencies` to our `package.json` file which contains the name of the package installed and its version.

```
"dependencies": {
    "chalk": "^4.0.0"
  }
```
The `node_module` folder contains the packages folder and its dependencies folders. It gets modifies as and when the npm package gets installed.<br>
The `package-lock.json` contains the code which makes NPM faster and secure.

```
"chalk": {
      "version": "4.0.0",
      "resolved": "https://registry.npmjs.org/chalk/-/chalk-4.0.0.tgz",
      "integrity": "sha512-N9oWFcegS0sFr9oh1oz2d7Npos6vNoWW9HvtCg5N1KRFpUhaAhvTv5Y58g880fZaEYSNm3qDz8SU1UrGvp+n7A==",
      "requires": {
        "ansi-styles": "^4.1.0",
        "supports-color": "^7.1.0"
      }
```
It mainly contains properties such as `version` which is the semantic version number.<br>
The `resolved` property is the directory or location from which the package was fetched, here in this case it was fetched from [chalk](https://www.npmjs.com/package/chalk).<br>
The `integrity` property is to assure, we get the same code if we install the dependency again.<br>
The `requires` object property represents the dependency of the `chalk` package.

**Note**:- Do not make any changes or edit these two files `node_modules` and `package-lock.json`

#### NPM Usage:
Now once we installed chalk to our project we can import it to our root project file using the `require()` method and store that module in a variable `chalk`.

%[https://gist.github.com/SarveshKadam/83f6095df56e83da154b9528129d089e]

Using the `red()` method of the `chalk` package, we have styled the "Hello World" text color in red. 
On running the command `node index.js` we get the following output


![chalkop.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1603966334203/3ulfhvZnz.png)

Now there are many ways you can style your command line output using the chalk package, for more information refer to the [Chalk official document](https://www.npmjs.com/package/chalk) on npm.

Also, you can install the npm packages globally that is on our operating system rather than installing it in your local project by adding the `-g` flag on the command line which stands for global as mentioned below 

```
npm i nodemon -g
```
This global package will not affect our `package.json` in any way since it is not installed locally.
we have installed the `nodemon` package globally which is used for automatic restarted of node application when file changes in the directory are observed.
Refer to [nodemon](https://www.npmjs.com/package/nodemon) for more information.

We can use the nodemon package by running the application using
```
nodemon index.js
```
It works similarly to `node index.js`, except it keeps an eye on the file changes and it restarts the application once changes are detected.
```
[nodemon] 2.0.6
[nodemon] to restart at any time, enter `rs`
[nodemon] watching path(s): *.*
[nodemon] watching extensions: js,mjs,json
[nodemon] starting `node index.js`
Hello World
```
**Note**: The `chalk` styling will probably not work when you used `nodemon`

Finally, we will go through the `dev dependencies`.There are some NPM packages or modules which won't be needed in our project production environment, but only for our development requirements.
Such modules we install in our project using the `dev` flag as shown below

```
 npm i nodemon --save-dev
```

It created new property in the `package.json` called `devDependencies`
```
"devDependencies": {
    "nodemon": "^2.0.6"
  }
```
#### Conclusion:

- NPM is a package manager that manages the 3rd Party Open source code which we can use in our project.

- Before using NPM modules, we need to initialize NPM locally using `npm init` on your command line in the root of your project folder.

- Install any NPM package by using the command `npm i <package name>`

- We can install the NPM package globally using the `-g` flag

- Also the package can be made development dependent using the `--save-dev` flag

>If you like this article do reach out to my [Twitter](https://twitter.com/kadamsarvesh10) as I document my learning



