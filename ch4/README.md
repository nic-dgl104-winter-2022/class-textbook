# DGL 104 Winter 2022 - Class Textbook
## Chapter 4

### TOC

Chapter 4
<h2>What is refactoring?</h2> 
Simply refactoring is the process of restructuring the code, making it small, and improving it without altering the outcome of the program. If the outcome of the program is the same then why do you have to have a headache about refactoring if it does not have anything about the program. Yes, it does not have anything to do with the output of the program however refactoring is necessary for everyone to be a better developer. Why?  The main goal of refactoring is to make code easier to understand and maintain in the future and avoid technical debt. Sometimes if you write a code for your project or something and you just give poor variables names, bloated classes, functions, and your code is messy then when you come to look at the code later you will be just lost in your own code. Clean code is easier to understand and if you are working in a group that will be easier for yourself and your colleague too. Similarly clean and less code will have fewer bugs and less maintenance tends to pass the tests.

<h2>Technical Depth</h2>
Suppose you wanna buy something but you don’t have money at all and you end up taking a loan from the bank. So now you will be able to purchase with that money but you have to pay the interest and principal back and sometimes you can end up paying more than you are able to and place you in a really bad situation. The exact same thing can happen with your code. You write a code without testing and refactoring and keep on adding new features but at some point it can put you in a situation where it slows your project as you need to test and force you to rewrite code at all.

<h2>Clean code and Dirty code</h2>

Clean code is easier to get and understand.

You can see the differences in the examples below 

if(!foo){
    foo = 'apple';         bar(foo || 'apple', kip);
  }
  bar(foo, kip);
 

    
TAX = 15000000; <br>
const SALARY = 150000000,

<br>

The above code can be written as

<br>
TAX = 15e6; <br>
const SALARY = 15e7,
 


let words = [];
 
function setWords(...theWords) {
words = [...theWords];
}
 
setWords( 'education', 'dog', 'cat', 'jumped' );
 
let showButton = document.getElementById('show');
showButton.addEventListener('click', showWords);
``
 
