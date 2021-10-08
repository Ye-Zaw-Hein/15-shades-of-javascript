# 15 Shades Of Javascript
## 1. Prototype

```javascript
function Bike(model,color){
   this.model = model,
   this.color = color,
this.getDetails = function(){
     return this.model+' bike is '+this.color;
   }
}
var bikeObj1 = new Bike('BMW','BLACK');
var bikeObj2 = new Bike('BMW','WHITE');
console.log(bikeObj1.getDetails()); //output: BMW bike is BLACK
console.log(bikeObj2.getDetails()); //output: BMW bike is WHITE

//creating two objects, bikeObj1,bikeObj2 using a constructor.In JavaScript, every object has its own methods and properties. In our example, two objects have two instances of the constructor function getDetails().

function Bike(model,color){
  this.model = model,
  this.color = color
}
Bike.prototype.getDetails = function(){
 return this.model+’ bike is ‘+this.color;
}
var bikeObj1 = new Bike(‘BMW’,’Black’);
console.log(bikeObj1.getDetails());

console.log(bikeObj1.__proto__ === Bike.prototype );
//output : true
```
## 2. Class 
```

```


## 3. IIFE (Immediately Invoked Function Expression) 

```javascript
//IIFE (Immediately Invoked Function Expression) is a JavaScript function that runs as soon as it is defined.

var custom_type = (function() {
    return 'foo';
})();

var custom_type2 = function() {
    return 'bar';
};

console.log('iife = ' + custom_type);//output: iife = foo 
console.log('non-iife = ' + custom_type2);//output: non-iife = function(){return 'bar'};

```
## 4. Closures

```javascript

//A closure is the combination of a function and the lexical environment within which that function was declared.

//a closure is a function that is evaluated in an environment containing one or more bound variables. When called, the function can access these variables.

//A closure is an inner function that has access to the outer (enclosing) function’s variables — scope chain. The closure has three scope chains: it has access to its own scope (variables defined between its curly brackets), it has access to the outer function’s variables, and it has access to the global variables.

function User(name){
  var displayName = function(greeting){
   console.log(greeting+' '+name);
  }
return displayName;
}
var myFunc = User('Raj');
myFunc('Welcome '); //Output: Welcome Raj
myFunc('Hello '); //output: Hello Raj

```
## 5. Modules
```
```
## 6. Hoisting

```javascript
//In JavaScript, a variable can be declared after it has been used.

//In other words; a variable can be used before it has been declared.


x = 5; // Assign 5 to x

elem = document.getElementById("demo"); // Find an element 
elem.innerHTML = x;           // Display x in the element

var x; // Declare x
//output: x =5

```
## 7. Scopes

```javascript

//Global Scope
//Local Scope

var greeting='Welcome to blog';
(function(){
  console.log(greeting); //Output: Welcome to blog
})();

(function(){
  var greeting = 'Welcome to blog';
  console.log(greeting); //Output: Welcome to blog
})();
console.log(greeting); //Output:Reference-Error greeting not defined

```

