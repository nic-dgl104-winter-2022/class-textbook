# <div align = "center"> Chapter 7 - Design Patterns </div>
<!-- DESIGN PATTERNS -->
<br />
<p align="center"> <img src="./assets/design-patterns-keywords.png" > </p>
<br>
<p align="justify">
In 1994, "The Gang Of Four" published the book Design Patterns: Elements of Reusable Object-Oriented Software, which introduced software design patterns to the developer community. This book is a legendary source that addresses the problems of <i>Object-Oriented Programming (OOP)</i> in the language C++. Since the advent of the design patterns, many modern programming languages have become more flexible and robust by implementing these concepts. So what are exactly design patterns? 
</p>

<p align="center"> <img src="./assets/Design_Patterns_Gang_Of_Four.jpeg" > </p>
<br>

## 1. What are design patterns ?
<p align="justify">
    Most programming languages support <i>Object-Oriented Programming (OOP)</i> with different mechanisms in software development. Since working with the concept of OOP, many developers have similar problems and handle them with similar solutions repeatedly. Therefore, design patterns are introduced as reusable solutions for commonly occurring issues in a high-level abstract meaning. In other words, you can not apply design patterns just by copying and pasting code. In contrast, they are implemented differently in different programming languages but remain the same core intention. This is because design patterns are concepts that explain the problem and describe the intent in an object-oriented way. 
</p>

<p>According to <a href="https://refactoring.guru/design-patterns/catalog">Refactoring Guru</a>, there are 3 types of design patterns:</p>
<ul>
    <li>
        <b>Creational patterns</b>
        <p>These patterns provide various object creation mechanisms, which increase flexibility and reuse of existing code.</p>
        <p>Include: <i> Factory Method, Abstract Factory, Prototype, Singleton, and Builder</i> </p>
    </li>
    <li>
        <b>Structural patterns</b>
        <p>These patterns explain how to assemble objects and classes into larger structures while keeping these structures flexible and efficient.</p>
        <p>Include: <i>Decorator, Facade, Flyweight, Adapter, Bridge, Composite and Proxy</i> </p>
    </li>
    <li>
        <b>Behavioral patterns</b>
        <p>These patterns are concerned with algorithms and the assignment of responsibilities between objects.</p>
        <p>Include: <i>Chain of Responsibility, Command, Iterator, Mediator, Memento, Observer, State, Strategy, Template Method and Visitor</i> </p>
    </li>
</ul>

<p align="justify">
   Above mentioned design patterns are common in software development. However, modern programming languages have problems, and new design patterns are also introduced. Thus, please keep in mind that the design patterns are also developing along with the growth of programming language; more design patterns will tackle modern problems in the future.
</p>
<br>

## 2. Why we need them?
<p align="justify">
    All of the patterns are proven and tested by experienced developers;
    therefore, instead of reinventing the wheel, we should implement design patterns to solve the same problem. Moreover, it is good to learn some design patterns to enhance your problem-solving skills. However, exploiting them will make everything more complicated and unnecessary. Design patterns do not solve all problems in software design, and the workflow will become complex and lengthy if developers implement them without consideration. On the other hand, software engineers use them as terms in communication to describe the ideas or solutions they mention.
</p>
<br>


## 3. Facade
<p align="justify">
    To have a clear picture of implementing design patterns in software development, this section will describe one of the common <i>Structural patterns</i>: <b>Facade</b>.
</p>
<p align="center"> <img src="./assets/facade-structure.png" > </p>
<br>

### **Intent**
<p align="justify">
    The idea behind Facade is to provide a more straightforward interface to interact with other third-party libraries or frameworks.
</p>

### **Problem**
<p align="justify">
    When the system integrates with other third-party libraries or frameworks, you need to keep track of every structure they provide. Moreover, initializing them requires running configuration with correct order or different steps chaining together. Therefore, It is tough to maintain or alter without rewriting the entire system.
</p>

### **Solution**
<p align="justify">
    The solution is to create a class that includes all the features that we need from the library. That class needs to grab everything that it needs from the third-party library to develop simplified versions of them. Then, if we need to change the feature, all we need to do is rewrite the Facade class instead of changing all the calls of third-party’s functions.
</p>

### **Implementation**
1.	Check if you could create a simpler version of it. If possible, define a **Facade** class that contains all the features you need from the library.
2.	The **Facade** class has a responsibility to initialize the third-party library and only needs to make changes here when you want to change the library's configuration.
3.	Make sure the subsystem code only communicates with your **Facade** class when it uses the feature of the third-party library.
4.	If the code becomes long and complicated, break it down into small classes.

<br>

