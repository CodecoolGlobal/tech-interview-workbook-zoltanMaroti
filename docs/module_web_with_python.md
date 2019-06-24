# Web with Python questions

## Software design

### Clean code

#### Point out 5 suggestions, how to format an SQL query!
    ?
#### What layers can you name in a simple web application?
    The standard three layered architecture for Web Applications:
    
    Presentation Layer: The most external is the View Layer, it is the visible part of the application, which interacts with the user.
    The technologies usually involved in this layer on the web development context are mainly the markup that is processed by the browser (HTML/ XHTML/ ...), the style of the page (CSS) and client-side scripts (Javascript/ Flash/ ...).

    Business Layer: The layer in the middle is the Business Logic Layer, which serves as an intermediate between the View (or presentation)
    and the innermost Data Layer. The central layer of the model deals with the logic of the program. It receives data from the upper level and transforms it, using in the inner application logics. The tools used in this level are usually server-side scripts like PHP,ASP.NET Ruby or CGI. There is even a solution that uses server-side Javascript, called node.js.

    Data Layer: This last one is where all the data used by the application is stored. The deepest level in the layered architecture, the data layer deals with data retrieval from its sources. Most of the web applications currently active use relational databases, but now the market is seeing a change of paradigm in the form of the NoSQL.

    The benefits of using layered models in software development are in the way that it is easier to know exactly what each part of the application does. It makes easier to construct the application, to debug it, and to maintain and reuse the code.

      
### Error handling
#### What error can occur, when an array does not have an element on the requested index?
    In Python, IndexError exception is raised when a sequence reference is out of range.
    In Javascript, ReferenceError is raised when the script attempts to access an object property which doesn't exist ("undefined").
    Attempting to access an index outside of the array, returns the value undefined.

#### What is the “finally” block, and how would you use it?
    The try statement allows you to define a block of code to be tested for errors while it is being executed.
    The catch statement allows you to define a block of code to be executed, if an error occurs in the try block.
    The finally statement lets you execute code, after try and catch, regardless of the result.

    The catch and finally statements are both optional, but you need to use one of them (if not both) while using the try statement.

    Example:
    try {
        tryCode - Block of code to try
    }
    catch(err) {
        catchCode - Block of code to handle errors
    } 
    finally {
        finallyCode - Block of code to be executed regardless of the try / catch result
    }
#### Why should we catch special exception types?

### Security
#### What is SQL injection? How to protect an application against it?
    SQL injection is a code injection technique that might destroy your database.
    SQL injection is one of the most common web hacking techniques.
    SQL injection is the placement of malicious code in SQL statements, via web page input.
    It usually occurs when you ask a user for input, like their username/userid, and instead of a name/id, the user gives you an SQL statement that you will unknowingly run on your database.

    Example:
        txtUserId = getRequestString("UserId");
        txtSQL = "SELECT * FROM Users WHERE UserId = " + txtUserId;

    Protection against SQL injection:
        - Parameterized Statements: Input validation and parametrized queries including prepared statements. 
        - The developer must sanitize all input, not only web form inputs such as login forms.
        - Check that supplied fields like email addresses match a regular expression.
        - Ensure that numeric or alphanumeric fields do not contain symbol characters.
        - Reject (or strip) out whitespace and new line characters where they are not appropriate.
        - Turn off the visibility of database errors on your production sites.
        - Escaping Inputs: Ensure proper escaping of special string characters in input parameters.
        - Password Hashing: Applications should store user passwords as strong, one-way hashes, preferably salted. 
        - Third Party Authentication: Facebook, Twitter, and Google all provide mature OAuth APIs, which can be used to let users log into your website using their existing accounts on those systems. This saves you as an application developer from rolling your own authentication, and assures your users that their passwords are only stored in a single location.

#### What is XSS? How to protect an application against it?
    Cross-site scripting (XSS) is a security exploit which allows an attacker to inject into a website malicious client-side code. This code is executed by the victims and lets the attackers bypass access controls and impersonate users. The user's browser cannot detect the malicious script is untrustworthy, and so gives it access to any cookies, session tokens, or other sensitive site-specific information, or lets the malicious script rewrite the HTML content. Cross-site scripting attacks usually occur when 1) data enters a Web app through an untrusted source (most often a Web request) or 2) dynamic content is sent to a Web user without being validated for malicious content. The malicious content often includes JavaScript, but sometimes HTML, Flash, or any other code the browser can execute. The variety of attacks based on XSS is almost limitless, but they commonly include transmitting private data like cookies or other session information to the attacker, redirecting the victim to a webpage controlled by the attacker, or performing other malicious operations on the user's machine under the guise of the vulnerable site. XSS attacks can be put into three categories: stored (also called persistent), reflected (also called non-persistent), or DOM-based.

    How to protect yourself from XSS attacks?
    - Sanitize Data: it is simple to remove all values ​​from what is submitted and which are not of the desired type.
    - Validate the data: Validation is about making sure a value matches your expectation. Typically, you enable the user to resubmit the request once validation fails.
    - Escape the filters: script, alert, escaping invalid characters
    - X-XSS-Protection header: The HTTP X-XSS-Protection response header is a feature of Internet Explorer, Chrome and Safari that stops pages from loading when they detect reflected cross-site scripting (XSS) attacks. 
    - Content-Security-Policy: The HTTP Content-Security-Policy response header allows web site administrators to control resources the user agent is allowed to load for a given page. With a few exceptions, policies mostly involve specifying server origins and script endpoints. This helps guard against cross-site scripting attacks (XSS). For example, it disables the use of inline JavaScript ('unsafe-inline').
