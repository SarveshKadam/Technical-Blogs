## What exactly is the Queue Data Structure in JavaScript?

**Data Structure** are observed in every programming language be it in the form array, objects. They are nothing but a way of organizing, updating, retrieving, and storing data.
In this article, we'll discuss the queue data structure.
The queue is nothing but a collection of items having the **FIFO** ( **F**irst **I**n **F**irst **O**ut) format



![Standingqueue.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1601656692491/__5iLkmJP.jpeg)
*pic credit* [unsplash](https://unsplash.com/)

As you can see a real-life example of **first in first out**, the customer who is first in the queue gets first preference and he is the first one to move out of the queue.

Before moving forward with our data structure, let's just refresh some of the arrays methods


- `pop()` removes last element of array

- `push()` adds a new element to the end of the array

- `unshift()` adds a new element to the beginning of the array

- `shift()` removes the first element of the array

For further reference, you can visit [mdn](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array).

Now we will go through five simple functionalities of the queue data structure


- `enqueue`: adding an element

- `dequeue`: remove element

- `peek`: which is the next element to be removed

- `length`: length of the array/queue

- `isEmpty`: verify if the queue is empty

![Add a subheading (2).png](https://cdn.hashnode.com/res/hashnode/image/upload/v1601658389246/00Vp_ja4N.png)

Here in this queue, A is the first person and D is the last one, Once A is done with his order at the shop he will move out of the queue and B will have his turn after him.

Let's create an array and add element(person) by using the `enqueue` function which we will create

```
let q = []
function enqueue(item){
        q.unshift(item)
}

enqueue("A")
enqueue("B")
enqueue("C")
enqueue("D") 

```
The output will be
`["D", "C", "B", "A"]`

Now the first element will move out, so we'll create the `dequeue()` function
```
function dequeue(){
        return q.pop()
  }

console.log(q) //Output :"A"

```
`peek()` will be a function in which we give back the item which is the next one to move out of the queue. So once "A" is out of the queue, the `peek()` function will return "B" as output

```
function  peek(item){
            return q[q.length - 1]
        }
```
Finally, we'll create `length()` and `isEmpty()` to validate how many items are remaining in the queue and later one determine whether the queue is empty or not

```
function length(){
            return q.length
      }
function isEmpty(){
            return q.length === 0
        }
```

Let us consolidate all the functions discussed above in a single function called `queue()` so it will be clear to us what exactly is happening here.

```
function queue(){
    let q = []
    return{
        enqueue(item){
             q.unshift(item)
         },
        dequeue(){
            return q.pop()
        },
        peek(item){
            return q[q.length - 1]
        },
        length(){
            return q.length
        },
        isEmpty(){
            return q.length === 0
        },
        display(){
            return q
        }
    }
}

const action = queue()

console.log(action.isEmpty())   //Output: true


action.enqueue("A")
action.enqueue("B")
action.enqueue("C")
action.enqueue("D")

console.log(action.display())   //Ouput :["D", "C", "B", "A"]


console.log(action.dequeue())   //Output : A

console.log(action.peek())   //Output : B

console.log(action.length())  //Output : 3

```
Now we can also create above mention functionalities using ES6 **Classes**.

`class` is a special type of function where the `class` keyword helps to initialize it and uses the `constructor` method to store the properties. You can learn more ES6 classes
[here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes)

```
class queue{
    constructor(){
        this.q = []
    }
    
    enqueue(item){
       this.q.unshift(item) 
    }
    dequeue(){
        return this.q.pop()
    }
    peek(){
        return this.q[this.q.length - 1]
    }
    
    display(){
        return this.q
    }
}


const q = new queue()
q.enqueue("A")
q.enqueue("B")
q.enqueue("C")
q.enqueue("D")
console.log(q.display()) //Output :- ["D", "C", "B", "A"]

console.log(q.dequeue())   //Output :- A

console.log(q.display())  //Output :- ["D", "C", "B"]

console.log(q.peek())    //Output :- B

```

**Finally**, we will combine two different queues in a single one by creating a `weave` function


![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1601810609615/gKM9fMoz_.png)

Here we will insert items from each element alternatively to a brand new queue

```
class queue{
    constructor(){
        this.q = []
    }
    
    enqueue(item){
       this.q.unshift(item) 
    }
    dequeue(){
        return this.q.pop()
    }
    peek(){
        return this.q[this.q.length - 1]
    }
    
    display(){
        return this.q
    }
}


const q1 = new queue()
q1.enqueue("A")
q1.enqueue("B")
console.log(q1.display())

const q2 = new queue()
q2.enqueue("Y")
q2.enqueue("Z")
console.log(q2.display())

const weave = new queue()
function weaving(q1,q2){
while(q1.peek() || q2.peek()){
    if(q1.peek()){
        weave.enqueue(q1.dequeue())   
    }
    
    if(q2.peek()){
        weave.enqueue(q2.dequeue())
    }   
}
 return console.log(weave.display())
}
weaving(q1,q2) //Ouput:- [ 'Z', 'B', 'Y', 'A' ]
```
So above `peek()` method is used in the `If` statement to determine if there are any items left in the queue which are to be added to the `weave` array.
Using the enqueue method we add the element from each array alternatively to the new `weave` array created

**Conclusion**:

- Queue has FIFO( First In First Out) format 


- 
By using functions we created five functionalities  `enqueue`, `dequeue`,`peek()` and `isEmpty()`


- 
We created the same functionality using ES6 classes

- Then we combined two array different arrays by creating the `weave` function

>Thank you for your time for reading the article, please, give a follow on my [twitter](twitter.com/kadamsarvesh10)  as I document my learning