function showWords (e) {
let edWords = document.getElementById('edwords');
let otherWords = document.getElementById('otherwords');
var ed = [];
var other = [];
 
for (let i=0; i<words.length; i++) {
if ( words[i].includes ("ed")) {
ed.push(`<li class="list-group-item"> ${words[i]} </li>`)
    }
 
 else{
other.push (`<li class="list-group-item" >${words[i]} </li>`);
        }}
console.log (ed);
edWords.innerHTML = ed.join("");
otherWords.innerHTML = other.join("");







'use strict';
 
let words = [];
 
function setWords(...theWords) {
    words = [...theWords];
}
 
setWords( 'education', 'dog', 'cat', 'jumped' );
 
let showButton = document.getElementById('show');
 
showButton.addEventListener('click', showWords);
``
 
function showWords (e) {
 
    let edWords = document.getElementById('edwords');
    let otherWords = document.getElementById('otherwords');
 
    var ed = [];
    var other = [];
 
    for (let i=0; i<words.length; i++) {
    
        if ( words[i].includes ("ed")) {
        ed.push(`<li class="list-group-item"> ${words[i]} </li>`)
    }
 
        else {
        other.push (`<li class="list-group-item" >${words[i]} </li>`);
        }
    }
 
    console.log (ed);
 
    edWords.innerHTML = ed.join("");
    otherWords.innerHTML = other.join("");
}


<h2>When To Refactor?</h2>
Whenever adding new features you should refactor and make sure your existing code and design are good so that it will be easy for writing new code. If you have to deal with somebody else dirty code first try to refactor it so that clean code is easier to get for you. If you have to fix bugs first try to make your code clean by refactoring so the bugs will appear themselves.

<h2>Refactoring Principles</h2>
Key things you could focus on while refactoring 
Removing the duplication as it will make your code smaller by making different functions and strings. Give the proper names to the functions and variables as it will be more specific to understanding the code. Try to make your code small as it will help you to better understand, test and maintenance. Always keep testing frequently as you refactor so that no bugs are introduced and the outcome of the program is not altered.

<h2>Refactoring Examples</h2>

![image](https://user-images.githubusercontent.com/90713152/161491787-61a3f756-531f-4dde-8ab6-ec0cad42b81c.png)


The above code can be refactored as-


![image](https://user-images.githubusercontent.com/90713152/161491899-17e7ca58-352f-4adc-808a-1994a1dff721.png)









   
                               
If (isSpecialDeal()) {                                                        If (isSpecialDeal()) {      
   total = price * 1 ;                                                           total = price * 1;    
   send();                                                                     }
}                                                                             else {
else {                                                                            total = price * 1.5;
   total = price * 1.5;                                                        }                                                      
   send();                                                                    send();
}
 
Try to give specific names to your functions, methods, variables related to its purpose
like createOrder(), getFirstName(), getSecondName(), instead of giving short forms as it will be harder for yourself to get your own code later. 

5 Common Mistakes You Might Be Making As An Aspiring Developer

Ryan Stich

Now that you’ve learned how to debug your code, it's time to take a look into what makes good code so good. And how you as a programmer can write like a senior developer. IntentHQ (https://intenthq.com/blog/it-audience/what-is-good-code-a-scientific-definition/) asked 65 developers what makes good code, and by far the most common answer was that the code had to be readable by humans, not just computers. 

But what does that actually mean? Readable by humans? Isn’t all code readable… The short answer is yes but not all readable code is of the same caliber. Let's say you have a file with multiple functions written out in the file. You wrote these functions knowing their intent and purpose, and at the time of writing them, all of these things made sense. But 6 months or maybe even a year later it's time for your codebase to receive a slight upgrade. Confidently you pass off your excellent functions to another developer as this new developer will be overseeing the upgrades. And that's when things go awry. 

The developer comes back to you and gives you a list of things wrong with your perfectly created functions. No code commenting, poor naming conventions, repeating code, variables have multiple purposes, and all of the whitespaces are essentially non-existent. 

This is where refactoring comes to the rescue. Refactoring is the process of restructuring existing code & changing the factoring without actually changing any of the code behavior. This can be something as simple as upgrading your code by changing the naming conventions to something that better reflects your functions & variables, or this could be something such as changing your basic javascript function to an ES6 arrow function. 

So now that you’re aware of how you can refactor code, let's dive into a few examples of where beginner programs often leave their biggest mistakes.

And what better place to start than where we just left off! The most common problem that any developer could make across the board, whether you’re a junior or a senior not using comments is a massive problem! Let’s take a look at this THREE.JS code. First without comments, and then again with an explanation

`const scene = new THREE.Scene(); const camera = new THREE.PerspectiveCamera( 75, window.innerWidth / window.innerHeight, 0.1, 1000 ); const renderer = new THREE.WebGLRenderer(); renderer.setSize( window.innerWidth, window.innerHeight ); document.body.appendChild( renderer.domElement );`


As someone who’s maybe just getting started with javascript frameworks can be confusing enough, but there can come times when you are thrown into a mix of code and you are not entirely sure what the purpose is. So now let’s take a look at this code, but with some proper commenting and explanations involved.

// To be able to create anything within three.js, first, we need to create a scene. And that's exactly what we’re doing below

const scene = new THREE.Scene(); 

// From here to render our scene, we need some eyeballs on the scene. But since three.js doesn't have an eyeball option, it looks like these cameras will work! So first thing to get us started we’re going to be adding a camera to our scene. These cameras take a few parameters before we can get them into action, these include things such as a field of view and an aspect ratio. 

const camera = new THREE.PerspectiveCamera( 75, window.innerWidth / window.innerHeight, 0.1, 1000 ); 

// Next up here is the renderer, This is where our scene truly comes to life. Because we’ll be setting our entire scene up to be rendered, by our renderer. 

const renderer = new THREE.WebGLRenderer(); 

// Next we’ll be setting the size of our renderer, for this example, we’ll be using the entire page. And then we’re going to append our renderer to our DOM so that we can view it in our browser.

renderer.setSize( window.innerWidth, window.innerHeight ); 
document.body.appendChild( renderer.domElement );

See the difference a few comments can make? While these comments may be slightly over the top, the better of an explanation you can give, the more it can clear up some foggy code for a teammate.

 When team environments are working on multiple projects on a daily basis and writing bits and pieces of code all over the place, it’s pretty much guaranteed that we will forget what we have written. This is because programmers often find themselves jumping between one complex problem after another, requiring their full attention. So the practice of refactoring your code to include comments (or just writing them as you code!) will be helpful to us in the future, as well as respectful practice for your teammates. When it comes to problem-solving commenting allows you or a team member to easily dive into a section that could have a bug in it, therefore with the combination of good clean refactored code and your debugging knowledge, nothing should get in your way of writing excellent code.

The second mistake that can lead to a debugging and refactoring nightmare can be writing code to solve a problem that you as a developer, don't fully understand. Working in a team environment you can sometimes be broken off to write a chunk of code, requiring that piece of code to later be integrated into your codebase. This can quickly become a headache if you do not understand the problem, therefore in my own architecture, I believe it's important to seek first to understand before being understood. This is an extremely important principle in writing clean code. And this is just another example of how abstract the art of refactoring can truly be. Before even writing a line of code you can be refactoring ideas and structurally sound architecture maps in your head. And this leads us to our next item on the list!

Let’s say for example that we’ve got a client who is searching for an eCommerce store to be built, our client has chosen to go with a fully custom build and does not want to use Shopify. Someone new to development may dive in and begin to write some code and solve the problems as they arise. However, the correct approach would first be to brainstorm your options, talk about solutions amongst your team and then begin developing some code. 

Brainstorming. The reason refactoring exists is because there are so many ways that you can write code. You can write some terrible code and often times it can still manage to get the job done. However, it may not look too sharp within your portfolio when you’re applying for jobs! We all wanna get better at what we do, it's human nature to improve. Therefore before we write code we should always weigh our options before going with our first immediate thought. In design, there is a commonly known and talked about principle that “your first idea may not always be your best idea”. Most designers will take days and sometimes weeks to map out their ideas, before selecting one to move forward with. As your first idea is unfortunately seldom the best or most creative possible solution to a problem, actually it's often said that your first idea was the most obvious. In the world of programming, the designers have often completed their work before passing it off to us, and as the project crunch comes down to meeting the deadline we often don't have those extra days we would like to take for brainstorming. And that's where your team can come in handy. Getting together for a quick 2-3 hour brain-storm before writing a single line of code and just throwing ideas at the wall can oftentimes be just enough to eliminate any of those poor ideas that you may have. So remember, always refactor ideas before you refactor any code! It saves time in the end and can make you a better programmer in the end.

Taking small steps. Many people fresh learning how to code can easily find themselves getting lost within the many different communities that take place in coding, Whether that's through Youtube, Discord, Twitter, Reddit. Pick your poison they arent hard to find! But one thing that can become increasingly scary and overwhelming, to begin with, is where and how to start carving out your own path within this ever-evolving world of development. When I was first getting started I was heavily influenced by a few YouTuber's skillsets so much so that I ended up trying to take a course in React without ever really having the basics of javascript down. Small steps are extremely beneficial to big-picture learning. That’s why it's important to get a strong base knowledge in things such as javascript before learning typescript, or CSS before learning sass. 
Taking small but prominent steps forward in your learning allows you to later take small steps within your refactoring process. If you can’t translate the code you wrote from code to English in your head, line by line; refactoring in itself can become extremely difficult and you could potentially be putting in hours to a problem that should only take minutes. Given the nature of code, especially a language such as javascript that I have chosen to focus on throughout this entire introductory blog post. Javascript on a good day can be incredibly finicky to get just right, so throwing the wrench of refactoring without a strong base knowledge can trip you up very fast. Leaving you and your team in a worse position than you were to start. in the end, this might be one of the most important aspects to consider next time you are refactoring code. This issue ties in strongly with writing code to solve a problem that you as a developer, don't fully understand. 

And our last, but not least important topic of this post has to be saving time by making duct-tape fixes within your work. There's a good chance as a programmer you are constantly busy with one thing or another. When one piece of code is fixed another one breaks, that's essentially the way things go. It can oftentimes be tempting to throw a quick, mediocre fix within an error that will at least temporarily stop the bleeding and you can get back to your main priorities. However, the issue with this is, that as one fix becomes another fix this can be a fast and effective way to kill the quality of your organization's codebase. If you’re in a hurry and can’t fix this bug at the time of it being spotted, then it's best that you or a member on your team put a quick fix in, but schedule time to refactor the code that caused the bug to occur in the first place.

Now that you’re familiarized with some of the best practices in refactoring, as well as some of the best practices for becoming a better developer. Let's get started in the next chapter by diving into our refactoring principles!



<h2>Common Code Issues - Ryan Stich</h2>

Now that you’ve got some insight regarding issues that can occur as a programmer, it’s time to dive into the most common code issues that we as developers can encounter while on the job. As you’ve learned previously through the study of debugging and introduction to refactoring, you’re probably familiar with how these issues can start, and snowball over time. When it comes to refactoring we often are not aiming to fix mistakes, that comes in the debugging process. The majority of code issues usually stem from things such as incorrect variables names, poor code structure, and of course undocumented code.

When refactoring it is good practice to test often and make sure you are not introducing any new problems that had not been previously there before. Understanding that refactoring is not just a single job but an ongoing process that spans the lifetime of the codebase you are working with is something that many programmers could benefit from. adapting, altering, and tweaking is all a part of the job; and our job as refactoring experts is to make sure that the code is in a better condition than the way we found it. With the goal of creating a welcoming environment for other developers to jump in and out of. 

If you’ve ventured into the world of programming, via self-taught projects, tutorials, or through a class, you’ve likely heard the term “don’t repeat yourself”. This is one of the simplest phrases but has become engrained in all programmer's heads as it is one of the most important pieces of advice that can be given. Duplicated code and many functions that ultimately do the same thing can cause processes to become slower and more tedious. This problem can come in many forms, from code to logic this is all something we’re guilty of from time to time. But with this knowledge in mind, you can take your programming skills to the next level. Let’s take a look at an example and how we could improve upon it. 

`function logText(text) {
console.log(text)
}`

In this function, we are taking in some text and we are going to log it into our console and see what we get. But let's say perhaps this file we wrote this in pertains to only one section in our codebase, and as we begin writing code in a new file we forget about what we’ve written there. 

`
Const logSameText(message, text) => {
console.log(message, text)
}
`
Now we’ve written this function because in our new file we’d like to see a message and that original piece of text. There is nothing wrong with either of these functions, the issue actually arises with our duplicated code. And as these functions are living in very different sections of our codebase, finding them can be a pain in the neck. As you begin to build out various sections of your website or web app these things can begin to add up. The proper solution here would be to create a single function that we can then call upon in various sections of our app. This practice is known as keeping code DRY (Do Not Repeat). Becoming a dry programmer can be a tough task at first but after you’ve begun to mindfully implement this practice, it will become second nature. 

Another main refactoring issue that we run into on our journey is poor naming conventions. When we create functions and variables it makes sense to give these things names that play into the regard of what they actually do. However, while that may sound simple on the surface, that does not mean that you should name your next variable “my_Favoruite_Number_Is_ThirtyTwo” Instead there are three basic concepts that we should keep in mind when we name our variables, and those are as follows

The variable name must describe the information that is represented by this said variable. We should aim to quickly display what value this variable holds, simply by looking at the name

Your code will be read infinitely more than your code will be written, with this in mind its important that we as developers always aim to prioritize how easy the legible of our code is over than how quickly it is constructed.

Implementing standard code practices for naming -  for your specific language, as different languages follow different naming practices this is something important to look into

So in theory this sounds easy enough to follow, but what does this actually look like in practice? Well let's take a look at some poor naming conventions and some good ones, and you can decide for yourself if, located inside a codebase, this would make a difference to you.

For this example we’ll be creating someone's full name, so to do that we’ll need 3 variables. A user's first name, last name, and the user's middle name. I’ll give you 3 different sets of variables and let you choose which section of variables you think follows the proper conventions. 

Section one

`
Var FIRSTNAME = “Ryan”
Let MIDDLENAME = “Wayne”
Const LASTNAME = “Stich”




Section Two
`
Let firstName = “Ryan”
Let middleName= “Wayne”
Let lastName = “Stich”
`

Section Three

`
Let FIRST_NAME= “Ryan”
Let MiddleName = “Wayne”
Let LAST_NAME = “Stich”
`

Given those three sections, if you had chosen anything outside of code block #2, you would be conforming to poor naming convention standards. The above code is written in javascript and javascript is known for its use of camelCase variables, as well as PascalCase. However, this can get messy as javascript variables are case-sensitive. This means that you could generate three different variables that all look identical, such as name, Name & NAME. That’s why it's equally as important to choose the correct type of variables, such as let for something that is mutable and const for something that is immutable. 

We all desire to write the perfect code that follows all best practices and of course, is bug-free, but the reality of the engineering code is that just simply isn't possible as human error will forever be unavoidable. But one thing that can assist us in our process, especially when we’re working in teams can be design patterns. Design patterns enable us to implement tried and true solutions to common problems that other developers have faced and overcome. Implementing well-documented solutions, allows us to inch our code closer to that perfect code we’re all aiming for. This is something you’ll learn more about in chapter 7. So until then, we’ll just be focusing on the next section which is a step-by-step guide on how to refactor. 


<>h2Code Review</h2>

As part of the refactoring process, code review is an essential part of software
development. When refactoring, you do not want to accidentally change the function of
the code or introduce new bugs. Software is limited in how it can assist with code
review. A human brain is required to truly understand and review any code that is
refactored and having a fellow developer review your code might catch issues or
problems that you have overlooked.
1. Code Review Purpose
The purpose of code review is to ensure code quality. Perfect code is impossible, and
developers should be striving for better code during review rather than perfect code. Code
review also encourages communication within programming teams and acts as a
learning opportunity for new developers as well as senior developers.
2. Code Review Etiquette
Two parties are involved in the code review process, the reviewer, and the reviewee.
Before the code is submitted for review, the reviewer should be confident that their
code works as intended and should be prepared to justify the choices they made during
refactoring or development. The reviewer should be prepared to take constructive
criticism and take notes on the suggestions the reviewer gives to them. The reviewer
needs to be respectful of the reviewee. The purpose of code review is to teach your
fellow programmer and help them improve the code, providing constructive criticism
rather than just criticizing them with no sense of respect.
Good feedback: “I suggest using a loop for loop to input the values into the linked list
rather than writing a call to the function for each value.”
Bad feedback: “Why are you using if-else statements when you can just as easily
use a switch statement! It makes your code almost unreadable!

3. What to Look for in Code Review.
The first thing to look for during code review is the overall design of the code.
What is the intended purpose of the program? How do all the components of the
code fit together to make the program work? Understanding how the code is
supposed to work is essential to review the code properly. Good practice is to
have documentation outlining the intended purpose of the code.
After understanding the design of the code, the next step is to review the styling
of the code. Why styling before testing functionality? Because if the code is
readable, then it will be easier to find bugs. The style of the variable names and
methods should be consistent with the official styling guide for whatever
programming language is given. Variable names should be descriptive rather
than shortened, future programmers may not be able to decipher what “jwlry”
means, especially if English is not their first language, a better name would be
“jewelry”. Avoid repeating variables and names since it can make calling a
specific function in the future hard. Each variable should have its own name.
Good example java:
public int ticketBooth(int price) {
int priceAfterTaxes = price * 1.12;
return price;
}
Bad example java:
public int TBooth(int p) {
int pTaxes = p * 1.12;
return pTaxes
}
After cleaning up the styling of the code, the next thing to test for is the
functionality of the code. Does the code work as intended? This is the time to
look for any bugs and find any logical errors in the code. When testing the code,
one should strive to make the code fail and fail fast. Test as many values as
possible and note which ones work with the program and which make the code
fail. That way you can know exactly what the program is and is not capable of.
Static code will fail faster than dynamic code which will fail faster than the wrong
answer. When appropriate, choose for methods to return a value rather than print
a value, that way the value can be used for other functions rather than for only
printing the answer.

Avoid over complicated code. Code that is too complicated can make it harder for
other programmers to update in the future. Over complicated code is usually the
result of over engineering, usually because of programmers anticipating what the
code might need in the future. Good practice to avoid over engineering is to
focus on what need to be programed now, rather than what need to be
programmed in the future. Deal with issues as they come along.


4. Code Review Methods
There are many ways to conduct code review. The most straightforward method is to
have a colleague look at the code with you at your computer. This allows for real time
code review and allows you to talk about the code directly. Another method is to email
multiple numbers of colleagues for code review, this allows for your code to be reviewed
even if there is no one physically there to look at your code and provide feedback
directly. The downside is that with multiple reviews comes a variety of different methods
that you as the reviewee will have to filter out. Two programmers may decide to work on
their projects concurrently and review each others code while the code is in
development, and software tools can be used to aid in code review.
5. Ensure Code is Adaptable
All in all, whenever changes are made to the code, whether you are refactoring or
whether you are adding a new feature, always ensure that the code can be updated in
the future. Due to the constant changes in technology, code that is not consistently
refactored and updated will become stale and lose its function over time. That is why
when writing code, it should be done in a way that allows the code to be updated over
time. This can be achieved by following good coding practice which is improved by code
review.

SOURCES

Ryan Stich Blost Post 

IntentHQ - https://intenthq.com/blog/it-audience/what-is-good-code-a-scientific-definition/

Refactoring - https://www.bmc.com/blogs/code-refactoring-explained/
https://medium.com/swlh/the-ultimate-engineers-guide-to-code-refactoring-c38372632906

Ideas for choosing common mistakes 
https://www.toptal.com/web/top-10-mistakes-that-web-developers-make
https://medium.com/geekculture/9-common-mistakes-that-developers-often-make-4ceeab9ca09a

Design Philosophy - https://hbr.org/2021/01/your-best-ideas-are-often-your-last-ideas
https://hbr.org/2017/08/to-come-up-with-a-good-idea-start-by-imagining-the-worst-idea-possible


Ryan Stich Blost Post *END*

Ryan Stich Common Code Issues In Refactoring

Refactoring Problems https://blog.devgenius.io/problems-that-we-may-run-into-when-refactoring-96ba081cabe
https://www.altexsoft.com/blog/engineering/code-refactoring-best-practices-when-and-when-not-to-do-it/
https://www.merixstudio.com/blog/10-signs-your-codebase-needs-refactoring/

References - Refactoring Principles
Shakshyam
Refactoring: clean your code
The Pragmatic Programmer (nic.bc.ca)
Refactoring
 
 
REFERENCE: Code Review
 Isabella 
 
Reading 4: Code Review (mit.edu)
The Standard of Code Review | eng-practices (google.github.io)
What to look for in a code review | eng-practices (google.github.io)
What Is Code Review? | SmartBear
Instructor Ashley’s slides on code Review were used
 
 