### **Example (with Javascript)**
#### ***Scenario***

<p align="justify">
This example has a straightforward scenario. However, it requires you a little knowledge about HTML, CSS, and Javascript. The scenario is that you have a table on your webpage, and you need to provide a feature that alters the table. 
</p>

<p align="center"> <img src="./assets/table.png" > </p>
<br>
<p align="justify">In particular, to add a row to your table, these are the steps that you need to do in your code:</p>

```javascript
function addNewRow() {
    const row = document.createElement("tr")
    // Company
    const companyCell = document.createElement("td")
    const companyText = document.createTextNode("Facade")
    companyCell.appendChild(companyText)

    // Contact
    const contactCell = document.createElement("td")
    const contactText = document.createTextNode("Phat Tran")
    contactCell.appendChild(contactText)

    // Country
    const countryCell = document.createElement("td")
    const countryText = document.createTextNode("Vietnam")
    countryCell.appendChild(countryText)

    // Attach cells to row
    row.appendChild(companyCell)
    row.appendChild(contactCell)
    row.appendChild(countryCell)

    // Add row to table
    const tableElement = document.getElementsByTagName("table")[0]
    tableElement.appendChild(row)
}

addNewRow()
```
<br>

### ***Problem #1***
<p align="justify">Obviously, the code is long and a little complex. It requires extra steps before a new row is created:</p>

<ul>
    <li>Create a <b>td</b> element</li>
    <li>Create a <b>text node</b> and then append it to the <b>td</b> </li>
    <li>Repeat two steps above for creating another cell</li>
    <li>Append those <b>cells</b> to the <b>row</b> element</li>
    <li>Finally, attach the row to the table</li>
</ul>
<p>
    It needs to be refactored so that the developers can reuse it to add any rows from the users. So let's refactor the code above.
</p>

```javascript

function createCell(text) {
    const tdElement = document.createElement("td")
    const textNode = document.createTextNode(text)
    tdElement.appendChild(textNode)
    return tdElement
}

function createNewRow(companyText, contactText, countryText) {
    const row = document.createElement("tr")

    // Cells
    const companyCell = createCell(companyText)
    const contactCell = createCell(contactText)
    const countryCell = createCell(countryText)

    // Attach cells to row
    row.appendChild(companyCell)
    row.appendChild(contactCell)
    row.appendChild(countryCell)

    return row
}

const row = createNewRow("Facade", "Phat Tran", "Vietnam")
// Add row to table
const tbodyElement = document.getElementsByTagName("tbody")[0]
tbodyElement.appendChild(row)
```
<br>

### ***Problem #2***
<p align="justify">
    During the refactoring process, I focus only on the reusability of creating cells and adding rows. Thus, I split the previous code and put it into two different functions. As a result, it seems more reusable and flexible than the last code. However, the code will be easier to maintain and more clarified if wrapped within a class. 
</p>

```javascript
class Table {
    constructor(table) {
        // Check if the table already existed
        if (table) {
            this._ = table
        } else {
            // Create new one
            this._ = document.createElement("table")
            document.getElementsByTagName("body")[0].appendChild(this._)
        }
    }

    createCell(content) {
        const cell = document.createElement("td")
        const textNode = document.createTextNode(content)
        cell.appendChild(textNode)

        return cell
    }

    addRow(cells) {
        const row = document.createElement("tr")

        cells.forEach((cell) => {
            const cellElement = this.createCell(cell)
            row.appendChild(cellElement)
        })

        // Add row to table
        document.getElementsByTagName("tbody")[0].appendChild(row)

        return row
    }
}
```

<p align="justify">
    The purpose of wrapping within a class is to make it easier to maintain. Moreover, if the code requires more functions for creating a header or styling the cell, the time spent altering this class's implementation will not take long. All you do is call extra methods instead of refactoring the process.
</p>

```javascript
// Mockup data
const rows = [["Facade", "Phat Tran", "Vietnam"]]

// Create table instance
const table = new Table(document.getElementsByTagName("table")[0])

// Add rows to table
rows.forEach((row) => table.addRow(row))
```

<p align="justify">
    As you can see, the implementation of the <b>Table</b> class. It only takes one line to call the function <i>addRow</i>. Imagine if we need to add more functions to create a  header and footer. All we have to do is to call another function from the <b>table</b> variable.
</p>

```javascript
table.createHeader("Table header")
 ```
<br>

### Conclusion
<p align="justify">
After the above steps, you might realize that the Facade is similar to refactoring code. The Facade pattern intends to simplify the complex process, library, or framework. Thus, it requires a refactoring step to simplify your process and make them easy to use the function. Furthermore, in a real-life project, you integrate with other third-party APIs and might only use some of the features. This is where Facade comes in and helps you to wrap any necessary features and make them easier for anyone who might not get in deep into their documentation.
</p>
<br>
<hr>
<br>

