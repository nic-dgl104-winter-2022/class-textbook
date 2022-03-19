
# Object-Oriented Programming & Interface Segregation Principle
---
## Intro

## OOP paradigms
### Definition 
>Object Oriented programming (OOP) is a programming paradigm that relies on the concept of classes and objects. 
It is used to structure a software program into simple, reusable pieces of code blueprints (usually called classes), 
which are used to create individual instances of objects. 
There are many object-oriented programming languages including JavaScript, C++, Java, and Python.
-Erin Doherty 

### Example

<img src="pic/oop-car-example.png"/>

As illustrated in the picture, we first have a Car class that contains Attributes and Methods. 
Inside Attributes, we got color, brand, year make then witing each attribute we have different values. 
Inside Methods, we have functions that are only accessible to car objects; 
for example, the Repaint method will help us change the car color for each instance  we create; 
the same goes for Tiers upgrade method.

#### Why should you use OOP
* Opp wil help you simplify your complex structer :relaxed:
* You can use it across programs! :star2:
* You can set class specific behaviour through polymorphism :+1:
* It will make debuging a braze :relieved:



<img src="pic/oop-car-example-2.png"/>
A real example of how OOP can create an easy program for a pet shop. 

when we use OPP, we specify the attribute and method once, and as more dogs check-in, we fill out their name and age; for today's date and age, data will be pulled from the main class to reflect today's date and age. 
* :one: We crated parent class "Dog class"
* :two: We creatrd child classes represanting diffrant subcategories "Attributes & Methods"
* :three: We added unique attributes and behaviors "Name, Birthday, Today's date, Calculate age" 
* :four: We Createed objects from the child class "Rufus & fluffy information"

```
NON-OPP
//Object of one individual dog
var rufus = {
    name: "Rufus",
    birthday: "2/1/2017",
    age: function() {
        return Date.now() - this.birthday;
    },
    attendance: 0
}

//Object of second individual dog
var fluffy = {
    name: "Fluffy",
    birthday: "1/12/2019",
    age: function() {
        return Date.now() - this.birthday;
    },
    attendance: 0
}
```

On the other hand, when we didn't use OPP, we had to create a different variable for each dog then add different specifications for them, meaning whenever new dog check-in, we'll have to fill out today's date again and retype the function to give us their age. 

In short, OOP will is ideal for complex structures which allow you to reuse your code and avoid repetition, you can a classes that has specific Attributes and Methods that has many instances as you like. 


### Principles of OOP
Object-oriented programs has four principles which are Inheritance, Encapsulation, Abstraction, and Polymorphism

#### Inheritance
Defenition: Inheritance is the procedure in which one class inherits the attributes and methods of another class. 

Example: 
```
public class dogs {

}

public class dogs extends cats{

}
```
#### Encapsulation
Defenition: Encapsulation is a method to hide the data in a single entity or unit along with a method to protect information from outside. 
```
public class BankInformation {
    private int accBalance;
    
}

```
Example: bank software declarer your balance as a private variable; therefore, it's only available to you when you log in. if they declare it as a public variable, it would be available to everyone, and they fail to protect your privacy. 



#### Abstraction
Defenition: Abstraction is the method of hiding the unwanted information.
Example: 
```
public class Dog {
    //Declared private variables 
    private int dateOfBirth;
    private int todayDate;
}
public int getAge(){
    //Created get method to access private variables
        return dogAge;
    }
  

```
#### Polymorphism
Defenition: Polymorphism means "many forms", and it occurs when we have many classes that are related to each other by inheritance. 
Example: In our [first illustration](<img src="pic/oop-car-example.png"/>) the attribute color behaved differently for each instance; for sam's car, it reflected green, for Abe's car, it was yellow, and bills car was blue



## Open–Closed Principle In OPP + examples & writeup



## Interface Segregation Principle + examples & writeup    




## Refrances:

* [What is object-oriented programming? OOP explained in depth By Erin Doherty](https://www.educative.io/blog/object-oriented-programming) 
* [Inheritance in Java Programming](https://beginnersbook.com/2013/03/inheritance-in-java/)
* [Encapsulation in Java](https://www.scientecheasy.com/2020/07/encapsulation-in-java.html/#:~:text=Every%20Java%20class%20is%20an,encapsulates%20several%20combinations%20of%20medicine.)
* [Difference between Abstraction and Encapsulation in Java](https://www.geeksforgeeks.org/difference-between-abstraction-and-encapsulation-in-java-with-examples/)