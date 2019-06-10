# Web with Python questions

## Software design

### Clean code

#### Point out 5 suggestions, how to format an SQL query!
#### What layers can you name in a simple web application?

### Error handling
#### What error can occur, when an array does not have an element on the requested index?
#### What is the “finally” block, and how would you use it?
#### Why should we catch special exception types?

### Security
#### What is SQL injection? How to protect an application against it?
#### What is XSS? How to protect an application against it?
#### How to properly store passwords?
#### What is HTTPS?
#### What is encryption and decryption?
#### What is hashing?
#### What is the difference between encryption and hashing? When would you use which?
#### What encryption methods do you know?
#### What hashing methods do you know?
#### How/where would you store sensitive data (like db password, API key, ...) of your application?

## Computer science

### Algorithms

#### What is the difference between Stack and Queue data structure?
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
#### Write a recursive function which calculates the Fibonacci numbers!
#### How to store a function in a variable in Python?
#### List the ways of defining a callable logical unit in JavaScript!
#### What is an event listener? How to attach one?
#### How to trigger an event in JavaScript?
#### What is a callback function? Tell some examples of its usage.
#### What is a Python decorator? How does it work? Tell some examples of its usage.
#### What is the difference between synchronous and asynchronous execution?

## Programming languages

### SQL

#### How can you connect your application to a database server? What are the possible ways?
#### When do you use the DISTINCT keyword in SQL?
#### What are aggregate functions in SQL? Give 3 examples.
#### What kind of JOIN types do you know in SQL? Could you give examples?
#### What are the constraints in sql?
#### What is a cursor in SQL? Why would you use one?
#### What are database indexes? When to use?
#### What are database transactions? When to use?
#### What kind of database relations do you know? How to define them?
#### You have a table with an “address” field which contains data like “3525, Miskolc, Régiposta 9.” (postcode, city, street name and address). How would you query all records related to Miskolc?
#### How would you keep track of what kind of data has changed after an UPDATE or DELETE operation in a table?

### HTML & CSS

#### What’s the difference between XML, XHTML and HTML?
#### How to include a JavaScript file in a webpage?
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
#### When to use AJAX? Bring examples of its usage.
#### What is DOM and how to manipulate it from Javascript?
#### What are events and how/why to use them in Javascript?
#### What is event bubbling/capturing? How would you use it?
#### What is JSON and how do we use it?

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
#### What are the SCRUM ceremonies?
#### What are the SCRUM artifacts?
#### What is the main goal of a retrospective meeting?
#### Explain, when would you recommend to use the waterfall methodology?
