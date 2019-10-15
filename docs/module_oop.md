# OOP questions

## Software design

### Error handling

#### What does 'fail fast' mean in terms of exception handling? Why is it a good practice?
Some people recommend making your software robust by working around problems automatically. This results in the software “failing slowly.”
The program continues working right after an error but fails in strange ways later on. A system that fails fast does exactly the opposite: when a problem occurs, it fails immediately and visibly. If something unusually or unexpectedly occurs, let the software fail immediately instead of postponing the failure or working around the failure. The fail fast principle stands for stopping the current operation as soon as any unexpected error occurs. Adhering to this principle generally results in a more stable solution. The opposite to fail-fast is fail-silently. In most cases, adhering to the fail fast principle means we should shut down the application (probably, with a polite apology) in case of any unexpected situation. 

**Why Fail-Fast?**
- Bugs are earlier to detect, easier to reproduce and faster to fix.  
- It’s faster to stabilize softwares.
- Fewer bugs and defects will go into production, thus leading to higher-quality and more production-ready software.
- The cost of failures and bugs are reduced.

The longer it takes for a bug to appear on the surface, the longer it takes to fix and the greater it costs. Fail-fast is the principle behind many Agile practices:
- **Test-driven development:** Writing tests to cover all the cases in which it would fail and all the requirements it has to meet, before even implementing it.
- **Continuous integration:** An Agile practice in software development, where developers are required to integrate their current works into shared repository/branch several times a days. Each integration is verified by an automated builds, thus helping team to find and fix problems early.

## Computer Science

### Data structures

#### How to find the middle element of singly linked list in O(n)?
If we need to find the middle element in only one pass, the best method is to create two pointers. As we traverse the list starting from the first element, at each step one of the pointers is moved by one, while the other is moved by two. At the moment, when the second pointer reaches the end of the list, the first pointer will be right on the middle element.

```java
class LinkedList {
    Node head; // head of linked list
 
    class Node {
        int data;
        Node next;
        Node(int d) {
            data = d;
            next = null;
        }
    }
 
    /* Function to print middle of linked list */
    void printMiddle() {
        Node slow_ptr = head;
        Node fast_ptr = head;
        if (head != null) {
            while (fast_ptr != null && fast_ptr.next != null) {
                fast_ptr = fast_ptr.next.next;
                slow_ptr = slow_ptr.next;
            }
            System.out.println("The middle element is " + slow_ptr.data + ".");
        }
    }
 }
 ```

#### Given an array of integers going from 1 to 100 (both inclusive) there is a duplicated entry. How to find it?
**Solution 1 – Sorting**<br>
We sort the array and then we compare each element to the previous element.

```java
class Solution {
    public int findDuplicate(int[] nums) {
        Arrays.sort(nums);
        for (int i = 1; i < nums.length; i++) {
            if (nums[i] == nums[i-1]) {
                return nums[i];
            }
        }
        return -1;
    }
}
```
Time complexity: O(n*lgn)<br>
Space complexity: O(1) (or O(n) if we are not allowed to modify the input array)

**Solution 2 – Using a set**<br>
We store each element in a set as we iterate over the array, before saving a new element we simply check if it's already in the set.

```java
class Solution {
    public int findDuplicate(int[] nums) {
        Set<Integer> seen = new HashSet<Integer>();
        for (int num : nums) {
            if (seen.contains(num)) {
                return num;
            }
        seen.add(num);
        }
        return -1;
    }
}
```
Time complexity: O(n)<br>
Space complexity: O(n)

#### What is a linked list? How to find if a linked list has a loop?
A linked list is a linear data structure where each element is a separate object. Each element (we will call it a node) of a list is comprising of two items - the data and a reference to the next node. The last node has a reference to null. The entry point into a linked list is called the head of the list. It should be noted that head is not a separate node, but the reference to the first node. If the list is empty then the head is a null reference.

