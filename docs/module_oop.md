# OOP questions

## Software design

### Error handling

#### What does 'fail fast' mean in terms of exception handling? Why is it a good practice?

## Computer Science

### Data structures

#### How to find the middle element of singly linked list in O(n)?
#### Given an array of integers going from 1 to 100 (both inclusive) there is a duplicated entry. How to find it?
#### What is a linked list? How to find if a linked list has a loop?
#### What is the Big O time complexity of the common operations in an ArrayList, LinkedList, HashMap? And of a bubble sort, quicksort, finding items in a Binary Search tree?
#### How does HashMap work?
#### Why is it important for keys in a map to have an immutable type? (Consider String for example.)

### Other

#### What is a garbage collector, in a nutshell?
Automatic garbage collection is the process of looking at heap memory, identifying which objects are in use and which are not, and deleting the unused objects. An in use object, or a referenced object, means that some part of your program still maintains a pointer to that object. An unused object, or unreferenced object, is no longer referenced by any part of your program. So the memory used by an unreferenced object can be reclaimed. Garbage Collection tracks each and every object available in the JVM heap space and removes unused ones. In a programming language like C, allocating and deallocating memory is a manual process. In Java, process of deallocating memory is handled automatically by the garbage collector. 

**Advantages:**
- No manual memory allocation/deallocation handling
- Automatic Memory Leak management

## Programming paradigms

### Procedural

#### What is casting? What is the difference between up vs downcasting?
#### Which order should we catch the exceptions? Why?

### Object-oriented

#### What is a class?
#### What is an object?
#### What is a constructor?
#### Do we require parameter for constructors?
#### What is an interface?
#### What are access modifiers?
#### What is data hiding?
#### Can a static method use non-static members?
#### What is the difference between hiding a static method and overriding an instance method?
#### Define the following terms: Instantiation, Attribute, Method
#### Could we access a static variable (or method) from a non-static method? Why?
#### Could we access a non-static variable (or method) from a static method? Why?
#### How many instances you have of a static variable of a given class?
#### Why is it not a good practice to write a lot of static methods?
#### What are the features of static attributes and static methods of a class? What are the benefits, when to use them?
#### What is the ‘this’ reference?
#### What are base class, subclass and superclass?
#### Draw an object oriented family (as entities, with relations) on the whiteboard.
#### Difference between overloading and overriding?
#### What are the Object Oriented Principles? Explain the concepts with realistic examples!
#### What is method overloading?
#### What is method overriding?
#### Explain how object oriented languages attempt to simplify memory management for Programmers.
#### Explain the “Single Responsibility” principle!
#### What is an object oriented program? Explain, show.
#### How do you make a class immutable? What do you need to watch out for?
#### How many instances can be created for an abstract class?

## Programming languages

### Java

#### What is autoboxing and unboxing?
#### If you have a variable, that shall store a positive whole number between 0 and 200, what primitive type would you use to store it?
#### What is the "golden rule" of variable scoping in Java? What is the lifetime of variables?
#### What is the purpose of the ‘equals()’ method?
In Java, string ```equals()``` method compares the two given strings based on the data/content of the string. If all the contents of both the strings are same then it returns true. If all characters are not matched then it returns false.

#### What is the difference between '==' and 'equals()'?
In general both equals() and “==” operator in Java are used to compare objects to check equality but here are some of the differences between the two:

- Main difference between .equals() method and == operator is that one is method and other is operator.
- We can use == operators for reference comparison (address comparison) and .equals() method for content comparison. In simple words, == checks if both objects point to the same memory location whereas .equals() evaluates to the comparison of values in the objects.

#### What does the ‘static’ keyword mean?
Everything in Java must have a type. ```static``` tells Java compiler that this is a method that is part of the class, but is not a method for any other instance of the class. We can apply java ```static``` keyword with variables, methods, blocks and nested class. ?Csak az adott osztály hívhatja meg a függvényt.?

#### Why is the main() method declared as static? Explain.
#### What is the default access modifier in a class?
Default – No keyword required: When no access modifier is specified for a class, method or data member – It is said to be having the default access modifier by default. Classes having default access modifier are accessible only within the same package.