#### How to properly store passwords?
    The best way to protect passwords is to employ salted password hashing. Hash algorithms are one way functions. They turn any amount of data into a fixed-length "fingerprint" that cannot be reversed. Well-designed key stretching algorithms such as PBKDF2, bcrypt, and scrypt. DO NOT use: Fast cryptographic hash functions such as MD5, SHA1, SHA256, SHA512, RipeMD, WHIRLPOOL, SHA3, etc.

    The general workflow for account registration and authentication in a hash-based account system is as follows:
        1. The user creates an account.
        2. Their password is hashed and stored in the database. The plain-text (unencrypted) password is never written to the hard drive.
        3. When the user attempts to login, the hash of the password they entered is checked against the hash of their real password.
        4. If the hashes match, the user is granted access. If not, the user is told they entered invalid login credentials.
        5. Steps 3 and 4 repeat every time someone tries to login to their account.

    Only cryptographic hash functions may be used to implement password hashing. Hash functions like SHA256, SHA512, RipeMD, and WHIRLPOOL are cryptographic hash functions.

    Salt: We can randomize the hashes by appending or prepending a random string, called a salt, to the password before hashing. To check if a password is correct, we need the salt, so it is usually stored in the user account database along with the hash, or as part of the hash string itself.
#### What is HTTPS?
    HTTPS (HTTP Secure) is an encrypted version of the HTTP protocol. It usually uses SSL (Secure Sockets Layer) or TLS (Transport Layer Security) protocols to encrypt all communication between a client and a server. This secure connection allows clients to safely exchange sensitive data with a server, for example for banking activities or online shopping.
#### What is encryption and decryption?
#### What is hashing?
    Hashing is generating a value or values from a string of text using a mathematical function.
    Hash algorithms are one way functions. They turn any amount of data into a fixed-length "fingerprint" that cannot be reversed. Well-designed key stretching algorithms such as PBKDF2, bcrypt, and scrypt. DO NOT use for password hashing: Fast cryptographic hash functions such as MD5, SHA1, SHA256, SHA512, RipeMD, WHIRLPOOL, SHA3, etc. Only cryptographic hash functions may be used to implement password hashing. Hash functions like SHA256, SHA512, RipeMD, and WHIRLPOOL are cryptographic hash functions.
#### What is the difference between encryption and hashing? When would you use which?
#### What encryption methods do you know?
#### What hashing methods do you know?
    Well-designed key stretching algorithms such as PBKDF2, bcrypt, and scrypt. DO NOT use for password hashing: Fast cryptographic hash functions such as MD5, SHA1, SHA256, SHA512, RipeMD, WHIRLPOOL, SHA3, etc.
#### How/where would you store sensitive data (like db password, API key, ...) of your application?
    For public and private authentication keys I would use environmental variables. An environment variable is a KEY=value pair that is stored on the local system where your code/app is being run and is accessible from within your code. An environment variable is a variable whose value is set outside the program, typically through functionality built into the operating system or microservice. The primary use case for environment variables is to limit the need to modify and re-release an application due to changes in configuration data. You can also avoid (accidentally) committing (exposing) your private keys, passwords or other sensitive details(by hard-coding in them in your script) to GitHub by storing them as environment variables. This way we can use our keys and tokens in our local environment and be safe from getting these sensitive data exposed to others on Github.

## Computer science

### Algorithms

#### What is the difference between Stack and Queue data structure?
    Data structure: A data structure is a specialized format for organizing and storing data. General data structure types include the array, the file, the record, the table, the tree, and so on. Any data structure is designed to organize data to suit a specific purpose so that it can be accessed and worked with in appropriate ways. In computer programming, a data structure may be selected or designed to store data for the purpose of working on it with various algorithms.

    Stack is an abstract data type with a bounded(predefined) capacity. It is a simple data structure that allows adding and removing elements in a particular order. Every time an element is added, it goes on the top of the stack and the only element that can be removed is the element that is at the top of the stack, just like a pile of objects. 

    Basic features of Stack:
    - Stack is an ordered list of similar data type.
    - Stack is a LIFO (Last in First out) structure
    - push() function is used to insert new elements into the Stack and pop() function is used to remove an element from the stack. Both insertion and removal are allowed at only one end of Stack called Top.
    - Stack is said to be in Overflow state when it is completely full and is said to be in Underflow state if it is completely empty.

    Applications of Stack:
    - Parsing
    - Expression Conversion, to reverse a word

    Analysis of Stack Operations / time complexities for various operations:
    - Push Operation : O(1)
    - Pop Operation : O(1)
    - Search Operation : O(n)

    Queue is also an abstract data type or a linear data structure, just like stack data structure, in which the first element is inserted from one end called the REAR(also called tail), and the removal of existing element takes place from the other end called as FRONT(also called head). This makes queue as FIFO (First in First Out) data structure, which means that element inserted first will be removed first.
    Which is exactly how queue system works in real world. If you go to a ticket counter to buy movie tickets, and are first in the queue, then you will be the first one to get the tickets. Right? Same is the case with Queue data structure. Data inserted first, will leave the queue first. The process to add an element into queue is called Enqueue and the process of removal of an element from queue is called Dequeue.

    Basic features of Queue:
    - Like stack, queue is also an ordered list of elements of similar data types
    - Queue is a FIFO( First in First Out ) structure
    - Once a new element is inserted into the Queue, all the elements inserted before the new element in the queue must be removed
    - peek( ) function is oftenly used to return the value of first element without dequeuing it

    Applications of Queue:
    - Serving requests on a single shared resource, like a printer, CPU task scheduling etc
    - In real life scenario, Call Center phone systems uses Queues to hold people calling them in an order, until a service representative is free
    - Handling of interrupts in real-time systems. The interrupts are handled in the same order as they arrive i.e First come first served

    Complexity Analysis of Queue Operations:
    - Enqueue: O(1)
    - Dequeue: O(1)
    - Size: O(1)

#### What is BubbleSort? Describe the main logic of this sorting algorithm.
#### Explain the process of finding the maximum and minimum value in a list of numbers!
#### Explain the process of calculating the average value in an array of numbers!
#### What is Big O complexity? Explain time and space complexity!
#### Explain the process of calculating the average value in a linked list of numbers!

### Procedural
#### How the CASE condition works in SQL?
#### How the switch-case condition works in JavaScript?
#### How to achieve a switch-case-like structure in Python?
#### Explain variable scoping in Python!
#### What’s the difference between const and var in JavaScript?
#### How the list comprehension looks like in Python?
    List comprehensions provide a concise way to create lists. 
    It consists of brackets containing an expression followed by a for clause, then
    zero or more for or if clauses. The expressions can be anything, meaning you can
    put in all kinds of objects in lists. The result will be a new list resulting from
    evaluating the expression in the context of the for and if clauses which follow it.

    Syntax:
        [ expression for item in list if conditional ]

    This is equivalent to:
        for item in list:
            if conditional:
                expression
    
    Example:
        string = "Hello 12345 World"
        numbers = [number for number in string if number.isdigit()]

