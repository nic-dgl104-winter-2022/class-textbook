# Typical Debugging Tools

## Introduction

Bugs can be one of the most frustrating things in code and they would only be worse if it wasn’t for debugging tools. A debugging tool helps you pinpoint and fix errors in code. The following documentation is going to be based on the IDE, “Visual Studio Code”, but most of the concepts and features are applicable to other programs.

One of the best things about Visual Studio Code is its great debugging support. VS Code has built-in debugging support for JavaScript, TypeScript, or any other language that gets transpiled to JavaScript with Node.js. For debugging other languages, you can look for “Debuggers extensions” in the VS Code Marketplace or select “Install Additional Debuggers” in the “Run” dropdown menu. To launch your app with the debugger attached, select Run and debug start view or press F5.

These next features talked about are some of the most important features in the debugging process. A “breakpoint” is a feature in VSCode that allows breaking the execution of code at a specific point to help narrow down where the bug occurred. Some more features of a breakpoint are “pause/resume, step over, step into, step out, restart, and stop”.

Pause/Resume allows you to either continue the execution of the code when it is in a paused state or pause the execution when a function is currently being executed. Step over lets you skip functions altogether (aka step over the code). You can do this by pressing F11 or pressing the “Step over” button and it can be used for skipping through code that you aren’t interested in. Step into is similar to step over, but it lets you only execute the next function before pausing on the first line inside, so you can more easily keep track of what is happening in your code. The keyboard shortcut to Step into is F10. The Step out button executes all the code in the current function before pausing at the next. You can Step out by pressing the “Step out” button as shown on the diagram or using Shift+F11.

A little more advanced feature in VSCode’s built-in debugger you can create a conditional breakpoint. A conditional breakpoint allows you to pause the execution of your code after certain conditions have been met which gives you much more control to stop exactly where you might want to stop.
