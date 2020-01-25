# Programming Basics questions

## Computer science

### Data structures

#### What is the purpose of a list (array in some programming languages) data structure? Name some methods of it!
Lists are very useful in Python because we can solve many problems with them, we can iterate throught the list, we can measure the elements, we can modify them , we can sort them...
#### What is the difference between a list/array and a set?
List can contain the same element more than once, while sets cant contain the same element multiple times.
#### What is the purpose and methods of a dictionary/map data structure?
A dictionary contains key:value pairs, the keys must be immutable while the values are mutable.

### Algorithms

#### Fibonacci sequences. Write a method (or pseudo code), that generates the Fibonacci sequences.
```
fib[n] = fib[n-1] + fib[n-2]
```

```Python
def Fibonacci(n): 
    if n<0: 
        print("Incorrect input") 
    # First Fibonacci number is 0 
    elif n==0: 
        return 0
    # Second Fibonacci number is 1 
    elif n==1: 
        return 1
    else: 
        return Fibonacci(n-1)+Fibonacci(n-2) 
```
#### How do you find a max value in a list/array if you can’t use any built-in functions?
```Python
max_num = list[0]
for num in list:
    if num > max_num:
        max_num = num
max_num is the max value now
```
#### How do you find the average of values in a list/array if you can’t use any built-in functions?
#### What do we call an *in-place* sort?
When we do in place sort it won't produce a new sorted structure, it will do with the original 
#### Explain an algorithm which sorts a list!

### Programming paradigms - procedural

#### What is the call stack?
A call stack is used for several related purposes, but the main reason for having one is to keep track of the point to which each active subroutine should return control when it finishes executing. The call stack is a Last-In, First-Out (return goes back to the point of the most recent call) data structure containing the address at which execution will resume and often local variables and parameters from each call.
#### What is “Stack overflow”?
A stack overflow is an undesirable condition in which a particular computer program tries to use more memory space than the call stack has available.
#### What are the main parts of a function?
Function signature: function name, return type, parameter list
Function body
### Programming languages - Python  
#### How do you use a dictionary in Python?
Usually store key : value pairs in a dictionary. For example for an inventory a dictionary is a good idea in my opinion, because we can check that is there an item already in the dict, if no we can add it , or we can modify the value if the dict contains that key.
#### What does it mean that an object is immutable in Python?
Immutable objects are strings, numbers(int, floats), tuples. We cannot modify them in place.
#### What is conditional expression in Python?
```Python
<expr1> if <conditional_expr> else <expr2>
```
#### What are different types of arguments in Python?
Positional arguments and keyword arguments
#### What is variable shadowing? (context: variable scope)
Variable shadowing occurs when a variable declared within a certain scope (decision block, method, or inner class) has the same name as a variable declared in an outer scope. 
#### What can happen if you try to delete/drop/add an item from a List, while you are iterating over it in Python?
In general, it is not possible to modify the data structure without making the iteration invalid. 
#### What is the "golden rule" of variable scoping in Python (context: LEGB)? What is the lifetime of variables?
LEGB stands for:

- Local
- Enclosed
- Global
- Built-in
#### If you need to access the iterator variable after a for loop, how would you do it in Python?
While iterating through an iterable in the body of the loop I can create a variable with the desired iterator variable.
#### What type of elements can a list contain in Python?
strings, list, numbers, tuples, dictionaries, sets...
#### What is slice operator in Python and how to use?
The slice operator [n:m] returns the part of the string from the n’th character to the m’th character, including the first but excluding the last.
#### What arithmetic operators (+,*,-,/) can be used on lists in Python? What do they do?
With + we can add to lists together, with * and a number we can multiply the list as many times as the number l = [1] , l*3 ===> [1,1,1] 
#### What is the purpose of the in and not in membership operators in Python?
We can check the membership of an item with 'in' or 'not in' in a container. 
#### What does the + operator mean when used with strings in Python?
Concatenates to the string
#### Explain f strings in Python?
Also called “formatted string literals,” f-strings are string literals that have an f at the beginning and curly braces containing expressions that will be replaced with their values.
#### Name 4 iterable types in Python!
string, list, tuples, dictionary
#### What is the difference between list/set/dictionary comprehension and a generator expression in Python?
#### Does the order of the function definitions matter in Python? Why?
Yes, because if we call a function before we define it we will get "name error" with the function name and it will say its not defined.
#### What does unpacking mean in Python?
When we define a function and we add parameters with *(for tuples) or **(for dictionaries) python has to unpack those to work with them
#### What happens when you try to assign the result of a function which has no return statement to a variable in Python?
If we dont give a return value it still has a return value which is None, so then the variable will be None
## Software engineering

### Debugging

#### What techniques can you use while debugging a program in Python?
We can go step by step , we can add breakpoints , we can watch variables, we can watch the call stack...
#### What does step over, step into and step out mean while using the debugger?
Step Into - A method is about to be invoked, and you want to debug into the code of that method, so the next step is to go into that method and continue debugging step-by-step.
Step Over - A method is about to be invoked, but you're not interested in debugging this particular invocation, so you want the debugger to execute that method completely as one entire step.
Step Out – An action to take in the debugger that returns to the line where the current function was called.
#### How can you start to debug a program from a certain line using the debugger?
Put a breakpoint next to the code and start in debug mode.

