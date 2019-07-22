# Web with Python questions

## Software design

### Clean code

#### Point out 5 suggestions, how to format an SQL query!
- Use upper case: SQL keywords are not case sensitive. However, it is common practice to write them in upper case.
- Use indentation: put every clause into a new line, and split lines if they would become too long otherwise.
- Naming: always choose shorter, pronouncable, meaningful names, conveying specific information.
- Use a collective name or, less ideally, a plural form. For example staff and employees.
- Never give a table the same name as one of its columns and vice versa.
- Columns: Always use the singular name.
- Functions or stored procedures should start with a verb that tells what it does
- Give consistent, meaningful aliases to joined tables in a query
- Avoid descriptive prefixes or Hungarian notation
- Ensure the name is unique and does not exist as a reserved keyword.
- Use underscores: words are usually either separated by an underscore.
- Comments: Include comments in SQL code where necessary. /* ... */ opening and closing.
- Avoid CamelCase: it is difficult to scan quickly.

#### What layers can you name in a simple web application?
The benefits of using layered models in software development are that it is easier to know exactly what each part of the application does. It makes easier to construct the application, to debug it, and to maintain and reuse the code.
The standard three layered architecture for Web Applications:

**Presentation / View Layer:** The most external layer, it is the visible part of the application, which interacts with the user. The technologies usually involved in this layer on the web development context are mainly the markup that is processed by the browser (HTML/ XHTML/ ...), 
the style of the page (CSS) and client-side scripts (Javascript/ Flash/ ...).

**Business Layer:** The layer in the middle is the Business Logic Layer, which serves as an intermediate between the View (or presentation) and the innermost Data Layer. The central layer of the model deals with the logic of the program. 
It receives data from the upper level and transforms it, using in the inner application logics. The tools used in this level are usually server-side scripts like PHP,ASP.NET Ruby or CGI. There is even a solution that uses server-side Javascript, called node.js.

**Data Layer:** This last one is where all the data used by the application is stored. The deepest level in the layered architecture, the data layer deals with data retrieval from its sources. Most of the web applications currently active use relational databases, 
but now the market is seeing a change of paradigm in the form of the NoSQL.

### Error handling
#### What error can occur, when an array does not have an element on the requested index?
In Python, IndexError exception is raised when a sequence reference is out of range.
In Javascript, ReferenceError is raised when the script attempts to access an object property which doesn't exist ("undefined").
Attempting to access an index outside of the array, returns the value undefined.

#### What is the “finally” block, and how would you use it?
**The try statement** allows you to define a block of code to be tested for errors while it is being executed.<br />
**The catch statement** allows you to define a block of code to be executed, if an error occurs in the try block.<br />
**The finally statement** lets you execute code, after try and catch, regardless of the result.<br />

The catch and finally statements are both optional, but you need to use one of them (if not both) while using the try statement.

**Example:**
```javascript
try {
    // Block of code to try
}
catch(err) {
    // Block of code to handle errors
} 
finally {
    // Block of code to be executed regardless of the try / catch result
}
```

#### Why should we catch special exception types?
Never try to implement a catch-all handler for the base exception type. Catching all exceptions wholesale is never a good idea in any language, whether it’s globally on a base application level, or in a small method used only once. It is bad practice to catch generic Exception because it will obfuscate whatever really happened, damaging both maintainability and extensibility. We can waste a huge amount of time debugging what the actual problem is, when it could be as simple as a syntax error. This is not a good programming practice as it will catch all exceptions and handle every case in the same way. We can specify which exceptions an except clause will catch. It is only good practice to catch a specific exception if it can actually be handled by the catch block.

### Security
#### What is SQL injection? How to protect an application against it?
SQL injection is one of the most common web hacking techniques. SQL injection is the placement of malicious code in SQL statements, via web page input that might destroy the database. It usually occurs when you ask a user for input, like their username / userid, and instead of a name / id, the user gives you an SQL statement that you will unknowingly run on your database.

**Example:**
```sql
txtUserId = getRequestString("UserId");
txtSQL = "SELECT * FROM Users WHERE UserId = " + txtUserId;
```

**Protection against SQL injection:**
- Input validation and parametrized queries including prepared statements. 
- The developer must sanitize all input, not only web form inputs such as login forms.
- Check that supplied fields like email addresses match a regular expression.
- Ensure that numeric or alphanumeric fields do not contain symbol characters.
- Reject (or strip) out whitespace and new line characters where they are not appropriate.
- Turn off the visibility of database errors on your production sites.
- Escaping Inputs: Ensure proper escaping of special string characters in input parameters.
- Third Party Authentication: Facebook, Twitter, and Google all provide mature OAuth APIs, which can be used to let users log into your website using their existing accounts on those systems. This saves you as an application developer from rolling your own authentication, and assures your users that their passwords are only stored in a single location.

#### What is XSS? How to protect an application against it?
XSS (Cross-site scripting) is a security exploit which allows an attacker to inject malicious client-side code into a website. This code is executed and lets the attackers bypass access controls and impersonate users, redirecting the victim to a webpage controlled by the attacker. The user's browser cannot detect the malicious script is untrustworthy, and gives it access to any cookies, session tokens, or other sensitive site-specific information, or lets the malicious script rewrite the HTML DOM content. The malicious content often includes JavaScript, but sometimes HTML, Flash, or any other code the browser can execute. Cross-site scripting attacks usually occur when:
- Data enters a Web app through an untrusted source (most often a Web request)
- Dynamic content is sent to a Web user without being validated for malicious content. 

**How to protect yourself from XSS attacks?**
- Sanitize Data: it is simple to remove all values ​​from what is submitted and which are not of the desired type.
- Validate the data: Validation is about making sure a value matches your expectation.
- Escape the filters: script, alert, escaping invalid characters
- X-XSS-Protection header: The HTTP X-XSS-Protection response header is a feature of Internet Explorer, Chrome and Safari that stops pages from loading when they detect reflected cross-site scripting (XSS) attacks. 
- Content-Security-Policy: The HTTP Content-Security-Policy response header allows web site administrators to control resources the user agent is allowed to load for a given page. This helps guard against cross-site scripting attacks (XSS). For example, it disables the use of inline JavaScript ('unsafe-inline').

#### How to properly store passwords?
The best way to protect passwords is to employ salted password hashing. <br />
**Salt:** We can randomize the hashes by appending or prepending a random string, called a salt, to the password before hashing. To check if a password is correct, we need the salt, so it is usually stored in the user account database along with the hash, or as part of the hash string itself.

The general workflow for account registration and authentication in a hash-based account system is the following:
1. The user creates an account.
2. Their password is hashed and the hash is stored in the database. The plain-text (unencrypted) password is never written to the hard drive.
3. When the user attempts to login, the hash of the password they entered is checked against the hash of their real password.
4. If the hashes match, the user is granted access. If not, the user is told they entered invalid login credentials.

#### What is HTTPS?
HTTPS (HTTP Secure) is an encrypted version of the HTTP protocol. It usually uses SSL (Secure Sockets Layer) or TLS (Transport Layer Security protocols to encrypt all communication between a client and a server. This secure connection allows clients to safely exchange sensitive data with a server, for example for banking activities or online shopping.

#### What is encryption and decryption?
Encryption is the practice of scrambling information in a way that only someone with a corresponding key can unscramble and read it. Encryption is a two-way function. When you encrypt something, you’re doing so with the intention of decrypting it later.
To encrypt data you use something called a cipher (which is an algorithm) to encrypt and decrypt information.

#### What is hashing?
Hashing is generating a value or values from a string of text using a mathematical function. Hash algorithms are one way functions. They turn any amount of data into a fixed-length "fingerprint" that cannot be reversed. Well-designed key stretching algorithms such as PBKDF2, bcrypt, and scrypt. 

#### What is the difference between encryption and hashing? When would you use which?
Encryption is a two-way function. When you encrypt something, you’re doing so with the intention of decrypting it later.
Hashing is a one-way function where data is mapped to a fixed-length value. Hashing is primarily used for authentication.
The key is that encryption is reversible. Hashing is not.

#### What encryption methods do you know?
AES, RSA, ECC, PGP, Blowfish

#### What hashing methods do you know?
Well-designed key stretching algorithms such as PBKDF2, bcrypt, and scrypt. **DO NOT** use for password hashing: Fast cryptographic hash functions such as MD5, SHA1, SHA256, SHA512, RipeMD, WHIRLPOOL, SHA3, etc.

#### How/where would you store sensitive data (like db password, API key, ...) of your application?
For public and private authentication keys I would use environmental variables. An environment variable is a KEY=value pair which is set outside the program and stored on the local system where your code/app is being run and is accessible from within your code. You can also avoid (accidentally) committing (exposing) your private keys, passwords or other sensitive details (by hard-coding in them in your script) to GitHub by storing them as environment variables. This way we can use our keys and tokens in our local environment and be safe from getting these sensitive data exposed to others on Github.

## Computer science

### Algorithms

#### What is the difference between Stack and Queue data structure?
**Data structure:** A data structure is a specialized format for organizing and storing data to suit a specific purpose so that it can be accessed and worked with in appropriate ways with various algorithms. General data structure types include the array, the file, the record, the table, the tree, and so on. 

**Stack** is an abstract data type with a predefined capacity. It is a simple data structure that allows adding and removing elements in a particular order. Every time an element is added, it goes on the top of the stack and the only element that can be removed is the element that is at the top of the stack, just like a pile of objects. 

**Basic features of Stack:**
- Stack is an ordered list of similar data type
- Stack is a LIFO (Last in First out) structure
- push() function is used to insert new elements into the Stack and pop() function is used to remove an element from the stack. Both insertion and removal are allowed at only one end of Stack called Top.
- Stack is said to be in Overflow state when it is completely full and is said to be in Underflow state if it is completely empty.

**Applications of Stack:**
- Parsing, Memory management, Search
- Expression Conversion, to reverse a word
- used in "undo" mechanism in text editor

**Queue** is also an abstract data type or a linear data structure, just like stack data structure. The first element is inserted from one end called the REAR (also called tail), and the removal of existing element takes place from the other end called as FRONT (also called head. This makes queue as FIFO (First in First Out) data structure, which means that element inserted first will be removed first. The process to add an element into queue is called Enqueue and the process of removal of an element from queue is called Dequeue.
Real-world example: If you go to a ticket counter to buy movie tickets, and are first in the queue, then you will be the first one to get the tickets.

**Basic features of Queue:**
- Like stack, queue is also an ordered list of elements of similar data types
- Queue is a FIFO (First in First Out) structure
- Once a new element is inserted into the Queue, all the elements inserted before the new element in the queue must be removed

**Applications of Queue:**
- Serving requests on a single shared resource, like a printer, CPU task scheduling, Disk Scheduling
- In real life scenario, Call Center phone systems uses Queues to hold people calling them in an order, until a service representative is free
- Handling of interrupts in real-time systems. The interrupts are handled in the same order as they arrive i.e First come first served

#### What is BubbleSort? Describe the main logic of this sorting algorithm.
BubbleSort is the simplest sorting algorithm that works by repeatedly swapping the adjacent elements if they are in wrong order.

**Example:**<br />
First Pass:<br />
( **5 1** 4 2 8 ) –> ( **1 5** 4 2 8 ), Here, algorithm compares the first two elements, and swaps since 5 > 1.<br />
( 1 **5 4** 2 8 ) –>  ( 1 **4 5** 2 8 ), Swap since 5 > 4<br />
( 1 4 **5 2** 8 ) –>  ( 1 4 **2 5** 8 ), Swap since 5 > 2<br />
( 1 4 2 **5 8** ) –> ( 1 4 2 **5 8** ), Now, since these elements are already in order (8 > 5), algorithm does not swap them.<br />

Second Pass:<br />
( **1 4** 2 5 8 ) –> ( **1 4** 2 5 8 )<br />
( 1 **4 2** 5 8 ) –> ( 1 **2 4** 5 8 ), Swap since 4 > 2<br />
( 1 2 **4 5** 8 ) –> ( 1 2 **4 5** 8 )<br />
( 1 2 4 **5 8** ) –>  ( 1 2 4 **5 8** )<br />

Now, the array is already sorted, but our algorithm does not know if it is completed. The algorithm needs one whole pass without any swap to know it is sorted.

```python
def bubblesort(array):
    # we minus 1 because we are always comparing the current value with the next value
    length_of_array = len(array) - 1
    # number of rounds will be the total length - 1, for array with length 5, we will do 4 rounds: 0 and 1, 1 and 2, 2 and 3, 3 and 4.
    for i in range(length_of_array):
        # at each round, we compare the current j with the next value
        for j in range(length_of_array - i):
            # only swap their positions if left value < right value as we aim to move all the small values to the back
            if array[j] < array[j + 1]:
                array[j], array[j + 1] = array[j + 1], array[j]

    return array


array = [2, 1, 5, 4, 3]
print bubblesort(array)
```

#### Explain the process of finding the maximum and minimum value in a list of numbers!
**METHOD 1 (Simple Linear Search)**<br />
Initialize values of min and max as minimum and maximum of the first two elements respectively.  Starting from 3rd, compare each element with max and min, and change max and min accordingly (i.e., if the element is smaller than min then change min, else if the element is greater than max then change max, else ignore the element).

**METHOD 2 (Tournament Method)**<br />
Divide the array into two parts and compare the maximums and minimums of the the two parts to get the maximum and the minimum of the the whole array.

#### Explain the process of calculating the average value in an array of numbers!
Average is the sum of array elements divided by the number of elements.
```python
def average( a , n ): 
    # Find sum of array element 
    sum = 0
    for i in range(n): 
        sum += a[i] 
      
    return sum/n; 
  
# Driver code 
arr = [10, 2, 3, 4, 5, 6, 7, 8, 9] 
n = len(arr) 
print(average(arr, n)) 
```

#### What is Big O complexity? Explain time and space complexity!
An algorithm is a set of instructions designed to perform a specific task.

Big O notation is used in Computer Science to describe the performance or complexity of an algorithm. Big O specifically describes the worst-case scenario, and can be used to describe the execution time required or the space used (e.g. in memory or on disk) by an algorithm.

**Complexity:**<br />
When we talk about complexity we express how the growth of some input/condition affects the consumption of some resource. This resource can be either time or memory. In this regard complexity is a function.
- its output depends on it's input
- it represents a rate of growth

**Time complexity:**<br />
**O(1):** O(1) describes an algorithm that will always execute in the same time (or space) regardless of the size of the input data set.<br />
**O(N):** O(N) describes an algorithm whose performance will grow linearly and in direct proportion to the size of the input data set.<br /> 
**O(N2):** O(N2) represents an algorithm whose performance is directly proportional to the square of the size of the input data set. This is common with algorithms that involve nested iterations over the data set. Deeper nested iterations will result in O(N3), O(N4) etc.<br />
**O(2N):** O(2N) denotes an algorithm whose growth doubles with each additon to the input data set. The growth curve of an O(2N) function is exponential - starting off very shallow, then rising meteorically. An example of an O(2N) function is the recursive calculation of Fibonacci numbers.<br />
**O(log N):**Binary search. This type of algorithm is described as O(log N). The iterative halving of data sets described in the binary search example produces a growth curve that peaks at the beginning and slowly flattens out as the size of the data sets increase e.g. an input data set containing 10 items takes one second to complete, a data set containing 100 items takes two seconds, and a data set containing 1000 items will take three seconds.

**Memory/space complexity:**<br />
Space complexity is the amount of memory used by the algorithm. We try to answer these two questions:
- At any given time how many elements are in collections or any other way in the memory
- What is the memory footprint of one element in the collection(s) (for example an integer is usually calculated as 4bytes)

#### Explain the process of calculating the average value in a linked list of numbers!
**Linked list** is a linear collection of data elements, whose order is not given by their physical placement in memory. Instead, each element points to the next. It is a data structure consisting of a collection of nodes which together represent a sequence. In its most basic form, each node contains: data, and a reference (in other words, a link) to the next node in the sequence. This structure allows for efficient insertion or removal of elements from any position in the sequence during iteration.

Like arrays, Linked List is a linear data structure. Unlike arrays, linked list elements are not stored at a contiguous location; the elements are linked using pointers. Linked lists are among the simplest and most common data structures. They can be used to implement several other common abstract data types, including lists, stacks, queues, associative arrays, and S-expressions, though it is not uncommon to implement those data structures directly without using a linked list as the basis.

**Advantages over arrays:**<br />
1) Dynamic size
2) Ease of insertion/deletion