The list comprehension always returns a result list. 
#### How the “ternary expression” looks like in Python?
    Ternary operators are more commonly known as conditional expressions in Python. 
    These operators evaluate something based on a condition being true or not. 
    It allows to quickly test a condition instead of a multiline if statement.

    Syntax: 
        condition_if_true if condition else condition_if_false

    Example: 
        is_nice = True
        state = "nice" if is_nice else "not nice"
#### How the ternary expression looks like in JavaScript?
    The conditional (ternary) operator is frequently used as a shortcut for the if statement.
    You can shorten your if statements into one line of code with the conditional operator. 

    Syntax: condition ? exprIfTrue : exprIfFalse
        condition: An expression whose value is used as a condition.
        exprIfTrue: An expression which is evaluated if the condition evaluates to a truthy value.
        exprIfFalse: An expression which is executed if the condition is falsy.

    Example: person.driver = person.age >= 16 ? 'You can drive' : 'You can't drive';
#### How to import a function from another module in Python?
#### How to import a function from another module in JavaScript?

### Functional
#### What is recursion?
    ? Recursion in computer science is a method of solving a problem where the solution depends on solutions to smaller instances of the same problem (as opposed to iteration). The process in which a function calls itself directly or indirectly is called recursion and the corresponding function is called as recursive function.? A method or function that calls itself until some exit condition is reached.
#### Write a recursive function which calculates the Fibonacci numbers!
    In Python:
        def Fibonacci(n): 
            if n < 0: 
                print("Incorrect input") 
            # First Fibonacci number is 0 
            elif n == 1: 
                return 0
            # Second Fibonacci number is 1 
            elif n == 2: 
                return 1
            else: 
                return Fibonacci(n-1) + Fibonacci(n-2)
    
    In Javascript:
        function fibonacci(num) {
            if (num <= 1) return 1;
            return fibonacci(num - 1) + fibonacci(num - 2);
        }

#### How to store a function in a variable in Python?
#### List the ways of defining a callable logical unit in JavaScript!
#### What is an event listener? How to attach one?
#### How to trigger an event in JavaScript?
    In the browser most code is event-driven and writing interactive applications in JavaScript is often about waiting for and reacting to events, to alter the behavior of the browser in some way. Events occur when the page loads, when user interacts (clicks, hovers, changes) and myriad other times, and can be triggered manually too. To react to an event you listen for it and supply a function which will be called by the browser when the event occurs. This function is known as an event listener (aka event handler) which is a type of callback.
    When an event is happening we say the event has been triggered or fired. When js/we catch an event then we say event is handled => event handling. 

    How to define event listeners:
        let element = document.querySelectorAll('.btn')[0];
        element.addEventListener('click', clickHandler);

        function clickHandler(event) {
            console.log('button is clicked');
        }
#### What is a callback function? Tell some examples of its usage.
    CallBack Function is a function which passed into another function as an argument and is expected to execute after some kind of event. The purpose of the callback is to inform a class Sync/Async if some work in other class is done. This is very useful when working with Asynchronous tasks. Suppose we want to perform some routine tasks like perform some operation or display content after some clicking a button, or fetching data from internet. This is also used in event handling, as we get notified when a button clicked via callback function. 
