	function spacify(str) {
  		return str.split('').join(' ');
	}
	
	'hello world'.spacify();
	
	String.prototype.spacify = function(){
  		return this.split('').join(' ');
	};


	function log(msg){
  		console.log(msg);
	}

	function log(){
		console.log.apply(console,arguments);
	};
	
	
		
	
	var User = {
 	count: 1,

  	getCount: function() {
    	return this.count;
  		}
	};

	console.log(User.getCount());
	//answer = 1

	var func = User.getCount;
		console.log(func());
	// answer = undefined due to scope issue, func 		is called on the window object
	
	// need binding:
	var func = User.getCount.bind(User);
	console.log(func());	
	
	
	$('.overlay').click(closeOverlay);
	// will close if children are clicked
	
	// stop bubbling
	$('.overlay').click(function(e){
  		if (e.target == e.currentTarget)
   		closeOverlay();
	});
	
	
Function declarations loads before any code is executed. While function expressions loads only when the interpreter reaches that line of code.

ex. Function Expression

	alert(foo()); 
	var foo = function() { return 5; } 

ex. Function Declaration - loads first!

	alert(foo()); 
	function foo() { return 5; } 
	
Apply lets you invoke the function with (unknown number of)arguments as an array; call requires the parameters be listed explicitly.

	theFunction.apply(valueForThis, arrayOfArgs)

	theFunction.call(valueForThis, arg1, arg2, ...)


In javascript, null is an object with no value and undefined is a type.

Triple equals === is used to compare the value AND type of two operands.

	// Declaring my main namespace
	var myapplication = myapplication || {};

	// Declaring modules usermodule
	// createMessage: only accessible inside this module
	// sayHello is a public method
	
	myapplication.usermodule = (function() {  
    	var createMessage = function(message) {
        	return "Hello! " + message;
    	}
		return {
      		sayHello: function(message) {
          		return createMessage(message);
       		}
      	}
	})();
	
	myapplication.usermodule.sayHello("This is my module");
	
Create JavaScript Classes:

Singleton - 

	var person = new function() {  
    	this.setName = function(name) {
        	this.name = name;
    	}
    	
    	this.sayHi = function() {
        	return "Hi, my name is " + this.name;
    	}
    }
   
Class literal notation - 

	var person = {  
    	name: "",
    	setName: function(name) {
        	this.name = name;
    	}
	}
	
Class function constructor - It's very important to notice that you have to use the keyword new when creating a new instance of that class 

	function Person(name) {  
    	this.name = name;
	}