![alt text](https://people.engr.ncsu.edu/efg/210/s99/Notes/LLdefs.gif "Linked list")

A linked list is a dynamic data structure. The number of nodes in a list is not fixed and can grow and shrink on demand. Any application which has to deal with an unknown number of objects will need to use a linked list.

One disadvantage of a linked list against an array is that it does not allow direct access to the individual elements. If you want to access a particular item then you have to start at the head and follow the references until you get to that item.

Another disadvantage is that a linked list uses more memory compare with an array - we extra 4 bytes (on 32-bit CPU) to store a reference to the next node.

**Types of Linked Lists:**
- A singly linked list is described above
- A doubly linked list is a list that has two references, one to the next node and another to previous node.
- Another important type of a linked list is called a circular linked list where last node of the list points back to the first node (or the head) of the list.

**Linked List vs Array:**
When an array is created, it needs a certain amount of memory. On the other hand, when a linked list is born, it doesn’t need memory all in one place. Linked lists don’t need to take up a single block of memory; instead, the memory that they use can be scattered throughout.

The fundamental difference between arrays and linked lists is that arrays are static data structures, while linked lists are dynamic data structures. A static data structure needs all of its resources to be allocated when the structure is created; this means that even if the structure was to grow or shrink in size and elements were to be added or removed, it still always needs a given size and amount of memory. On the other hand, a dynamic data structure can shrink and grow in memory. It doesn’t need a set amount of memory to be allocated in order to exist, and its size and shape can change, and the amount of memory it needs can change as well.

**How to find if a linked list has a loop?**
Use Hashing: Traverse the list one by one and keep putting the node addresses in a Hash Table. At any point, if NULL is reached then return false and if next of current node points to any of the previously stored nodes in Hash then return true.

#### What is the Big O time complexity of the common operations in an ArrayList, LinkedList, HashMap? And of a bubble sort, quicksort, finding items in a Binary Search tree?
**ArrayList:**
- adding to the beginning (or near the beginning): the whole list needs to be "re-indexed": **O(n)**
- adding to the end (or near to the end): **O(1)**
- remove from the end: **O(1)**
- remove from elsewhere: "re-indexing": **O(n)**
- get (by index): **O(1)**
- contains: **O(n)**

**LinkedList:**
- adding to the beginning or end: **O(1)**
- adding elsewhere (somewhere middle): **O(n)**
- remove: **O(n)**
- get: **O(n)**
- contains: **O(n)**

**HashMap:**
- every task takes a single operation (except in edge cases, like hash clash).

**Bubble Sort:**
-needs a nested for loop: **O(n^2)**

**Quicksort:**
- on average: **O(log n)**
- worst case: **O(n^2)**

**Binary Search Tree:**
- **O(log n)**
- worst case (degenerate tree): **O(n)**

#### How does HashMap work?
HashMap in Java works on hashing principle. It is a data structure which allows us to store object and retrieve it in constant time O(1) provided we know the key. In hashing, hash functions are used to link key and value in HashMap. Objects are stored by calling ```put(key, value)``` method of HashMap and retrieved by calling ```get(key)``` method. When we call put method, ```hashcode()``` method of the key object is called so that hash function of the map can find a bucket location to store value object, which is actually an index of the internal array, known as the table. HashMap internally stores mapping in the form of Map.Entry object which contains both key and value object. When you want to retrieve the object, you call the ```get()``` method and again pass the key object. This time again key object generate same hash code (it's mandatory for it to do so to retrieve the object and that's why HashMap keys are immutable e.g. String) and we end up at same bucket location.

#### Why is it important for keys in a map to have an immutable type? (Consider String for example.)
HashMap is a data-structure where data is organized as key and values pairs. i.e. for every value there must be a  key to be produced to be stored into the hashmap. Keys are normally generated using hashcode() method.

Key’s hash code is used primarily in conjunction to its equals() method, for putting a key in map and then searching it back from map. So if hash code of key object changes after we have put a key-value pair in map, then its almost impossible to fetch the value object back from map. It is a case of memory leak. To avoid this, map keys should be immutable.

If immutable, the object's hashcode wont change and it allows caching the hashcode of different keys which makes the overall retrieval process very fast. String, Integer and other wrapper classes are best for HashMap key, and String is most frequently used key as well because String is immutable and final, and overrides equals and hashcode() method.

### Other

#### What is a garbage collector, in a nutshell?
Automatic garbage collection is the process of looking at heap memory, identifying which objects are in use and which are not, and deleting the unused objects. An in use object, or a referenced object, means that some part of your program still maintains a pointer to that object. An unused object, or unreferenced object, is no longer referenced by any part of your program. So the memory used by an unreferenced object can be reclaimed. Garbage Collection tracks each and every object available in the JVM heap space and removes unused ones. In a programming language like C, allocating and deallocating memory is a manual process. In Java, process of deallocating memory is handled automatically by the garbage collector. 

**Advantages:**
- No manual memory allocation/deallocation handling
- Automatic Memory Leak management

## Programming paradigms

### Procedural

#### What is casting? What is the difference between up vs downcasting?
Upcasting is casting to a supertype, while downcasting is casting to a subtype. Upcasting is always allowed, but downcasting involves a type check and can throw a ClassCastException.

Downcasting would be something like this:
``` java
Animal animal = new Dog();
Dog castedDog = (Dog) animal;
```

Basically what you're doing is telling the compiler that you know what the runtime type of the object really is. The compiler will allow the conversion, but will still insert a runtime sanity check to make sure that the conversion makes sense. In this case, the cast is possible because at runtime animal is actually a Dog even though the static type of animal is Animal.

However, if you were to do this:
```java
Animal animal = new Animal();
Dog notADog = (Dog) animal;
```

You'd get a ClassCastException. The reason why is because animal's runtime type is Animal, and so when you tell the runtime to perform the cast it sees that animal isn't really a Dog and so throws a ClassCastException.

![alt text](https://i.stack.imgur.com/Lkn0S.png "Upcastings vs downcasting")

#### Which order should we catch the exceptions? Why?
The order is whatever matches first, gets executed. If the first catch matches the exception, it executes, if it doesn't, the next one is tried and on and on until one is matched or none are. If the exceptions have parent-child relationship, the catch blocks must be sorted by the most specific exceptions first, then by the most general ones. So, when catching exceptions you want to always catch the most specific first and then the most generic (as RuntimeException or Exception).

### Object-oriented

#### What is a class?
In summary, in object oriented programming, each object has three dimensions: identity, attributes, and behavior. 
Attributes describe the object's current state, and what the object is capable of doing is demonstrated through the object's behavior.

A class describes what the object will be, but is separate from the object itself. In other words, classes can be described as blueprints, descriptions, or definitions for an object. You can use the same class as a blueprint for creating multiple objects (it's called instantiation - is the realization of a predefined object). The first step is to define the class, which then becomes a blueprint for object creation. Each class has a name, and each is used to define attributes and behavior. In other words, an object is an instance of a class.

A class has attributes and methods.
- Methods: Methods define behavior. A method is a collection of statements that are grouped together to perform an operation.
- The attributes are basically variables within a class.

![alt text](http://sce2.umkc.edu/BIT/burrise/pl/oop/car-objects.gif "Object")

#### What is an object?
Software objects are conceptually similar to real-world objects: they consist of state and behavior. An object stores its state in fields (variables in some programming languages) and exposes its behavior through methods (functions in some programming languages). Methods operate on an object's internal state and serve as the primary mechanism for object-to-object communication. Hiding internal state and requiring all interaction to be performed through an object's methods is known as data encapsulation — a fundamental principle of object-oriented programming.

Bundling code into individual software objects provides a number of benefits, including:

- Modularity: The source code for an object can be written and maintained independently of the source code for other objects. Once created, an object can be easily passed around inside the system.
- Information-hiding: By interacting only with an object's methods, the details of its internal implementation remain hidden from the outside world.
- Code re-use: If an object already exists (perhaps written by another software developer), you can use that object in your program.
- Pluggability and debugging ease: If a particular object turns out to be problematic, you can simply remove it from your application and plug in a different object as its replacement.

![alt text](https://docs.oracle.com/javase/tutorial/figures/java/concepts-object.gif "Object")

#### What is a constructor?
Constructors are special methods invoked when an object is created and are used to initialize them. A constructor can be used to provide initial values for object attributes. A constructor name must be the same as its class name. A constructor must have no explicit return type. You can think of constructors as methods that will set up your class by default, so you don’t need to repeat the same code every time. The constructor is called when you create an object using the new keyword. A single class can have multiple constructors with different numbers of parameters. Java automatically provides a default constructor, so all classes have a constructor, whether one is specifically defined or not.

**Constructor Overloading:**<br>
Sometimes there is a need of initializing an object in different ways. This can be done using constructor overloading. Overloaded constructor is called based upon the parameters specified when new is executed. If we want to have different ways of initializing an object using different number of parameters, then we must do constructor overloading.

![alt text](https://static.javatpoint.com/images/core/java-constructor.png "Constructor")

#### Do we require parameter for constructors?
A constructor should establish the initial invariant of your object, that is, put it in a valid and usable state. If it's impossible to provide all the information needed up-front to construct your object properly, you may want to consider some sort of builder to gather state incrementally before instantiating the object. You should favor parameterless constructors. Typically, the constructor initializes the fields of the object that need initialization. Java constructors can also take parameters, so fields can be initialized in the object at creation time.

#### What is an interface?
An interface is a completely abstract class that contains only abstract methods.

**Some specifications for interfaces:**<br>
- Defined using the interface keyword.
- May contain only static final variables.
- Cannot contain a constructor because interfaces cannot be instantiated.
- Interfaces can extend other interfaces.
- A class can implement any number of interfaces.

**An example of a simple interface:**<br>
```java
interface Animal {
    public void eat();
    public void makeSound();
}
```
Interfaces have the following properties:
- An interface is implicitly abstract. You do not need to use the abstract keyword while declaring an interface.
- Each method in an interface is also implicitly abstract, so the abstract keyword is not needed.
- Methods in an interface are implicitly public.
- A class can inherit from just one superclass, but can implement multiple interfaces!
- When you implement an interface, you need to override all of its methods.

Use the implements keyword to use an interface with your class.
```java
interface Animal {
    public void eat();
    public void makeSound();
}

class Cat implements Animal {
    public void makeSound() {
        System.out.println("Meow");
    }
    public void eat() {
        System.out.println("omnomnom");
    }
}
```

#### What are access modifiers?
Access modifiers in Java helps to restrict the scope of a class, constructor, variable, method or data member. Access level modifiers determine whether other classes can use a particular field or invoke a particular method. There are two levels of access control:

- At the top level—public, or package-private (no explicit modifier).
- At the member level—public, private, protected, or package-private (no explicit modifier).

A class may be declared with the modifier public, in which case that class is visible to all classes everywhere. If a class has no modifier (the default, also known as package-private), it is visible only within its own package. 

At the member level, you can also use the public modifier or no modifier (package-private) just as with top-level classes, and with the same meaning. For members, there are two additional access modifiers: private and protected. The private modifier specifies that the member can only be accessed in its own class. The protected modifier specifies that the member can only be accessed within its own package (as with package-private) and, in addition, by a subclass of its class in another package.

**Tips on Choosing an Access Level:**<br> 
- Use the most restrictive access level that makes sense for a particular member. Use private unless you have a good reason not to.
- Avoid public fields except for constants.

- **Default – No keyword required:** When no access modifier is specified for a class, method or data member – It is said to be having the default access modifier by default. Having default access modifier are accessible only within the same package.

- **Private** - The methods or data members declared as private are accessible only within the class in which they are declared. Any other class of same package will not be able to access these members. Top level Classes or interface can not be declared as private, they apply only to nested classes.

- **Protected:** The methods or data members declared as protected are accessible within the same package or sub classes in different packages.

- **Public:** The public access modifier has the widest scope among all other access modifiers. Classes, methods or data members which are declared as public are accessible from everywhere in the program. There is no restriction on the scope of a public data members.

![alt text](http://net-informations.com/java/basics/img/access-modifier.png "Constructor")

#### What is data hiding?
Encapsulation is a central design principle of OOP. It means that the internal structure and the implementation of a class should be hidden from the world. This can be done by restricting the access to these parts. Every Object Oriented language provides access modifiers to set the visibility of classes and its members (fields, constructors, and methods) separately. This is called data hiding.

#### Can a static method use non-static members?
The static modifier is used for creating static class methods and variables. The keyword static lets a method run without any instance of the class. A static method belongs to the class, so there’s no need to create an instance of the class to access it.

**Characteristics of Static methods:** <br>
- A static method is called using the class (className.methodName) as opposed to to an instance reference (new instanceOfClass = class; instanceOfClass.methodName.)
- Static methods can’t use non-static instance variables: a static method can’t refer to any instance variables of the class. The static method doesn’t know which instance’s variable value to use.
- Static methods can’t call non-static methods: non-static methods usually use instance variable state to affect their behaviour. Static methods can’t see instance variable state, so if you try to call a non-static method from a static method the compiler will complain regardless if the non-static method uses an instance variable or not.

#### What is the difference between hiding a static method and overriding an instance method?
**Instance Methods**<br>
An instance method in a subclass with the same signature and return type as an instance method in the superclass overrides the superclass's method. This ability of a subclass (to override a method) allows a class to inherit from a superclass and modify behaviour as needed. The overriding method has the same name, number and type of parameters, and return type as the method that it overrides. An overriding method can also return a subtype of the type returned by the overridden method. This subtype is called a covariant return type.

**Static Methods**<br>
If a subclass defines a static method with the same signature as a static method in the superclass, then the method in the subclass hides the one in the superclass.

**Differences**<br>
- Overridden Instance Methods: the method in the subclass gets invoked. (Unless it is called from the subclass with super.myMethod.)
- Hidden Static methods: it depends on whether it gets invoked from the superclass or the subclass.

#### Define the following terms: Instantiation, Attribute, Method
**Instantiating a Class:** The phrase "instantiating a class" means the same thing as "creating an object." When you create an object, you are creating an "instance" of a class, therefore "instantiating" a class. The new operator instantiates a class by allocating memory for a new object and returning a reference to that memory. The new operator also invokes the object constructor.

**Attribute:** An attribute is another term for a field. It’s typically a public field that can be accessed directly.

**Method:** A method is a collection of statements that perform some specific task and return the result to the caller. A method can perform some specific task without returning anything. A method is a block of code which only runs when it is called, and they are also known as functions. Methods allow us to reuse the code without retyping the code. In Java, every method must be part of some class which is different from languages like C, C++, and Python. A method must be declared within a class.

![alt text](https://media.geeksforgeeks.org/wp-content/uploads/methods-in-java.png "method")

#### Could we access a static variable (or method) from a non-static method? Why?
Yes, a non-static method can access a static variable or call a static method in Java. There is no problem with that because of static members i.e. both static variable and static methods belongs to a class and can be called from anywhere, depending upon their access modifier.

**The opposite is not exact:** you can access static members from non-static context, but you cannot access a non-static variable or method from a static method in Java.

#### Could we access a non-static variable (or method) from a static method? Why?
No. A static method can only access other static methods and variables. If we need to access a non-static variable or method from within a static method, we must first instantiate the class that the non-static method or variable belongs to.

#### How many instances you have of a static variable of a given class?
Java Language Specification states the following:

If a field is declared static, there exists exactly one incarnation of the field, no matter how many instances (possibly zero) of the class may eventually be created. A static field, sometimes called a class variable, is incarnated when the class is initialized.

#### Why is it not a good practice to write a lot of static methods?
One reason that static methods aren't very OO is that interfaces and abstract classes only define non-static methods. Static methods thus don't fit very well into inheritance. Static methods do not have access to "super", which means that static methods cannot be overridden in any real sense. Actually, they can't be overridden at all, only hidden.

#### What are the features of static attributes and static methods of a class? What are the benefits, when to use them?
Static attributes are also known class attributes. They are useful for example for counting IDs for created objects. Common use for static methods is to access static variables. Another good example is the singleton pattern’s getInstance() method, which is static as well.

#### What is the ‘this’ reference?
‘this’ is a reference variable that refers to the current object. Within an instance method or a constructor, 'this' is a reference to the current object — the object whose method or constructor is being called. You can refer to any member of the current object from within an instance method or a constructor by using 'this'.

#### What are base class, subclass and superclass?
The class from which the subclass is derived is called a superclass (also a base class or a parent class).</ br>
A class that is derived from another class is called a subclass (also a derived class, extended class, or child class). The class from which the subclass is derived is called a superclass (also a base class or a parent class). Excepting Object, which has no superclass, every class has one and only one direct superclass (single inheritance). In the absence of any other explicit superclass, every class is implicitly a subclass of Object. Classes can be derived from classes that are derived from classes that are derived from classes, and so on, and ultimately derived from the topmost class, Object. Such a class is said to be descended from all the classes in the inheritance chain stretching back to Object.

#### Draw an object oriented family (as entities, with relations) on the whiteboard.
#### Difference between overloading and overriding?
Overloading is about same function have different signatures. Overriding is about same function, same signature but different classes connected through inheritance. Overloading is an example of compiler time polymorphism and overriding is an example of run time polymorphism.

![alt text](http://cdncontribute.geeksforgeeks.org/wp-content/uploads/OverridingVsOverloading.png "overloading vs overriding")

#### What are the Object Oriented Principles? Explain the concepts with realistic examples!
**Encapsulation:** The implementation and state of each object are privately held inside a defined boundary, or class. Other objects do not have access to this class or the authority to make changes but are only able to call a list of public functions, or methods. This characteristic of data hiding provides greater program security and avoids unintended data corruption. Another way to think about encapsulation is, it is a protective shield that prevents the data from being accessed by the code outside this shield. Technically in encapsulation, the variables or data of a class is hidden from any other class and can be accessed only through any member function of own class in which they are declared. As in encapsulation, the data in a class is hidden from other classes, so it is also known as data-hiding. Encapsulation can be achieved by Declaring all the variables in the class as private and writing public methods in the class to set and get the values of variables. 

Encapsulation is the mechanism of hiding of data implementation by restricting access to public methods. Instance variables are kept private and accessor methods are made public to achieve this.

Az adatok és a metódusok osztályba való összezárását jelenti. Tulajdonképpen az objektum egységbezárja az állapotot (adattagok értékei) a viselkedésmóddal (műveletekkel). Következmény: az objektum állapotát csak a műveletein keresztül módosíthatjuk. Az objektum elrejti az adatait és bizonyos műveleteit. Ez azt jelenti, hogy nem tudjuk pontosan, hogy egy objektumban hogyan vannak az adatok ábrázolva, sőt a
műveletek implementációit sem ismerjük. Az információk elrejtése az objektum biztonságát szolgálja, amelyeket csak a ellenőrzött műveleteken keresztül érhetünk el.

**Abstraction:** Objects only reveal internal mechanisms that are relevant for the use of other objects, hiding any unnecessary implementation code. This concept helps developers make changes and additions over time more easily. Only the essential details are displayed to the user.The trivial or the non-essentials units are not displayed to the user. Ex: A car is viewed as a car rather than its individual components. Data Abstraction may also be defined as the process of identifying only the required characteristics of an object ignoring the irrelevant details. Consider a real-life example of a man driving a car. The man only knows that pressing the accelerators will increase the speed of car or applying brakes will stop the car but he does not know about how on pressing the accelerator the speed is actually increasing, he does not know about the inner mechanism of the car or the implementation of accelerator, brakes etc in the car. This is what abstraction is. In Java, abstraction is achieved by interfaces and abstract classes. We can achieve 100% abstraction using interfaces.

Abstract means a concept or an Idea which is not associated with any particular instance. Using abstract class/Interface we express the intent of the class rather than the actual implementation. In a way, one class should not know the inner details of another in order to use it, just knowing the interfaces should be good enough. Its main goal is to handle complexity by hiding unnecessary details from the user. That enables the user to implement more complex logic on top of the provided abstraction without understanding or even thinking about all the hidden complexity. Objects in an OOP language provide an abstraction that hides the internal implementation details. Similar to the coffee machine in your kitchen, you just need to know which methods of the object are available to call and which input parameters are needed to trigger a specific operation. But you don’t need to understand how this method is implemented and which kinds of actions it has to perform to create the expected result. 

Elvonatkoztatás. Segítségével privát implementációkat rejthetünk el egy nyilvános interfész mögé. 

Interfész: Viselkedésmódot definiál. Gyakorlatilag egy művelethalmaz deklarációját jelenti. Ha egy osztály implementál egy adott interfészt, akkor példányai az interfészben meghatározott viselkedéssel fognak rendelkezni. Csak konstans adattagokat tartalmazhat és minden tagja nyilvános. 

**Inheritance:** Relationships and subclasses between objects can be assigned, allowing developers to reuse a common logic while still maintaining a unique hierarchy. This property of OOP forces a more thorough data analysis, reduces development time and ensures a higher level of accuracy. It is the mechanism in Java by which one class is allow to inherit the features(fields and methods) of another class.

Inheritances expresses “is-a” and/or “has-a” relationship between two objects. Using Inheritance, In derived classes we can reuse the code of existing super classes. In Java, concept of “is-a” is based on class inheritance (using extends) or interface implementation (using implements).

Olyan osztályok között értelmezett viszony, amely segítségével egy általánosabb típusból (ősosztály) egy sajátosabb típust tudunk létrehozni (utódosztály). Az utódosztály adatokat és műveleteket (viselkedésmódot) örököl, kiegészíti ezeket saját adatokkal és műveletekkel, illetve felülírhat bizonyos műveleteket. A kód újrafelhasználásának egyik módja. Megkülönböztetünk egyszeres és többszörös örökítést.

**Polymorphism:** Objects are allowed to take on more than one form depending on the context. The program will determine which meaning or usage is necessary for each execution of that object, cutting down on the need to duplicate code. Polymorphism in Java are mainly of 2 types:
Overloading and Overriding.

It means one name many forms. It is further of two types — static and dynamic. Static polymorphism is achieved using method overloading and dynamic polymorphism using method overriding. It is closely related to inheritance. We can write a code that works on the superclass, and it will work with any subclass type as well.

#### What is method overloading?
If a class has multiple methods having same name but different in parameters, it is known as Method Overloading. Overloading allows different methods to have the same name, but different signatures where the signature can differ by the number of input parameters or type of input parameters or both. Overloading is related to compile time (or static) polymorphism.

Több azonos nevű, különböző szignatúrájú függvény. A függvényhívás aktuális paraméterei meghatározzák, hogy melyik függvény fog meghívódni. Ezt már a fordításidőben eldől (statikus, fordításidejű kötés).

Statikus (korai) kötés - Static (Early) Binding: Fordításidejű hozzárendelése a hívott metódusnak az objektumhoz. 

**Advantage of method overloading:**<br>
Method overloading increases the readability of the program. We don’t have to create and remember different names for functions doing the same thing.

**Different ways to overload the method:**<br>
- By changing number of arguments
- By changing the data type

#### What is method overriding?
If subclass (child class) has the same method as declared in the parent class, it is known as method overriding in Java. In other words, if a subclass provides the specific implementation of the method that has been declared by one of its parent class, it is known as method overriding.

Egy osztályhierarchián belül az utódosztály újradefiniálja az ősosztály metódusát. (azonos név, azonos szignatúra). Ha ősosztály típusú mutatón vagy referencián keresztül érjük el az osztályhierarchia példányait és ezen keresztül meghívjuk a felülírt metódust, akkor futási időben dől el, hogy pontosan melyik metódus kerül meghívásra. (dinamikus, futásidejű kötés).

**Usage of Java Method Overriding:**<br>
- Method overriding is used to provide the specific implementation of a method which is already provided by its superclass.
- Method overriding is used for runtime polymorphism

**Rules for Java Method Overriding:**<br>
- The method must have the same name as in the parent class
- The method must have the same parameter as in the parent class.
- There must be an IS-A relationship (inheritance).

#### Explain how object oriented languages attempt to simplify memory management for Programmers.
// TODO Java has automatic memory management, a nice and quiet garbage collector that works in the background to clean up the unused objects and free up some memory.

#### Explain the “Single Responsibility” principle!
Single Responsibility principle is a basic concept of programming, which means every class has only one task to do. That makes the code cleaner, more readable and easier to test or debug.

Every module or class should have responsibility over a single part of the functionality provided by the software, and that responsibility should be entirely encapsulated by the class. A class or module should have one, and only one, reason to be changed. This principle states that if we have 2 reasons to change for a class, we have to split the functionality in two classes. Each class will handle only one responsibility and if in the future we need to make one change we are going to make it in the class which handles it. When we need to make a change in a class having more responsibilities the change might affect the other functionality related to the other responsibility of the class.

#### What is an object oriented program? Explain, show.
In object oriented programming, importance is given to data rather than just writing instructions to complete a task. An object is a thing or idea that you want to model in your program. An object can be anything, example, employee, bank account, car etc.

Object-oriented programming (OOP) is a programming language model in which programs are organized around data, or objects, rather than functions and logic. An object can be defined as a data field that has unique attributes and behavior. Examples of an object can range from physical entities, such as a human being that is described by properties like name and address, down to small computer programs, such as widgets. This opposes the historical approach to programming where emphasis was placed on how the logic was written rather than how to define the data within the logic.

![alt text](https://miro.medium.com/max/1510/1*szU8ngrWSXmBNPYReMyK5w.png "oop program")

#### How do you make a class immutable? What do you need to watch out for?
To create an immutable class in java, you have to do following steps:
- Declare the class as final so it can’t be extended.
- Make all fields private so that direct access is not allowed.
- Don’t provide setter methods for variables
- Make all mutable fields final so that it’s value can be assigned only once.
- Initialize all the fields via a constructor performing deep copy.
- Perform cloning of objects in the getter methods to return a copy rather than returning the actual object reference.

#### How many instances can be created for an abstract class?
You cannot create an instance of an abstract class because it does not have a complete implementation. The purpose of an abstract class is to function as a base for subclasses. It acts like a template, or an empty or partially empty structure, you should extend it and build on it before you can use it.

## Programming languages

### Java

#### What is autoboxing and unboxing?
Autoboxing is the automatic conversion that the Java compiler makes between the primitive types and their corresponding object wrapper classes. For example, converting an int to an Integer, a double to a Double, and so on. If the conversion goes the other way, this is called unboxing. Converting a primitive value (an int, for example) into an object of the corresponding wrapper class (Integer) is called autoboxing. Autoboxing and unboxing lets developers write cleaner code, making it easier to read.

#### If you have a variable, that shall store a positive whole number between 0 and 200, what primitive type would you use to store it?
short (-32768 to 32767)

![alt text](http://4.bp.blogspot.com/-KviSh6mjDrs/VqoNwwxeWhI/AAAAAAAABao/46T-QGCGdyk/s1600/Primitive-Data-Types-in-Java-Programming-Language.png "primitive data types")

#### What is the "golden rule" of variable scoping in Java? What is the lifetime of variables?
General convention for a variable’s scope is, it is accessible only within the block in which it is declared.

**Instance variables:**<br>
A variable which is declared inside a class and outside all the methods and blocks is an instance variable. Lifetime of an instance variable is until the object stays in memory.

**Class variables:**<br>
A variable which is declared inside a class, outside all the blocks and is marked static is known as a class variable. The lifetime of a class variable is until the end of the program or as long as the class is loaded in memory.

**Local variables:**<br>
All other variables which are not instance and class variables are treated as local variables including the parameters in a method. The lifetime of a local variable is until the control leaves the block in which it is declared.

![alt text](https://www.startertutorials.com/corejava/wp-content/uploads/2014/09/Scope-and-lifetime-summary.jpg "variable scoping")

#### What is the purpose of the ‘equals()’ method?
In Java, string ```equals()``` method compares the two given strings based on the data/content of the string. If all the contents of both the strings are same then it returns true. If all characters are not matched then it returns false.

#### What is the difference between '==' and 'equals()'?
In general both equals() and “==” operator in Java are used to compare objects to check equality but here are some of the differences between the two:

- Main difference between .equals() method and == operator is that one is method and other is operator.
- We can use == operators for reference comparison (address comparison) and .equals() method for content comparison. In simple words, == checks if both objects point to the same memory location whereas .equals() evaluates to the comparison of values in the objects.

#### What does the ‘static’ keyword mean?
Everything in Java must have a type. ```static``` tells Java compiler that this is a method that is part of the class, but is not a method for any other instance of the class. We can apply java ```static``` keyword with variables, methods, blocks and nested class. ?Csak az adott osztály hívhatja meg a függvényt.?

#### Why is the main() method declared as static? Explain.
In Java, to start a program is to call an existing public static void
main(String[] args) method on a class.

- It must be public to be reachable from the outer world.
- It must be static to be callable before creating any objects.
- It is void since by design it does not return anything when the program ends normally.
- It is possible to pass (multiple) arguments after the name of the class to the java runtime – these arguments are visible by the method through the args parameter.

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
Long is a wrapper class around the primitive long. Therefore Long is an object; objects can be null, primitives can not. After auto-boxing feature is released in java the primitive long can be automatically converted to Long, which is an object.

#### Can a long store bigger numbers than a Long?
No, because long has the same maximum value like Long, 2^63-1. If you want to store bigger number you should use BigInteger.

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
It can contain constructors. If you create for example a ColorType.SPADES enum, it calls its constructor, and gives values to its fields (suitNumber -> 3, suitName -> “spades”). This constructor must be private or default (package-private). Enum can contain getters either. With them you can reach the values of the fields. It is possible to create setters as well if the fields are not final. It may not be a good idea, considering enums should be constants. You can also create methods that make calculations based on the field values of the enum constant.

#### When would you use a private/protected/public attribute? What is the difference?
- **private** scope when you want your property/method to be visible in its own class only.
- **protected** scope when you want to make your property/method visible in all classes that extend current class including the parent class.
- **public** scope to make that property/method available from anywhere, other classes and instances of the object.

#### How do you prevent developers from subclassing a class?
Officially, the Java language provides the keyword 'final' that is supposed to fulfill this task. You can also use private constructors.

#### How do you prevent developers from overriding a method in a subclass?
final modifier can be used to prevent method overriding in Java because there is no way someone can override final methods. Apart from final modifier, you can also use static and private modifier to prevent a method from being overridden.

private method is not accessible in subclass, which means they can not be overridden as well, because overriding happens at child class. Similarly, static methods can not be overridden in Java, because they are resolved and bonded during compile time, while overriding takes place at runtime. They are resolved based upon the type and not object. Overriding happens due to polymorphic property of objects.

#### How do you prevent developers from changing the value of a variable?
Use final keyword.

#### Think about money ;) How would you store a currency value, that shall support decimal parts? Think it through again, and try to think outside of the box!
A BigDecimal is an exact way of representing numbers. A Double has a certain precision. Working with doubles of various magnitudes (say d1=1000.0 and d2=0.001) could result in the 0.001 being dropped altogether when summing as the difference in magnitude is so large. With BigDecimal this would not happen. The disadvantage of BigDecimal is that it's slower, and it's a bit more difficult to program algorithms that way (due to + - * and / not being overloaded).

If you are dealing with money, or precision is a must, use BigDecimal. Otherwise Doubles tend to be good enough.

#### What happens if you try to call something, that you have no access to, because of data hiding?
The compiler throws an error: ". . . has private access in . . ."
It is illegal to access a variable declared private outside its class.

#### What happens if you try to delete/drop an item from an array, while you are iterating over it?
The length of an array is fixed after creation, therefore it is not possible to remove any elements while iterating, or just picked by value or index. However there is a method removeElement() in class ArrayUtils. This creates a new array without the element we want to remove. This works via iterating.

#### What happens if you try to delete/drop/add an item from a List, while you are iterating over it?
If you want to delete the item you are currently at while iterating, it will cause a ConcurrentModificationException, unless you are using an iterator and say iterator.remove(). Essentially, the ConcurrentModificationException is used to fail-fast when something we are iterating on is modified. 

#### What happens if you try to add an item to the end of an array, while you are iterating over it?
It is not possible, because arrays has a fixed size after they are created. It you want to add an element to the end of an array, you have to create a new array with length n + 1 (if the original list’s length was n), copy the original list elements to the new one, and add your element to the end of the new list.

#### If you need to access the iterator variable after a for loop, how would you do it?
I’d simply define the iterator variable before the loop, so after the loop I’d still have the latest value.

```java
int i;
for (i = 0; i < numbers.size(); i++) {
    sum += numbers.get(i);
}
```

#### Which interfaces extend the Collection interface in Java. Which classes?
The Java Collections Framework hierarchy consists of two distinct interface trees:
- Collection interface
- Map interface

The **Collection** interface provides the basic functionality used by all collections, such as add and remove methods. Its subinterfaces the Set, List, and Queue, provide for more specialized collections.
- The Set interface does not allow duplicate elements. 
- SortedSet is a subinterface of Set interface, that provides for ordering of elements in the set.
- The List interface provides for an ordered collection, for situations in which you need precise control over where each element is inserted.
- The Queue is a collection for holding elements prior to processing. Elements in a Queue are typically ordered in on a FIFO (first-in-first-out) basis.
- The Deque is a subinterface of Queue, a double-ended-queue. The elements can be used in both LIFO and FIFO.

![alt text](https://static.javatpoint.com/images/java-collection-hierarchy.png "collection interface")

#### What is the connection between equals() and hashCode()? How are they used in HashMap?
**equals(Object obj):** a method provided by java.lang.Object that indicates whether some other object passed as an argument is "equal to" the current instance. The default implementation provided by the JDK is based on memory location — two objects are equal if and only if they are stored in the same memory address. If two objects are equal, they MUST have the same hash code.

**hashcode():** a method provided by java.lang.Object that returns an integer representation of the object memory address.

HashMap uses hashCode(), == and equals() for entry lookup. The lookup sequence for a given key 'k' is as follows:

- Use k.hashCode() to determine which bucket the entry is stored
- If found, for each entry's key k1 in that bucket, if k == k1 || k.equals(k1), then return k1's entry
- Any other outcomes, no corresponding entry

When you ‘put’ in a hashmap, first the map finds a place in an array(bucket) based on the hashcode of the key. All entries of keys having same hashcode are placed in the same bucket. Once the bucket is identified, the equals method of the key comes into play. It checks, if any other key in the bucket is equal, if it is equal, it overrides that entry of value, else it adds a new entry of key value pair.

When we ‘get’ from hashMap, first it finds the hashcode of the key, using hashcode, finds the location/bucket of all keys having same hashcode. Then it uses the equals method of the key to identify which key value pair to be fetched from the bucket.

#### What is the difference between checked exceptions and unchecked exceptions? Could you bring example for each?
There are two exception types, checked and unchecked (also called runtime). The main difference is that checked exceptions are checked when compiled, while unchecked exceptions are checked at runtime.

#### What is Error in Java and how does it relate to Exception?
Both errors and exceptions are subclasses of the throwable class. Exceptions are related to the application itself while errors are related to the environment (JVM) in which the application is running.

Errors cannot and should not be handled or caught. They signal severe problems during runtime that should stop execution. Two most common examples are stack overflow and out-of-memory errors.

#### When does 'finally' block run? What it is used for? Could you give an example from your projects when you would use 'finally'?
The code we defined in the finally block runs whether there was a caught exception or not. We usually use finally block to clean up the resources - e.g. we are reading from a file in the try block, we want to close the file no matter what.

#### What is the largest number you can work with in Java?
Built-in Java primitive type, Double MAX_VALUE

```public static final double MAX_VALUE```
A constant holding the largest positive finite value of type double.

#### When you use method overriding, can you change the access level of the method, from protected to public? Why?When you use method overriding, can you change the access level of the method, from public to protected? Why?
A sub-class can always widen the access modifier, because it is still a valid substitution for the super-class. From the Java specification about Requirements in Overriding and Hiding:

The access modifier of an overriding or hiding method must provide at least as much access as the overridden or hidden method, as follows:
- If the overridden or hidden method is public, then the overriding or hiding method must be public; otherwise, a compile-time error occurs.
- If the overridden or hidden method is protected, then the overriding or hiding method must be protected or public; otherwise, a compile-time error occurs.
- If the overridden or hidden method has default (package) access, then the overriding or hiding method must not be private; otherwise, a compile-time error occurs.

#### Can the main method be overridden? Explain your answer!
No, because the main is a static method and a static method cannot be overridden.

#### When you use method overriding, can you throw fewer exceptions in the subclass than in the parent class? Why?
The overriding method must NOT throw checked exceptions that are new or broader than those declared by the overridden method. For example, a method that declares a FileNotFoundException cannot be overridden by a method that declares a SQLException, Exception, or any other non-runtime exception unless it's a subclass of FileNotFoundException.

It means that if a method declares to throw a given exception, the overriding method in a subclass can only declare to throw that exception or its subclass.

#### When you use method overriding, can you throw more exceptions in the subclass than in the parent class? Why?
The overriding method must NOT throw checked exceptions that are new or broader than those declared by the overridden method. 

#### What does "final" mean in case of a variable, method or a class?
- A final variable’s value cannot be modified or if it is a reference to an object, you cannot refer to another object with it.
- A final method cannot be overridden.
- A final class cannot be extended.

#### What is the super keyword?
The super keyword in Java is a reference variable which is used to refer immediate parent class object. Whenever you create the instance of subclass, an instance of parent class is created implicitly which is referred by super reference variable. We can use super keyword to access the data member or field of parent class. It is used if parent class and child class have same fields. The super keyword can also be used to invoke parent class method. It should be used if subclass contains the same method as parent class. In other words, it is used if method is overridden.

**Usage of Java super Keyword:**<br>
- super can be used to refer immediate parent class instance variable.
- super can be used to invoke immediate parent class method.
- super() can be used to invoke immediate parent class constructor: default constructor is provided by compiler automatically if there is no constructor. But, it also adds super() as the first statement.

#### What are “generics”? When to use? Show examples.
Using java generics programmers are able to write more general methods. It means that it is not necessary to specify the input type of a method, therefore it can handle Strings, Integers, Doubles and so on. It is very useful when for example we want to implement a sorting method. If we use generics our method will handle more type of Lists. Generics also provide compile-time type safety that allows programmers to catch invalid types at compile time.

```java
public class GenericMethodTest {
    // generic method printArray
    public static < E > void printArray ( E[] inputArray ) {
        // Display array elements
        for (E element : inputArray) {
            System.out.printf("%s ", element);
        }
        System.out.println();
    }
}
```

#### What is the benefit of having “generic” containers?
//TODO

```java
public class Container<T> {
    private final T value;

    public Container(T value) {
        this.value = value;
    }

    public T getValue() {
        return value;
    }
}
```

#### Given two Java programs on two different machines. How can you communicate between the two? What are the possible ways?
//TODO

#### What is an annotation? What can be annotated and how? Show examples.
Java Annotations allow us to add metadata information into our source code, although they are not a part of the program itself. Annotations can be applied to the classes, interfaces, methods and fields.

- Instructions to the compiler: There are three built-in annotations available in Java (@Deprecated, @Override & @SuppressWarnings) that can be used for giving certain instructions to the compiler.

- Compile-time instructors: Annotations can provide compile-time instructions to the compiler that can be further used by software build tools for generating code, XML files etc.

- Runtime instructions: We can define annotations to be available at runtime which we can access using java reflection and can be used to give instructions to the program at runtime.

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
You would need a database engine first. A database engine (or storage engine) is the underlying software component that a database management system (DBMS) uses to create, read, update and delete (CRUD) data from a database. 

**Connection**<br>
Connections are built by supplying an underlying driver or provider with a connection string, which is used to address a specific database or server and to provide instance and user authentication credentials.

Once a connection has been built, it can be opened and closed at will, and properties (such as the command time-out length, or transaction, if one exists) can be set. The connection string consists of a set of key-value pairs, dictated by the data access interface of the data provider. Some databases, such as PostgreSQL, only allow one operation to be performed at a time on each connection. If a request for data (a SQL Select statement) is sent to the database and a result set is returned, the connection is open but not available for other operations until the client finishes consuming the result set.  

Connections are a key concept in data-centric programming. Since some DBMSs require considerable time to connect, connection pooling is used to improve performance. No command can be performed against a database without an "open and available" connection to it.

**Pooling:**<br> 
Database connections are finite and expensive and can take a disproportionately long time to create relative to the operations performed on them. It is very inefficient for an application to create and close a database connection whenever it needs to update a database. Connection pooling is a technique designed to alleviate this problem. A pool of database connections is created and then shared among the applications that need to access the database. When an application needs database access, it requests a connection from the pool. When it is finished, it returns the connection to the pool, where it becomes available for use by other applications. This approach encourages the practice of opening a connection in an application only when needed, and closing it as soon as the work is done, rather than holding a connection open for the entire life of the application. In this manner, a relatively small number of connections can service a large number of requests. 

In a client–server architecture, on the other hand, a persistent connection is typically used so that server state can be managed. This "state" includes server-side cursors, connection-specific functional settings, and so on. Examples to connect to db: Psycopg2 in Python and JDBC in Java.

#### What do you know about database normalization?
Database normalization is the process of structuring a relational database in accordance with a series of so-called normal forms in order to reduce data redundancy and improve data integrity. Normalization entails organizing the columns (attributes) and tables (relations) of a database to ensure that their dependencies are properly enforced by database integrity constraints. 

In relational database design, the process of organizing data to minimize redundancy. Normalization usually involves dividing a database into two or more tables and defining relationships between the tables. The objective is to isolate data so that additions, deletions, and modifications of a field can be made in just one table and then propagated through the rest of the database via the defined relationships.

There are three main normal forms, each with increasing levels of normalization:
- **First Normal Form (1NF):** Each field in a table contains different information. For example, in an employee list, each table would contain only one birthdate field.
- **Second Normal Form (2NF):** Each field in a table that is not a determiner of the contents of another field must itself be a function of the other fields in the table.
- **Third Normal Form (3NF):** No duplicate information is permitted. So, for example, if two tables both require a birthdate field, the birthdate information would be separated into a separate table, and the two other tables would then access the birthdate information via an index field in the birthdate table. Any change to a birthdate would automatically be reflect in all tables that link to the birthdate table.
