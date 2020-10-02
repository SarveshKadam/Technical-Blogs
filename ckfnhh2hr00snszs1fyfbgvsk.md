## Getting started with JSON(JavaScript Object Notation)

JSON(**J**ava**S**cript **O**bject **N**otation) is a storage format that is completely language independent and it is used to store and transport data. It's quite an important topic as the data which we fetch from external API usually consists of Arrays of elements which are in JSON format. 

The syntax of JSON is quite similar to the Object literal syntax which also consists of name, value pairs. But here both names, as well as values, are quoted in inverted commas.

Let us look at the example below :
```
//Object literals syntax
let details = {
      firstName : "John",
      lastName : "Adams",
      age : 27
}

//JSON syntax
{
      "firstName" : "Mike",
      "lastName" :  "Bush",
      "age" : 25
}

```
It is believed that in previous years XML format was widely used which has tags surrounding the data.The above mention JSON data in XML format is represented as below
```
<details>
     <firstName>Mike</firstName>
     <lastName>Bush</lastName>
     <age>25</age>
</details>

```
As you can see the XML format is verbose as compare to JSON i.e. for a single value "Mike", the name "firstName" is repeated twice for the opening and closing tags which is quite unnecessary. Also, the JSON can be parsed to Object literal which makes it faster to work with.

JSON is so popular that even JavaScript understands it and it has inbuilt functions to convert from JSON to object literal and vice versa.


- 
Javascript provides `JSON.stringify()` method to convert data from object literal format to JSON format

```
 const objectData = {
    firstName : "Mike",
    lastName : "Bush"
 }

 const JSONdata = JSON.stringify(objectData)
 console.log(JSONdata)

```
*Output*:- 

```
{"firstName":"Mike","lastName":"Bush"}
```

- 
There is another method called`JSON.parse()` which converts JSON format data to Object literal format

```
const JSONdata = '{ "firstName" : "Mike", "lastName" : "Bush"}';
const ObjectData = JSON.parse(JSONdata)

console.log(ObjectData)
```
*Output*:-
```
{firstName: "Mike", lastName: "Bush"}
```
This is what I learned when I started with JSON. Understanding fundamentals and the methods of JSON are important as they are an elemental part of accessing information with API.

**Conclusion **:

- JSON syntax is similar to Object literal where both name-value pair is in inverted commas.

- 
`JSON.stringify()` Object --> JSON 
- `JSON.parse()` JSON --> Object 

<hr>
*Thank you for your time for reading the article, please leave a review and share it if it helped you. Also, give a follow on my twitter(https://twitter.com/kadamsarvesh10)
*

