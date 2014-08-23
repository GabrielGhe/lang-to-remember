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
  <li><a href="#7-probability">Probability</a></li>
  <li><a href="#8-files">Files</a></li>
  <li><a href="#9-sockets">Sockets</a></li>
  <li><a href="#10-regex">Regex</a></li>
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

  .toLowerCase()    	// "a string  "
  .toUpperCase()    	// "A STRING  "
  
  //takes a delimiter
  .split("")        	// ['A', 's', 't', 'r', 'i', 'n', 'g', ' ', ' ']
  
  //with split ^
  .join()		// "A string  "
  
  //takes startPos endPos
  .substring(2, 4)  	// "st"
  
  .indexOf("str")   	// 2
  
  .trim()           	// "A string"
  
  .replace("string", "blah"); // "A blah  "
  
  .match(/a str.*/i)	// "A string  "
  
  //takes in a position
  .charAt(0)		// "A"
  .charCodeAt(0)	// 65
  
  //takes in base
  4.toString(2)		// 110
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
	//but I called it before initialization!
	innerFunc();

	function innerFunc() {
		console.log(5);
	}
}

```

<h4>Bind method</h4>
```javascript
//instead of doing something like this
obj = {
...
	render: function () {
		var that = this;
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
<p>Here is a table of comparison sorting algorithms and their time complexity</p>


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
#			Probability
#
#########################################
-->
<h3><a href="#table-of-content">7. Probability</a></h3>
<p>There are 50 people in a room, what’s the probability that two people have the same birthday? (Ignoring the fact of leap year, i.e., 365 day every year)</p>

```javascript
public static double caculateProbability(int n){
	double x = 1; 
 
	for(int i=0; i<n; i++){
		x *=  (365.0-i)/365.0;
	}
 
	double pro = Math.round((1-x) * 100);
	return pro/100;
}
```

<!-- 
#########################################
#
#			Files
#
#########################################
-->
<h3><a href="#table-of-content">8. Files</a></h3>

<p>Writing to a file.</p>
```java
//java7... appends to file
try(Formatter f = new Formatter("myText.txt")) {
	f.format("this is output text", null);
} catch(IOException ioe){
	ioe.printStackTrace();
}

//older java
Formatter f;
try {
	f = new Formatter("myText.txt");
	f.format("this is output text", null);
} catch(IOException ioe){
	ioe.printStackTrace();
} finally {
	f.close();
}
```

<p>Reading from a file</p>
```java
//read all the lines in a file
try(Scanner scan = new Scanner(new File("myText.txt") ) ){
	ArrayList<String> x = new ArrayList<String>();
	while(scan.hasNext()){
		x.add(scan.nextLine());
	}
} catch (FileNotFoundException e) {
	e.printStackTrace();
}
```


<!-- 
#########################################
#
#			Files
#
#########################################
-->
<h3><a href="#table-of-content">9. Sockets</a></h3>

<p>Server that listens for a connection, writes the date and closes connection</p>
```java
//Server
ServerSocket listener = new ServerSocket(9090);
try {
    while (true) {
        Socket socket = listener.accept();
        try {
            ObjectOutputStream out =
                new ObjectOutputStream(socket.getOutputStream());
            out.writeObject("Hi there");
        } finally {
            socket.close();
        }
    }
}
finally {
    listener.close();
}


//Client the data is sent through serialization
//to send objects, they must be serializable
Socket s = new Socket(serverAddress, 9090);
try{
	ObjectInputStream input = new ObjectInputStream(s.getInputStream());
	String answer = (String)input.readObject();
} catch(ClassCastException cce){
	cce.printStackTrace();
} finally {
	s.close();
}

//On mac, you can open a terminal and write "nc localhost 9090" to connect to server socket
```


<!-- 
#########################################
#
#			Regex
#
#########################################
-->
<h3><a href="#table-of-content">10. Regex</a></h3>
<p>
The full documentation can be found here 
<a href="http://docs.oracle.com/javase/7/docs/api/java/util/regex/Pattern.html">
Docs
</a>
</p>

```java

//Long way, that can be reused
Pattern p = Pattern.compile("a*b");
Matcher m = p.matcher("aaaab");
boolean b = m.matches();

//shorthand
boolean b = Pattern.matches("a*b", "aaaaab");
```

<p><b>Regular-expression constructs</b></p>
<table>
	<tr>
		<td>[abc]</td>
		<td>a, b, or c (simple class)</td>
	</tr>
	
	<!-- 2 -->
	<tr>
		<td>
			[^abc]
		</td>
		<td>
			Any character except a, b, or c (negation)
		</td>
	</tr>
	
	<!-- 3 -->
	<tr>
		<td>
			[a-zA-Z]
		</td>
		<td>
			a through z or A through Z, inclusive (range)
		</td>
	</tr>
	
	<!-- 4 -->
	<tr>
		<td>
			[a-d[m-p]]
		</td>
		<td>
			a through d, or m through p: [a-dm-p] (union)
		</td>
	</tr>
	
	<!-- 5 -->
	<tr>
		<td>
			[a-z&&[def]]
		</td>
		<td>
			d, e, or f (intersection)
		</td>
	</tr>
	
	<!-- 6 -->
	<tr>
		<td>
			[a-z&&[^bc]]
		</td>
		<td>
			a through z, except for b and c: [ad-z] (subtraction)
		</td>
	</tr>
	
	<!-- 7 -->
	<tr>
		<td>
			[a-z&&[^m-p]]
		</td>
		<td>
			a through z, and not m through p: [a-lq-z](subtraction)
		</td>
	</tr>
</table>

<p><b>Predefined character classes</b></p>
<table>
	<!-- 1 -->
	<tr>
		<td>
			.
		</td>
		<td>
			Any character (may or may not match line terminators)
		</td>
	</tr>
	
	<!-- 2 -->
	<tr>
		<td>
			\d
		</td>
		<td>
			A digit: [0-9]
		</td>
	</tr>
	
	<!-- 3 -->
	<tr>
		<td>
			\D
		</td>
		<td>
			A non-digit: [^0-9]
		</td>
	</tr>
	
	<!-- 4 -->
	<tr>
		<td>
			\s
		</td>
		<td>
			A whitespace character: [ \t\n\x0B\f\r]
		</td>
	</tr>
	
	<!-- 5 -->
	<tr>
		<td>
			\S
		</td>
		<td>
			A non-whitespace character: [^\s]
		</td>
	</tr>
	
	<!-- 6 -->
	<tr>
		<td>
			\w
		</td>
		<td>
			A word character: [a-zA-Z_0-9]
		</td>
	</tr>
	
	<!-- 7 -->
	<tr>
		<td>
			\W
		</td>
		<td>
			A non-word character: [^\w]
		</td>
	</tr>
</table>


<p><b>Greedy quantifiers</b></p>

<table>
	<!-- 1 -->
	<tr>
		<td>
			X?
		</td>
		<td>
			X, once or not at all
		</td>
	</tr>
	
	<!-- 2 -->
	<tr>
		<td>
			X*
		</td>
		<td>
			X, zero or more times
		</td>
	</tr>
	
	<!-- 3 -->
	<tr>
		<td>
			X+
		</td>
		<td>
			X, one or more times
		</td>
	</tr>
	
	<!-- 4 -->
	<tr>
		<td>
			X{n}
		</td>
		<td>
			X, exactly n times
		</td>
	</tr>
	
	<!-- 5 -->
	<tr>
		<td>
			X{n,}
		</td>
		<td>
			X, at least n times
		</td>
	</tr>
	
	<!-- 6 -->
	<tr>
		<td>
			X{n,m}
		</td>
		<td>
			X, at least n but not more than m times
		</td>
	</tr>
</table>





