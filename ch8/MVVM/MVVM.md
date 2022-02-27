<img src="./assets/unsplash_illustration_image.jpg" width="700">

# A detailed exploration of the Model View ViewModel architectural pattern


As a part of my course, I want to introduce you to MVVM. Microsoft introduced this pattern in 2005, and it runs on [.NET](https://dotnet.microsoft.com/en-us/), [Silverlight](https://www.microsoft.com/silverlight/). Also, Google fully supports and [encourages using MVVM](https://developer.android.com/jetpack/guide) for Android development with their first-party libraries such as LiveData. Kotlin is a technology I’m going to use for my demonstration.

MVVM uses [Separation of concerns](https://en.wikipedia.org/wiki/Separation_of_concerns), separating a computer program into distinct sections. In the case of MVVM, there are three parts that help accomplish the separation of concerns: View, ViewModel, and DataModel.

<img src="./assets/MVVM_general.png" width="700">

## View
As in other patterns such as MVP or MVC, a View is a user interface that displays data and a layout that users can see and interact with, such as TextViews and RecyclerViews. Generally speaking, a View might do everything that Activity or Fragment can do.

## ViewModel
A ViewModel is like a middleman that prepares data for a View. It binds data and business logic from the repository.

<img src="./assets/ViewModel.png" width="700" >


In the image, you can see how that all works. A ViewModel makes the appropriate data observable. That means ViewModel exposes relevant data from a Model, and ViewModels don’t need to be directly connected to Views. Views are observing it and catch changes that ViewModel makes.

The advantage of this approach is that a ViewModel doesn’t know that Views are observing it. It can be easier for testing that there is less engagement between classes.
We would use the [LiveData](https://developer.android.com/topic/libraries/architecture/livedata) library for this observing data to create observables. The biggest advantage of this library is that it unsubscribe activities or fragments that have been already destroyed. A developer is free from managing the lifecycle methods then.

## Model
Model or also known as a DataModel, it exposes data. However, there is one intermediate step between the Model and a ViewModel called Repository. The Repository is known as the [Single Source of Truth](https://www.mulesoft.com/resources/esb/what-is-single-source-of-truth-ssot) (SSOT). It has access to the data sources and decides where the data is coming from. The data can be of any kind, and they can come from a remote server or the local database. Whenever a ViewModel needs some data, it gets them from the Repository. As it was with a ViewModel and a ViewModel, the Repository doesn’t know what ViewModels is using its data.

<img src="./assets/Model.png" width="700">

## Conclusion
MVVM offers lots of advantages of separation of concerns by leveraging data binding. Also, the Models drive as much business logic as possible and avoid the logic in Views.

Personally, it seems complicated the first time. Once you figure out how MVVM works and you might benefit from it, you will stick to this pattern.