Key Differences Between Array and Linked List:
- An array is the data structure that contains a collection of similar type data elements whereas the Linked list is considered as non-primitive data structure contains a collection of unordered linked elements known as nodes.
- In the array the elements belong to indexes, i.e., if you want to get into the fourth element you have to write the variable name with its index or location within the square bracket.
- In a linked list though, you have to start from the head and work your way through until you get to the fourth element.
- Accessing an element in an array is fast, while Linked list takes linear time, so it is quite a bit slower. 
- Operations like insertion and deletion in arrays consume a lot of time. On the other hand, the performance of these operations in Linked lists is fast.
- Arrays are of fixed size. In contrast, Linked lists are dynamic and flexible and can expand and contract its size.

**Program to find average of all nodes in a Linked List:**<br />
**Iterative Solution:**
1. Initialise a pointer 'ptr' with the head of the linked list and a 'sum' variable with 0.
2. Start traversing the linked list using a loop until all the nodes get traversed.
3. Add the value of current node to the sum i.e. sum += ptr -> data.
4. Increment the pointer to the next node of linked list i.e. ptr = ptr ->next.
5. Divide sum by total number of node and Return the average.

### Procedural
#### How the CASE condition works in SQL?
The CASE statement goes through conditions and returns a value when the first condition is met (like an IF-THEN-ELSE statement). So, once a condition is true, it will stop reading and return the result. If no conditions are true, it returns the value in the ELSE clause.
If there is no ELSE part and no conditions are true, it returns NULL.

**Syntax:**
```sql
CASE
    WHEN condition1 THEN result1
    WHEN condition2 THEN result2
    WHEN conditionN THEN resultN
    ELSE result
END;
```

**Example:**
```sql
SELECT OrderID, Quantity,
CASE
    WHEN Quantity > 30 THEN "The quantity is greater than 30"
    WHEN Quantity = 30 THEN "The quantity is 30"
    ELSE "The quantity is under 30"
END AS QuantityText
FROM OrderDetails;
```

#### How the switch-case condition works in JavaScript?
The switch statement executes a block of code depending on different cases, matching the expression's value to a case clause (using the strict comparison, ===), and executes statements associated with that case, as well as statements in cases that follow the matching case.
If no matching case clause is found, the program looks for the optional **default** clause, and if found, transfers control to that clause, executing the associated statements. If no default clause is found, the program continues execution at the statement following the end of switch. The optional **break** statement associated with each case label ensures that the program breaks out of switch once the matched statement is executed and continues execution at the statement following switch. If break is omitted, the program continues execution at the next statement in the switch statement.

**Syntax:**
```javascript
switch (expression) {
  case value1:
    //Statements executed when the
    //result of expression matches value1
    [break;]
  case value2:
    //Statements executed when the
    //result of expression matches value2
    [break;]
  ...
  case valueN:
    //Statements executed when the
    //result of expression matches valueN
    [break;]
  [default:
    //Statements executed when none of
    //the values match the value of the expression
    [break;]]
}
```

**Example:**
```javascript
switch (expr) {
  case 'Oranges':
    console.log('Oranges are $0.59 a pound.');
    break;
  case 'Apples':
    console.log('Apples are $0.32 a pound.');
    break;
  case 'Mangoes':
  case 'Papayas':
    console.log('Mangoes and papayas are $2.79 a pound.');
    break;
  default:
    console.log('Sorry, we are out of ' + expr + '.');
}
```

#### How to achieve a switch-case-like structure in Python?
Switch-case statement is a powerful programming feature that allows you control the flow of your program based on the value of a variable or an expression. You can use it to execute different blocks of code, depending on the variable value during runtime. Although popular languages like Java and PHP have in-built switch statement, you may be surprised to know that Python language doesn’t have one. As such, you may be tempted to use a series of if-else-if blocks, using an if condition for each case of your switch statement. However, because of the jump table, a switch statement is much faster than an if-else-if ladder. Instead of evaluating each condition sequentially, it only has to look up the evaluated variable/expression once and directly jump to the appropriate branch of code to execute it.

**How to implement switch statement in Python:**<br />
The Pythonic way to implement switch statement is to use the powerful dictionary mappings, also known as associative arrays, that provide simple one-to-one key-value mappings.
```python
def switch_demo(argument):
    switcher = {
        1: "January",
        2: "February",
        3: "March",
        4: "April",
        5: "May",
        6: "June",
        7: "July",
        8: "August",
        9: "September",
        10: "October",
        11: "November",
        12: "December"
    }
    print(switcher.get(argument, "Invalid month"))
```
If you'd like defaults you could use the dictionary get(key[, default])
```python
def f(x):
    return {
        'a': 1,
        'b': 2
    }.get(x, 9)    # 9 is default if x not found
```
#### Explain variable scoping in Python!
Not all variables are accessible from all parts of our program, and not all variables exist for the same amount of time. Where a variable is accessible and how long it exists depend on how it is defined. We call the part of a program where a variable is accessible its scope, and the duration for which the variable exists its lifetime.

**Global:**
A variable which is defined in the main body of a file is called a global variable. It will be visible throughout the file, and also inside any file which imports that file. Global variables can have unintended consequences because of their wide-ranging effects – that is why we should almost never use them. Only objects which are intended to be used globally, like functions and classes, should be put in the global namespace.

**Local:**
A variable which is defined inside a function is local to that function. It is accessible from the point at which it is defined until the end of the function, and exists for as long as the function is executing. The parameter names in the function definition behave like local variables, but they contain the values that we pass into the function when we call it. When we use the assignment operator (=) inside a function, its default behaviour is to create a new local variable – unless a variable with the same name is already defined in the local scope.

**Scope resolution via LEGB rule:**
In Python, the LEGB rule is used to decide the order in which the namespaces are to be searched for scope resolution. 
- Local (L): Defined inside function/class
- Enclosed (E): Defined inside enclosing functions (Nested function concept)
- Global (G): Defined at the uppermost level
- Built-in (B): Reserved names in Python builtin modules

#### What’s the difference between const and var in JavaScript?
**Const:**
Constants are block-scoped, much like variables defined using the let statement. The value of a constant cannot change through reassignment, and it can't be redeclared.

This declaration creates a constant whose scope can be either global or local to the block in which it is declared. Global constants do not become properties of the window object, unlike var variables. An initializer for a constant is required; that is, you must specify its value in the same statement in which it's declared (which makes sense, given that it can't be changed later). The const declaration creates a read-only reference to a value. It does not mean the value it holds is immutable, just that the variable identifier cannot be reassigned. A constant cannot share its name with a function or a variable in the same scope.

**Var:**
The var statement declares a variable, optionally initializing it to a value. Var declarations, wherever they occur, are processed before any code is executed. This is called hoisting. The scope of a variable declared with var is its current execution context, which is either the enclosing function or, for variables declared outside any function, global. If you re-declare a JavaScript variable, it will not lose its value. Assigning a value to an undeclared variable implicitly creates it as a global variable (it becomes a property of the global object) when the assignment is executed. The differences between declared and undeclared variables are:
- Declared variables are constrained in the execution context in which they are declared. Undeclared variables are always global.
- Declared variables are created before any code is executed. Undeclared variables do not exist until the code assigning to them is executed.
It is recommended to always declare variables, regardless of whether they are in a function or global scope.