#### What is a Python decorator? How does it work? Tell some examples of its usage.
#### What is the difference between synchronous and asynchronous execution?
    A synchronous operation blocks a process till the operation completes. An asynchronous operation is non-blocking and only initiates the operation. The caller could discover completion by some other mechanism. 
    Program execution in most high-level languages is usually very straightforward. Your program starts at the first line of source code and each line of code executed sequentially thereafter. Synchronous program execution is somewhat similar to the above. Your program is executed line by line, one line at a time. Each time a function is called, program execution waits until that function returns before continuing to the next line of code. This method of execution can have undesirable ramifications. Suppose a function is called to start a time consuming process. What if you want to stop the lengthy process? With synchronous execution, your program is “stuck,” waiting for the process to end, with no way out. Asynchronous execution avoids this bottleneck. You are essentially saying, “I know this function call is going to take a great deal of time, but my program doesn’t want to wait around while it executes.” 

    Code is a series of instructions, which are run one at a time in sequential order. During normal code execution, an instruction in one function might call out to another function. At this point, the instructions in the other function begin running and the original code is put aside for a moment. When the other function is done, it returns to our original code with some return value. Our original code resumes its execution and can do something with that return value. We refer to this as synchronous execution. However, some code operates outside the normal code execution. We refer to this as asynchronous execution, and it introduces the possibility for chaos into our otherwise orderly system. For example, we might be running some Javascript on our website that needs some data from a server. We call a function that sends a request to the server to get that data. This request is sent on our behalf, but it takes some time to get all the way there and back. In the meantime, the rest of our Javascript keeps running. At some point, the request will complete and will return our data. But there’s no way to get this data back to our original code. Instead of trying to get the data back to the original code to do something with it, we tell the asynchronous function what to do when it completes. In Javascript, this usually looks like passing a callback function as an argument.

    When you execute something synchronously, you wait for it to finish before moving on to another task. When you execute something asynchronously, you can move on to another task before it finishes.

    The difference between synchronous and asynchronous execution becomes important when dealing with many independent processes which are trying to coordinate their actions / behaviour by interacting with each other.

    Introduction:
    In programming, synchronous operations block instructions until the task is completed, while asynchronous operations can execute without blocking other operations. Asynchronous operations are generally completed by firing an event or by calling a provided callback function.

    Javascript has a:
    - Callstack
    - WebAPI
    - Event Loop
    - Callback Queue

    The event loop, the web APIs and the message queue/task queue are not part of the JavaScript engine, it’s a part of browser’s JavaScript runtime environment or Nodejs JavaScript runtime environment (in case of Nodejs). 

    The Event Loop
    The job of the Event loop is to look into the call stack and determine if the call stack is empty or not. If the call stack is empty, it looks into the message queue to see if there’s any pending callback waiting to be executed.

    DOM Events
    The Message queue also contains the callbacks from the DOM events such as click events and keyboard events. In case of DOM events, the event listener sits in the web APIs environment waiting for a certain event (click event in this case) to happen, and when that event happens, then the callback function is placed in the message queue waiting to be executed. Again the event loop checks if the call stack is empty and pushes the event callback to the stack if it’s empty and the callback is executed.

    The Callstack is the immediate work your program will do.
    WebAPI's are methods available from environments where JavaScript is run. In browsers, the window and its methods are apart of the WebAPI. When the WebAPI completes, it puts the callback on the Callback Queue. The Event Loop waits for the Callstack to complete the loaded work. Once the Event Loop notices the Callstack is clear it will add work to the Callstack from the Callback Queue. A callback executes once it is added to the Callstack. 

    Synchronous Operations:
    Synchronous Operations that run block the next operation until it completes. Blocking operations may not always seem like an issue because computers are fast. Making synchronous calls to resources can lead to long response times locking up the UI until the resource responds. Making requests to your own services like a database can have the same effect. A common webpage will have many requests to make under unique circumstances, and as a developer, you'll want those requests to start as soon as possible but still allow the rest of the page to load what it can to enable the requests. This is when asynchronous operations become powerful. 

    Asynchronous Operations:
    Asynchronous Operations happen independently from the main program flow. A common use for asynchronous code is querying a database and using the result. Passing in a callback is a way to interact with the response or error. While the database loads and responds to the request, the rest of the page or other resources cannot load. 

    Promises and Asynchronous Operations:
    Promises are another way to interact with asynchronous code. A Promise represents the work that is happening asynchronously. When the Promise resolves the result can be caught as an error, or used in a then method. then returns a Promise, this means then is chainable returning another Promise to the next then. 
    ES6 introduced the concept of job queue/micro-task queue which is used by Promises in JavaScript. The difference between the message queue and the job queue is that the job queue has a higher priority than the message queue, which means that promise jobs inside the job queue/ micro-task queue will be executed before the callbacks inside the message queue.

    Asynchronous Operations happen independently from the main program flow. A common use for asynchronous code is querying a database and using the result. Passing in a callback is a way to interact with the response or error. 

    Understanding Synchronous vs Asynchronous:
    Before understanding AJAX, let’s understand classic web application model and ajax web application model first.

    Synchronous (Classic Web-Application Model):
    A synchronous request blocks the client until operation completes i.e. browser is unresponsive. In such case, javascript engine of the browser is blocked. 

    Asynchronous (AJAX Web-Application Model):
    An asynchronous request doesn’t block the client i.e. browser is responsive. At that time, user can perform another operations also. In such case, javascript engine of the browser is not blocked. 

    Synchronous:
    If an API call is synchronous, it means that code execution will block (or wait) for the API call to return before continuing. This means that until a response is returned by the API, your application will not execute any further, which could be perceived by the user as latency or performance lag in your app. 

    Asynchronous:
    Asynchronous calls do not block (or wait) for the API call to return from the server. Execution continues on in your program, and when the call returns from the server, a "callback" function is executed. The important point is that program execution will continue, and asynchronously, the callback function will be called once program execution completes.

    SYNCHRONOUS Tasks:
    JavaScript is single-threaded, that means only one statement is executed at a time. As the JS engine processes our script line by line, it uses this single Call-Stack to keep track of codes that are supposed to run in their respective order. Like what a stack does, a data structure which records lines of executable instructions and executes them in a LIFO manner. That’s how a script of synchronous tasks gets handled by our browser without involving anything other than the “legendary” Call Stack. But things get a little bit complex when JS engine encounters an asynchronous task.

    ASYNCHRONOUS Tasks:
    What does asynchronous means? Unlike synchronous, asynchronous is a behaviour. We need this behaviour when things are slow. Synchronous executions of code may seem straightforward but can be slow. Tasks like image processing can be slow, file operations can be really slow, making network request and waiting for response is definitely slow, making huge calculations like over a 100 million for-loop iteration is somewhat slow. So such slow things in Call stack results in “Blocking”. When call stack is blocked, the browser prevents user’s interrupts and other code statements from executing until the blocking statement is executed and the call stack is freed. Hence Asynchronous callbacks are used to handle such situations. So this is where Event Loop, Callback Queue and Web APIs (in browser) kicks in. 

    Synchronous versus Asynchronous Execution:
    Using callbacks is a very common way to implement asynchronous operations. When a callback function is specified, the CRUD operation is non-blocking which means that the next statement is called immediately even though the result from the database has not yet been fetched. Only when the result is available is the callback called. 

    Synchronous Code:
    As mentioned above, synchronous code is somewhat straightforward and as a novice programmer, it is the code we are most familiar with. The synchronous program starts with the first line, and each line of code is executed afterward. Even when encountering a function, the program execution waits until that specific function returns before continuing to the next line of code. There is no way to execute another function while waiting for other code to execute. 

    Asynchronous Code:
    As you may expect, asynchronous code performs much differently. With an async function, we are able to say “Since I know this function call may take some time to execute, let the function finish in the background. ” This behavior helps us avoid the bottleneck of having to wait for a function call to finish before continuing to the rest of the program. 

    How Async Works:
    For starters, a good rule of thumb is to remember that synchronous code will always run first. There are two parts in the Javascript engine, one that reads code and adds operations to queue, and another processes the queue. When an asynchronous operation is encountered, the operation is put in the queue with a callback to be run when the operation completes. The program continues to run synchronous code and once finished with synchronous operations, will check the queue for any other operations that need to be complete. At this point, the callback comes in handy as it is executed with its intended functionality. Asynchronous code can prove helpful and necessary when you don’t know how long a certain operation will take (ajax request, API call, query to database).

    JavaScript is Synchronous
    Spoiler: at its base, JavaScript is a synchronous, blocking, single-threaded language. That just means that only one operation can be in progress at a time. That’s not the entire story, though! When you hear folks say that JavaScript is an asynchronous language, what they mean is that you can manipulate JavaScript to behave in an asynchronous way. It’s not baked in, but it’s possible! 

    Asynchronous Callbacks:
    We use asynchronous callbacks to make our code non-blocking.
    The earliest and most straightforward solution to being stuck in the synchronous world was asynchronous callbacks (think setTimeout()).
    Let’s use a database request as an example: asynchronous callbacks allow you to invoke a callback function which sends a database request (and any other nested callbacks) off to your app, where it waits for the response from the database, freeing up the rest of your code to continue running. Once the database request completes, the results (and any other nested code) are sent to the queue, and then processed through the event loop. 

    Promises:
    In order to deal with callback hell, libraries like Bluebird or Q allowed programmers to clean up their syntax and write code that operated asynchronously but looked synchronous. This resulted in code that was easier to read and faster to run. With a promise, instead of bundling all dependencies into one code block and sending the entire thing off to the browser, we’re able to separate them out. We can send the asynchronous callback (Function C) to the browser, and use .then() to hold all other dependencies. This allows us to code in a more modular, readable way, while still gaining the benefits of asynchronous programming.

    Async/Await:
    Promises were fantastic — so fantastic, in fact, that ES6 brought them into the language as a standard. Using promises still left asynchronous code looking and feeling slightly wonky, so we now have beautiful and stunning Async/Await to help us out! 
    Async/Await allows you to:
    - Continue using promises
    - Write asynchronous code that looks and feels synchronous
    - Cleans up your syntax and makes your code more human-readable

    Execution Context
    An Execution Context is an abstract concept of an environment where the JavaScript code is evaluated and executed. Whenever any code is run in JavaScript, it’s run inside an execution context. The function code executes inside the function execution context, and the global code executes inside the global execution context. Each function has its own execution context.

    Call Stack
    The call stack as its name implies is a stack with a LIFO (Last in, First out) structure, which is used to store all the execution context created during the code execution. JavaScript has a single call stack because it’s a single-threaded programming language. The call stack has a LIFO structure which means that the items can be added or removed from the top of the stack only.

    Asynchronicity in Programming Languages
    Computers are asynchronous by design. Asynchronous means that things can happen independently of the main program flow.
    JavaScript is synchronous by default and is single threaded. This means that code cannot create new threads and run in parallel.
    But JavaScript was born inside the browser, its main job, in the beginning, was to respond to user actions, like onClick, onMouseOver, onChange, onSubmit and so on. How could it do this with a synchronous programming model? The answer was in its environment. The browser provides a way to do it by providing a set of APIs that can handle this kind of functionality.

    Callbacks
    You can’t know when a user is going to click a button, so what you do is, you define an event handler for the click event. This event handler accepts a function, which will be called when the event is triggered. This is the so-called callback.
    A callback is a simple function that’s passed as a value to another function, and will only be executed when the event happens. We can do this because JavaScript has first-class functions, which can be assigned to variables and passed around to other functions (called higher-order functions)

    The problem with callbacks
    Callbacks are great for simple cases! However every callback adds a level of nesting, and when you have lots of callbacks, the code starts to be complicated very quickly

    Alternatives to callbacks
    Starting with ES6, JavaScript introduced several features that help us with asynchronous code that do not involve using callbacks:
    - Promises (ES2015)
    - Async/Await (ES2017): They make the code look like it’s synchronous, but it’s asynchronous and non-blocking behind the scenes.