## 8. Currying
```javascript
//Currying is a technique of evaluating the function with multiple arguments, into a sequence of function with a single argument.
//Mainly It helps to create a higher order function. It is extremely helpful in event handling.

var add =   function (a){
                 return function(b){
                       return function(c){
                              return a+b+c;
                              }        
                        }
                  }
console.log(add(2)(3)(4)); //output 9
console.log(add(3)(4)(5)); //output 12
```
## 9. Memoization
```javascript

//Memoization is a programming technique which attempts to increase a function’s performance by caching its previously computed results.

const memoizedAdd = () => {
        let cache = {};
        return (value) => {
            if (value in cache) {
                console.log('Fetching from cache');
                return cache[value];
            } else {
                console.log('Calculating result');
                let result = value + 10;
                cache[value] = result;
                return result;
            }
        }
    }

// returned function from memoizedAdd
const newAdd = memoizedAdd();
console.log(newAdd(9)); //output: 19 calculated
console.log(newAdd(9)); //output: 19 cached

 //Each time a memoized function is called, its parameters are used to index the cache. If the data is present, then it can be returned, without executing the entire function. However, if the data is not cached, then the function is executed, and the result is added to the cache.

```
## 10. Callback Function
```javascript

//A reference to executable code, or a piece of executable code, that is passed as an argument to other code.

//Callback functions in JavaScript are functions that can be passed to other functions as a parameter. They are also known as higher-order functions and are called (or executed) inside the function they were passed to. A callback is a convention, not an actual thing in the JavaScript language. Callbacks are used when you need to do things in your code which result in I/O, or input/output operations. Things like talking to a database, downloading a photo, or writing a file to disk are examples of I/O operations. These are asynchronous operations.

function greeting(name) {
console.log('Hello ' + name);
}
function processUserInput(callback) {
    //var name = prompt('Please enter your name.');
    name = 'raja';
    callback(name); // callback function
}
processUserInput(greeting); //output Hello Raja

//In this ab above program, function greeting passed as an argument to the processUserInput function, so I hope you now understood callback function in JavaScript.
```
## 11. Apply,Call and Bind methods
```javascript

var obj={
   num : 2
}
var add = function(num2,num3,num4){
   return this.num + num2 + num3 + num4;
}
var arr=[3,4,5];
//Call method 
console.log(add.call(obj,3,4,5));  //Output : 14

//Apply method
console.log(add.apply(obj,arr));   //Output : 14

//bind Method
var bound = add.bind(obj);
console.log(bound(3,4,5));         //output : 14 

1.Call method:
consider below code, obj have the property of num, using call method we can bound obj to add function,

2.Apply Method
The same way Apply method also works but the only difference is using apply method the passing arguments could be an array, refer below code.

3.Bind Method:
bind method returns a method instance instead of result value, after that need to execute a bound method with arguments.
```
## 12. Polymorphism
```javascript
```
## 13. Asynchronous Js
```javascript
<script src='index.js'>           //default Synchronous  scan above html code, run script and scan
below html

<script async src='index.js'>      //parse as Asynchronously scan js and html together, non blocking script

<script defer src='index.js'>      //parse as deferred scan all html code first and run script

//If synchronous <script > tag occurs, JS engine will download the code and execute that code and after that only parsing the below HTML code, generally Synchronous is a blocking script execution.

//If Asynchronous <script async> tag occurs, while downloading the code JS engine will parse the HTML and once If JS code gets downloaded pause the parsing and back into the JS Code Execution, generally Asynchronous is a Non-blocking script execution.

//If Asynchronous <script defer> tag occurs, JS Engine will parse the all HTML code and after that only executes the JS Code,
```
## 14. Promises

A promise represents the result of the asynchronous function. Promises can be used to avoid chaining of callbacks.

A Promise is in one of these states:
  - pending: initial state, neither fulfilled nor rejected.
  - fulfilled: meaning that the operation completed successfully.
  - rejected: meaning that the operation failed.

```javascript

var promise1 = new Promise(function(resolve, reject) {
    isDbOperationCompleted = false;
    if (isDbOperationCompleted) {
        resolve('Completed');
    } else {
        reject('Not completed');
    }
});
promise1.then(function(result) {
    console.log(result); //Output : Completed
}).catch(function(error) {
    console.log(error); //if isDbOperationCompleted=FALSE                                                  
    //Output : Not Completed
})

```

## 15. Async & Await
```javascript

//Async and Await are extensions of promises.

method: {
	notify(){
	swal({
	  title
	  text
	  icon
	}).then(confirmed => {
	 if(!confirmed)return;

	axios.post(this.url).then(() => {
	   flash('okay');
	});
	});
     }
}

method: {
	async notify(){
	let confirmed = await swal({
	  title
	  text
	  icon
	});
	 if(!confirmed)return;

	await axios.post(this.url);
	   flash('okay');
		
     }
}
```
