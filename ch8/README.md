# DGL 104 Winter 2022 - Class Textbook
## Chapter 8

**MVC** is an architectural pattern and it stands for Model, View, and Controller. It is a pattern to represent information and data to the user. It was used for desktop graphical user interfaces but nowadays is used in designing mobile apps and web apps. Let’s dive into it by first understanding its history.

## History:

Trygve Reenskaug was the first who proposed the idea of MVC to this world. According to Wikipedia, when he was a visiting scientist at Xerox Palo Alto Research Laboratory (PARC) in 1978/79, he wrote the initial reports on MVC. MVC was originally known as "Thing Model View Editor," but it was soon changed to "Model View Controller."

As with every technology, it keeps updating over time, something similar happened to MVC. It gets evolved over the years as Trygve & his mates designed it to address the issue of users controlling a large and complex data set. 
From the book Naked Objects <sup>[16]</sup> , the motivation behind MVC was to allow the creation of a graphical interface for any object.

According to Matin Fowler 2006 GUI Architectures blog <sup>[17]</sup> , MVC pattern started giving rise to other architectures like the hierarchical model–view–controller (HMVC), model–view–adapter (MVA), model–view–presenter (MVP), model–view–ViewModel (MVVM), etc.

<p align="center">
  <img src="https://user-images.githubusercontent.com/61209227/159332175-013dffe1-11ad-4cb8-a5bd-370b0dc16815.png" />
</p>

## MVC Architecture:

<p align="center">
  <img src="https://user-images.githubusercontent.com/61209227/159610172-24ec9d1a-d867-4f41-b328-af83c5001ef4.png" />
</p>

**1.	User View Interaction:** First of all a user will interact with the views present in the app or website. Views are like Textview, EditText, ImageView, etc. 

**2.	View Controller Interaction:** When a view is displayed to the user, it alerts the controller of that particular event. 

**3.	Controller Model Interaction:** Now, the controller updates the Model i.e. view requires data to show the user.

**4.	Model View Interaction:** Model alerts View that data is changed now in the Model.

**5.	View Model Interaction:** Final work of View is to get that updated data from the Model and display it to the user.

This cycle keeps rotating until and unless the user closes the app or website. Here, Model, View, and Controller are the main components of the MVC architecture let’s look more closely at each of them. 


## Model:

It is considered as a low level because it is responsible for data management.
Handle data logically, therefore it's all about data. Because the model is
linked to the database, anything you do with data will be represented in the
model. The model component is where you add or retrieve data.

Because the controller never connects to the database by itself, it reacts to controller
requests. The model interfaces with the database and then provides the
required data to the controller. It's important to note that the model never
directly communicated with the view.

## View:

The view component is in control of data representation. It creates the user
interface, or UI, for the user. So, when you think of a view component in a web
application, only think of the HTML/CSS section. 

The data acquired by the model component is used to generate views, but these data are passed
through the controller rather than directly to the view, so the view only
communicates with the controller.

## Controller:

Because the controller is the component that allows the interconnection
between the views and the model, it is known as the "main man." The
controller doesn't have to handle data logic; all it has to do is inform the
model what to do. 

After getting data from the model, it processes it before
sending it all to the display and explaining how to represent it to the user.
Views and models cannot interact directly.

## KeyPoints:

● The model is concerned with the facts and logic of your system.

● The controller maintains the link between the model and

● the view, while the view only displays data. This 'division' improves
the user experience and modularity while also making testing easier.


## Advantages & Disadvantages:

Let’s look at some advantages and disadvantages of MVC-


| **Advantages**                             | **Disadvantages**                  |
| ----------------------------------- | ----------------------------------------- |
| Good for large-size applications and websites.| Not suitable for small applications and websites.
| Using MVC you can easily modify your application or website. | The cost of frequent updates will increase if you have an application or website which required to be updated almost every week.
| Supports Test Driven Development, Asynchronous Method Invocation, and multiple views. | Implementation of MVCC is difficult in comparison to its other variants like MVVM. 

                                         
## MVC EXAMPLE:

Let’s try to understand the MVC architecture pattern using a very simple android application.
Here we will be building an app for login or authentication. We will be using Kotlin but you
can also use Java.

**Step 1. - Create a new Android Project**

Click on your Android Studio icon and create a new project with an empty activity. You can
name your project anything you like, we named it as MVC Example.

**Step 2. – Create three packages**

To implement MVC architecture in this project we have to create three different packages-

**1. Model**

**2. View**

**3. Controller**

Each package will be containing classes and interfaces. To create these package
folders –

                    Right Click on the project name > New > Package
             
**Step 3. – Create interfaces and classes**

Now, we have to create files and interfaces in the package we created above.
In Model Package create two files-

**iUser.kt**
```
package com.prabhjot.mvcexample.Model
interface iUser {
  fun getEmail(): String?
  fun getPassword(): String?
  fun isValid(): Int
}
```

**User.kt**
```
package com.prabhjot.mvcexample.Model

import android.text.TextUtils
import android.util.Patterns

class User(
    private val email: String?,
    private val password: String?
) : iUser {

    override fun getEmail(): String? {
        return email
    }

    override fun getPassword(): String? {
       return password
    }

    override fun isValid(): Int {
        if (TextUtils.isEmpty(getEmail()))
            return 0
        else if (!Patterns.EMAIL_ADDRESS.matcher(getEmail()).matches())
            return 1
        else if (TextUtils.isEmpty(getPassword()))
            return 2
        else if (getPassword()?.length!! <= 6)
            return 3
        else
            return -1;
    }
}
```
Now, for the controller package, we have to create one interface iLogin, and a class named as Login.

