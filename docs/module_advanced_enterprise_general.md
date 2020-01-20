# General enterprise questions

## Software engineering

### Architectures

#### What is n-tier (or multi-tier) architecture?
Multitier architecture (often referred to as n-tier architecture) or multilayered architecture is a client–server architecture in which presentation, application processing, and data management functions are physically separated. The most widespread use of multitier architecture is the three-tier architecture. N-tier application architecture provides a model by which developers can create flexible and reusable applications. By segregating an application into tiers, developers acquire the option of modifying or adding a specific layer, instead of reworking the entire application. A three-tier architecture is typically composed of a presentation tier, a domain logic tier, and a data storage tier. The layers should interact only with their direct neighbour below them
#### What are microservices? Advantages and disadvantages?
Microservices is an architecture used to separate a monolithic application into several independent services. These services are loosely connected and can be deployed independently, yet offer a cohesive experience to the end-user. Microservices are derivative of service-oriented architectures, as they break an application into a series of modules, each responsible for a unique function.

Advantages:
- Ease of understanding: With added simplicity, developers can better understand the functionality of a service.
- Smaller and faster deployments: Smaller codebases and scope = quicker deployments
- Scalability: Since your services are separate, you can more easily scale the most needed ones at the appropriate times, as opposed to the whole application
- Eliminate vendor or technology lock-in: Microservices provide the flexibility to try out a new technology stack on an individual service as needed.
- Improved fault isolation: Larger applications can remain mostly unaffected by the failure of a single module.
Disadvantages:
- Microservices are more complex
- Microservices are often more expensive (More services equals more resources)
- Global testing is difficult
- Microservices can present security threats
- Large vs small product companies: Microservices are great for large companies, but can be slower to implement and too complicated for small companies
#### What is Separation of Concerns?
Separation of concerns (SoC) is a design principle for separating a computer program into distinct sections such that each section addresses a separate concern. At a low level, this principle is closely related to the Single Responsibility Principle of object oriented programming. For example the business logic of the application is a concern and the user interface is another concern. Changing the user interface should not require changes to business logic and vice versa. The design will be more maintainable, less tightly coupled, and less likely to violate the Don’t Repeat Yourself principle. When concerns are well-separated, individual sections can be reused, as well as developed and updated independently. At an architectural level, separation of concerns is a key component of building layered applications.

#### What is a layered design and why is it important in enterprise applications?
Modern enterprise applications  can be large and daunting. The sheer amount of users, data, transactions, options, business cases, components, interacting systems, and a host of other factors, make designing business applications require a great deal of expertise. There are many examples of enterprise software that grew too complex, unmanageable, and fragile due to implementation, that did not account for change. It is for this reason that an effective enterprise application should be divided into layers. By defining each layer to have a separate responsibility, you achieve separation of concerns. 
#### What is Dependency Injection?
Dependency injection is a technique whereby one object supplies the dependencies of another object. Dependency injection is basically providing the objects that an object needs (its dependencies) instead of having it construct them itself. 

Dependencies can be injected into objects by many means:
1. constructor injection
2. setter injection
3. interface injection
4. dependency injection frameworks (e.g. Spring)

So now its the dependency injection’s responsibility to:

- Create the objects
- Know which classes require those objects
- And provide them all those objects

If there is any change in objects, then DI looks into it and it should not concern the class using those objects. This way if the objects change in the future, then its DI’s responsibility to provide the appropriate objects to the class.

Inversion of control —the concept behind DI
This states that a class should not configure its dependencies statically but should be configured by some other class from outside.

Benefits of using DI:
- Helps in Unit testing.
- Boiler plate code is reduced, as initializing of dependencies is done by the injector - component.
- Extending the application becomes easier.
- Helps to enable loose coupling, which is important in application programming.
#### What is the DAO pattern? When and how to implement?
The Data Access Object (DAO) pattern is a structural pattern that allows us to isolate the application / business layer from the persistence layer (usually a relational database, but it could be any other persistence mechanism) using an abstract API. The functionality of this API is to hide from the application all the complexities involved in performing CRUD operations in the underlying storage mechanism. This permits both layers to evolve separately without knowing anything about each other.

The participants in Data Access Object Pattern:

- **Data Access Object Interface** - The interfaces which provides a flexible design. This interface defines the standard operations to be performed on a model object(s).

- **Data Access Object concrete class** - This class implements above interface. This class is responsible to get data from a data source which can be database / xml or any other storage mechanism.

- **Model Object or Value Object** - The model which is transferred from one layer to the other. This object is simple POJO containing get/set methods to store data retrieved using DAO class.