## Programming languages

### SQL

#### How can you connect your application to a database server? What are the possible ways?
#### When do you use the DISTINCT keyword in SQL?
    Inside a table, a column often contains many duplicate values; and sometimes you only want to list the different (distinct) values.
    The SELECT DISTINCT statement is used to return only distinct (different) values.

    SELECT DISTINCT Syntax:
        SELECT DISTINCT column1, column2, ...
        FROM table_name;

#### What are aggregate functions in SQL? Give 3 examples.
    An aggregate function performs a calculation on a set of values, and returns a single value. Except for COUNT, aggregate functions ignore null values. Aggregate functions are often used with the GROUP BY clause of the SELECT statement. Aggregate functions allow us to easily produce summarized data from our database. 

    - COUNT: counts how many rows are in a particular column.
    - SUM: adds together all the values in a particular column.
    - MIN: and MAX return the lowest and highest values in a particular column, respectively.
    - AVG: calculates the average of a group of selected values.

#### What kind of JOIN types do you know in SQL? Could you give examples?
    A JOIN clause is used to combine rows from two or more tables, based on a related column between them.
    Different Types of SQL JOINs:
    - (INNER) JOIN: Returns records that have matching values in both tables
    - LEFT (OUTER) JOIN: Returns all records from the left table, and the matched records from the right table
    - RIGHT (OUTER) JOIN: Returns all records from the right table, and the matched records from the left table
    - FULL (OUTER) JOIN: Returns all records when there is a match in either left or right table

#### What are the constraints in sql?
    SQL constraints are used to specify rules for data in a table. Constraints are used to limit the type of data that can go into a table. This ensures the accuracy and reliability of the data in the table. If there is any violation between the constraint and the data action, the action is aborted. Constraints can be column level or table level. Column level constraints apply to a column, and table level constraints apply to the whole table. Constraints can be specified when the table is created with the CREATE TABLE statement, or after the table is created with the ALTER TABLE statement. 

    The following constraints are commonly used in SQL:
        - NOT NULL - Ensures that a column cannot have a NULL value
        - UNIQUE - Ensures that all values in a column are different
        - PRIMARY KEY - A combination of a NOT NULL and UNIQUE. Uniquely identifies each row in a table
        - FOREIGN KEY - Uniquely identifies a row/record in another table
        - CHECK - Ensures that all values in a column satisfies a specific condition
        - DEFAULT - Sets a default value for a column when no value is specified

    Syntax:
        CREATE TABLE table_name (
        column1 datatype constraint,
        column2 datatype constraint,
        column3 datatype constraint,
        ....
    );


#### What is a cursor in SQL? Why would you use one?
    A cursor is a temporary work area created in the system memory when a SQL statement is executed. A cursor contains information on a select statement and the rows of data accessed by it. This temporary work area is used to store the data retrieved from the database, and manipulate this data. A cursor can hold more than one row, but can process only one row at a time. The set of rows the cursor holds is called the active set. A database cursor can be thought of as a pointer to a specific row within a query result.  The pointer can be moved from one row to the next.  Depending on the type of cursor, you may be even able to move it to the previous row.