**var hoisting:**
Because variable declarations (and declarations in general) are processed before any code is executed, declaring a variable anywhere in the code is equivalent to declaring it at the top. This also means that a variable can appear to be used before it's declared. This behavior is called "hoisting", as it appears that the variable declaration is moved to the top of the function or global code. For that reason, it is recommended to always declare variables at the top of their scope (the top of global code and the top of function code) so it's clear which variables are function scoped (local) and which are resolved on the scope chain.

**Let:**
The let statement declares a block scope local variable, optionally initializing it to a value.
let allows you to declare variables that are limited to a scope of a block statement, or expression on which it is used, unlike the var keyword, which defines a variable globally, or locally to an entire function regardless of block scope. The other difference between var and let is that the latter is initialized to value only when parser evaluates it. Just like const the let does not create properties of the window object when declared globally. Variables declared by let have their scope in the block for which they are defined, as well as in any contained sub-blocks. In this way, let works very much like var. The main difference is that the scope of a var variable is the entire enclosing function. 

**let hoisting:**
let bindings are created at the top of the (block) scope containing the declaration, commonly referred to as "hoisting". Unlike variables declared with var, which will start with the value undefined, let variables are not initialized until their definition is evaluated. Accessing the variable before the initialization results in a ReferenceError. The variable is in a "temporal dead zone" from the start of the block until the initialization is processed.

#### How the list comprehension looks like in Python?
List comprehensions provide a concise way to create lists. It consists of brackets containing an expression followed by a for clause, then zero or more for or if clauses. The expressions can be anything, meaning you can put in all kinds of objects in lists. The result will be a new list resulting from evaluating the expression in the context of the for and if clauses which follow it. The list comprehension always returns a result list.

**Syntax:**
```
[ expression for item in list if conditional ]
```

This is equivalent to:
```python
for item in list:
    if conditional:
        expression
```
    
**Example:**
```python
string = "Hello 12345 World"
numbers = [number for number in string if number.isdigit()]
```

#### How the “ternary expression” looks like in Python?
Ternary operators are more commonly known as conditional expressions in Python. These operators evaluate something based on a condition being true or not. It allows to quickly test a condition instead of a multiline if statement.

**Syntax:**
condition_if_true if condition else condition_if_false

**Example:** 
```python
is_nice = True
state = "nice" if is_nice else "not nice"
```

#### How the ternary expression looks like in JavaScript?
The conditional (ternary) operator is frequently used as a shortcut for the if statement. You can shorten your if statements into one line of code with the conditional operator. 

**Syntax:** 
condition ? exprIfTrue : exprIfFalse
- condition: An expression whose value is used as a condition.
- exprIfTrue: An expression which is evaluated if the condition evaluates to a truthy value.
- exprIfFalse: An expression which is executed if the condition is falsy.

**Example:** 
```javascript
person.driver = person.age >= 16 ? "You can drive" : "You can't drive";
```

#### How to import a function from another module in Python?
Python code in one module gains access to the code in another module by the process of importing it. The import statement combines two operations; it searches for the named module, then it binds the results of that search to a name in the local scope. When a module is first imported, Python searches for the module and if found, it creates a module object, initializing it. If the named module cannot be found, a ModuleNotFoundError is raised. 

**Example**
```python
from file import function
```

#### How to import a function from another module in JavaScript?
**1. Exporting module features**<br />
The first thing you need to do to get access to module features is export them. This is done using the export statement.
You can export functions, var, let, const, and classes. They need to be top-level items; you can't use export inside a function.

**Example:** 
```javascript
export const name = 'Zoli';

export function greetings() {
  return 'Hello World'
```

**2. Importing features into your script**<br />
Once you've exported some features out of your module, you need to import them into your script to be able to use them. Once you've imported the features into your script, you can use them just like they were defined inside the same file. The simplest way to do this is as follows:

```javascript
import { name, draw } from './modules/main.js';
```

**3. Applying the module to your HTML**<br />
Now we just need to apply the main.js module to our HTML page. 
First of all, you need to include type="module" in the script element, to declare this script as a module:

```html
<script type="module" src="main.js"></script>
```

### Functional
#### What is recursion?
Recursion in computer science is a method of solving a problem where the solution depends on solutions to smaller instances of the same problem (as opposed to iteration). The process in which a function calls itself directly or indirectly is called recursion and the corresponding function is called as recursive function. A method or function that calls itself until some exit condition is reached.

Recursion simply means “self reference”. When something refers to itself or describes itself, it is called recursive. In programming, recursive function is a function that calls itself.

In computer programming, the term recursive describes a function or method that repeatedly calculates a smaller part of itself to arrive at the final result. It is similar to iteration, but instead of repeating a set of operations, a recursive function accomplishes repetition by referring to itself in its own definition. Using recursive logic can have some downfalls, including the creation of an endless loop in programming. For this reason, ensuring there is an escape condition (like a do until) in the programming helps reduce, if not eliminate, the chance of an endless loop from occurring.

#### Write a recursive function which calculates the Fibonacci numbers!
**In Python:** 
```python
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
```   

**In Javascript:**
```javascript
function fibonacci(num) {
    if (num <= 1) return 1;
    return fibonacci(num - 1) + fibonacci(num - 2);
}
```  

#### How to store a function in a variable in Python?
variable = function 
**NOT** variable = function(), because it calls the function and stores the return value. It does not store the function. 

#### List the ways of defining a callable logical unit in JavaScript!
**1. Function declaration:**<br />
A function declaration is made of function keyword, followed by an obligatory function name, a list of parameters in a pair of parenthesis (para1, ..., paramN) and a pair of curly braces {...} that delimits the body code. The function declaration creates a variable in the current scope with the identifier equal to function name. This variable holds the function object. The function variable is hoisted up to the top of the current scope, which means that the function can be invoked before the declaration. The created function is named, which means that name property of the function object holds its name. It is useful when viewing the call stack: in debugging or error messages reading. 

```javascript
// function declaration
function isEven(num) {
  return num % 2 === 0;
}
isEven(24); // => true
isEven(11); // => false
```

**2. Function expression:**<br />
A function expression is determined by a function keyword, followed by an optional function name, a list of parameters in a pair of parenthesis (para1, ..., paramN) and a pair of curly braces { ... } that delimits the body code. When the expression has the name specified, this is a **named function expression**. 

```javascript
const count = function(array) { // Function expression
  return array.length;
}
```

A function is anonymous when it does not have a name (name property is an empty string ''). This is an **anonymous function**, which name is an empty string.

```javascript
function(variable) {return typeof variable; }
```

**4. Arrow function:**<br />
An arrow function is defined using a pair of parenthesis that contains the list of parameters (param1, param2, ..., paramN), followed by a fat arrow => and a pair of curly braces {...} that delimits the body statements.
When the arrow function has only one parameter, the pair of parenthesis can be omitted. When it contains a single statement, the curly braces can be omitted too. The arrow function is anonymous.

```javascript
const absValue = (number) => {
  if (number < 0) {
    return -number;
  }
  return number;
}
absValue(-10); // => 10
absValue(5);   // => 5
```

**5. Generator function:**<br />
The generator function in JavaScript returns a Generator object. Its syntax is similar to function expression, function declaration or method declaration, just that it requires a star character *.

```javascript
function* indexGenerator(){
  var index = 0;
  while(true) {
    yield index++;
  }
}
```

**6. new Function:**<br />
In JavaScript functions are first class objects - a function is a regular object of type function. The function object type has a **constructor: Function.** When Function is invoked as a constructor new Function(arg1, arg2, ..., argN, bodyString), a new function is created. The arguments arg1, args2, ..., argN passed to constructor become the parameter names for the new function and the last argument bodyString is used as the function body code. The functions created this way don’t have access to current scope, thus closures cannot be created. They are always created in the global scope.

```javascript
const sumFunction = new Function(numberA, numberB, 
   'return numberA + numberB'
);
sumFunction(10, 15) // => 25
```

**Which to use?**<br />
- If the function uses this from the enclosing function, the arrow function is a good solution. When the callback function has one short statement, the arrow function is a good option too, because it creates short and light code.
- For a shorter syntax when declaring methods on object literals, the shorthand method declaration is preferable.
- new Function way to declare functions generally should not be used. Mainly because it opens potential security risks, doesn’t allow code auto-complete in editors and lose the engine optimizations.

#### What is an event listener? How to attach one?
In the browser most code is event-driven and writing interactive applications in JavaScript is often about waiting for and reacting to events to alter the behavior of the browser in some way. Events occur when the page loads, when user interacts (clicks, hovers, changes) and many other times, and can be triggered manually too. To register to an event you listen for it and supply a function which will be called by the browser when the event occurs. This function is known as an event listener (aka event handler) which is a type of callback.
When an event is happening we say the event has been triggered or fired. When js catch an event then we say the event is handled => event handling. 

**How to define event listeners:**
```javascript
let element = document.querySelectorAll('.btn')[0];
element.addEventListener('click', clickHandler);

function clickHandler(event) {
    console.log('button is clicked');
}
``` 

#### How to trigger an event in JavaScript?
In the browser most code is event-driven and writing interactive applications in JavaScript is often about waiting for and reacting to events to alter the behavior of the browser in some way. Events occur when the page loads, when user interacts (clicks, hovers, changes) and many other times, and can be triggered manually too. To register to an event you listen for it and supply a function which will be called by the browser when the event occurs. This function is known as an event listener (aka event handler) which is a type of callback.
When an event is happening we say the event has been triggered or fired. When js catch an event then we say the event is handled => event handling. 

**How to define event listeners:**
```javascript
let element = document.querySelectorAll('.btn')[0];
element.addEventListener('click', clickHandler);

function clickHandler(event) {
    console.log('button is clicked');
}
``` 

#### What is a callback function? Tell some examples of its usage.
CallBack Function is a function which is passed into another function as an argument and is expected to execute after some kind of event. The purpose of the callback is to inform a class Sync/Async if some work in other class is done. This is very useful when working with Asynchronous tasks. For example when we want to perform some routine tasks like perform some operation or display content after some clicking a button, or fetching data from internet. This is also used in event handling, as we get notified when a button is clicked via callback function. 

#### What is a Python decorator? How does it work? Tell some examples of its usage.
In Python, functions are the first class objects, which means that:
- Functions are objects; they can be referenced to, passed to a variable and returned from other functions as well.
- Functions can be defined inside another function and can also be passed as argument to another function.

Decorators are very powerful and useful tool in Python since it allows programmers to modify the behavior of function or class. Decorators allow us to wrap another function in order to extend the behavior of wrapped function, without permanently modifying it. In Decorators, functions are taken as the argument into another function and then called inside the wrapper function.

Simply put, decorators wrap a function, modifying its behavior.

#### What is the difference between synchronous and asynchronous execution?
**Synchronous (Classic Web-Application Model) execution:**<br />
Synchronous program execution in most high-level languages is usually very straightforward. Your program starts at the first line of source code and each line of code executed sequentially thereafter. Each time a function is called, program execution waits until that function returns before continuing to the next line of code. This method of execution can have undesirable ramifications. Blocking operations may not always seem like an issue because computers are fast. Making synchronous calls to resources can lead to long response times locking up the UI until the resource responds. Making requests to your own services like a database can have the same effect.  Suppose a function is called to start a time consuming process. What if you want to stop the lengthy process? With synchronous execution, your program is “stuck,” waiting for the process to end, with no way out. A synchronous request blocks the client until operation completes i.e. browser is unresponsive. In such case, javascript engine of the browser is blocked. If an API call is synchronous, it means that code execution will block (or wait) for the API call to return before continuing. This means that until a response is returned by the API, your application will not execute any further, which could be perceived by the user as latency or performance lag in your app. Asynchronous execution avoids this bottleneck. You are essentially saying, “I know this function call is going to take a great deal of time, but my program doesn’t want to wait around while it executes.”