**Example:**
With above mentioned components, let’s try to implement the DAO pattern. We will use 3 components here:

- The Book model which is transferred from one layer to the other.
- The BookDao interface that provides a flexible design and API to implement.
- BookDaoImpl concrete class that is an implementation of the BookDao interface.

![alt text](https://cdn.journaldev.com/wp-content/uploads/2017/11/DAO-Pattern.png "dao")

#### What is SOA? When to use?

### Testing
#### What are unit test, integration test, system test, regression test, acceptance test? What is the major difference between these?
**Unit test:** The goal of Unit testing is to test each unit separately and ensure that each unit is working as expected. The unit test cases writing and execution is done by the developer (not the tester) to make sure that individual units are working as expected. The scope of Unit testing is narrow, it covers the Unit or small piece of code under test. The smallest part of individual components like functions, procedures, classes, interfaces etc.  The main intention of this activity is to check whether units are working as per design and handling error and exception more neatly. The both positive and negative conditions should handle properly. Unit tests should have no dependencies on code outside the unit tested. Complex dependencies and interactions to the outside world are stubbed or mocked. This is very first step in level of testing and started before doing integration testing.

**Integration test:** Once all modules are developed and integrated with other modules then Integration testing is to be carried out to discover the issues arise when different modules are interacting with each other to build overall system. Integration testing is a type of testing to check if different pieces of the modules are working together. The scope of Integration testing is wide, it covers the whole application under test and it requires much more effort to put together. Integration testing is dependent on other outside systems like databases, hardware allocated for them etc. 

**System test:** System testing is the type of testing to check the behaviour of a complete and fully integrated software product based on the software requirements specification (SRS) document. The main focus of this testing is to evaluate Business / Functional / End-user requirements. This is black box type of testing where external working of the software is evaluated with the help of requirement documents & it is totally based on Users point of view. For this type of testing do not required knowledge of internal design or structure or code. This testing is to be carried out only after System Integration Testing is completed. In the integration testing testers are concentrated on finding bugs/defects on integrated modules. But in the Software System Testing testers are concentrated on finding bugs/defects based on software application behavior, software design and expectation of end user. 

**Regression test:** Regression testing is type of testing carried out to ensure that changes made in the fixes or any enhancement changes are not impacting the previously working functionality. It is executed after enhancement or defect fixes in the software or its environment.

**Acceptance test:** User acceptance is a type of testing performed by the Client to certify the system with respect to the requirements that was agreed upon.  This is beta testing of the product & evaluated by the actual end users. The main purpose of this testing is to validate the end to end business flow.

![alt text](http://e8c5h7a9.stackpathcdn.com/wp-content/uploads/2012/09/levels-of-testing.jpg
 "testing")

#### What is code coverage? Why is it used? How you can measure?
Code Coverage is a measurement of how many lines / blocks / arcs of your code are executed while the automated tests are running. 

#### What does mocking mean? How would you do it 'manually' (i. e. without using any fancy framework)?
Mocking is primarily used in unit testing. An object under test may have dependencies on other (complex) objects. To isolate the behavior of the object you want to replace the other objects by mocks that simulate the behavior of the real objects. This is useful if the real objects are impractical to incorporate into the unit test. In short, mocking is creating objects that simulate the behavior of real objects.

#### What is a test case? What is an assertion? Give examples!
An assertion is a boolean expression at a specific point in a program which will be true unless there is a bug in the program. A test assertion is defined as an expression, which encapsulates some testable logic specified about a target under test. Usually the logic for each test assertion is limited to one single aspect specified. An assertion allows testing the correctness of any assumptions that have been made in the program. If an assertion fails, the method call does not return and an error is reported. If a test contains multiple assertions, any that follow the one that failed will not be executed. For this reason, it's usually best to try for one assertion per test.

Example:

public int Add (int num1, int num2)
{
    return num1 + num2 
}


int expected = 5
Int actual = Add(2, 3)

Assert.AreEqual(expected, actual);
#### What is TDD? What are the benefits?
TDD is an innovative software development approach where tests are written before writing the bare minimum of code required for the test to be fulfilled. The code will then be refactored, as often as necessary, in order to pass the test, with the process being repeated for each piece of functionality. With TDD, tests will be automated, saving a lot of time compared to manually testing functionality. Writing tests, followed by minimum code changes after each test run, will make sure there is good unit test coverage for the software which will again contribute to the overall quality of the product. Tests written ahead of time will also ensure good code quality.

#### What are the unit testing best practices? (Eg. how many assertion should a test case contain?)
1. Naming your tests: The name of your test should consist of three parts:
- The name of the method being tested.
- The scenario under which it's being tested.
- The expected behavior when the scenario is invoked.

For example: Add_SingleNumber_ReturnsSameNumber()

2. Avoid logic in tests: When writing your unit tests avoid manual string concatenation and logical conditions such as if, while, for, etc.
3. Check only a single thing in one test method (practically: use 1 assert per test method)
4. Never push a failing test to the repository. (Use @Ignore if really necessary.)
5. Use separate folder for tests as you might not want to deliver (ie. give to the user) your test along with the production code.

#### What is arrange/act/assert pattern?
Arrange, Act, Assert is a common pattern when unit testing. As the name implies, it consists of three main actions:
1. **Arrange** your objects, creating and setting them up as necessary.
2. **Act** on an object.
3. **Assert** that something is as expected.

``` C#
public void Add_EmptyString_ReturnsZero()
{
    // Arrange
    var stringCalculator = new StringCalculator();

    // Act
    var actual = stringCalculator.Add("");

    // Assert
    Assert.Equal(0, actual);
}
```

### DevOps
#### What is continuous integration? Why is CI important?
Continuous Integration (CI) is a development practice that requires developers to integrate code into a shared repository several times a day. Each check-in is then verified by an automated build, allowing teams to detect problems early. By integrating regularly, you can detect errors quickly, and locate them more easily. Integrate as often as possible, this will lead to small or non-existent merge conflicts and bugs.
#### Why are tests important in the CI workflow?
Developers practicing continuous integration merge their changes back to the main branch as often as possible. The developer's changes are validated by creating a build and running automated tests against the build. By doing so, you avoid the integration hell that usually happens when people wait for release day to merge their changes into the release branch.

Continuous integration puts a great emphasis on testing automation to check that the application is not broken whenever new commits are integrated into the main branch.

A nicely working CI process needs the following:

- Good unit testing coverage
- Automation: tests need to run with every commit / merge automatically.
- Ideally many kinds of tests: integration testing, UI testing, acceptance testing.

#### Name some software that help the CI workflow!
The most popular CI tools are:

- Jenkins
- Travis
- Lots of hosted CI services: Gitlab CI, AWS CI, Microsoft VSTS CI...
#### What is Continuous Delivery?
Continuous delivery is an extension of continuous integration to make sure that you can release new changes to your customers quickly in a sustainable way. This means that on top of having automated your testing, you also have automated your release process and you can deploy your application at any point of time by clicking on a button.
#### What is Continuous Deployment?
Continuous deployment goes one step further than continuous delivery. With this practice, every change that passes all stages of your production pipeline is released to your customers. There's no human intervention, and only a failed test will prevent a new change to be deployed to production.

Continuous deployment is an excellent way to accelerate the feedback loop with your customers and take pressure off the team as there isn't a Release Day anymore. Developers can focus on building software, and they see their work go live minutes after they've finished working on it.
#### What is DevOps?
DevOps (a compound word made from "Development" and "Operations") is a new practice and job role in Software development that emerged from the birth of the cloud and agile methodologies. It can be seen as an evolution of the SysAdmin role, but requires much more knowledge.

Typical tasks of a DevOps person is everything IT related except actually writing the software. In practice this means the following:
- Build systems that enable CI/CD workflows
- Manage the "cloud", set up its infrastructure, security, install and configure apps
- Make sure that there are monitoring and alerting systems in place in case of issues
- Automate everything: deployments, releases, upgrades.

### Software Methodologies
#### What kind of software-lifecycle models do you know?
A software lifecycle model is a standardised format for planning, organising and running a new development project. 

Agile, Lean, Waterfall, Iterative, Spiral, DevOps, Extreme Programming, Rapid Prototyping
#### What is a UML diagram? What kind of diagram types do you know?
The Unified Modeling Language is a standard visual modeling language intended to be used for modeling business and similar processes, analysis, design, and implementation of software-based systems. UML is a common language for business analysts, software architects and developers used to describe, specify, design, and document existing or new business processes, structure and behavior of artifacts of software systems.

There are two main categories; structure diagrams and behavioral diagrams:
1. Structure Diagrams
- Class Diagram
- Component Diagram
- Deployment Diagram
- Object Diagram
...

2. Behavioral Diagrams
- Use Case Diagram
- Activity Diagram
- State Machine Diagram
- Sequence Diagram
- Communication Diagram
- Timing Diagram
...
#### What is a UML class diagram? What are the typical elements?
A class diagram in the Unified Modeling Language (UML) is a type of static structure diagram that describes the structure of a system by showing the system's classes, their attributes, methods, and the relationships among objects.

The class diagram is the main building block of object-oriented modeling.

Elements:
- Class
- Attribute
- Generalization
- Association
- Multiplicity
- Aggregation
#### What kind of design patterns do you know? Bring at least 3 examples.
**Factory Pattern** - In Factory pattern, we create object without exposing the creation logic to the client and refer to newly created object using a common interface.

**Singleton Pattern** - This pattern involves a single class which is responsible to create an object while making sure that only single object gets created. This class provides a way to access its only object which can be accessed directly without need to instantiate the object of the class.

**Iterator Pattern** - This pattern is used to get a way to access the elements of a collection object in sequential manner without any need to know its underlying representation. The elements of an aggregate object can be accessed and traversed without exposing its representation (data structures).

**MVC Pattern** - MVC Pattern stands for Model-View-Controller Pattern. This pattern is used to separate application's concerns. 
#### What is the purpose of the Iterator Pattern?
This pattern is used to get a way to access the elements of a collection object in sequential manner without any need to know its underlying representation. The elements of an aggregate object can be accessed and traversed without exposing its representation (data structures).
#### What do you know about the SOLID principles?
These 5 principles were introduced by Robert C. Martin (Uncle Bob), in his 2000 paper Design Principles and Design Patterns. The intention of these principles is to make software designs more understandable, easier to maintain and easier to extend.

**S — Single responsibility principle**
Every module or class should have responsibility over a single part of the functionality provided by the software.

**O — Open/closed principle**
"Software entities ... should be open for extension, but closed for modification."
We can make sure that our code is compliant with the open/closed principle by utilizing inheritance and/or implementing interfaces that enable classes to polymorphically substitute for each other.

**L — Liskov substitution principle**
"Objects in a program should be replaceable with instances of their subtypes without altering the correctness of that program."
If S is a subtype of T, then objects of type T may be replaced (or substituted) with objects of type S. More generally it states that objects in a program should be replaceable with instances of their subtypes without altering the correctness of that program.

**I — Interface segregation principle**
"Many client-specific interfaces are better than one general-purpose interface."
No client should be forced to depend on methods it does not use. Put more simply: Do not add additional functionality to an existing interface by adding new methods. Instead, create a new interface and let your class implement multiple interfaces if needed.

**D - Dependency inversion principle**
"One should "depend upon abstractions, [not] concretions."
Dependency inversion principle is a way to decouple software modules. This principle states that High-level modules should not depend on low-level modules. Both should depend on abstractions. Abstractions should not depend on details. Details should depend on abstractions.

#### How would you separate data storage code and business logic code (which uses stored data) in an application?
I would use MVC design pattern

## Computer science

### Data Structures
#### What is the difference between Stack and Queue data structure?
#### What is a graph? What are simple graphs? What are directed graphs? What are weighted graphs?
#### What are trees? What are binary trees? What are binary search trees?
#### How can you store graphs in programs? What are the advantages/disadvantages per each?
#### What are graph traversal algorithms? What is BFS, how does it work? What is DFS, how does it work?
#### How does dictionary work?
#### Why is it important for keys in a hashmap to have an immutable type? (Consider string for example.)

### Algorithms
#### What is QuickSort? Describe the main logic of this sorting algorithm.

## Software design

### Security

#### What is OAuth2?
OAuth 2 is an authorization framework that enables applications to obtain limited access to user accounts on an HTTP service, such as Facebook, GitHub, Amazon... It works by delegating user authentication to the service that hosts the user account, and authorizing third-party applications to access the user account. It is commonly used as a way for Internet users to grant websites or applications access to their information on other websites but without giving them the passwords. OAuth essentially allows access tokens to be issued to third-party clients by an authorization server, with the approval of the resource owner. The third party then uses the access token to access the protected resources hosted by the resource server. OAuth 2 provides authorization flows for web and desktop applications, and mobile devices.

![alt text](https://assets.digitalocean.com/articles/oauth/abstract_flow.png
 "oauth")

#### What is Basic Authentication?
#### What is CORS, why it’s needed in browsers?
Cross-Origin Resource Sharing (CORS) is a mechanism that uses additional HTTP headers to tell browsers to give a web application running at one origin, access to selected resources from a different origin. A web application executes a cross-origin HTTP request when it requests a resource that has a different origin (domain, protocol, or port) from its own. An example of a cross-origin request: the front-end JavaScript code served from https://domain-a.com uses XMLHttpRequest to make a request for https://domain-b.com/data.json.

CORS is a way to bypass the "Same Origin Policy" which is the security measure preventing you from making ajax requests to a different domain.

**Same Origin Policy**
For security reasons, browsers restrict cross-origin HTTP requests initiated from scripts. The Same Origin Policy states that a website on one domain cannot make an xhr request to another domain. This prevents a malicious website from making requests to a known website (think Facebook or Google). For example, XMLHttpRequest and the Fetch API follow the same-origin policy.

#### How can you initialize a CSRF attack?
#### What is JWT used for? Where to store it on client side?
JSON Web Token (JWT) is an Internet standard for creating JSON-based access tokens that assert some number of claims. For example, a server could generate a token that has the claim "logged in as admin" and provide that to a client. The client could then use that token to prove that it is logged in as admin. The tokens are signed by one party's private key (usually the server's), so that both parties (the other already being, by some suitable and trustworthy means, in possession of the corresponding public key) are able to verify that the token is legitimate.