### Version control

#### What are the advantages of using a version control system?
With version control systems we can save our project in different stages and can rollback an older version if needed and we can work separetly on the same project with the team and we can trace back every steps of our project.
#### What is the difference between the working directory, the staging area and the repository in git?
Working directory is a local place where we work on our project.
Stagin area is the place where we add our files which we want to send to the remote server, but we can remove it , its something like a security level to check we really want to push it to the repository.
Repository is the place where we store our current project. 
#### What are remote repositories in git?
A remote in Git is a common repository that all team members use to exchange their changes. In most cases, such a remote repository is stored on a code hosting service like GitHub or on an internal server. In contrast to a local repository, a remote typically does not provide a file tree of the project's current state.
#### Why does a merge conflict occur?
A conflict arises when two separate branches have made edits to the same line in a file, or when a file has been deleted in one branch but edited in the other. Conflicts will most likely happen when working in a team environment. There are many tools to help resolve merge conflicts.
#### Through what series of commands could you put a new file into a remote repository connected to your existing local repository?
#### What does it mean atomic commits and descriptive commit messages?
When making code changes, you want to make commits that are generally smaller and that encompass only one irreducible feature, fix, or improvement. It's a single irreducible unit, clear and concise. 
#### What’s the difference between git and GitHub?
Git is a revision control system, a tool to manage your source code history.
GitHub is a hosting service for Git repositories.

## Software design

### Clean code

#### What does clean code mean?
Clean code is readable and easy to understand by everyone whether the reader is the author of the code or a new programmer.
#### What steps do we usually do during a clean code refactoring?
renaming, clearing repetitions, making functions while we don't loose features


### Error handling

#### What is exception handling?
Exception handling is the process of responding to exceptions when a computer program runs. An exception occurs when an unexpected event happens that requires special processing. Exception handling attempts to gracefully handle these situations so that a program (or worse, an entire system) does not crash.
#### What are the basics of exception handling in Python?
zero divison error, value error, type error, name error
#### In which case should we catch an exception? Why?
Most of the time we want to catch them because when we run into one it will terminate the program. If we catch it we can modify the code to handle those events and give us a message what is incorrect and we can use our program smoothly.
#### What can/should we do with an exception in the ‘except’ block?
#### What does the else and finally statement do in a try-except block in Python?
You can include an else clause when catching exceptions with a try statement. The statements inside the else block will be executed only if the code inside the try block doesn’t generate an exception.
If a finally clause is present, the finally clause will execute as the last task before the try statement completes. The finally clause runs whether or not the try statement produces an exception.

## Software Development Methodologies

#### What is the main goal of a retrospective meeting?
Retro is a good chance to sum our successes and fails of the week and set a goal to the next time we should achieve. It is good for learn from our mistakes and be proud of successes.

## Programming environment

### Unix

#### What is UNIX and what is Linux?
Unix and Unix-like operating systems are a family of computer operating systems that derive from the original Unix System from Bell Labs which can be traced back to 1965. Unix is considered as the mother of most of the operating systems.

Linux is not Unix, but it is a Unix-like operating system. Linux system is derived from Unix and it is a continuation of the basis of Unix design. A standard Linux distribution consists of a Linux kernel, GNU system, GNU utilities, libraries, compiler, additional software, documentation, a window system, window manager and a desktop environment.
#### What do we call the shell in Linux?
Simply put, the shell is a program that takes commands from the keyboard and gives them to the operating system to perform. The default shell in Linux is BASH.
#### What does root means in a Linux environment?
root is the user name or account that by default has access to all commands and files on a Linux or other Unix-like operating system. It is also referred to as the root account, root user and the superuser.
#### How do you access your personal files in Linux?
#### How can you install an application in Linux?
$ sudo apt install app_name
#### What is package management in Linux, what are repositories?
In few words, package management is a method of installing and maintaining (which includes updating and probably removing as well) software on the system. Debian packages (and Ubuntu of course) can be managed from command line using the package manager “apt”.

A Linux repository is a storage location from which your system retrieves and installs OS updates and applications. Each repository is a collection of software hosted on a remote server and intended to be used for installing and updating software packages on Linux systems.
#### How do you navigate in the filesystem with the command line?
Looking at the Contents of Directories with “ls”
Moving Around the Filesystem with “cd”
To move up one level, we can type: cd ..
Create a File with “touch”
Moving and Renaming Files and Directories with “mv”
Copying Files and Directories with “cp”
Removing Files and Directories with “rm” and “rmdir”
#### What does the following commands do: mkdir, rm, cat, cp, touch?
mkdir - Attempts to create the directory specified by pathname.
Rm - remove
Cat - It will show content of given filename
Cp - copying files and directories
Touch - The touch command is the easiest way to create new, empty files.
#### How can you look up what does a command do in Linux if you have no internet connection?
Use "whatis" keyword
#### What does the following commands do: head, tail, more, less?
head = displays the first ten lines of a file, unless otherwise stated.
tail = display the last part of the file
more = to view a text file one page at a time, press spacebar to go to the next page
less = is much the same as more command
#### How do you download a file from internet using the terminal?
Using wget "http://domain.com/directory/4?action=AttachFile&do=view&target=file.tgz" 
