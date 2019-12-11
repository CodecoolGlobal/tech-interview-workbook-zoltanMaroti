# General enterprise questions

## Software engineering

### Architectures

#### What is n-tier (or multi-tier) architecture?
#### What are microservices? Advantages and disadvantages?
#### What is Separation of Concerns?
Separation of concerns is a software architecture design pattern / principle for separating an application into distinct sections, so each section addresses a separate concern. Separation of concerns is the idea that each module or layer in an application should only be responsible for one thing and should not contain code that deals with other things. It reduces code complexity by breaking a large application down into many smaller units of encapsulated functionality. It is achieved by the establishment of boundaries. A boundary is any logical or physical constraint which delineates a given set of responsibilities. Some examples of boundaries would include the use of methods, objects, components, and services to define core behavior within an application; projects, solutions, and folder hierarchies for source organization; application layers and tiers for processing organization.

Separation of concerns - advantages:
- Lack of duplication and singularity of purpose - the overall system easier to maintain.
- The system becomes more stable as a byproduct of the increased maintainability.
- The decoupling which results from requiring components to focus on a single purpose leads to components which are more easily reused in other systems, or different contexts within the same system.

#### What is a layered design and why is it important in enterprise applications?
#### What is Dependency Injection?
Dependency Injection is passing dependency to other objects or framework (dependency injector). Dependency injection is basically providing the objects that an object needs (its dependencies) instead of having it construct them itself. It's a very useful technique for testing, since it allows dependencies to be mocked or stubbed out. The intent behind dependency injection is to achieve Separation of Concerns of construction and use of objects. This can increase readability and code reuse. Dependency injection separates the creation of a client's dependencies from the client's behavior, which allows program designs to be loosely coupled and to follow the dependency inversion and single responsibility principles.

```c#
public SomeClass() {
    myObject = Factory.getObject();
}
```

**Problem:** If myObject involves services such as disk access or network access, it is hard to do unit test on SomeClass(). Programmers have to mock myObject.

**Alternative solution:** Passing myObject in as an argument to the constructor.

```c#
public SomeClass (MyClass myObject) {
    this.myObject = myObject;
}
```

Dependencies can be injected into objects by many means (such as constructor injection or setter injection). One can even use specialized dependency injection frameworks (e.g. Spring) to do that, but they certainly aren't required.

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
#### Why are tests important in the CI workflow?
#### Name some software that help the CI workflow!
#### What is Continuous Delivery?
#### What is Continuous Deployment?
#### What is DevOps?

### Software Methodologies
#### What kind of software-lifecycle models do you know?
#### What is a UML diagram? What kind of diagram types do you know?
#### What is a UML class diagram? What are the typical elements?
#### What kind of design patterns do you know? Bring at least 3 examples.
#### What is the purpose of the Iterator Pattern?
#### What do you know about the SOLID principles?
#### How would you separate data storage code and business logic code (which uses stored data) in an application?

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