In authentication, when the user successfully logs in using their credentials, a JSON Web Token will be returned and must be saved locally (typically in local or session storage, but cookies can also be used), instead of the traditional approach of creating a session in the server and returning a cookie.

### Threaded programming

#### When do you need to use threads in an application?
Multithreading is a widespread programming and execution model that allows multiple threads to exist within the context of one process. These threads share the process's resources, but are able to execute independently. The threaded programming model provides developers with a useful abstraction of concurrent execution. Multithreaded applications have the following advantages:
- Responsiveness
- Faster execution
- Lower resource consumption
- Parallelization: applications looking to use multicore or multi-CPU systems can use multithreading to split data and tasks into parallel subtasks and let the underlying architecture manage how the threads run

#### What is a daemon thread?
Daemon thread is a low priority thread that runs in background to perform tasks such as garbage collection. Traditionally daemon processes in UNIX were those that were constantly running in background, much like services in Windows. A daemon thread in Java is one that doesn't prevent the JVM from exiting. Specifically the JVM will exit when only daemon threads remain.

#### What is the difference between concurrent and parallel execution of code?
Concurrency and parallelism are two related but distinct concepts.

**Concurrency** means that two or more calculations happen within the same time frame, and there is usually some sort of dependency between them. It's a form of computing in which several computations are executed during overlapping time periods — concurrently —instead of sequentially. A concurrent system is one where a computation can advance without waiting for all other computations to complete. (async-await)

