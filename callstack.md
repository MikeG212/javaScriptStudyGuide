Callstack

What is the call stack (execution stack)?
	records where in the program we are
	when you call a function in Javascript, the engine pushes it on to the call stack to keep track of what’s happening
	A LIFO data structure to temporarily store and manage function invocations(call)
	single threaded
	code execution is synchronous
	function invocation creates a stack Frame that occupies a temporary memory
What causes stack overflow?
	when a recursive function doesn’t have an exit point
How does the browser execute code?
	top to bottom

What is execution context?
	every time you run JavaScript in a browser, the engine goes through a series of steps
	an abstract concept of an environment where the Javascript code is evaluated and excecuted
	one of these steps is the creation of the global execution context

What is the javascript engine?
	It runs the code, top to bottom
	2 components: memory heap (where memory allocation happens) and call stack(where stack frames are as code executes)

What is the global execution context?
	code that is not inside any function is here
	creates a global object (window object) and sets the value of this equal to the global object
	there can only be one global execution context in a program

What happens in the global creation phase?
	create a global object
	creates an object called this
	set up memory space for variables and functions
	assigns variable declaration a default value of undefined while placing function declarations in memory (hoisting

What happens during the execution phase?
		code is finally executed line by line
		real values are assigned to the variables in memory

What is global memory?
	contains global variables and function declarations for later use

What is the local execution context?
	created when you call a function
	exists alongside the function
	has local memory
	in creation
		1) Create an arguments object (with args passed in)
		2) Create an object called this
		3) set up memory space for functions and variables
		4) variables default to undefined, function declarations put into memory

How is the execution context created?
	1) Creation phase
		lexical environment is created
			stores let and const bindings
			an object that holds the variable/ function names as keys, and values as values
			environment record- where variable and function declarations are stored inside lex env
				declarative environment record: stores variable and functional declarations
				object env rec: the lexical environment for global code, stores global binding object (window object in browsers)
			reference to the outer environment
				it can look at variables inside the outer environment that are not in the current lexical context
			binding
				what does this mean?
		variable environment is created
			stores var bindings only
	2) Execution phase
		code is finally executed line by line
		real values are assigned to the variables in memory



What is the regular event queue (callback queue)?
	FIFO queue
	once call stack is empty, we move the first item in event loop to call stack
	
	What is a starved event loop?
		when code from the current Call Stack prevents code in the event loop from being executed
What happens when we call setTimeOUt?
	We have a WebAPI with the browser to handle the code asynchronously
	then waits for the requested amount of time
	pushed on to the event loop (Not the call stack which could interfere with already executing code)
	when the call stack is empty, the we go to the event loop and take the first item (FIFO) and move it to call stack for execution

What is hoisting?
	during the creation phase, before they are declared, let and const are unitialized, vars are set to undefined
	so you can access var variables in the creation phase, before they are declared but you get a reference error if you access let and const before they are declared

What is a callback queue?

What does it mean that JavaScript is SingleThreaded?
	It has a single call stack, it can do one thing at a time

What is a stack frame?
	a single entry in the call stack

Why do we use asynchronous callbacks?
	execute heavy code without blocking the ui and making the browser unresponsive

Why is V8 a good engine?
	inlining
		optimization is replacing call site (line of code where function is called) with the body of the function
		allows for further optimizations
	hidden classes
		more efficient than looking up in the dictionary
	inline caching
	compiles to machine code
	garbage collection??
		

How do you optimize Methods?
	code that executes the same method repeatedly will run faster than code that executes many different methods only once (due to inline caching).
How do you optimize Arrays?
	 avoid sparse arrays where keys are not incremental numbers. Sparse arrays which don’t have every element inside them are a hash table. Elements in such arrays are more 		expensive to access. Also, try to avoid pre-allocating large arrays. It’s better to grow as you go. Finally, don’t delete elements in arrays. It makes the keys sparse.

What is scope?
	the current context of execution
	variables created inside a function are locally scoped

What happens if javaScript engine can’t find a variable local to the function’s execution context?
	looks at nearest parent, and keeps going up until we get to the global execution context

What are closures?
	closing over the variable environment of its parent
	we have a function nested inside another function
	so the inner function has access to the outer function through closure even after the outer function has been popped off the execution stack