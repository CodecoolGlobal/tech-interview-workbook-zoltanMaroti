# Enterprise module (C# branch)

### ASP.NET Core, WCF

#### What Is the difference between .NET Core and .NET Standard? How do them relate to “classic” .NET?
**.NET Standard**
The .NET Standard is a specification and not a .NET implementation. It specifies a set of APIs that all the .NET implementations have to implement. The Base Class Library (BCL) contains classes such as exception handling, strings, XML, I/O, networking, and collections. .NET Standard is a specification for implementing the BCL. We can create only class library type projects with it. Framework Class Libraries (FCL) such as WPF, WCF, and ASP.NET are not part of the BCL, and therefore are not included in .NET Standard. .NET Framework, Xamarin, and .NET Core each implement .NET Standard for the BCL in their managed framework.

**.NET Core**
.NET Core is a free, cross-platform, open source implementation of .NET, which runs on Windows, Linux, and macOS. Its open-source and Microsoft accepts third party contribution to .NET Core. It supports four types of applications: console, ASP.NET Core, cloud, and Universal Windows Platform (UWP). Windows Forms and Windows Presentation Foundation(WPF) are not part of .NET Core. 
A .Net Core Class Library is built upon the .Net Standard. 
#### What is ASP.NET MVC?
The ASP.NET MVC is a discontinued web application framework developed by Microsoft, which implements the model–view–controller (MVC) pattern. ASP.NET Core has since been released, MVC 6 was abandoned due to Core and is not expected to be released. ASP.NET MVC allows software developers to build a web application as a composition of three roles: Model, View and Controller. The MVC model defines web applications with 3 logic layers:

- Model (business layer)
- View (display layer)
- Controller (input control)

The ASP.NET MVC framework couples the models, views, and controllers using interface-based contracts, thereby allowing each component to be tested independently.

The Model-View-Controller (MVC) architectural pattern separates an application into three main groups of components: Models, Views, and Controllers. This pattern helps to achieve separation of concerns. Using this pattern, user requests are routed to a Controller which is responsible for working with the Model to perform user actions and/or retrieve results of queries. The Controller chooses the View to display to the user, and provides it with any Model data it requires.
#### Can you explain Model, Controller and View in MVC?
**Model**
An MVC model contains all of your application logic that is not contained in a view or a controller. The model should contain all of your application business logic, validation logic, and database access logic.

**View**
A view contains the HTML markup and content that is sent to the browser. A view is the equivalent of a page when working with an ASP.NET MVC application. A view should contain only logic related to generating the user interface. 

**Controller**
A controller is responsible for controlling the way that a user interacts with an MVC application. A controller contains the flow control logic for an ASP.NET MVC application. A controller determines what response to send back to a user when a user makes a browser request. A controller should only contain the bare minimum of logic required to return the right view or redirect the user to another action (flow control). Everything else should be contained in the model. 

In general, you should strive for fat models and skinny controllers. Your controller methods should contain only a few lines of code. If a controller action gets too fat, then you should consider moving the logic out to a new class in the Models folder.
#### Explain the page lifecycle of MVC.
The ASP.NET Core MVC Request Life Cycle is a sequence of events, stages or components that interact with each other to process an HTTP request and generate a response that goes back to the client.

