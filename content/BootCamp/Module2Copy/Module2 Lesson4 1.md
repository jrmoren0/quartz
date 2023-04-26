---
title: "Lesson 4"
---
##### Previous Lesson
[Module2 Lesson3](Module2%20Lesson3.md)


# Polymorphism
[Polymorphism](https://learn.microsoft.com/en-us/dotnet/csharp/fundamentals/object-oriented/polymorphism) is  a Greek word that means "many-shaped, and it has two distinct aspects: 
- At run time, objects of a derived class may be treated as objects of a base class in places such as method parameters and collections or arrays
- -   Base classes may define and implement [virtual](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/virtual)  methods, and derived classes can [override](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/override) them, which means they provide their own definition and implementation. At run-time, when client code calls the method, the CLR looks up the run-time type of the object, and invokes that override of the virtual method. In your source code you can call a method on a base class, and cause a derived class's version of the method to be executed.
![Polymorphism](Excalidraw/Polymorphism.md)
![](BootCamp/image/Polymorphism.png)
e.g. [Tranform.Tranlate()](https://docs.unity3d.com/ScriptReference/Transform.Translate.html)


# Method Overloads
Method overloading means multiple methods can have the same name with different parameters.
```c#
public virtual void Move(Vector2 direction){}
public virtual void Move(float speed) { }
```

# Documentation Comments
In C#, there are 3 types of comments:

1.  Single Line Comments ( `//` )
2.  Multi Line Comments (`/* */`)
3.  XML Comments ( `///` )
```C#
/// <summary>
/// Validates the date.
/// </summary>
/// <param name="date">The date.
/// <returns><c>true</c> if the date is valid; otherwise <c>false</c>.</returns>
public bool validateDate(string date)
{
    // Do something
}
```

# Code Planning and Documentation

[https://lucid.app/lucidchart/e61c96a3-e33b-4dab-9db0-e0b25483e6e1/edit?shared=true&page=HWEp-vi-RSFO#](https://lucid.app/lucidchart/e61c96a3-e33b-4dab-9db0-e0b25483e6e1/edit?shared=true&page=HWEp-vi-RSFO#)

# Activity and Sequence Diagrams

### Activity Diagrams 
*Activity Diagram Bowling Score*
![](BootCamp/image/Scoring%20flow.drawio%201.png)
 _Activity Diagram Bowling Score_
 ![Activity Diagram Bowling Throw](BootCamp/image/Ball%20throwing%20flow.drawio.png)





### Sequence Diagrams 

![](BootCamp/image/phpAm8i9t.png)
# Objects! Planning
# Objects! Enemy Attack and Bullets

##### Next Lesson
[Module2 Lesson5](Module2%20Lesson5.md)
