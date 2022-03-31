# Program Structure

Structured programming is one of the several different ways in which a programming language can be constructed. Structured programming was introduced as a way to get away from the “spaghetti code” that was being used in the early days of computer programming. It was also intended to provide a way for programmers to follow code written by other programmers. At low levels, structured programs are composed of simple, hierarchical program flow structures. 

## Basic Structure of a Python Program
### Expressions
An expression is any legal combination of symbols that represents a value. An expression represents something which python evaluates and which produces a value.

### Statements
A Statement is a programming instruction that does something, i.e. some action takes place. A statement executes and may or may not result in a value. 

### Comments
Comments are the additional readable information to clarify the source code. Comments in python are the non-executable statements in which begin with a hash symbol (#) and generally ends with the end of the line. 

### Function
A function is a code that has  a name, and it can be reused (executed again) by specifying its name in the program, where needed. A function begins with a ‘def’ statement.

### Blocks and indentation
A group of statements which are part of another statement, or a function are called block, code-block, or suite in Python. Indentation is used to show blocks in Python. Four spaces together mark the next indent level.

## Basic Structure of a Java Program
__Project package__ ``package helloworld;``
Package is a folder of classes and related files for your project.  ``helloworld`` is the name of the package. 

__Class header__ ``public class HelloWorld {`` 
Public is the access specifier. Classes can either be public or private. When the class is  public, you can access this class anywhere throughout your program. When the class is private, it can only be accessed inside its own class. Curly braces are used extensively in Java to indicate the start and the end of a code block. 

__Method header__ ``public static void main(string[] args { System.out.println(“Hello World”);}}`` 
Public means that it can be accessed anywhere throughout the files, static means you can use this method without creating an instance or an object of that class.  Void is the return type of the method main. Void simply tells the compiler that the main method does not return a value. The key word static allows the main method to be called without having to instantiate a particular instance of the class.  Main is the name of the method, and inside the parentheses is the parameter of the method. The square brackets after the word string mean that this method can accept a string of text as an array. Main is the entry point of all Java applications. It is the first method to be called. Also, inside the main method is a ``println`` statement telling the compiler to print the words Hello World. Finally, there is the semicolon. All Java ends with a semicolon to indicate to the compiler where an instruction ends and where the next instruction begins. 

## Coding Standards and Best Practices
