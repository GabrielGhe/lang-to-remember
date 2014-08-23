JavascriptToRemember
=================
Things to remember for javascript

<h3 id="tableOfContent">Table of content</h3>
<ol>
  <li><a href="#1-string">Strings</a></li>
  <li><a href="#2-callbacks">Callbacks</a></li>
  <li><a href="#3-promises">Promises</a></li>
  <li><a href="#4-context">Context</a></li>
  <li><a href="#5-sorting">Sorting</a></li>
  <li><a href="#6-bit-manipulation">Bit Manipulation</a></li>
  <li><a href="#7-math">Math</a></li>
</ol>

<!-- 
#########################################
#
#		String
#
#########################################
-->
<h3 id="string"><a href="#table-of-content">1. String</a></h3>
```javascript
"A string  "

  .toLowerCase()        // "a string  "
  .toUpperCase()        // "A STRING  "
  
  //takes a delimiter
  .split("")            // ['A', 's', 't', 'r', 'i', 'n', 'g', ' ', ' ']
  
  //with split ^
  .join()               // "A string  "
  
  //takes startPos endPos
  .substring(2, 4)      // "st"
  
  .indexOf("str")       // 2
  
  .trim()               // "A string"
  
  .replace("string", "blah"); // "A blah  "
  
  .match(/a str.*/i)    // "A string  "
  
  //takes in a position
  .charAt(0)            // "A"
  .charCodeAt(0)        // 65
  
  //takes in base
  4.toString(2)         // 110
```

<!-- 
#########################################
#
#	Callbacks
#
#########################################
-->
<h3><a id="callbacks" href="#table-of-content">2. Callbacks</a></h3>

<p>Callbacks are a big part of javascript</p>

```javascript
function callFuncOnFive(cb){
	return cb(5);
}

var returnedValue = callFuncOnFive(function(num){
	return num * num;
});

console.log(returnedValue); // 25 (5*5)
```


<!-- 
#########################################
#
#		Promises
#
#########################################
-->
<h3><a href="#table-of-content">3. Promises</a></h3>
<p>Promises allow you to flatten a callback pyramid</p>

```javascript
//using callbacks
function one() {
	function two() {
		function three() {
			
		}
	}
}

//using promises
promiseOne()
	.then(promiseTwo)
	.then(promiseThree)
```

<p>A popular promise library for nodejs is <a href="https://github.com/kriskowal/q">Q</a></p>

```javascript
//it allows you to do many awesome things like
var Q = require("q");


//chain promises
promiseOne()
	.then(promiseTwo)
	.then(promiseThree)
	.then(function() {
		//normal anonymous function
	})
	.fail(function(error) {
		//can handle error
	})
	.done() //like a finally
	
	
//Create promises from async methods
Q.ninvoke(obj, "asyncMethod", { param1: "parameter" })
	.then(function(resultFromAsyncMethod) {
		//do stuff
	});
	

//Use callbacks and promises together
function async(err, val){
	//this is a async callback
	var deferred = Q.defer();
	
	if (err) {
		deferred.reject(new Error(err));
	} else {
		deferred.resolve(val);
	}
	return deferred.promise;
}


//A value can be turned into a promise
Q({ x:5 })
 .then(function(val){
 	//val == 5
 });
```

<!-- 
#########################################
#
#				Context
#
#########################################
-->
<h3><a href="#table-of-content">4. Context</a></h3>

<h4>Hoisting</h4>
<p>Javascript hoists variable declarations</p>
```javascript
function blah() {
	var a = 1;
}

//is the same as

var a;
function sameBlah() {
	a = 1;
}

```

<p>It also hoists up function declarations</p>
```javascript
function outerFunc() {
	//How did it work?? I called innerFunc before initialization it!
	innerFunc();

	function innerFunc() {
		console.log(5);
	}
}

//is not the same as
function outerFunc() {
	x(); //won't work

	var x = function() {
		console.log(5);
	}
	
	x(); //will work
}

```

<h4>Bind method</h4>
```javascript
//instead of doing something like this
obj = {
...
	render: function () {
		var that = this; //have to do this every time...
		this.getAsyncData(function () {
			that.specialFunction();
			that.anotherSpecialFunction();
		});
	}
...
};


//We do
obj = {
...
	render: function () {
		this.getAsyncData(function () {
			this.specialFunction();
			this.anotherSpecialFunction();
		}.bind(this)); 
		//This bind means that when getAsyncData gets called
		//this === obj
	}
...
};

```


<!-- 
#########################################
#
#				SORTING
#
#########################################
-->
<h3><a href="#table-of-content">5. Sorting</a></h3>
<p>Sorting in javascript is easy</p>

```javascript
var sorted = [4, 3, 5, 2, 1].sort(function(a, b) {
	return a-b;
});
console.log(sorted) // [1, 2, 3, 4, 5]


var reversed = [4, 3, 5, 2, 1].sort(function(a, b) {
	return b-a;
});
console.log(reversed) // [5, 4, 3, 2, 1]
```


<!-- 
#########################################
#
#				Bit Manipulation
#
#########################################
-->
<h3><a href="#table-of-content">6. Bit Manipulation</a></h3>
<p>Bit operators</p>

<table>
	<!-- Header -->
	<tr>
		<td>Operation name</td>
		<td>Java symbol</td>
		<td>Example</td>
		<td>Result</td>
		<td>Explanation</td>
	</tr>
	<!-- Row 1 -->
	<tr>
		<td>AND</td>
		<td>&</td>
		<td>7 & 5</td>
		<td>5</td>
		<td>111 & 101 = 101</td>
	</tr>
	<!-- Row 2 -->
	<tr>
		<td>OR</td>
		<td>|</td>
		<td>8 | 3</td>
		<td>11</td>
		<td>1000 | 0011 = 1011</td>
	</tr>
	<!-- Row 3 -->
	<tr>
		<td>XOR</td>
		<td>^</td>
		<td>15 ^ 5</td>
		<td>10</td>
		<td>1111 ^ 0101 = 1010</td>
	</tr>
	<!-- Row 5 -->
	<tr>
		<td>Right Shift</td>
		<td>>></td>
		<td>7 >> 1</td>
		<td>3</td>
		<td>111 >> 1 = 011</td>
	</tr>
	<!-- Row 6 -->
	<tr>
		<td>Not</td>
		<td>~</td>
		<td>~0</td>
		<td>-1</td>
		<td>~000 = 111 which is 2's complement -1</td>
	</tr>
</table>


<!-- 
#########################################
#
#			Math
#
#########################################
-->
<h3><a href="#table-of-content">7. Math</a></h3>

```javascript
var x = Math.random() // float [0, 1[
Math.floor((Math.random() * 100) + 1); // int [1, 100[
```
