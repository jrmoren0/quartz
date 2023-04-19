---
title: "Lesson 2"
---
##### Previous Lesson
[Module2 Lesson1](Module2%20Lesson1.md)

# Static Modifier

- *Statitc Field:*  A Static field will be  bound to the class not a particular instance of the class (it is shared between all instances of the class.)
```c#
public static int numberOfEnemies;
```

- *Static Method* : A static method is bound to the class itself not any instance of the class.
```c#
public static void AddEnemy()
    {
        count++;
    }
public static void SubtractEnemy()
    {
        numberOfEnemies--;
    }
```

- *Static class* : A [static](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/static) class is basically the same as a non-static class, but there is one difference: a static class cannot be instantiated. In other words, you cannot use the [new](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/operators/new-operator) operator to create a variable of the class type.

	-  Contains only static members.
	-   Cannot be instantiated.
	-   Is sealed.
	-   Cannot contain [Instance Constructors](https://learn.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/instance-constructors).
	
```c#
public static class Math
```
![Static Modifiers](BootCamp/image/Static_Modifiers.png)
# Inheritance
[Inheritance](https://learn.microsoft.com/en-us/dotnet/csharp/fundamentals/object-oriented/inheritance) allows us to create a new class from an existing class. The new class will "inherit" the fields and methods of the original class.  We can then add functionality and specificity to the new class.

- The original class is referred to as the base class (or parent class)
- And the new class is referred to as the derived class (or child class)

Example of Inheritance in Objects!:
```c#
using UnityEngine;  
  
// inheritance 
public class Player : PlayableObject
```
# Override Modifier 

The [Override Modifier](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/override) allows us to change the functionality of an inherited method.
In  order to overide a method the method must be declared as virtual or already be overridden.

The [virtual](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/virtual) keyword is used to modify a method, property, indexer, or event declaration and allow for it to be overridden in a derived class. For example, this method can be overridden by any class that inherits it.


# Relationships in OOP
The main reason for object-oriented programming is to reuse and organize code.

- #### Inheritance (is a)
	Inheritance is used to model an "is-a" relationship between two classes It allows one class (the derived class ) to be based upon another (the base class) and inherit all of its functionality automatically.
	**e.g A cat "is a(n)" Animal**(Enemies and enemy variants) 
		
 - #### Association (uses a)
	Association relationship is referred to as "uses a" relationship where a class uses another class to perform some operation. In association, both classes can exist independently where nobody is the owner of another. Some people refer to association as collaboration or delegation.
	*e.g A patient "uses" a DR./ DR "uses" a patient.* (Player and Enemies)
	
		
- #### Aggregation (has a)
	Aggregation is a  "has a" relationship where a class can contain other classes as properties  but those classes can exist independently.
	*e.g A wallet "has" money. (but the both the wallet and the money can exist without each other)*(Player and Weapon)
	
 - #### Composition (part of) (has a)
	Composition is referred to as "part of" relationship. Composition relationship is formed when a class has a reference to another class as an instance property. 
	*e.g. a heart is "part of" a human*
	*e.g. a human "has a" heart* (Player and Health)

![Static Modifiers](BootCamp/image/OOPRelationships.png)


##### Next Lesson
[Module2 Lesson3](Module2%20Lesson3.md)