**iLogin.kt**
```
package com.prabhjot.mvcexample.Controller

interface iLogin {
    fun OnLogin(email: String?, Password: String?)
}
```

**Login.kt**
```
package com.prabhjot.mvcexample.Controller

import com.prabhjot.mvcexample.Model.User
import com.prabhjot.mvcexample.View.LoginView

class Login(
    private val loginView: LoginView
) : iLogin {

    override fun OnLogin(email: String?, password: String?) {
        val user = User(email, password)
        val loginCode = user.isValid()

        when (loginCode) {
            0 -> {
                loginView.OnLoginError("Enter Email");
            }
            1 -> {
                loginView.OnLoginError("Enter a valid Email");
            }
            2 -> {
                loginView.OnLoginError("Enter Password");
            }
            3 -> {
                loginView.OnLoginError("Enter Password greater the 6 char");
            }
            else -> {
                loginView.OnLoginSuccess("You logged in.");
            }
        }

    }
}
```

We are done with model and controller. Now, its time to design UI using View so that data will be displayed in the views.

**LoginView.kt**
```
package com.prabhjot.mvcexample.View

interface LoginView {
    fun OnLoginSuccess(message: String?)
    fun OnLoginError(message: String?)
}
```

**Output –**

<p align="center">
  <img src="https://user-images.githubusercontent.com/61209227/159333316-b352134f-0978-49d8-8739-4bd50e41c5d1.png" />
</p>

With this example, we learned how we can implement MVC architecture in an Android App
using Kotlin. Below are some recommended posts by which you can understand MVC
examples more clearly.

## Conclusion:

So MVC isn't easy to understand; in fact, it's really difficult to understand,
but it's not impossible to learn, and every developer should keep it in mind
when designing an application. Keep in mind that MVC is a software
architecture that breaks down your software into smaller pieces. The model
is concerned with the facts and logic of your system. The controller maintains
the link between the model and the view, while the view only displays data.
This 'division' improves the user experience and modularity while also
making testing easier.

## Resources :

**1.**  [All about MVC from Wikipedia](https://en.wikipedia.org/wiki/Model%E2%80%93view%E2%80%93controller)

**2.**  [Notes and Historical documents from Trygve Reenskaug, inventor of MVC.](https://folk.universitetetioslo.no/trygver/themes/mvc/mvc-index.html)

**3.**  [The Evolution of MVC and other UI architectures from Martin Fowler](https://martinfowler.com/eaaDev/uiArchs.html)

**3.**  [Model View Controller Theory from raywenderlich](https://www.raywenderlich.com/books/advanced-android-app-architecture/v1.0/chapters/2-model-view-controller-theory)

**4.**  [What is wrong with MVC from cocoasts](https://cocoacasts.com/what-is-wrong-with-model-view-controller)

**5.**  [Benefits of using MVC from gfg](https://www.geeksforgeeks.org/benefit-of-using-mvc/)

**6.**  [FreeCodeCamp- What is MVC, and how is it like a sandwich shop?](https://www.freecodecamp.org/news/simplified-explanation-to-mvc-5d307796df30/)

**7.**  [Video- The Principles of Clean Architecture by Uncle Bob Martin](https://www.youtube.com/watch?v=o_TH-Y78tt4&feature=youtu.be)

**8.**  [Video- MVC Explained in 4 minutes.](https://www.youtube.com/watch?v=DUg2SWWK18I)

**9.**  [Video- Why ASP.NET MVC and MVC vs WebForms ?](https://www.youtube.com/watch?v=bGpBgDDDVlM)

**10.** [MVC Architecture Pattern in Android with Example](https://www.geeksforgeeks.org/mvc-model-view-controller-architecture-pattern-in-android-with-example/)

**11.** [Use MVC pattern to create very basic Shopping Cart](https://androidexample.com/Use_MVC_Pattern_To_Create_Very_Basic_Shopping_Cart__-_Android_Example/index.php?view=article_discription&aid=116)

**12.** [Implementing MVC pattern in Android with Kotlin](https://www.codementor.io/@dragneelfps/implementing-mvc-pattern-in-android-with-kotlin-i9hi2r06c)

**13.** [The Model View Controller – MVC Architecture and Frameworks Explained.](https://www.freecodecamp.org/news/the-model-view-controller-pattern-mvc-architecture-and-frameworks-explained/)

**14** [MVC Login Validation Example in JAVA](https://protocoderspoint.com/model-view-controller-android-mvc-example-login-validation/)

**15** [MVC Login Validation Example in Kotlin](https://medium.com/@anilkumar2681/kotlin-login-demo-using-mvc-pattern-with-validation-a4e030b50f9f)

**16** [Book Naked Objects by Richard Pawson & Robert Mathews](https://www.amazon.com/Naked-Objects-Richard-Pawson/dp/0470844205)

**17** [Matin Fowler 2006 GUI Architectures blog](https://martinfowler.com/eaaDev/uiArchs.html)





                   