JavaScript is single-threaded, that means only one statement is executed at a time. As the JS engine processes our script line by line, it uses this single Call-Stack to keep track of codes that are supposed to run in their respective order. Like what a stack does, a data structure which records lines of executable instructions and executes them in a LIFO manner. That’s how a script of synchronous tasks gets handled by our browser without involving anything other than the “legendary” Call Stack. But things get a little bit complex when JS engine encounters an asynchronous task. Spoiler: at its base, JavaScript is a synchronous, blocking, single-threaded language. That just means that only one operation can be in progress at a time. However you can manipulate JavaScript to behave in an asynchronous way. It’s not baked in, but it’s possible! JavaScript was born inside the browser, its main job, in the beginning, was to respond to user actions, like onClick, onMouseOver, onChange, onSubmit and so on. How could it do this with a synchronous programming model?

**Example**<br />
For example, we might be running some Javascript on our website that needs some data from a server. We call a function that sends a request to the server to get that data. This request is sent on our behalf, but it takes some time to get all the way there and back. In the meantime the rest of our Javascript keeps running. At some point, the request will complete and will return our data. But there’s no way to get this data back to our original code. Instead of trying to get the data back to the original code to do something with it, we tell the asynchronous function what to do when it completes. In Javascript, this usually looks like passing a callback function as an argument. Passing in a callback is a way to interact with the response or error.

**Asynchronous (AJAX Web-Application Model) execution:**
What does asynchronous means? Unlike synchronous, asynchronous is a behaviour. We need this behaviour when things are slow. Synchronous executions of code may seem straightforward but can be slow. Tasks like image processing can be slow, file operations can be really slow, making network request and waiting for response is definitely slow, making huge calculations like over a 100 million for-loop iteration is somewhat slow. So such slow things in Call stack results in “Blocking”. When call stack is blocked, the browser prevents user’s interrupts and other code statements from executing until the blocking statement is executed and the call stack is freed. Asynchronous code can prove helpful and necessary when you don’t know how long a certain operation will take (ajax request, API call, query to database). An asynchronous request doesn’t block the client i.e. browser is responsive. At that time, user can perform another operations also. In such case, javascript engine of the browser is not blocked. Asynchronous calls do not block (or wait) for the API call to return from the server. Execution continues on in your program, and when the call returns from the server, a "callback" function is executed. The important point is that program execution will continue, and asynchronously, the callback function will be called once program execution completes. Hence Asynchronous callbacks are used to handle such situations. So this is where Event Loop, Callback Queue and Web APIs (in browser) kicks in. 

**Asynchronous Callbacks:**
Using callbacks is a very common way to implement asynchronous operations. When a callback function is specified, the CRUD operation is non-blocking which means that the next statement is called immediately even though the result from the database has not yet been fetched. Only when the result is available is the callback called. We use asynchronous callbacks to make our code non-blocking. The earliest and most straightforward solution to being stuck in the synchronous world was asynchronous callbacks (think setTimeout()). Let’s use a database request as an example: asynchronous callbacks allow you to invoke a callback function which sends a database request (and any other nested callbacks) off to your app, where it waits for the response from the database, freeing up the rest of your code to continue running. Once the database request completes, the results (and any other nested code) are sent to the queue, and then processed through the event loop. You can’t know when a user is going to click a button, so what you do is, you define an event handler for the click event. This event handler accepts a function, which will be called when the event is triggered. This is the so-called callback. A callback is a simple function that’s passed as a value to another function, and will only be executed when the event happens. We can do this because JavaScript has first-class functions, which can be assigned to variables and passed around to other functions (called higher-order functions)

**The problem with callbacks:**
Callbacks are great for simple cases! However every callback adds a level of nesting, and when you have lots of callbacks, the code starts to be complicated very quickly

**Alternatives to callbacks:**
Starting with ES6, JavaScript introduced several features that help us with asynchronous code that do not involve using callbacks:
- Promises (ES2015)
- Async/Await (ES2017): They make the code look like it’s synchronous, but it’s asynchronous and non-blocking behind the scenes.

**Promises and Asynchronous Operations:**
Promises are another way to interact with asynchronous code. A Promise represents the work that is happening asynchronously. When the Promise resolves the result can be caught as an error, or used in a .then() method. then() returns a Promise, this means then is chainable returning another Promise to the next then. ES6 introduced the concept of job queue/micro-task queue which is used by Promises in JavaScript. The difference between the message queue and the job queue is that the job queue has a higher priority than the message queue, which means that promise jobs inside the job queue/ micro-task queue will be executed before the callbacks inside the message queue. In order to deal with callback hell, libraries allowed programmers to clean up their syntax and write code that operated asynchronously but looked synchronous. This resulted in code that was easier to read and faster to run. With a promise, instead of bundling all dependencies into one code block and sending the entire thing off to the browser, we’re able to separate them out. We can send the asynchronous callback to the browser, and use .then() to hold all other dependencies. This allows us to code in a more modular, readable way, while still gaining the benefits of asynchronous programming.

**Async / Await:**
Promises were fantastic — so fantastic, in fact, that ES6 brought them into the language as a standard. Using promises still left asynchronous code looking and feeling slightly wonky, so we now have beautiful and stunning Async/Await to help us out! 
Async/Await allows you to:
- Continue using promises
- Write asynchronous code that looks and feels synchronous
- Cleans up your syntax and makes your code more human-readable

**Execution Context:**
An Execution Context is an abstract concept of an environment where the JavaScript code is evaluated and executed. Whenever any code is run in JavaScript, it’s run inside an execution context. The function code executes inside the function execution context, and the global code executes inside the global execution context. Each function has its own execution context.

**Call Stack:**
The call stack as its name implies is a stack with a LIFO (Last in, First out) structure, which is used to store all the execution context created during the code execution. JavaScript has a single call stack because it’s a single-threaded programming language. The call stack has a LIFO structure which means that the items can be added or removed from the top of the stack only.

**Javascript has a:**
- Callstack
- WebAPI
- Event Loop
- Callback Queue

The event loop, the web APIs and the message queue / task queue are not part of the JavaScript engine, it’s a part of browser’s JavaScript runtime environment or Nodejs JavaScript runtime environment (in case of Nodejs). 

**The Event Loop:**
The job of the Event loop is to look into the call stack and determine if the call stack is empty or not. If the call stack is empty, it looks into the message queue to see if there’s any pending callback waiting to be executed.

**DOM Events:**
The Message queue also contains the callbacks from the DOM events such as click events and keyboard events. In case of DOM events, the event listener sits in the web APIs environment waiting for a certain event (click event in this case) to happen, and when that event happens, then the callback function is placed in the message queue waiting to be executed. Again the event loop checks if the call stack is empty and pushes the event callback to the stack if it’s empty and the callback is executed.

The Callstack is the immediate work your program will do.
WebAPI's are methods available from environments where JavaScript is run. In browsers, the window and its methods are apart of the WebAPI. When the WebAPI completes, it puts the callback on the Callback Queue. The Event Loop waits for the Callstack to complete the loaded work. Once the Event Loop notices the Callstack is clear it will add work to the Callstack from the Callback Queue. A callback executes once it is added to the Callstack. 

**Summary:**<br />
In programming, synchronous operations block instructions until the task is completed, while asynchronous operations can execute without blocking other operations. Asynchronous operations are generally completed by firing an event or by calling a provided callback function. The difference between synchronous and asynchronous execution becomes important when dealing with many independent processes which are trying to interact with each other. When you execute something synchronously, you wait for it to finish before moving on to another task. When you execute something asynchronously, you can move on to another task before it finishes. A synchronous operation blocks a process until the operation completes. An asynchronous operation is non-blocking and only initiates the operation. The caller could discover completion by some other mechanism. Asynchronous Operations happen independently from the main program flow. 

## Programming languages

### SQL

#### How can you connect your application to a database server? What are the possible ways?
Connections are built by supplying an underlying driver or provider with a connection string, which is a way of addressing a specific database or server and instance as well as user authentication credentials (for example, Server=sql_box;Database=Common;User ID=uid;Pwd=password;). Once a connection has been built it can be opened and closed at will, and properties (such as the command time-out length, or transaction, if one exists) can be set. The Connection String is composed of a set of key/value pairs as dictated by the data access interface and data provider being used.

Many databases (such as PostgreSQL) only allow one operation to be performed at a time on each connection. If a request for data (a SQL Select statement) is sent to the database and a result set is returned, the connection is open but not available for other operations until the client finishes consuming the result set. Other databases, like SQL Server 2005 (and later), do not impose this limitation. However, databases that provide multiple operations per connection usually incur far more overhead than those that permit only a single operation task at a time.

```python
# setup connection string
user_name = "your db username"
password = "your password"
host = "usually it is: localhost"
database_name = "name of the db you want to open"

# this string describes all info for psycopg2 to connect to the database
connect_str = "postgresql://{user_name}:{password}@{host}/{database_name}".format(
    user_name=user_name,
    password=password,
    host=host,
    database_name=database_name
)
# connection describes and maintaines a connection to the database
# to get a connection you can call the connect function of psycopg2
connection = psycopg2.connect(connect_str)

# set autocommit option, to do every query when we call it
connection.autocommit = True
```

#### When do you use the DISTINCT keyword in SQL?
Inside a table, a column often contains many duplicate values; and sometimes you only want to list the different (distinct) values. The SELECT DISTINCT statement is used to return only distinct (different) values.

**SELECT DISTINCT Syntax:**
```sql
SELECT DISTINCT column1, column2, ...
FROM table_name;
```

#### What are aggregate functions in SQL? Give 3 examples.
An aggregate function performs a calculation on a set of values, and returns a single value. Except for COUNT, aggregate functions ignore null values. Aggregate functions are often used with the GROUP BY clause of the SELECT statement. Aggregate functions allow us to easily produce summarized data from our database. 

- COUNT: counts how many rows are in a particular column.
- SUM: adds together all the values in a particular column.
- MIN: and MAX return the lowest and highest values in a particular column.
- AVG: calculates the average of a group of selected values.

#### What kind of JOIN types do you know in SQL? Could you give examples?
A JOIN clause is used to combine rows from two or more tables, based on a related column between them.<br />

**Different Types of SQL JOINs:**
- (INNER) JOIN: Returns records that have matching values in both tables
- LEFT (OUTER) JOIN: Returns all records from the left table, and the matched records from the right table
- RIGHT (OUTER) JOIN: Returns all records from the right table, and the matched records from the left table
- FULL (OUTER) JOIN: Returns all records when there is a match in either left or right table

#### What are the constraints in sql?
SQL constraints are used to specify rules for data in a table. Constraints are used to limit the type of data that can go into a table. This ensures the accuracy and reliability of the data in the table. If there is any violation between the constraint and the data action, the action is aborted. Constraints can be column level or table level. Column level constraints apply to a column, and table level constraints apply to the whole table. Constraints can be specified when the table is created with the CREATE TABLE statement, or after the table is created with the ALTER TABLE statement. 

**The following constraints are commonly used in SQL:**
- NOT NULL - Ensures that a column cannot have a NULL value
- UNIQUE - Ensures that all values in a column are different
- PRIMARY KEY - A combination of a NOT NULL and UNIQUE. Uniquely identifies each row in a table
- FOREIGN KEY - Uniquely identifies a row/record in another table
- CHECK - Ensures that all values in a column satisfies a specific condition
- DEFAULT - Sets a default value for a column when no value is specified

**Syntax:**
```sql
CREATE TABLE table_name (
column1 datatype constraint,
column2 datatype constraint,
column3 datatype constraint,
....
);
```

#### What is a cursor in SQL? Why would you use one?
A cursor is a temporary work area created in the system memory when a SQL statement is executed. This temporary work area is used to store the data retrieved from the database, and manipulate this data. A cursor can hold more than one row, but can process only one row at a time. A database cursor can be thought of as a pointer to a specific row within a query result. The pointer can be moved from one row to the next.