#### What are database indexes? When to use?
#### What are database transactions? When to use?
#### What kind of database relations do you know? How to define them?
    One-to-One: A row in table A can have only one matching row in table B, and vice versa. This is not a common relationship type.

    One-to-Many (or Many-to-One): In this type of relationship, a row in table A can have many matching rows in table B, but a row in table B can have only one matching row in table A. This is the most common relationship type.

    Many-to-Many: a row in table A can have many matching rows in table B, and vice versa. A many-to-many relationship could be thought of as two one-to-many relationships, linked by an intermediary table. The intermediary table is typically referred to as a “junction table” (also as a “cross-reference table”). This table is used to link the other two tables together. It does this by having two fields that reference the primary key of each of the other two tables.

    Self Referencing Relationships: This is used when a table needs to have a relationship with itself.
#### You have a table with an “address” field which contains data like “3525, Miskolc, Régiposta 9.” (postcode, city, street name and address). How would you query all records related to Miskolc?
#### How would you keep track of what kind of data has changed after an UPDATE or DELETE operation in a table?

### HTML & CSS

#### What’s the difference between XML, XHTML and HTML?
    HTML is the HyperText Markup Language, which is designed to create structured documents and provide for semantic meaning behind the documents. HTML5 is the next version of the HTML specification.

    XML is the Extensible Markup Language, which provides rules for creating, structuring, and encoding documents. You often see XML being used to store data and to allow for communication between applications. It's programming language-agnostic - all of the major programming languages provide mechanisms for reading and writing XML documents, either as part of the core or in external libraries.

    XHTML is an XML-based HTML. It serves the same function as HTML, but with the same rules as XML documents. These rules deal with the structure of the markup.
#### How to include a JavaScript file in a webpage?
    The <script> tag is used to define a client-side script (JavaScript).
    The <script> element either contains scripting statements, or it points to an external script file through the src attribute.
    Attributes:
        async, defer, src, type, charset

    The <script> tag can be placed in the <head> section of your HTML, in the <body> section, or after the </body> close tag, depending on when you want the JavaScript to load. Generally, JavaScript code can go inside of the document <head> section in order to keep them contained and out of the main content of your HTML document. However, if your script needs to run at a certain point within a page’s layout, you should put it at the point where it should be called, usually within the <body> section.

    Example:
        <script src="myscripts.js"></script>
    
    Note: There are several ways an external script can be executed:
    - If async="async": The script is executed asynchronously with the rest of the page (the script will be executed while the page continues the parsing)
    - If async is not present and defer="defer": The script is executed when the page has finished parsing
    - If neither async or defer is present: The script is fetched and executed immediately, before the browser continues parsing the page

    Non-blocking script tags can be placed just about anywhere:
        <script src="script.js" async></script>
        <script src="script.js" defer></script>
        <script src="script.js" async defer></script>
    
    The current state-of-the-art is to put scripts in the <head> tag and use the async or defer attributes. This allows your scripts to be downloaded asap without blocking your browser.

    <noscript>: element for users that have disabled scripts in their browser, or have a browser that doesn't support client-side scripting.


#### How to include a CSS file in a webpage?
#### How to select an element using its id in CSS?
#### How to select elements using their class in CSS?
#### How to select elements which have the ‘alpha’ and ‘beta’ classes in CSS?
#### How to select all list items in all ordered lists on the page in CSS?
#### How to select elements using their attributes in CSS?
#### What are UX and UI?
#### Please list some points that an application should fulfill to have good UX.
#### What is XML, XSLT, DTD?
#### What is the difference between HTML and XML?

### Javascript

#### What is javascript?
    JavaScript (JS) is a lightweight interpreted programming language with first-class functions (when functions in that language are treated like any other variable). While it is most well-known as the scripting language for Web pages, many non-browser environments also use it, such as Node.js, Apache CouchDB and Adobe Acrobat. JavaScript is a prototype-based, multi-paradigm, dynamic language, supporting object-oriented, imperative, and declarative (e.g. functional programming) styles. JavaScript runs on the client side of the web, which can be used to design / program how the web pages behave on the occurrence of an event. Another common application for JavaScript is as a (Web) server side scripting language. Node.js is a popular example of this.
    
    The standard for JavaScript is ECMAScript. This specification is updated from time to time to contain modern features. After some time different javascript engines (for example in the browsers) implement these new features. ECMAScript 2015 (ES2015 or it was called ES6 some time ago) was a larger change. Current edition: 9th Edition - ECMAScript 2018.

#### When to use AJAX? Bring examples of its usage.
    Ajax is not a technology but group of inter-related technologies. 
    AJAX technologies includes:
    - HTML/XHTML and CSS: These technologies are used for displaying content and style. It is mainly used for presentation.
    - DOM: It is used for dynamic display and interaction with data.
    - XML or JSON: For carrying data to and from server. JSON (Javascript Object Notation) is like XML but short and faster than XML.
    - XMLHttpRequest: For asynchronous communication between client and server
    - JavaScript: It is used to bring above technologies together.

    An object of XMLHttpRequest is used for asynchronous communication between client and server. It performs following operations:
    - Sends data from the client in the background
    - Receives the data from the server
    - Updates the webpage without reloading it.
    If you use an asynchronous XMLHttpRequest, you receive a callback when the data has been received. This lets the browser continue to work as normal while your request is being handled. Use XMLHttpRequest (XHR) objects to interact with servers. You can retrieve data from a URL without having to do a full page refresh. This enables a Web page to update just part of a page without disrupting what the user is doing. XMLHttpRequest is used heavily in AJAX programming. Despite its name, XMLHttpRequest can be used to retrieve any type of data, not just XML.

    AJAX stands for Asynchronous JavaScript And XML. In a nutshell, it is the use of the XMLHttpRequest object to communicate with servers. It can send and receive information in various formats, including JSON, XML, HTML, and text files. AJAX’s most appealing characteristic is its "asynchronous" nature, which means it can communicate with the server, exchange data, and update the page without having to refresh the page.
    The two major features of AJAX allow you to do the following:
    - Make requests to the server without reloading the page
    - Receive and work with data from the server

    Properties of XMLHttpRequest object:
    - onReadyStateChange: It is called whenever readystate attribute changes.
    - readyState: 	represents the state of the request. It ranges from 0 to 4.
    - reponseText: returns response as text.
    - responseXML: returns response as XML

    Methods of XMLHttpRequest object:
    - open(method, URL, async): opens the request specifying get or post method and url, specifies asynchronous or not.
    - send(): sends get request.
    - setRequestHeader(header,value): it adds request headers.

    How AJAX works?
    AJAX communicates with the server using XMLHttpRequest object.
    1. User sends a request from the UI and a javascript call goes to XMLHttpRequest object.
    2. HTTP Request is sent to the server by XMLHttpRequest object.
    3. Server interacts with the database using JSP, PHP, Servlet, ASP.net etc.
    4. Data is retrieved.
    5. Server sends XML data or JSON data to the XMLHttpRequest callback function.
    6. HTML and CSS data is displayed on the browser.

