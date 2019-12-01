# General enterprise questions

## Software engineering

### Architectures

#### What is n-tier (or multi-tier) architecture?
#### What are microservices? Advantages and disadvantages?
#### What is Separation of Concerns?
#### What is a layered design and why is it important in enterprise applications?
#### What is Dependency Injection?
#### What is the DAO pattern? When and how to implement?
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
#### What is Basic Authentication?
#### What is CORS, why it’s needed in browsers?
#### How can you initialize a CSRF attack?
#### What is JWT used for? Where to store it on client side?

### Threaded programming

#### When do you need to use threads in an application?
#### What is a daemon thread?
#### What is the difference between concurrent and parallel execution of code?
#### What is the most important problem developers are faced when using threads?
#### In what kind of situations can deadlocks occur?
#### What are possible ways to prevent deadlocks from occurring?
#### What does critical section or critical region mean in the context of concurrent programming?