**Parallelism** means that two or more calculations happen simultaneously. Parallel programming means using a set of resources to solve some problem in less time by dividing the work. This is the abstract definition and it relies on this part: solve some problem in less time by dividing the work (source). Code running in parallel can utilize threads, but code can be executed on different physical machines as well, crossing "thread-boundaries" (cluster)

Put boldly, concurrency describes a problem (two things need to happen together), while parallelism describes a solution (two processor cores are used to execute two things simultaneously).

#### What is the most important problem developers are faced when using threads?
- Resource contention - a conflict over access to a shared resource 
- Race condition - because resource contention exists program can and do arise when multiple threads are executing. They're racing for accessing a database or file. 
- Synchronization. With the use of Locks, Semaphores, Queues, etc. programmers can avoid or control race conditions.
- Deadlock - a deadlock occurs when a thread enters a waiting state because a requested system resource is held by another waiting process.

#### In what kind of situations can deadlocks occur?
A deadlock occurs when a thread enters a waiting state because a requested system resource is held by another waiting process, which in turn is waiting for another resource held by another waiting process. Held in this context means that there's some locking or synchronization in place. A deadlock is a state in which each member of a group is waiting for another member, including itself, to take action, such as sending a message or more commonly releasing a lock. Deadlock is a common problem in multiprocessing systems, parallel computing, and distributed systems, where software and hardware locks are used to arbitrate shared resources and implement process synchronization

#### What are possible ways to prevent deadlocks from occurring?
Deadlock prevention works by preventing one of the four Coffman conditions from occurring.

- Eliminate Mutual Exclusion: no process will have exclusive access to a resource. Algorithms that avoid mutual exclusion are called non-blocking synchronization algorithms.
- Eliminate Hold and wait: requiring processes to request all the resources they will need before starting up. 
- Eliminate No Preemption: Preempt resources from the process when resources required by other high priority processes.
- Eliminate Circular Wait: disabling interrupts during critical sections and using a hierarchy to determine a partial ordering of resources. Each resource will be assigned with a numerical number. A process can request the resources in the order of numbering.

#### What does critical section or critical region mean in the context of concurrent programming?
In concurrent programming, concurrent accesses to shared resources can lead to unexpected behavior, so parts of the program where the shared resource is accessed need to be protected in ways that avoid the concurrent access. This protected section is the critical section or critical region. It cannot be executed by more than one process at a time. Typically, the critical section accesses a shared resource, such as a data structure, a peripheral device, or a network connection, that would not operate correctly in the context of multiple concurrent accesses.