![alt text](https://www.c-sharpcorner.com/article/asp-net-core-mvc-request-life-cycle/Images/Picture1.png "request pipeline")

**1. Middleware**
Middleware component forms the basic building block of application HTTP pipeline. These are a series of components that are combined to form a request pipeline in order to handle any incoming request. Whenever a new request comes, it is passed to the first middleware component. The component then decides, whether to generate a response after handling that incoming request or to pass it to the next component. The response is sent back along these components, once the request has been handled.

**2. Routing**
Routing is a middleware component that implements MVC framework. The routing Middleware component decides how an incoming request can be mapped to Controllers and actions methods, with the help of convention routes and attribute routes. Routing bridges middleware and MVC framework by mapping incoming request to controller action methods. MVC provides default routes that are given a name and a template to match incoming request URLs. The Controllers and action variables are placeholders that are replaced by matching segments of the URL.

**3. Controller Initialization**
At this stage of ASP.NET MVC Core Request Life Cycle, the process of initialization and execution of controllers takes place. Controllers are responsible for handling incoming requests. The controller factory is the component that is responsible for creating controller instance. The controller selects the appropriate action methods on the basis of route templates provided. A controller class inherits from controller base class.

**4. Action method execution**
All the public methods of a Controller class are called Action methods. They are like any other normal methods with the following restrictions:

- Action method must be public. It cannot be private or protected
- Action method cannot be overloaded
- Action method cannot be a static method.

After the controllers are initialized, the action methods are executed. Controllers contain Action methods whose responsibility is to generate a response to an incoming request Action method inside controller classes executes logic to create Action Result. Action methods return objects that implements the IActionResult interface from the Microsoft.AspNetCore.Mvc namespace. The various types of response from the controller such as rendering a view or redirecting the client to another URL, all these responses are handled by IActionResult object, commonly known as action result.

**5. Result Execution**
The action method returns action result. If an action method returns a view result, the MVC view engine renders a view and returns the HTML response. If result is not of view type, then action method will generate its own response.
Different types of action result are: ViewResult, ContentResult, JsonResult, HttpNotFoundResult...
#### What is Razor View Engine?
Razor View engine is a markup syntax which helps us to create dynamic web pages with the C#. Razor is a templating engine and ASP.NET MVC has implemented a view engine which allows us to use Razor inside of an MVC application to produce HTML.
#### What you mean by Routing in MVC?
Routing is a mechanism in MVC that decides which action method of a controller class to execute. Without routing there's no way an action method can be mapped. to a request. Routing is a part of the MVC architecture so ASP.NET MVC supports routing by default. ASP.NET introduced Routing to eliminate needs of mapping each URL with a physical file. Routing enable us to define URL pattern that maps to the request handler.
#### What is Layout in MVC?
Layouts are used in MVC to provide a consistent look and feel on all the pages of our application. Most web apps have a common layout that provides the user with a consistent experience as they navigate from page to page. The layout typically includes common user interface elements such as the app header, navigation or menu elements, and footer. All of these shared elements may be defined in a layout file, which can then be referenced by any view used within the app. Layouts reduce duplicate code in views. 
#### What ConfigureServices() method does in Startup.cs?
ASP.NET Core apps use a Startup class, which is named Startup by convention. The Startup class includes a ConfigureServices method to configure the app's services. A service is a reusable component that provides app functionality. Services are registered in ConfigureServices and consumed across the app via dependency injection (DI) or ApplicationServices. The Startup class also includes a Configure method to create the app's request processing pipeline. ConfigureServices and Configure are called by the ASP.NET Core runtime when the app starts.
#### What Configure() method does in Startup.cs?
The Startup class also includes a Configure method to create the app's request processing pipeline. ConfigureServices and Configure are called by the ASP.NET Core runtime when the app starts. The Configure method is used to specify how the app responds to HTTP requests. The request pipeline is configured by adding middleware components to an IApplicationBuilder instance.
#### What is wwwroot folder in ASP.NET Core?
wwwroot folder stores all of the static files in your project.  These are assets that the app will serve directly to clients, including HTML files, CSS files, image files, and JavaScript files. The wwwroot folder is the root of your web site. 
#### What’s the usage of [InternalsVisibleTo] attribute? What are pros and cons of it?
If your code contains classes, interfaces or structs that have the internal (c#) access qualifier, you cannot access them from another assembly (e.g. unit testing). But what if you need to make them visible just for a specific assembly? Thats where the assembly InternalsVisibleTo attribute comes into play. It gives you the ability to expose methods / classes marked internal to a specific assembly.
#### Explain what is WCF?
Windows Communication Foundation (WCF) is a framework for building service-oriented applications. Using WCF, you can send data as asynchronous messages from one service endpoint to another. A service endpoint can be part of a continuously available service hosted by IIS, or it can be a service hosted in an application. An endpoint can be a client of a service that requests data from a service endpoint. The messages can be as simple as a single character or word sent as XML, or as complex as a stream of binary data.
#### Mention what is the endpoint in WCF and what are the three major points in WCF?
A service endpoint can be part of a continuously available service hosted by IIS, or it can be a service hosted in an application. An endpoint can be a client of a service that requests data from a service endpoint.
1. Address — Specifies the location of the service which will be like http://Myserver/MyService.Clients will use this location to communicate with our service.
2. Contract — Specifies the interface between client and the server. It’s a simple interface with some attribute.
3. Binding — Specifies how the two parties will communicate in term of transport and encoding and protocols
#### Object Relational Mapping, Entity Framework
#### What is an ORM? What are benefits, when to use?
An ORM or Object-Relational Mapping is a software technique or library to create an abstraction between your application and the database, so that you can do away with writing native SQL of your database. By using an ORM, your app can achieve a certain level of database-independence, which is probably the biggest and most popular benefit of an ORM. You can, in effect, replace your back end from MySQL to Oracle or even Microsoft SQL Server with minimal configuration changes to your app if you are accessing the database through an ORM library instead of directly (native SQL dialect). Object-Relational Mapping is a technique that lets you query and manipulates data from a database using an object-oriented paradigm. ORMs can be thought of as a translator converting our code from one form to another. The ORM software generates objects (as in OOP) that virtually map (like the map of a city) the tables in your database. Then the programmer would use these objects to interact and play with the database.

Advantages:
- Speeds-up Development - eliminates the need for repetitive SQL code.
- Reduces Development Time.
- They make the code easier to update, maintain, and reuse as the developer can think of, and manipulate data as objects
- ORMs provide the concept of Database Abstraction which makes switching databases easier and creates a consistent code base for your application.
- ORMs will shield your application from SQL injection

Disadvantages:
- Loss in developer productivity whilst they learn to program with ORM.
- Developers lose understanding of what the code is actually doing - the developer is more in control using SQL.
- ORM has a tendency to be slow.
- ORM fail to compete against SQL queries for complex queries.
#### What is Entity Framework? What are the advantages, limitations?
Entity Framework is an open-source ORM framework for .NET applications supported by Microsoft. It enables developers to work with data using objects of domain specific classes without focusing on the underlying database tables and columns where this data is stored. With the Entity Framework, developers can work at a higher level of abstraction when they deal with data, and can create and maintain data-oriented applications with less code compared with traditional applications.

Official Definition: “Entity Framework is an object-relational mapper (O/RM) that enables .NET developers to work with a database using .NET objects. It eliminates the need for most of the data-access code that developers usually need to write.”

Advantages:
- One common syntax (LINQ) for all object queries
- easy to implement SoC
- less coding required to accomplish complex tasks
- Its fast and straight forward using LINQ/FE objects For Add/Modify/Delete/Update
- It keeps a good performance when you work with a small / middle domain model
- Provide Auto Migrations: easier to set up or modify the database

Limitations:
- Scalability: It is not good for huge domain model.
- Slow Performance of Entity Framework.
- Lazy loading is the main drawbacks of EF
- It is not available for every RDMS
- Need to handle data in nontraditional way
- It does not work if we change any schema of the database. We need to update the schema on the solution.
#### What is lazy loading?
Lazy loading is a design pattern commonly used in computer programming to defer initialization of an object until the point at which it is needed. Lazy Loading is a programming practice in which you only load or initialize an object when you first need it. This can potentially give you a big performance boost, especially if you have a lot of components in your application. 

Example in web:
It is an optimization technique for the online content, be it a website or a web app. Instead of loading the entire web page and rendering it to the user in one go as in bulk loading, the concept of lazy loading assists in loading only the required section and delays the remaining, until it is needed by the user.

Advantages of Lazy loading:
- On-demand loading reduces time consumption and memory usage thereby optimizing content delivery.
- Unnecessary code execution is avoided.
#### What is the difference between code first and DB first approach?
**Code First Approach**
The Code-First approach allows the developer to define model objects using only standard classes, without the need of any design tool, XML mapping files, or cumbersome piles of autogenerated code. We can say that going Code-First means writing the Data Model entity classes we’ll be using within our project and let Entity Framework generate the Database accordingly. Code First is a very popular approach and has full control over the code rather than database activity. In this approach, we can do all the database operations from the code and manual changes to database have been lost and everything is depending on the code. You need to create POCO entities as data model. Code-First uses migrations to create the database from the data model you define.

**Database-First**
Database first approach is used when database is ready then Entity Framework will complete his duty and create POCO entities for you. If you have already a designed database and you don't want to do extra effort then you can go with this approach. You can modify the database manually and update model from database. So, we can say, entity framework is able to create your model classes based on tables and columns from relational database.

Code first creates an in-memory model based on attributes on classes and/or fluent mappings in code.
Database and Model first create an in-memory model based on a .EDMX file, which is then used to generate classes.
Code first: Coding the POCOs first (the conceptual model) then generating the database (migrations);
Database-First: Given an existing database, manually coding the POCOs to match. (The difference here being that the POCOs are not automatically generated give then existing database). 
#### What is a migration script?
Whereas a build script creates a database, a migration script, or ‘change’ script, alters a database. It is called a migration script because it changes all or part of a database from one version to another. It ‘migrates’ it between versions. This alteration can be as simple as adding or removing a column to a table, or a complex refactoring task such as splitting tables or changing column properties in a way that could affect the data it stores.
#### What is a navigation property?
In Entity Framework, an entity can be related to other entities through an association or relationship. Each relationship contains two ends that describe the entity type and the multiplicity of the type (one, zero-or-one, or many) for the two entities in that relationship. 

Navigation properties provide a way to navigate an association between two entity types. Every object can have a navigation property for every relationship in which it participates. Navigation properties allow you to navigate and manage relationships in both directions, returning either a reference object (if the multiplicity is either one or zero-or-one) or a collection (if the multiplicity is many). 
#### Name 3 different attributes used in EF Core, what can they do for you?
Attributes are a kind of tag that you can place on a class or property to specify metadata about that class or property.

Table - The database table and/or schema that a class is mapped to.
Column - The database column that a property is mapped to.
ForeignKey - Specifies the property is used as a foreign key in a relationship.
NotMapped - Applied to properties or classes that are to be excluded from database mapping.