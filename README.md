Introduction:
As someone stepping into the tech industry, everything can feel overwhelming and bleak; everything is a mess, and nothing makes sense. This article will discuss common Java mistakes such as over-engineering and designing and how proper DRY principles and organization can make implementation much more accessible and healthier for a code base. 

Table of Contents/Over-View: 
Introduction: 
[main]
Over-engineering: Wet and dry an example using methods, classes, and functions, 
[Sub-main]:
(Describe the function and methods. 
Summary of how function and methods work (and its various subcategories work) 
[Conclusion]


Over Engineering, on the surface, it seems like a simple thing to avoid, "Oh, I will just do the bare minimum required for the project!" However, making the code base more extensive when the project begins is much easier than needed. 
Before fully exploring over-engineering, we must research methods and their "functionality" in Java. 

Methods:
Methods are "A | block of code which only runs when called." [1] (Refsnes Data, n.d.) Functions, alongside their sister series classes, make up the backbone of modern applications. 
The syntax is as follows:
Modifier returnType method name (parameter list) {}
Example: Public static double additionMethod(double firstNum, double secondNum) {
]
Modifier: Modifiers, also known as access modifiers, set an object's accessibility, class, or method.
The compatible modifiers are as follows: Public, Private, Protected.
We will discuss these modifiers in more detail later in this article. 
ReturnType: ReturnType is the value that will be returned from the method using the return keyword; all data types, including void, can be a method's return type. A void in functions means they will not have a return value. Void is commonly used in helper methods such as user-defined (get() set() and print() methods, among many others. 
Static represents that a method belongs to the main class and is not an object of that class; in principle, this means that static methods, especially in separate classes from the main, do not need an associated class object to call them, as seen in the example below. 
And finally, parameter types. Parameters act as variables initialized outside the method; let us call this method with some numbers.
```java
additionMethod(2, 8); 
This means that firstNum is equal to 2.0, and secondNum is equal to 8.0 due to passive type conversion inside our method if we have the following code inside:

  return (firstNum + secondNum); 
```
Then, our method would return 10.0, which we could print to the screen using the following:
Public static double additionMethod(double firstNum, double secondNum ) {
  return (firstNum + secondNum); 
}
// This would contain code declaring the main method 
  System.out.println(additionMethod(2, 8);
// Output printed to the user is 10. 

system. out.println(additionMethod(2, 8) returns 10.0 to the user's screen. As an example of println, it is an instance of the print-stream type, a public and static method of the System class. 
Now that we fully understand the basics of Methods, let us look at an example of a WET or (write everything twice) method with some obvious and less obvious examples:

public static double additionmultiplicationMethod(double additionOne double multiOne, double multiTwo;) {
  double firstMulti;
  double secondMulti; 
  double firstAddition;
  double multiplicationResult; 
  firstMulti = additionOne; 
  secondMulti = additionTwo; 
  additionOne = additionOne; 
  multiplicationResult = additionOne + firstMulti * secondMulti 
  return multiplicationResult; 
}
// After main method declaration:
  additionmultiplicationMethod(5, 2, 3);
  // result = 20. 
Now, let us try to fix the apparent problems. Is it still WET?

public static double additionmultiplicationMethod(double additionOne double multiOne, double multiTwo;) {
  double firstMulti = multiOne;
  double secondMulti = multiTwo;
  double firstAddition = additionResult;
  return additionOne + (firstMulti * secondMulti);
}
  // After multiplication and other results.
  // result = 20
  
It is still WET since multiple factors repeat or are unnecessary in the code base. For example, we do not need the finalVariable since it stores the addition result calculated at that line. We do not need to separate the arithmetic into multiple calculations.
Now, finally, let us make this method “DRY or (Do not Repeat Yourself)”: [2]

public static double additionmultiplicationMethod(double additionOne double multiOne, double multiTwo;) {
  return (additionOne + (multiOne * multiTwo)); 
}

As you can see, the method is much more concise and accessible to read when added to a much larger code base with multiple classes and functions. It is also quicker and more concise on the device's hardware since it does not need to allocate memory to the variables and return the following arithmetic. 

However, as a reader, especially a novice, a question may be, "But why is the dry implementation of the code a problem? It works, so what's the problem?" To fully explain the question, we must dissect and examine each example in further detail, precisely the first. 
The first has many problems, including code redundancy, code legibility, and overworking the GPU and CPU. While this may be obvious, more often than not, there are reasons why a beginner might code this way; this and a further discussion on what code written as this does to both a developer's phycology and the machine internally as our further discussion points. 
The main reason that beginners write code this way is due to uncertainty and lack of experience with the concepts provided; the author admits that when she was starting, she coded mainly the first example's dry code and then the second example as she learned Until she finally understood and prioritized Wet Code. 

It mainly comes down to understanding how methods and, by extension, parameters work. Parameters are values that are initialized through the data provided by the calling method. However, as a beginner, it is prevalent not to understand how that works and instead rely on variables instead of parameters.  
Parameters = whose value is defined by the calling method or default values. 
This redundancy can make code much less readable, and with much larger methods or code such as this one, Having WET code would make it nearly unreadable. 
Another aspect of Wet Code is how it affects debugging; as a beginner, debugging is either something that's easy to fix due to simple applications or is a labyrinth of a confusing mess. Either way, having redundant code makes the codebase much more extensive, which means that it is harder to scan and also makes it harder to know what exactly is causing the bug or error. Is it the variables we initiated? How did we call the method or something earlier in the program? This undoubtedly results in more mental work for the developer, and debugging using the step/in/out and breakpoints make debugging more time-consuming. 
Wet code also affects the program internally; the exact details are far beyond the scope of this article, but we will attempt to summarize them.

Everything in high-level programming is just a simple set of instructions that the compiler converts to machine-level code, essentially representations of the instructions through bits 1 and 0. Every variable and value in code is stored internally inside the computer's memory, located at an index inside the memory.  
Variables are references to the index where the value is stored. 
However, if multiple values are stored inside at once, the device's memory and CPU have to work harder to keep track of them, which makes apps slower and, if done incorrectly, can lead to potential crashes.
That does not even consider recursion, which, if done incorrectly, can begin a stack overflow, which can leak memory and cause intense problems for the program.
In short, while it may seem better to be a bit redundant to solve a problem, its effects ripple throughout the program. 
The second example's problem is mainly code redundancy. While less intense than the first example's and still readable by most reviewers, we must discuss problems, such as what it does mentally to the developer. 
While code redundancy may feel like an easier and safer way to solve a problem, the far-reaching effects of what it does mentally to a developer must be addressed. When writing code this way, it is easy to make it a habit that goes all throughout the program; not only will this habit affect the developer mentally and in their work. However, also professionally and their learning of programming, as most teams want developers who write WET code outside their teams.

Dry or redundant code usually results from a fear that the code base will not work. This fear also stunts a developer's growth, as someone working in tech must learn and adapt as technology constantly evolves. Reinforcing ideology will hurt the developer's learning in the long term. 
In Conclusion, organized Dry code is an important principle that affects the code base in many ways, from faster-optimized code to clear classes and methods and more manageable code identification. Implementation and problem-solving for leading developers, developers reviewing, and future clients! We hope this article has made it easier to understand Java and how making Dry code is manageable. It will help you be a more professional developer. 
-Written by Kaia Kitching while using Grammarly Premium


References and Learning throughout the entire project:

[1]
Refsnes Data. (n.d.). Java Methods. W3C Schools. Retrieved Febuary 10, 2024, from [WC3 Schools: Java Methods:](https://www.w3schools.com/java/java_methods.asp)

[2]
Don't repeat yourself. (2024, January 9). In Wikipedia. 
https://en.wikipedia.org/wiki/Don%27t_repeat_yourself


[3] https://www.w3schools.com/java/java_classes.asp
[4] https://www.w3schools.com/java/java_oop.asp
[5] https://www.w3schools.com/java/java_modifiers.asp
[6] https://www.w3schools.com/java/java_constructors.asp
[7] https://www.baeldung.com/java-logging-intro
[8] https://code.visualstudio.com/docs/java/java-debugging
[9] https://code.visualstudio.com/docs/editor/debugging#:~:text=Variables%20can%20be%20inspected%20in,in%20the%20CALL%20STACK%20section.