#### What are database indexes? When to use?
Indexes are special lookup tables that the database search engine can use to speed up data retrieval. Simply put, an index is a pointer to data in a table. An index in a database is very similar to an index in the back of a book. A database index allows a query to efficiently retrieve data from a database.  Indexes are related to specific tables and consist of one or more keys.  A table can have more than one index built from it. PostgreSQL provides several index types: B-tree, Hash, GiST, SP-GiST and GIN. Each Index type uses a different algorithm that is best suited to different types of queries. By default, the CREATE INDEX command creates B-tree indexes, which fit the most common situations. An index helps to speed up SELECT queries and WHERE clauses; however, it slows down data input, with UPDATE and INSERT statements. Indexes can be created or dropped with no effect on the data. Indexes are automatically created for primary key constraints and unique constraints (Implicit indexes).

**Sequential Scanning:**<br />
You go over all of the records, until you find the person whose phone number you are looking for, this is super inefficient. 

**Index Scanning:**<br />
Simply said, Postgres will issue a scan based on the indexes, therefore finding the exact location of the user that we are looking for and returning it. This is a much cheaper operation then using a sequential scan.

**Clustered Indexes:**<br />
Clustering means that the data is in a distinct order, resulting the row data to be stored in order. Also, clustered indexes increase the write time, because when new data arrives, all of the data has to be rearranged. But on the bright side - they can greatly increase the reading speed of the table. To summarize - clustered indexes order the data physically (on disk) in clusters.

**Non-clustered Indexes:**<br />
Non-clustered indexes are indexes that keep a separate ordering list that has pointers to the physical rows. So, to summarize - non-clustered indexes do not order the data physically, they just keep a list of the data order.

**When Should Indexes be Avoided?**<br />
Although indexes are intended to enhance a database's performance, there are times when they should be avoided. 
- Indexes should not be used on small tables.
- Tables that have frequent, large batch update or insert operations.
- Indexes should not be used on columns that contain a high number of NULL values.
- Columns that are frequently manipulated should not be indexed.

#### What are database transactions? When to use?
A transaction is a unit of work that is performed against a database. Transactions are units or sequences of work accomplished in a logical order, whether in a manual fashion by a user or automatically by some sort of a database program. For example, if you are creating a record, updating a record, or deleting a record from the table, then you are performing transaction on the table. It is important to control transactions to ensure data integrity and to handle database errors.

**Transaction Isolation in PostgreSQL:**<br />
PostgreSQL comes with solid, time-tested features that lets you define exactly what should happen when multiple clients try to update the same data concurrently. One of them is the isolation level of transactions. Transactions are the fundamental way to mutate data in an RDBMS. Modern RDBMS allow more than one transaction to run concurrently. Transaction isolation levels and pessimistic locks are two such tools.
The isolation level of a transaction, in PostgreSQL, can be one of:
- **Read Committed:** What happens when one (unfinished) transaction inserts rows in a table and the other (also unfinished) transaction tries to read all rows in the table? The read committed isolation level guarantees that dirty reads will never happen.
- **Repeatable Read:** These happen when a transaction reads a row, and then reads it again a bit later but gets a different result – because the row was updated in between by another transaction. PostgreSQL will then ensure that the second (or any) read will also return the same result as the first read. 
- **Serializable:** Updates performed in one transaction can be “lost”, or overwritten by another transaction that happens to run concurrently. PostgreSQL places a lock to prevent another update until the first transaction is finished.

Every transaction has it’s isolation level set to one of these when it is created. The default level is “read committed”.

#### What kind of database relations do you know? How to define them?
**One-to-One:** A row in table A can have only one matching row in table B, and vice versa.

**One-to-Many (or Many-to-One):** a row in table A can have many matching rows in table B, but a row in table B can have only one matching row in table A. This is the most common relationship type.

**Many-to-Many:** a row in table A can have many matching rows in table B, and vice versa. A many-to-many relationship could be thought of as two one-to-many relationships, linked by an intermediary table. The intermediary table is typically referred to as a “junction table” (also as a “cross-reference table”). This table is used to link the other two tables together. It does this by having two fields that reference the primary key of each of the other two tables.

**Self Referencing Relationships:** This is used when a table needs to have a relationship with itself.

#### You have a table with an “address” field which contains data like “3525, Miskolc, Régiposta 9.” (postcode, city, street name and address). How would you query all records related to Miskolc?
```sql
SELECT postcode, streetname, address 
FROM tablename
WHERE city = "Miskolc";
```

#### How would you keep track of what kind of data has changed after an UPDATE or DELETE operation in a table?
Database security is always an essential issue in any database application. Especially when critical data is stored, it might be interesting to know who has changed which data when and how. To track those changes made to tables in PostgreSQL you can write yourself a generic changelog trigger. The easiest way to do that is to write a generic PL/pgSQL function and use it for all tables in the system. As PostgreSQL provides good support for stored procedures. At the basic database level you can track changes by having a separate table that gets an entry added to it via triggers on INSERT/UPDATE/DELETE statements. Thats the general way of tracking changes to a database table.

**Creating a table to store some history:**<br />
The point of this table is to keep track of all changes made to a table. We want to know which operation has been taking place. 

### HTML & CSS

#### What’s the difference between XML, XHTML and HTML?
**HTML** is the HyperText Markup Language, which is designed to create structured documents and provide for semantic meaning behind the documents.

**XML** is the Extensible Markup Language, which provides rules for creating, structuring, and encoding documents. You often see XML being used to store data and to allow for communication between applications. All of the major programming languages provide mechanisms for reading and writing XML documents.

**XHTML** is an XML-based HTML. It serves the same function as HTML, but with the same rules as XML documents. These rules deal with the structure of the markup.

#### How to include a JavaScript file in a webpage?
The ```<script>``` tag is used to define a client-side script (JavaScript). The ```<script>``` element either contains scripting statements, or it points to an external script file through the src attribute.

**Attributes:** async, defer, src, type, charset

The ```<script>``` tag can be placed in the head section of your HTML, in the body section, or after the ```</body>``` close tag, depending on when you want the JavaScript to load. Generally, JavaScript code can go inside of the document head section in order to keep them contained and out of the main content of your HTML document. However, if your script needs to run at a certain point within a page’s layout, you should put it at the point where it should be called, usually within the body section.

**Example:**
```html
<script src="myscripts.js"></script>
```
**Note:** There are several ways an external script can be executed:
- If async="async": The script is executed asynchronously with the rest of the page (the script will be executed while the page continues the parsing)
- If async is not present and defer="defer": The script is executed when the page has finished parsing
- If neither async or defer is present: The script is fetched and executed immediately, before the browser continues parsing the page

Non-blocking script tags can be placed just about anywhere:
```html
<script src="script.js" async></script>
<script src="script.js" defer></script>
<script src="script.js" async defer></script>
```

The current state-of-the-art is to put scripts in the head tag and use the async or defer attributes. This allows your scripts to be downloaded asap without blocking your browser.

```<noscript>:``` element for users that have disabled scripts in their browser, or have a browser that doesn't support client-side scripting.

#### How to include a CSS file in a webpage?
An external style sheet is used to define the style for many HTML pages. To use an external style sheet, add a link to it in the ```<head>``` section of the HTML page:
```html
<!DOCTYPE html>
<html>
<head>
  <link rel="stylesheet" href="styles.css">
</head>
<body>
...
</body>
</html>
```

#### How to select an element using its id in CSS?
The CSS ID selector matches an element based on the value of its id attribute. In order for the element to be selected, its ID attribute must match exactly the value given in the selector.

**Syntax:**<br />
```css
#id_value { style properties }
```
**Example:**<br />
```css
/* The element with id="demo" */
#demo {
  border: red 2px solid;
}
```
```html
<div id="demo">This div has a special ID on it!</div>
```

#### How to select elements using their class in CSS?
The CSS class selector matches elements based on the contents of their class attribute.

**Syntax:**<br />
```css
.class_name { style properties }
```
**Example:**<br />
```css
.red {
  color: #f33;
}

.yellow-bg {
  background: #ffa;
}

/* All elements with class="spacious" */
.spacious {
  margin: 2em;
}

/* All <li> elements with class="spacious" */
li.spacious {
  margin: 2em;
}
```

```html
<p class="red">This paragraph has red text.</p>
<p class="red yellow-bg">This paragraph has red text and a yellow background.</p>
```

#### How to select elements which have the ‘alpha’ and ‘beta’ classes in CSS?
```css
/* All elements with class="alpha" */
.alpha {
  style properties
}
/* All elements with class="beta" */
.beta {
  style properties
}
```

#### How to select all list items in all ordered lists on the page in CSS?
```css
.li.ol {
  style properties
}
```

#### How to select elements using their attributes in CSS?
The CSS attribute selector matches elements based on the presence or value of a given attribute.

**Example:**
```css
/* <a> elements with a title attribute */
a[title] {
  color: purple;
}

/* <a> elements with an href matching "https://example.org" */
a[href="https://example.org"] {
  color: green;
}

/* <a> elements with an href containing "example" */
a[href*="example"] {
  font-size: 2em;
}

/* <a> elements with an href ending ".org" */
a[href$=".org"] {
  font-style: italic;
}

/* Internal links, beginning with "#" */
a[href^="#"] {
  background-color: gold;
}
```

#### What are UX and UI?
UX Design refers to the term User Experience Design, while UI Design stands for User Interface Design. Both elements are crucial to a product and work closely together. Where UX Design is a more analytical and technical field, UI Design is closer to what we refer to as graphic design, though the responsibilities are somewhat more complex.

**What is User Experience Design?**<br />
- User experience design is a human-first way of designing products.
- User experience design (UXD or UED) is the process of enhancing customer satisfaction and loyalty by improving the usability, ease of use, and pleasure provided in the interaction between the customer and the product. 
- User Experience Design is the process of development and improvement of quality interaction between a user and all facets of a company.
- User Experience Design is responsible for being hands on with the process of research, competitor and customer analysis, testing, wireframing, development, content, and prototyping to test for quality results.
- User Experience Design is in theory a non-digital (cognitive science) practice, but used and defined predominantly by digital industries.

**What is UI Design?**<br />
- User Interface Design is responsible for the transference of a brand’s strengths and visual assets to a product’s interface as to best enhance the user’s experience.
- User Interface Design is a process of visually guiding the user through a product’s interface via interactive elements and across all sizes/platforms. It is responsible for the transference of a product’s development, research, content and layout into an attractive, guiding and responsive experience for users.
- User Interface Design is a digital field, which includes responsibility for cooperation and work with developers or code.

#### Please list some points that an application should fulfill to have good UX.
1. Design Should Concentrate on User Experience:
Graphics, layout, text, and interactive elements work in synergy to present the user with an experience, not just present them with information.
2. Websites Are Scanned, Not Read:
It is a must that your website is scannable because people do not read websites, they scan them. Infographics and visuals have become the way for anyone trying to convey instructions or data.
3. Users Want Clarity and Simplicity:
Don’t make it difficult to find action buttons. Visually focus attention on the main button versus a bunch of buttons on the home page.
4. Common Design Elements Versus Creativity:
When design elements are common elsewhere, don’t reinvent them by becoming creative with new UI patterns. Making users think too hard to figure out your UI interface is not what you want.
5. Know the Audience:
You must have a good idea of who the audience is for the intended website or app before you create it. When you’ve identified your audience, remember to incorporate their feedback into your design. Considering end user’s actionable feedback is significantly valuable.
6. Visual Hierarchy:
When putting the most important elements on the interface, highlight them so that users focus on them.
7. User Experience Qualities:
- Useful – Content should be original and fulfill a need
- Usable – Site must be easy to find
- Desirable – Design elements bring about emotion and appreciation
- Findable – Content needs to be locatable and navigable offsite and onsite
- Accessible – Content needs to be accessible to people with disabilities
- Credible – Users must believe and trust what you tell them.