#### What is the JVM?
Java Virtual Machine - A Java legjellemzőbb tulajdonsága, hogy a compiler által lefordított kódot (bytecode-ot) nem közvetlenül az operációs rendszer, hanem egy köztes futtatókörnyezet futtatja, ezt nevezzük JVM-nek. Ez nem egy emulációs szoftver, hanem egy szoftverréteg, amely a hordozhatóságot és a biztonságos futást valósítja meg. A Java fordító nem a célplatform, hanem a virtuális gép utasításkészletére fordítja le. A Javac (Java Compiler) a class és interface definíciókat platformfüggetlen bytecode-ra fordítja, amelyet a JVM futtat, és fordítja le a ténylegesen végrehajtható hardveres utasításkészletre (gépi kódra). Compiler: összekötő kapocs az ember által olvasható kód és a gépi kód között.

**Előnyei:**
- Hordozhatóság (“Write Once, Run Anywhere”): A program futtatható minden olyan platformon, amelyre létezik JVM.
- Biztonság (Managed code): A programok nem közvetlenül a futtató számítógépen hajtódnak végre, ezért nehezebben tudnak kárt okozni

**Megjegyzés:** A Java nemcsak nyelvnek, hanem platformnak is tekinthető: a JVM képes több bytecode-ra fordított nyelvet is futtatni, ezeket hívjuk JVM nyelveknek: Scala, Kotlin, Clojure, de létezik Pythonból is JVM-en futó változat (Jython).