#### What is DOM and how to manipulate it from Javascript?
    The DOM is an API that allows access to and modification of the current document. It allows manipulation of document Node and Element.
    The Document Object Model (DOM) connects web pages to scripts or programming languages by representing the structure of a document—such as the HTML representing a web page—in memory. The DOM is an object-oriented representation of the web page, which can be modified with a scripting language such as JavaScript. The DOM represents a document with a logical tree. Each branch of the tree ends in a node, and each node contains objects. DOM methods allow programmatic access to the tree; with them you can change the document's structure, style, or content. Nodes can also have event handlers attached to them; once an event is triggered, the event handlers get executed. DOM is a WEB API. 

    Most important DOM interfaces: ChildNode, Document, Event, Node, NodeList, ParentNode, Window...
#### What are events and how/why to use them in Javascript?
    Events are responsible for interaction of JavaScript with HTML web pages. The general definition of event is any act can occur by someone. In the web development, the definition of events is also same. Events can be subscribed by listeners that occurs only when the particular event can be fired. HTML events are "things" that happen to HTML elements. When JavaScript is used in HTML pages, JavaScript can "react" on these events. An HTML event can be something the browser does, or something a user does.
    Here are some examples of HTML events:
        - An HTML web page has finished loading
        - An HTML input field was changed
        - An HTML button was clicked

    Often, when events happen, you may want to do something. JavaScript lets you execute code when events are detected.

    DOM Events are sent to notify code of interesting things that have taken place. Each event is represented by an object which is based on the Event interface, and may have additional custom fields and/or functions used to get additional information about what happened. Events can represent everything from basic user interactions to automated notifications of things happening in the rendering model.
    The Event interface represents an event which takes place in the DOM. An event can be triggered by the user action e.g. clicking mouse button or tapping keyboard, or generated by APIs to represent the progress of an asynchronous task. There are many types of events, some of which use other interfaces based on the main Event interface. Event itself contains the properties and methods which are common to all events. Many DOM elements can be set up to accept (or "listen" for) these events, and execute code in response to process (or "handle") them. Event-handlers are usually connected (or "attached") to various HTML elements (such as <button>, <div>, <span>, etc.) using EventTarget.addEventListener(). The Event() constructor creates a new Event.


#### What is event bubbling/capturing? How would you use it?
    Event Bubbling and Event Capturing is the foundation of event handler and event delegation in JavaScript.
    Event bubbling and capturing are two ways of event propagation in the HTML DOM API, when an event occurs in an element inside another element, and both elements have registered a handle for that event. The event propagation mode determines in which order the elements receive the event. Event Bubbling is the event starts from the deepest element or target element to its parents, then all its ancestors which are on the way to bottom to top. Event Capturing is the event starts from top element to target element. 

    With bubbling, the event is first captured and handled by the innermost element and then propagated to outer elements.
    With capturing, the event is first captured by the outermost element and propagated to the inner elements.

    We can use the addEventListener(type, listener, useCapture) to register event handlers for in either bubbling (default) or capturing mode. To use the capturing model pass the third argument as true.

    Full View of Event Flow :
    Every event flow has three phase:

        - Event Capturing
        - Event Target
        - Event Bubbling.

#### What is JSON and how do we use it?
    JSON is a string format which is very similar to the one that javascript uses to define objects. Browsers has a built in JSON object to convert a variable to JSON string (JSON.stringify function) and to convert a JSON string back to a variable (JSON.parse function). Data is either converted to or from JSON, using methods called stringify and parse respectively.
    JSON.stringify converts an object into a JSON string. The string can then be converted back to a JavaScript object using JSON.parse.
    JSON — JavaScript Object Notation — is a set of text formatting rules for storing and transferring data in a machine and human readable way. It looks a lot like the object literal syntax of JavaScript, and it is from there JSON originates.
    JSON is used to transfer information - between your browser to a server, or saved in text files for retrieval later - because it’s simply text. That means you can’t store complex data like a function, but you can store arrays, objects containing simple data, strings and numbers. JSON is taking over from XML as the data-transfer format of the web, and many new web APIs are written exclusively serving JSON, which can mean that you can be using AJAX technology to grab JSON.
    It is useful to:
        - send/receive data: between js code and a server / between two servers
        - store data: in localStorage or sessionStorage which can save only strings
    
    Example:
        { "name": "Yoda", age: 894, "lightsaber" : { "color": "green" } }



## Software engineering

### Version control

#### What type of branching strategy would you use?
#### What would you do if you find a bug on the production code (master branch)?
#### How can you move changes from one branch to another in GIT?
#### How does a VCS help with code reviews?
#### What is your favorite git command? Why?
#### What does remote/local mean in Git? 

### DevOps

#### Why is it good to use a package manager software?
#### Why is it good to use a virtual environment for a project?

### Networks