#### What is XML, XSLT, DTD?
**XML:**<br />
eXtensible Markup Language (XML) is a generic markup language specified by the W3C, similar to HTML. Moreover, HTML is a presentation language, whereas XML is a data-description language. This means, unlike other markup languages, XML is not predefined so you must define your own tags. XML tags resemble HTML tags, but XML is much more flexible because it lets users define their own tags. In this way XML acts like a meta-language—that is, it can be used to define other languages, such as RSS. The primary purpose of the language is the sharing of data across different systems, such as the Internet. There are many languages based on XML; Some examples are XHTML, MathML, SVG, XUL, XBL, RSS, and RDF. You can also create your own. This means that XML has far broader applications than just the Web. For example, Web services can use XML to exchange requests and responses.

**XSLT:**<br />
Extensible Stylesheet Language Transformations (XSLT) is an XML-based language used, in conjunction with specialized processing software, for the transformation of XML documents. Although the process is referred to as "transformation," the original document is not changed; rather, a new XML document is created based on the content of an existing document. Then, the new document may be serialized (output) by the processor in standard XML syntax or in another format, such as HTML or plain text. XSLT is most often used to convert data between different XML schemas or to convert XML data into web pages or PDF documents.

**DTD:**<br />
Document Type Declaration. In HTML, the doctype is the required ```<!DOCTYPE html>``` preamble found at the top of all documents. Its sole purpose is to prevent a browser from switching into so-called “quirks mode” when rendering a document. DOCTYPEs are required for legacy reasons. When omitted, browsers tend to use a different rendering mode that is incompatible with some specifications. Including the DOCTYPE in a document ensures that the browser makes a best-effort attempt at following the relevant specifications.

#### What is the difference between HTML and XML?
**HTML:**<br />
- HTML (Hypertext Markup Language) is the markup language for constructing web pages. The markup commands employed in the web-based content signifies structure of the document and its layout to the browser. 
- HTML is predefined markup language
- Purpose of the language: Presentation of the data

**XML:**<br />
- XML (Extensible Markup Language) is a language that enables a user to define a representation of data or data structure where values are assigned in each field in the structure.
- Provides a framework for specifying markup languages
- Purpose of the language: Transfer of information		

**Key Differences Between XML and HTML:**<br />
1. XML is a text-based markup language which has the self-describing structure and can effectively define another markup language. On the other hand, HTML is a predefined markup language and has a limited capability.
2. XML provides logical structuring of the document while HTML structure is predefined where “head” and “body” tags are used.
3. When it comes to language type HTML is case insensitive. As against, XML is case sensitive.
4. HTML was designed with the emphasis on the presentational features of the data. In contrast, XML is data specific where the data storage and transfer was the prior concern.
5. XML does not permit any mistake if there are some errors in the code it could not be parsed. Inversely, in HTML small errors can be neglected.
6. Whitespaces in XML are used for a specific use as XML considers every single character. On the contrary, HTML can ignore the whitespaces.
7. The tags in XML are mandatory to be closed, whereas in HTML an open tag can also work completely fine.
8. Nesting in XML should be done correctly, it has a big importance in XML syntax. Conversely, HTML does not care much about nesting.

### Javascript

#### What is javascript?
JavaScript (JS) is a lightweight interpreted programming language with first-class functions (when functions in that language are treated like any other variable). JavaScript is a prototype-based, multi-paradigm, dynamic language, supporting object-oriented, imperative, and declarative (e.g. functional programming) styles. JavaScript runs on the **client side** of the web, which can be used to design / program how the web pages behave on the occurrence of an event. Another common application for JavaScript is as a (Web) **server side** scripting language. Node.js is a popular example of this.

The standard for JavaScript is ECMAScript. This specification is updated from time to time to contain modern features. After some time different javascript engines (for example in the browsers) implement these new features. ECMAScript 2015 (ES2015 or it was called ES6 some time ago) was a larger change. Current edition: 9th Edition - ECMAScript 2018.

#### When to use AJAX? Bring examples of its usage.
Ajax is not a technology but group of inter-related technologies. AJAX stands for Asynchronous JavaScript And XML. In a nutshell, it is the use of the XMLHttpRequest object to communicate with servers. It can send and receive information in various formats, including JSON, XML, HTML, and text files. AJAX’s most appealing characteristic is its "asynchronous" nature, which means it can communicate with the server, exchange data, and update the page without having to refresh the page.

**AJAX technologies includes:**
- HTML/XHTML and CSS: These technologies are used for displaying content and style. It is mainly used for presentation.
- DOM: It is used for dynamic display and interaction with data.
- XML or JSON: For carrying data to and from server. JSON (Javascript Object Notation) is like XML but short and faster than XML.
- XMLHttpRequest / Fetch API: For asynchronous communication between client and server
- JavaScript: It is used to bring above technologies together.

An object of XMLHttpRequest is used for asynchronous communication between client and server. It performs following operations:
- Sends data from the client in the background
- Receives the data from the server
- Updates the webpage without reloading it.

If you use an asynchronous XMLHttpRequest, you receive a callback when the data has been received. This lets the browser continue to work as normal while your request is being handled. Use XMLHttpRequest (XHR) objects to interact with servers. You can retrieve data from a URL without having to do a full page refresh. This enables a Web page to update just part of a page without disrupting what the user is doing. XMLHttpRequest is used heavily in AJAX programming. Despite its name, XMLHttpRequest can be used to retrieve any type of data, not just XML.

**How AJAX works?**
AJAX communicates with the server using XMLHttpRequest object / Fetch API.
1. User sends a request from the UI and a javascript call goes to XMLHttpRequest object.
2. HTTP Request is sent to the server by XMLHttpRequest object.
3. Server interacts with the database using JSP, PHP, Servlet, ASP.net etc.
4. Data is retrieved.
5. Server sends XML data or JSON data to the XMLHttpRequest callback function.
6. HTML and CSS data is displayed on the browser.

#### What is DOM and how to manipulate it from Javascript?
The DOM is a WEB API that allows access to and modification of the current document. The DOM is an object-oriented representation of the web page, which can be modified with a scripting language such as JavaScript. The DOM represents a document with a logical tree. Each branch of the tree ends in a node, and each node contains objects (elements). DOM methods allow programmatic access to the tree; with them you can change the document's structure, style, or content. Nodes can also have event handlers attached to them; once an event is triggered, the event handlers get executed.

**Most important DOM interfaces:** ChildNode, Document, Event, Node, NodeList, ParentNode, Window...

#### What are events and how/why to use them in Javascript?
Events are responsible for interaction of JavaScript with HTML web pages. The general definition of event is any act can occur by someone. Events can be subscribed by listeners that occurs only when the particular event can be fired. HTML events are "things" that happen to HTML elements. When JavaScript is used in HTML pages, JavaScript can "react" on these events. An HTML event can be something the browser does, or something a user does.

**Here are some examples of HTML events:**
- An HTML web page has finished loading
- An HTML input field was changed
- An HTML button was clicked

Often, when events happen, you may want to do something. JavaScript lets you execute code when events are detected.
DOM Events are sent to notify code of interesting things that have taken place. Each event is represented by an object which is based on the Event interface, and may have additional custom fields and/or functions used to get additional information about what happened. Events can represent everything from basic user interactions to automated notifications of things happening in the rendering model. The Event interface represents an event which takes place in the DOM. An event can be triggered by the user action e.g. clicking mouse button or tapping keyboard or generated by APIs to represent the progress of an asynchronous task. There are many types of events, some of which use other interfaces based on the main Event interface. Many DOM elements can be set up to accept (or "listen" for) these events, and execute code in response to process (or "handle") them. Event-handlers are usually connected (or "attached") to various HTML elements (such as button, div, span, etc.) using EventTarget.addEventListener(). The Event() constructor creates a new Event.

#### What is event bubbling/capturing? How would you use it?
Event Bubbling and Event Capturing is the foundation of event handling in JavaScript. Event bubbling and capturing are two ways of event propagation in the HTML DOM API, when an event occurs in an element inside another element, and both elements have registered a handle for that event. The event propagation mode determines in which order the elements receive the event. **Event Bubbling** is the event starts from the deepest element or target element to its parents, then all its ancestors which are on the way to bottom to top. **Event Capturing** is the event starts from top element to target element. 

**With bubbling,** the event is first captured and handled by the innermost element and then propagated to outer elements.<br />
**With capturing,** the event is first captured by the outermost element and propagated to the inner elements.<br />

We can use the addEventListener(type, listener, useCapture) to register event handlers for in either bubbling (default) or capturing mode. To use the capturing model pass the third argument as true.

#### What is JSON and how do we use it?
JSON — JavaScript Object Notation — is a set of text formatting rules (string format) for storing and transferring data in a machine and human readable way. It looks a lot like the object literal syntax of JavaScript, and it is from there JSON originates. JSON is used to transfer information - between your browser to a server, or saved in text files for retrieval later - because it’s simply text. That means you can’t store complex data like a function, but you can store arrays objects containing simple data, strings and numbers. Data is either converted to or from JSON, using methods called stringify and parse respectively. JSON.stringify converts an object into a JSON string. The string can then be converted back to a JavaScript object using JSON.parse. JSON is taking over from XML as the data-transfer format of the web, and many new web APIs are written exclusively serving JSON, which can mean that you can use AJAX technology to grab JSON.

**It is useful to:**
- send/receive data: between js code and a server / between two servers
- store data: in localStorage or sessionStorage which can save only strings

**Example:**
```javascript
{ "name": "Yoda", age: 894, "lightsaber" : { "color": "green" } }
```

## Software engineering

### Version control

#### What type of branching strategy would you use?
Branching is all about handling massive collaboration issues. But it's worthless, without using a workflow, in which the rules are kept by all participants. A very simple branching workflow is the **Feature branch** workflow, here you have one master branch and several branches for the features you are developing. 

The core idea behind the **Feature Branch Workflow** is that all feature development should take place in a dedicated branch instead of the master branch. This encapsulation makes it easy for multiple developers to work on a particular feature without disturbing the main codebase. It also means the master branch will never contain broken code, which is a huge advantage for continuous integration environments. The Feature Branch Workflow assumes a central repository, and master represents the official project history. Instead of committing directly on their local master branch, developers create a new branch every time they start work on a new feature. Feature branches should have descriptive names, like animated-menu-items or issue-#1061. The idea is to give a clear, highly-focused purpose to each branch. Git makes no technical distinction between the master branch and feature branches, so developers can edit, stage, and commit changes to a feature branch.

Encapsulating feature development also makes it possible to leverage **pull requests**, which are a way to initiate discussions around a branch. They give other developers the opportunity to sign off on a feature before it gets integrated into the official project. Or, if you get stuck in the middle of a feature, you can open a pull request asking for suggestions from your colleagues. The point is, pull requests make it incredibly easy for your team to comment on each other’s work.

#### What would you do if you find a bug on the production code (master branch)?
1. create a new branch (in our repository) forked off the master branch, called, e.g., issue-1722
2. develop the fix in this branch
3. when the fix is ready, merge it into master

#### How can you move changes from one branch to another in GIT?
You can create a new branch pointing to the current commit using ```git branch branchname``` (or ```git checkout -b branchname``` if you want to check it out directly). This will basically duplicate your master branch, so you can continue working on there.

#### How does a VCS help with code reviews?
- Commit Comments: commit each milestone and add a commit message describing the milestone.
- Pull Request Preamble: write a detailed Pull Request description of the purpose of your pull request with text and pictures.
- History: Browse commits, comments, and references related to your pull request in a timeline-style interface.
- Diffs: Preview changes in context with your code to see what is being proposed.

#### What is your favorite git command? Why?
git commit -m "some comments about my recent code"

#### What does remote/local mean in Git? 
Git has two repository types: local and remote.  The local repo is on your computer for only your direct use.  The remote repo is typically elsewhere and for your indirect use.  Git supports multiple remote repositories.

**Local Repo:**<br />
The local repo is on your computer and has all the files and their commit history, enabling full diffs, history review, and committing when offline.  This is one of the key features of a “distributed” version control system (DVCS), locally having the full repository history.