![alt text](https://beginnersbook.com/wp-content/uploads/2013/05/JVM.jpg "JVM")

#### What is the difference between the JRE and the JDK?
Minden Java változat két disztribúcióban érhető el:
- **Java Runtime Environment (JRE):** A lefordított Java programok futtatásához szükséges futtatókörnyezetet (JVM) és az osztálykönyvtárat tartalmazza.
- **Java Development Kit (JDK):** A futtatókörnyezeten kívül tartalmazza a fordítót és más fejlesztői segédeszközöket it.

![alt text](https://s3.shunyafoundation.com/s3/1578452c3f66d8fd0d04d5d195328ae1359d8caa/jdk-jvm.png "JRE vs JDK")

#### What is the difference between long and Long?
#### Can a long store bigger numbers than a Long?
#### What kind of packages do you know under java.util.* ? Bring at least 3 examples.
- java.util.Arrays
- java.util.Scanner
- java.util.Collections

#### What are the access modifiers in Java? Which one could we use for class?
Access modifiers in Java helps to restrict the scope of a class, constructor, variable, method or data member. There are four types of access modifiers available in Java:

1. **Default** – No keyword required: When no access modifier is specified for a class, method or data member – It is said to be having the default access modifier by default. Having default access modifier are accessible only within the same package. >> [default] - accessible to the class and package. 
2. **Private** - The methods or data members declared as private are accessible only within the class in which they are declared. Any other class of same package will not be able to access these members. Top level Classes or interface can not be declared as private, they apply only to nested classes. >> private - accessible to the classes only.
3. **Protected:** The methods or data members declared as protected are accessible within the same package or sub classes in different packages. >> protected - accessible to class, package, and subclasses.
4. **Public:** The public access modifier has the widest scope among all other access modifiers. Classes, methods or data members which are declared as public are accessible from everywhere in the program. There is no restriction on the scope of a public data members. >> public - accessible to global.

![alt text](http://net-informations.com/java/basics/img/access-modifier.png "access modifiers")

#### Can an “enum” contain methods in Java? Explain.
#### When would you use a private/protected/public attribute? What is the difference?
#### How do you prevent developers from subclassing a class?
#### How do you prevent developers from overriding a method in a subclass?
#### How do you prevent developers from changing the value of a variable?
#### Think about money ;) How would you store a currency value, that shall support decimal parts? Think it through again, and try to think outside of the box!
#### What happens if you try to call something, that you have no access to, because of data hiding?
#### What happens if you try to delete/drop an item from an array, while you are iterating over it?
#### What happens if you try to delete/drop/add an item from a List, while you are iterating over it?
#### What happens if you try to add an item to the end of an array, while you are iterating over it?
#### If you need to access the iterator variable after a for loop, how would you do it?
#### Which interfaces extend the Collection interface in Java. Which classes?
#### What is the connection between equals() and hashCode()? How are they used in HashMap?
#### What is the difference between checked exceptions and unchecked exceptions? Could you bring example for each?
There are two exception types, checked and unchecked (also called runtime). The main difference is that checked exceptions are checked when compiled, while unchecked exceptions are checked at runtime.

#### What is Error in Java and how does it relate to Exception?
#### When does 'finally' block run? What it is used for? Could you give an example from your projects when you would use 'finally'?
#### What is the largest number you can work with in Java?
#### When you use method overriding, can you change the access level of the method, from protected to public? Why?When you use method overriding, can you change the access level of the method, from public to protected? Why?
#### Can the main method be overridden? Explain your answer!
#### When you use method overriding, can you throw fewer exceptions in the subclass than in the parent class? Why?
#### When you use method overriding, can you throw more exceptions in the subclass than in the parent class? Why?
#### What does "final" mean in case of a variable, method or a class?
#### What is the super keyword?
#### What are “generics”? When to use? Show examples.
#### What is the benefit of having “generic” containers?
#### Given two Java programs on two different machines. How can you communicate between the two? What are the possible ways?
#### What is an annotation? What can be annotated and how? Show examples.

### C&#35;

#### Explain the purpose of IL and how does it relate to CLR?
#### What does “managed code” mean?
#### What is an assembly?
#### What is the difference between an EXE and a DLL?
#### What is strong-typing versus weak-typing? Which is preferred? Why?
#### What is a namespace?
#### Explain sealed class in C#?
#### What is explicit vs. implicit conversion? Give examples of both of them.
#### Is a struct stored on the heap or stack?
#### Can a struct have methods?
#### Can DateTimes be null?
#### List out the differences between Array and ArrayList in C#?
#### How is the using() pattern useful? What is IDisposable? How does it support deterministic finalization?
#### How can you make sure that objects using dedicated resources (database connection, files, hardware, OS handle, etc.) are released as early as possible?
#### Why to use keyword “const” in C#? Give an example.
#### What is the difference between “const” and “readonly” variables in C#?
#### What is a property in C#?
#### List out two different types of errors in C#?
#### What is the difference between “out” and “ref” parameters in C#?
#### Can we override private virtual method in C#?
#### What's the difference between IEquatable and just overriding Object.Equals()?
#### Explain the differences between public, protected, private and internal. Explain access modifier – “protected internal” in C#!
#### What’s the difference between using `override` and `new` keywords when defining method in child class?
#### Explain StringBuilder class in C#!
#### How we can sort the array elements in descending order in C#?
#### Can you use a value type as a generic type argument in C#? For example when implementing an interface like (IEquatable).
#### What are Nullable Types in C#?
#### Conceptually, what is the difference between early-binding and late-binding?
#### What is delegate, event, callback, multicast delegate?
#### What is enum in C#?
#### What is null-conditional operator?
#### What is null-coalescing operator?
#### What is serialization?
#### What is the difference between Finalize() and Dispose() methods?
#### How do you inherit a class from another class in C#?
#### What is difference between “is” and “as” operators in C#?
#### What are indexers in C# .NET?
#### What is the difference between returning IQueryable<T> vs. IEnumerable<T>?
#### What is LINQ? Explain the idea of extension methods.
#### What are the advantages and disadvantages of lazy loading?
#### How to use of “yield” keyword? Mention at least one practical scenario where it can be used?
#### What are attributes in C#? Give some examples of usage of them.
#### By what mechanism does NUnit know what methods to test?
#### What is the GAC? What problem does it solve?
#### What is the largest number you can work with in C#?

### Database

#### How can you connect your application to a database server? What are the possible ways?
#### What do you know about database normalization?