#### What kind of HTTP status codes do you know?
    All HTTP response status codes are separated into five classes (or categories). 
    The first digit of the status code defines the class of response. 
        1xx (Informational): The request was received, continuing process
        2xx (Successful): The request was successfully received, understood and accepted
        3xx (Redirection): Further action needs to be taken in order to complete the request
        4xx (Client Error): The request contains bad syntax or cannot be fulfilled
        5xx (Server Error): The server failed to fulfill an apparently valid request
    
    Most important status codes:
        200 OK: Standard response for successful HTTP requests.
        301 Moved Permanently: This and all future requests should be directed to the given URI.
        400 Bad Request: The server cannot or will not process the request due to an apparent client error. 
        403 Forbidden: The request was valid, but the server is refusing action. The user might not have the necessary permissions.
        404 Not Found: The requested resource could not be found but may be available in the future.
        405 Method Not Allowed: A request method is not supported for the requested resource.
        408 Request Timeout: The server timed out waiting for the request.
        500 Internal Server Error: A generic error message, given when an unexpected condition was encountered. 
        501 Not Implemented: The server either does not recognize the request method, or it lacks the ability to fulfil the request.
#### What is a API?
    An API (Application Programming Interface) is a set of features and rules that exist inside a software program (the application) enabling interaction with it through software - as opposed to a human user interface. The API can be seen as a simple contract (the interface) between the application offering it and other items, such as third party software or hardware. 
    An application programming interface (API) is a set of subroutine definitions, communication protocols, and tools for building software. In general terms, it is a set of clearly defined methods of communication among various components. A good API makes it easier to develop a computer program by providing all the building blocks. In Web development, an API is generally a set of code features (e.g. methods, properties, events, and URLs) that a developer can use in their apps for interacting with components of a user's web browser, or other software/hardware on the user's computer, or third party websites and services. 
    When writing code for the Web, there are a great many Web APIs available. Below is a list of all the APIs and interfaces (object types) that you may be able to use while developing your Web app or site. Web APIs are typically used with JavaScript, although this doesn't always have to be the case.

    Web APIs: DOM, Fetch API, Web Storage API...
#### What is REST API?
#### What is JSON? When to use?
    JSON (JavaScript Object Notation) is a lightweight data-interchange format. It is easy for humans to read and write. 
    JSON is a text format that is completely language independent. JSON is a syntax for storing and exchanging data.
    When exchanging data between a browser and a server, the data can only be text.
    JSON is text, and we can convert any JavaScript object into JSON, and send JSON to the server.
    We can also convert any JSON received from the server into JavaScript objects.
    This way we can work with the data as JavaScript objects, with no complicated parsing and translations.
    JSON uses JavaScript syntax, but the JSON format is text only.
    Text can be read and used as a data format by any programming language.

    JSON is built on two structures: 
        A collection of name/value pairs. In various languages, this is realized as an object, dictionary, hash table. 
        An ordered list of values. In most languages, this is realized as an array, vector, list, or sequence.
    
    Methods:
        JSON.parse(): Parse a string as JSON, optionally transform the produced value and its properties, and return the value.
        JSON.stringify(): Return a JSON string corresponding to the specified value.

    Example:
        var myObj = {name: "John", age: 31, city: "New York"};
        var myJSON = JSON.stringify(myObj);

        var myJSON = '{"name":"John", "age":31, "city":"New York"}';
        var myObj = JSON.parse(myJSON);
#### What is TCP/IP? What layers does it define, what are they responsible for?
#### What’s the difference between TCP and UDP?
#### How does an HTTP Request look like? What are the most relevant HTTP header fields?
#### How does an HTTP Response look like? What are the most relevant HTTP header fields?
#### What is DNS? How does it work?
    Domain Name Servers are like an address book for websites. When you type a web address in your browser, 
    the browser looks at the DNS to find the website's real address before it can retrieve the website. 
    The browser needs to find out which server the website lives on, so it can send HTTP messages to the right place. 
    The Domain Name System (DNS) is a hierarchical and decentralized naming system for computers, services, or other 
    resources connected to the Internet or a private network. Web browsers interact through Internet Protocol (IP) addresses. 
    DNS translates domain names to IP addresses so browsers can load Internet resources. Each device connected to the Internet 
    has a unique IP address which other machines use to find the device. The process of DNS resolution involves converting 
    a hostname (such as www.example.com) into a computer-friendly IP address (such as 192.168.1.1). A DNS name server is 
    a server that stores the DNS records for a domain; a DNS name server responds with answers to queries against its database.

#### What is a web server?
#### Explain the client-server architecture.
    Computers connected to the web are called clients and servers. 
    Clients are the typical web user's internet-connected devices (for example, your computer connected to your Wi-Fi, 
    or your phone connected to your mobile network) and web-accessing software available on those devices 
    (usually a web browser like Firefox or Chrome).
    Servers are computers that store webpages, sites, or apps. When a client device wants to access a webpage, 
    a copy of the webpage is downloaded from the server onto the client machine to be displayed in the user's web browser.
    Client–server model is a distributed application structure that partitions tasks or workloads between the providers 
    of a resource or service, called servers, and service requesters, called clients. A server host runs one or more server 
    programs which share their resources with clients. A client does not share any of its resources, but requests a server's 
    content or service function. Clients therefore initiate communication sessions with servers which await incoming requests. 
    Examples of computer applications that use the client–server model are Email, network printing, and the World Wide Web.

        1. The browser goes to the DNS server, and finds the real address of the server that the website lives on.
        2. The browser sends an HTTP request message to the server, asking it to send a copy of the website to the client. 
           This message, and all other data sent between the client and the server, is sent across your internet connection using TCP/IP.
        3. If the server approves the client's request, the server sends the client a "200 OK" message and then starts sending 
           the website's files to the browser as a series of small chunks called data packets.
        4. The browser assembles the small chunks into a complete website and displays it to you.

#### What would you use a session for?
#### What would you use a cookie for?

## Software Development Methodologies

#### What kind of software development methodologies do you know? What are the main features of these?
#### What are the SCRUM roles?
    Scrum has three roles: product owner, scrum master and the development team members. 

    Product Owner: The person with the product vision. 
        Responsibilities:
            - Managing the scrum backlog 
            - Release management
            - Stakeholder management

    Scrum Master: The scrum expert who helps the team build the product according to the scrum framework

    Development Team: The team members who execute the work
#### What are the SCRUM ceremonies?
#### What are the SCRUM artifacts?
#### What is the main goal of a retrospective meeting?
#### Explain, when would you recommend to use the waterfall methodology?