**Remote Repo:**<br />
Git refers to the centralized server as a “remote repository”.  The remote repo is usually not on your machine and is the one shared by the team. The team “pushes” commits to it when ready to share with the team. While one of your remote repos could be another team member’s local repo, in a corporate environment at least one (or the only!) is typically a Git repo on a server anointed as the central/official repo. Note that a remote repo is optional.  When not sharing code with others, there is technically no need for a remote repo (you may want one for backup or CI).  There is also no need for a remote repo if your local repo is considered the central one by all team members (which means your local repo is their remote repo).

### DevOps

#### Why is it good to use a package manager software?
A package manager or package-management system is a collection of software tools that automates the process of installing, upgrading, configuring, and removing computer programs for a computer's operating system. Package Managers are used to automate the process of installing, upgrading, configuring, and removing programs. There are many package managers today for Unix/Linux-based systems. Package managers are designed to eliminate the need for manual installs and updates. This can be particularly useful for large enterprises whose operating systems are based on Linux and other Unix-like systems, typically consisting of hundreds or even tens of thousands of distinct software packages. Package managers are also used for installing and managing modules for languages such as Python, Ruby, etc.

A package manager deals with packages, distributions of software and data in archive files. A package is simply an archive that contains binaries of software, configuration files, and information about dependencies. Packages contain metadata, such as the software's name, description of its purpose, version number, vendor, checksum, and a list of dependencies necessary for the software to run properly. They work closely with software repositories, binary repository managers, and app stores. Packages gets downloaded from software repositories, often simply called repos. These repos are available online at well-defined locations and they serve as a central distribution point for packages. For performance and redundancy, these repos may be mirrored by many other locations worldwide.

The basic functions of the PM are the following:
- Working with file archivers to extract package archives
- Ensuring the integrity and authenticity of the package by verifying their digital certificates and checksums
- Looking up, downloading, installing or updating existing software from a software repository or app store
- Managing dependencies to ensure a package is installed with all packages it requires, thus avoiding dependency hell

#### Why is it good to use a virtual environment for a project?
Package installation may lead to having incompatibility issues or make other applications unworkable. And you may discover that your code does not work on some machines while it just works flawlessly on your local machine. Why? Python environment.

So, not to have a daily nightmare about incompatibility issues, individual python environment needs to be created for a project. A virtual environment is a bunch of scripts and directories that can run python isolated. By using a virtual environment, each python project can have its own dependencies regardless of other projects and system python environments.

### Networks

#### What kind of HTTP status codes do you know?
All HTTP response status codes are separated into five classes (or categories). The first digit of the status code defines the class of response. 
- 1xx (Informational): The request was received, continuing process
- 2xx (Successful): The request was successfully received, understood and accepted
- 3xx (Redirection): Further action needs to be taken in order to complete the request
- 4xx (Client Error): The request contains bad syntax or cannot be fulfilled
- 5xx (Server Error): The server failed to fulfill an apparently valid request

**Most important status codes:**
- 200 OK: Standard response for successful HTTP requests.
- 301 Moved Permanently: This and all future requests should be directed to the given URI.
- 400 Bad Request: The server cannot or will not process the request due to an apparent client error. 
- 403 Forbidden: The request was valid, but the server is refusing action. The user might not have the necessary permissions.
- 404 Not Found: The requested resource could not be found but may be available in the future.
- 405 Method Not Allowed: A request method is not supported for the requested resource.
- 408 Request Timeout: The server timed out waiting for the request.
- 500 Internal Server Error: A generic error message, given when an unexpected condition was encountered. 

#### What is a API?
An API (Application Programming Interface) is a set of features and rules that exist inside a software program (the application) enabling interaction with it through software. In general terms, it is a set of clearly defined methods of communication among various components. A good API makes it easier to develop a computer program by providing all the building blocks. In Web development, an API is generally a set of code features (e.g. methods, properties, events, and URLs) that a developer can use in their apps for interacting with components of a user's web browser, or other software/hardware on the user's computer, or third party websites and services. When writing code for the Web, there are many Web APIs available. Below is a list of all the APIs and interfaces (object types) that you may be able to use while developing your Web app or site. Web APIs are typically used with JavaScript, although this doesn't always have to be the case.

**Examples:**
Web APIs: DOM, Fetch API, Web Storage API...

#### What is REST API?
n computing, representational state transfer (REST) or RESTful is an architectural style used for web development. Systems and sites designed using this style aim for fast performance, reliability and the ability to scale (to grow and easily support extra users). To achieve these goals, developers work with reusable components that can be managed and updated without affecting the system as a whole while it is running. ... APIs that adhere to the REST architectural constraints are called RESTful APIs. Representational State Transfer (REST) refers to a group of software architecture design constraints that bring about efficient, reliable, and scalable distributed systems. A system is called RESTful when it adheres to those constraints.

**Key REST principles:**<br />
- Give every “thing” an ID: Use URIs to identify everything that merits being identifiable, specifically, all of the “high-level” resources that your application provides. For example: http://example.com/products?color=green 

- Link things together: Use links to refer to identifiable things (resources) wherever possible. Hyperlinking is what makes the Web the Web.

- Use standard methods: For clients to be able to interact with your resources, they should implement the default application protocol (HTTP) correctly, i.e. make use of the standard methods GET, PUT, POST, DELETE.

- Resources with multiple representations: Provide multiple representations of resources for different needs.
- Communicate statelessly

#### What is JSON? When to use?
JSON (JavaScript Object Notation) is a lightweight data-interchange format. It is easy for humans to read and write. JSON is a text format that is completely language independent. JSON is a syntax for storing and exchanging data. When exchanging data between a browser and a server, the data can only be text. JSON is text, and we can convert any JavaScript object into JSON, and send JSON to the server. We can also convert any JSON received from the server into JavaScript objects. This way we can work with the data as JavaScript objects, with no complicated parsing and translations. JSON uses JavaScript syntax, but the JSON format is text only. Text can be read and used as a data format by any programming language.

**JSON is built on two structures:** 
- A collection of name/value pairs. In various languages, this is realized as an object, dictionary, hash table. 
- An ordered list of values. In most languages, this is realized as an array, vector, list, or sequence.
    
**Methods:**
- JSON.parse(): Parse a string as JSON, optionally transform the produced value and its properties, and return the value.
- JSON.stringify(): Return a JSON string corresponding to the specified value.

**Example:**
```javascript
var myObj = {name: "John", age: 31, city: "New York"};
var myJSON = JSON.stringify(myObj);

var myJSON = '{"name":"John", "age":31, "city":"New York"}';
var myObj = JSON.parse(myJSON);
```

#### What is TCP/IP? What layers does it define, what are they responsible for?
TCP (Transmission Control Protocol) is an important network protocol that lets two hosts connect and exchange data streams. TCP guarantees the delivery of data and packets in the same order as they were sent. TCP role is to ensure the packets are reliably delivered, error free.  The widely used term “TCP/IP” refers to TCP over IP.

TCP/IP (Transmission Control Protocol/Internet Protocol) is widely used throughout the world to provide network communications. TCP/IP communications are composed of four layers that work together. When a user wants to transfer data across networks, the data is passed from the highest layer through intermediate layers to the lowest layer, with each layer adding information. At each layer, the logical units are typically composed of a header and a payload. The payload consists of the information passed down from the previous layer, while the header contains layer-specific information such as addresses. 

- **Application Layer:** This layer sends and receives data for particular applications, such as Domain Name System (DNS), HyperText Transfer Protocol (HTTP), and Simple Mail Transfer Protocol (SMTP).
- **Transport Layer:** This layer provides connection-oriented or connectionless services for transporting application layer services between networks. Transmission Control Protocol (TCP) and User Datagram Protocol (UDP) are commonly used transport layer protocols.
- **Network Layer:** This layer routes packets across networks.  Internet Protocol (IP) is the fundamental network layer protocol for TCP/IP. 
- **Data Link Layer:** This layer handles communications on the physical network components.  The best-known data link layer protocol is Ethernet.

#### What’s the difference between TCP and UDP?
Both TCP and UDP are protocols used for sending bits of data — known as packets — over the Internet. They both build on top of the Internet protocol. In other words, whether you are sending a packet via TCP or UDP, that packet is sent to an IP address.

**TCP:**<br />
TCP stands for Transmission Control Protocol. It is the most commonly used protocol on the Internet. When you load a web page, your computer sends TCP packets to the web server’s address, asking it to send the web page to you. The web server responds by sending a stream of TCP packets, which your web browser stitches together to form the web page and display it to you. When you click a link, sign in, post a comment, or do anything else, your web browser sends TCP packets to the server and the server sends TCP packets back. TCP is not just one way communication — the remote system sends packets back to acknowledge it is received your packets. TCP guarantees the recipient will receive the packets in order by numbering them. The recipient sends messages back to the sender saying it received the messages. If the sender does not get a correct response, it will resend the packets to ensure the recipient received them. Packets are also checked for errors. TCP is all about this reliability — packets sent with TCP are tracked so no data is lost or corrupted in transit. This is why file downloads do not become corrupted even if there are network hiccups.

**UDP:**<br />
UDP stands for User Datagram Protocol — a datagram is the same thing as a packet of information. The UDP protocol works similarly to TCP, but it throws all the error-checking stuff out. All the back-and-forth communication and deliverability guarantees slow things down. When using UDP, packets are just sent to the recipient. The sender will not wait to make sure the recipient received the packet — it will just continue sending the next packets. UDP is used when speed is desirable and error correction is not necessary. For example, UDP is frequently used for live broadcasts and online games.

#### How does an HTTP Request look like? What are the most relevant HTTP header fields?
**Sending a client request:**<br />
Once the connection is established, the user-agent can send the request. A client request consists of text directives, separated by CRLF (carriage return, followed by line feed), divided into three blocks:
- The first line contains a request method followed by its parameters
- Subsequent lines represent an HTTP header, giving the server information about what type of data is appropriate (e.g., what language, what MIME types), or other data altering its behavior
- The final block is an optional data block, which may contain further data mainly used by the POST method.

**Example requests:**<br />
```http
GET / HTTP/1.1
Host: developer.mozilla.org
Accept-Language: fr
```

```http
POST /contact_form.php HTTP/1.1
Host: developer.mozilla.org
Content-Length: 64
Content-Type: application/x-www-form-urlencoded

name=Joe%20User&request=Send%20me%20one%20of%20your%20catalogue
```

**Request methods:**<br />
HTTP defines a set of request methods indicating the desired action to be performed upon a resource. Although they can also be nouns, these requests methods are sometimes referred as HTTP verbs. The most common requests are GET and POST:
- The GET method requests a data representation of the specified resource. Requests using GET should only retrieve data.
- The POST method sends data to a server so it may change its state. This is the method often used for HTML Forms.

**HTTP request headers:**<br />
HTTP headers allow the client and the server to pass additional information with the request or the response.
Host, User-Agent, Accept, Accept-Language, Referer, Connection, Cookie...

**Note:**<br />
The client-server model does not allow the server to send data to the client without an explicit request for it. To work around this problem, web developers use several techniques: ping the server periodically via the XMLHTTPRequest, Fetch APIs, using the WebSockets API, or similar protocols.

#### How does an HTTP Response look like? What are the most relevant HTTP header fields?
```http
200 OK
Access-Control-Allow-Origin: *
Connection: Keep-Alive
Content-Encoding: gzip
Content-Type: text/html; charset=utf-8
Date: Mon, 18 Jul 2016 16:06:00 GMT
Etag: "c561c68d0ba92bbeb8b0f612a9199f722e3a621a"
Keep-Alive: timeout=5, max=997
Last-Modified: Mon, 18 Jul 2016 02:36:04 GMT
Server: Apache
Set-Cookie: mykey=myvalue; expires=Mon, 17-Jul-2017 16:06:00 GMT; Max-Age=31449600; Path=/; secure
Transfer-Encoding: chunked
Vary: Cookie, Accept-Encoding
X-Backend-Server: developer2.webapp.scl3.mozilla.com
X-Cache-Info: not cacheable; meta data too large
X-kuma-revision: 1085259
x-frame-options: DENY
```

