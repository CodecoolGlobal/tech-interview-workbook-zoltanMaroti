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
#### What type of elements can a list contain in Python?
strings, list, numbers, tuples, dictionaries, sets...
#### What is slice operator in Python and how to use?
The slice operator [n:m] returns the part of the string from the n’th character to the m’th character, including the first but excluding the last.
#### What arithmetic operators (+,*,-,/) can be used on lists in Python? What do they do?
#### What is the purpose of the in and not in membership operators in Python?
#### What does the + operator mean when used with strings in Python?
#### Explain f strings in Python?
#### Name 4 iterable types in Python!
string, list, tuples, dictionary
#### What is the difference between list/set/dictionary comprehension and a generator expression in Python?
#### Does the order of the function definitions matter in Python? Why?
#### What does unpacking mean in Python?
#### What happens when you try to assign the result of a function which has no return statement to a variable in Python?

## Software engineering

### Debugging

#### What techniques can you use while debugging a program in Python?
#### What does step over, step into and step out mean while using the debugger?
#### How can you start to debug a program from a certain line using the debugger?

### Version control

#### What are the advantages of using a version control system?
#### What is the difference between the working directory, the staging area and the repository in git?
#### What are remote repositories in git?
#### Why does a merge conflict occur?
#### Through what series of commands could you put a new file into a remote repository connected to your existing local repository?
#### What does it mean atomic commits and descriptive commit messages?
#### What’s the difference between git and GitHub?

## Software design

### Clean code

#### What does clean code mean?
#### What steps do we usually do during a clean code refactoring?

### Error handling

#### What is exception handling?
#### What are the basics of exception handling in Python?
#### In which case should we catch an exception? Why?
#### What can/should we do with an exception in the ‘except’ block?
#### What does the else and finally statement do in a try-except block in Python?

## Software Development Methodologies

#### What is the main goal of a retrospective meeting?

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
#### What does the following commands do: mkdir, rm, cat, cp, touch?
mkdir - Attempts to create the directory specified by pathname.
Rm - remove
Cat - It will show content of given filename
Cp - copying files and directories
Touch - The touch command is the easiest way to create new, empty files.
#### How can you look up what does a command do in Linux if you have no internet connection?
#### What does the following commands do: head, tail, more, less?
#### How do you download a file from internet using the terminal?
wget "http://domain.com/directory/4?action=AttachFile&do=view&target=file.tgz" 