<!-- ANTI-PATTERNS -->
# <div align = "center">Anti-patterns </div>
<p align="center"> <img src="./assets/anti-patterns-introduction-bg.jpeg" > </p>
<br>

## 1. What are anti-patterns ?
<p align="justify">
Since the design patterns' advent, anti-patterns were also introduced later to the developer community. However, unlike design patterns, anti-patterns are bad solutions to learn. 
Anti-patterns mostly come from managers or developers who are not having the experience or knowledge to handle the problem. It might get the job done in general; however, their solution is risky and might bring more harm than good. On the other hand, any solutions or methods that make the system counterproductive and sluggish are also considered anti-patterns.
</p>

<p>
According to <a href="https://sourcemaking.com/antipatterns">Source Making</a>, Anti-patterns consist of 3 groups:
</p>

<ul>
    <li>
        <b>Software Development Anti-patterns</b>
        <p>A key goal of development Anti-patterns is to describe useful forms of software refactoring. Software refactoring is a form of code modification, used to improve the software structure in support of subsequent extension and long-term maintenance. In most cases, the goal is to transform code without impacting correctness.</p>
    </li>
    <li>
        <b>Software Architecture Anti-patterns</b>
        <p>Architecture Anti-patterns focus on the system-level and enterprise-level structure of applications and components. Although the engineering discipline of software architecture is relatively immature, what has been determined repeatedly by software research and experience is the overarching importance of architecture in software development.</p>
    </li>
    <li>
        <b>Software Project Management Anti-patterns</b>
        <p>In the modern engineering profession, more than half of the job involves human communication and resolving people issues. The management Anti-patterns identify some of the key scenarios in which these issues are destructive to software processes.</p>
    </li>
</ul>
<br>

## 2. Examples
### **Magic numbers and strings**
<p align="justify">
    You can see numbers and strings in any source code project. Some numbers have an implicit meaning. For example, in the US, alcoholic drinks are only allowed for people who are 21 and over. Imagine that your project validates the person's age if they can drink alcohol. The condition will be like this.
</p>

```javascript
const age = 18
 
if (age < 21) {
    console.log("You are not allowed to order alcoholic drinks")
} else {
    console.log("You are allowed to order alcoholic drinks")
}
```
<br>
<p align="justify">
It looks pretty normal to the code above; however, it might be very confusing for those who do not live in the US, where it has a different rule for drinking alcohol. 
To avoid this, we can declare a variable with a name to make it easier to understand the context.
</p>

```javascript
const age = 18
const legalDrinkingAge = 21

if (age < legalDrinkingAge) {
    console.log("You are not allowed to order alcoholic drinks")
} else {
    console.log("You are allowed to order alcoholic drinks")
}
```
<br>
<p align="justify">
    Suppose the project extends to another country where the law is different, and you need to change the number. In that case, all you have to do is to change to the number at “legalDrinkingAge,” and other places that use the number 21 will automatically be applied.
</p>
<br>

### **Spaghetti Code**
<br>
<p align="center"> <img src="./assets/spaghetti-code.png" width=600> </p>
<br>
<p align="justify">
    This Anti-pattern is very common in new developers, making the code with zero structure, and nothing is modulized. It makes the project difficult to maintain or add new functionality.
    The solution for this pattern is to break things into small groups and start writing annotations for their functionality. Then, define the relationship between groups and modulize them by their relationship. The key is to make everything is more reusable and extendable.
</p>

<p>You can acknowledge this Anti-pattern in the example code of Facade, where all the code is wrapped within one function.</p>
<br>

### **Gold Hammer**
<br>
<p align="center"> <img src="./assets/gold-hammer.jpeg" width=600> </p>
<br>
<p align="justify">
    Imagine that you are very good at implementing the Facade pattern, and you started exploiting it in every project. However, the task gets more extensive, and the Facade pattern is no longer suitable. You do not care about the performance because it gets the job done. However, the unproductive and lagging will cost your business money and bring a bad experience to the customers.
    There is no "best" technology in this industry, and every technology is born to solve a problem. If you pick the wrong tool to fix a problem, the result will worsen.
</p>
<br>
<hr>
<br>

<!-- DESIGN PATTERNS IN  MOBILE DEVELOPMENT-->
# <div align = "center">Design Patterns In Mobile Development </div>
<p align="center"> <img src="./assets/design-patterns-mobile.webp" width=600> </p>
<br>