**HTTP response headers:**<br />
A response header is an HTTP header that can be used in an HTTP response and that doesn't relate to the content of the message.
Connection, Content-Type, Keep-Alive, Server, Set-Cookie, Age, Location, Content-Length...

#### What is DNS? How does it work?
Domain Name Servers are like an address book for websites. When you type a web address in your browser, the browser looks at the DNS to find the website's real address before it can retrieve the website. The browser needs to find out which server the website lives on, so it can send HTTP messages to the right place. The Domain Name System (DNS) is a hierarchical and decentralized naming system for computers, services or other resources connected to the Internet or a private network. Web browsers interact through Internet Protocol (IP) addresses. DNS translates domain names to IP addresses so browsers can load Internet resources. Each device connected to the Internet has a unique IP address which other machines use to find the device. The process of DNS resolution involves converting a hostname (such as www.example.com) into a computer-friendly IP address (such as 192.168.1.1). A DNS name server is a server that stores the DNS records for a domain; a DNS name server responds with answers to queries against its database.

#### What is a web server?
"Web server" can refer to hardware or software, or both of them working together.

1. On the hardware side, a web server is a computer that stores web server software and a website's component files (e.g. HTML documents, images, CSS stylesheets, and JavaScript files). It is connected to the Internet and supports physical data interchange with other devices connected to the web.

2. On the software side, a web server includes several parts that control how web users access hosted files, at minimum an HTTP server. An HTTP server is a piece of software that understands URLs (web addresses) and HTTP (the protocol your browser uses to view webpages). It can be accessed through the domain names (like mozilla.org) of websites it stores, and delivers their content to the end-user's device.

At the most basic level, whenever a browser needs a file which is hosted on a web server, the browser requests the file via HTTP. When the request reaches the correct web server (hardware), the HTTP server (software) accepts request, finds the requested document (if it doesn't then a 404 response is returned), and sends it back to the browser, also through HTTP. To publish a website, you need either a static or a dynamic web server.

A **static web server**, or stack, consists of a computer (hardware) with an HTTP server (software). We call it "static" because the server sends its hosted files "as-is" to your browser.

A **dynamic web server** consists of a static web server plus extra software, most commonly an application server and a database. We call it "dynamic" because the application server updates the hosted files before sending them to your browser via the HTTP server.

For example, to produce the final webpages you see in the browser, the application server might fill an HTML template with contents from a database. Sites like MDN or Wikipedia have many thousands of webpages, but they aren't real HTML documents, only a few HTML templates and a giant database. This setup makes it easier and quicker to maintain and deliver the content.

#### Explain the client-server architecture.
Computers connected to the web are called clients and servers. 
**Clients** are the typical web user's internet-connected devices (for example, your computer connected to your Wi-Fi, 
or your phone connected to your mobile network) and web-accessing software available on those devices 
(usually a web browser like Firefox or Chrome).

**Servers** are computers that store webpages, sites, or apps. When a client device wants to access a webpage, 
a copy of the webpage is downloaded from the server onto the client machine to be displayed in the user's web browser.<br />

**Client–server model** is a distributed application structure that partitions tasks or workloads between the providers 
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

In client-server protocols, like HTTP, sessions consist of three phases:

1. The client establishes a TCP connection (or the appropriate connection if the transport layer is not TCP).
2. The client sends its request, and waits for the answer.
3. The server processes the request, sending back its answer, providing a status code and appropriate data.

**Establishing a connection:**<br />
In client-server protocols, it is the client which establishes the connection. Opening a connection in HTTP means initiating a connection in the underlying transport layer, usually this is TCP. With TCP the default port, for an HTTP server on a computer, is port 80. Other ports can also be used, like 8000 or 8080.

#### What would you use a session for?
Http is stateless protocol, that means that it doesn't store anything on client or server side about the connection (whether we send a request or waiting for something) so normally we don't know anything about any previous requests when we do a request to a web server. 
Because HTTP is stateless, in order to associate a request to any other request, you need a way to store user data between HTTP requests.
However, sometimes (actually quite often) we need to preserve state, that means we want to know something that happened before our current http request. The simplest example is the user login mechanisms of various sites. 

Cookies or URL parameters ( for ex. like http://example.com/myPage?asd=lol&boo=no ) are both suitable ways to transport data between 2 or more request. However they are not good in case you don't want that data to be readable/editable on client side. The cookies are client side storage mechanism, but what if we want to store some data about the user and we don't want the user modifying it or we want the data to be only accessible by the server?

The solution is to store data on the server side, so it cannot be reached by the user, we can store data that can be trusted. Session allows you to store information specific to a user from one request to the next. This is implemented on top of cookies for you and signs the cookies cryptographically. What this means is that the user could look at the contents of your cookie but not modify it, unless they know the secret key used for signing. In order to use sessions you have to set a secret key.

#### What would you use a cookie for?
Using the Set-Cookie header field, an HTTP server can pass name/value pairs and associated metadata (called cookies) to a user agent. When the user agent makes subsequent requests to the server, the user agent uses the metadata and other information to determine whether to return the name/value pairs in the Cookie header. So a cookie is a small piece of data sent from a website and stored on the user's computer by the user's web browser while the user is browsing. Since it is stored on the client side, it can be deleted or modified by the user or the user can disable the whole cookie feature in her browser.

Cookies are supported by all browsers, can expire, but have a limitations of storing only around 4KB of data. Cookies are mainly used for simple data that shouldn't be trusted (since the user can tamper with it), mainly for preferences settings on a site (but cookies are used for e.g. showing you personalized ads as well). So cookies are stored on client side, but can be set on server side.

## Software Development Methodologies

#### What kind of software development methodologies do you know? What are the main features of these?
**Waterfall:** <br />
The waterfall method is a sequential design process used in software development processes, in which progress is seen as flowing steadily downwards (like a waterfall) through the phases of conception, initiation, analysis, design, construction, testing, production/implementation and maintenance. The waterfall development model originates in the manufacturing and construction industries: highly structured physical environments in which after-the-fact changes are prohibitively costly, if not impossible. Because no formal software development methodologies existed at the time, this hardware-oriented model was simply adapted for software development.

**Major advantages of the Waterfall Model:**
- Simple and easy to understand and use
- Easy to manage due to the rigidity of the model. Each phase has specific deliverables and a review process.
- Phases are processed and completed one at a time.
- Works well for smaller projects where requirements are very well understood.
- Clearly defined stages.
- Well understood milestones.
- Easy to arrange tasks.
- Process and results are well documented.

**Major disadvantages of the Waterfall Model:**
- No working software is produced until late during the life cycle.
- High amounts of risk and uncertainty.
- Not a good model for complex and object-oriented projects.
- Poor model for long and ongoing projects.
- Not suitable for the projects where requirements are at a moderate to high risk of changing. So, risk and uncertainty is high with this process model.
- It is difficult to measure progress within stages.
- Cannot accommodate changing requirements.
- Adjusting scope during the life cycle can end a project.
- Integration is done as a "big-bang. at the very end, which doesn't allow identifying any technological or business bottleneck or challenges early.

In the past 10 years, waterfall model is used in less and less projects because of it's disadvantages. It's not a really good method for handling projects, where the requirements are not 100% clear, or where changes on the project's scope have to be handled regularly. 

**Agile & Scrum:**<br />
In the context of software development: Agile is a time boxed, iterative approach to software delivery that builds software incrementally from the start of the project, instead of trying to deliver it all at once near the end. It works by breaking projects down into little bits of user functionality called user stories, prioritizing them, and then continuously delivering them in short two week cycles called iterations. 

**Features of Agile:**
- Analysis, design, coding, and testing are continuous activities: You are never done analysis, design, coding and testing on an Agile project. So long as there are features to build, and the means to deliver them, these activities continue for the duration of the project.
- Development is iterative: Iterative development means starting with something really simple, and adding to it incrementally over time.
- Planning is adaptive: When reality disagrees with their plans, Agilists find it easier to change their plans than reality. They call this adaptive planning.
- Roles blur: Roles really blur on Agile projects. When it’s done right, joining an Agile team is a lot like working in a mini-startup. People pitch in and do whatever it takes to make the project successful—regardless of title or role. On an agile project, narrowly defined roles like analyst, programmer, and tester don’t really exist - at least not in the traditional sense.
- Requirements can change: Through a combination of modern software engineering practices, and open and honest planning, Agilsts accept and embrace change even late in delivery process.

- Quality improves because testing starts from day one.
- Visibility improves because you are 1/2 way through the project when you have built 1/2 the features.
- Risk is reduced because you are getting feedback early, and
- Customers are happy because they can make changes without paying exorbitant costs.

**Scrum** is an agile way to manage a project, usually software development. Agile software development with Scrum is often perceived as a methodology; but rather than viewing Scrum as methodology, think of it as a framework for managing a process.

#### What are the SCRUM roles?
Scrum has three roles: product owner, scrum master and the development team members. 

**Product Owner:** The person with the product vision. His / her responsibilities are: managing the scrum backlog, release management, stakeholder management<br />
**Scrum Master:** The scrum expert who helps the team build the product according to the scrum framework<br />
**Development Team:** The team members who execute the work

#### What are the SCRUM ceremonies?
Meetings or “ceremonies” are an important part of agile development. They help to disseminate timely information, bring common goal and vision, and share team progress to all team members.

**Sprint planning:** The goal of Sprint Planning is to answer the questions “What are we going to work on, and how are we going to do it?”<br />
**Sprint review:** Held at the end of each sprint to demonstrate the added functionality. The goal is to get feedback from the product owner and other stakeholders to ensure that the delivered increment met the business need and to revise the Product Backlog based on the feedback.<br />
**Sprint retrospective:** Retrospectives typically last 90 minutes and are there to help us incorporate continuous improvement into our team culture and into our Sprint cadence. This is where the Scrum Team meets to reflect on their previous Sprint and to figure out how to improve as a team by asking – what went well, what did not and what can be improved. <br />
**Daily scrum:** Once we begin a Sprint, we have what we call a Daily Scrum every day. Organized by the Scrum Master, Daily Scrum is typically a 15-minute stand-up meeting to synchronize the work of team members, i.e. what’s done on the prior day, what needs to be done today. 

#### What are the SCRUM artifacts?
Scrum Artifacts provide key information that the Scrum Team and the stakeholders need to be aware of for understanding the product under development, the activities being planned, and the activities done in the project. The following artifacts are defined in Scrum Process Framework.

- Product Vision: the Product Vision is an artifact to define the long-term goal of the project/product.
- Sprint Goal: the Sprint Goal helps to focus the Sprint.
- Product Backlog: a product backlog is a list of all the things that are required in the product.
- Sprint Backlog: the Sprint Backlog is the set of Product Backlog items selected for the Sprint.
- Definition of Done: every Product Backlog item has acceptance criteria when the item is declared to be done.
- Burn-Down Chart: Burndown charts are graphs that give an overview of progress over time while completing a project.
- Increment: The Increment is the sum of all the Product Backlog items completed during a Sprint and all previous Sprints.

#### What is the main goal of a retrospective meeting?
Retrospectives typically last 90 minutes and are there to help us incorporate continuous improvement into our team culture and into our Sprint cadence. This is where the Scrum Team meets to reflect on their previous Sprint and to figure out how to improve as a team by asking – what went well, what did not and what can be improved. It allows the team to focus on its overall performance and identify strategies for continuous improvement, so that they can continuously learn and improve from each other.

#### Explain, when would you recommend to use the waterfall methodology?
**Some situations where the use of Waterfall model is most appropriate are:**
- Requirements are very well documented, clear and fixed.
- Product definition is stable.
- Technology is understood and is not dynamic.
- There are no ambiguous requirements.
- Ample resources with required expertise are available to support the product.
- The project is short.
