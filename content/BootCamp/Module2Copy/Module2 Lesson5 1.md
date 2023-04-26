---
title: "Lesson 5"
---
##### Previous Lesson
[Module2 Lesson4](Module2%20Lesson4.md)
# Data Structures And Collections
Collection are used to store and organize data in different ways


```c#
int year = 1998;
int year = 1997;
int year = 1950'
```

# Array
Arrays are used to store similar types of multiple data items using a single name
![Array.excalidraw](Excalidraw/Array.excalidraw.md)
#### Pros:
- strongly typed
- performant 
- Can access elements by index

#### Cons:
- strongly typed
- fixed size
		

```c#
int[] numbers;
```


```c#
int[] numbers = new int[5];  //{0,0,0,0,0} actually hull 
```


```c#
int[] numbers = new int[] { 1, 2, 3, 4, 5 };
```



# LinkedList
LinkedList consists of nodes where each node contains a data field and a reference(link) to the next node in the list.
![](BootCamp/image/LinkList.excalidraw%201%201.png)
![](BootCamp/image/Linked%20List.webp)
![](https://miro.medium.com/v2/resize:fit:1400/1*UWyY_qX0193MwNhpD9foXg.png)

![](BootCamp/https://miro.medium.com/v2/resize:fit:1400/1*QEPR7Z-EMXHwq-D8TjDyLg.png)
#### Pros:
- easily change size
- performant 
#### Cons:
- more memory used because   needs to be store in addition to data
- no direct access to data( must traverse list)
- more complex to deal with
- doesn't make sense to use with small datasets

# List

```C#
List<Part> parts = new List<Part>();

```
![](BootCamp/image/Lists.excalidraw%202.png)
#### Pros:
- easily change size
- performant 
- Can access elements by index

#### Cons:
- Lists occupy more memory than arrays.

# Queue
Represents a first-in, first-out collection of objects(FIFO)
```c#
Queue<string> numbers = new Queue<string>();
```
![](BootCamp/image/Queue.excalidraw.png)

```c#
// Add an element to the back of the queue
numbers.Enqueue("One");
//Remove the first element from a queue
numbers.Dequeue();

//Return the value of the first element without removing it
numbers.Peek();
```
#### Pros:
- Enqueuing and  Dequeuing are always fast
- shorter Code

#### Cons:
- Less Flexible List


# Stack  
Represents a variable size last-in-first-out (LIFO) collection of instances of the same specified type.

```c#
Stack myStack = new Stack();
```

![](BootCamp/image/Stack.excalidraw.png)
```c#
// Add an element to the top tof the stack
myStack.Push("One");
//Remove the first element from a stack
myStack.Pop();

//Return the value of the first element without removing it
myStack.Peek();
```
#### Pros:
- Popping and  Pushing are always fast
- shorter Code 
- can save headache and performance over using a list

#### Cons:
- Less Flexible List

# Dictionary
Represents a collection of keys and values.
```c#
Dictionary<string, string> openWith = new Dictionary<string, string>();

```




