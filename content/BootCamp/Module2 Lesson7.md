---
title: "Lesson 7"
---
##### Previous Lesson
[Module2 Lesson3](Module2%20Lesson3.md)


# JSON (JavaScript Object Notation)
[JSON](https://www.json.org/json-en.html) (JavaScript Object Notation) is a lightweight data-interchange format. It is easy for humans to read and write. It is easy for machines to parse and generate.

JSON is built on two structures:

-   A collection of name/value pairs. (C#)
-   An ordered list of values.(C#)

```JSON
 {  "name": "Marge",
	 "score": 22.1
 	 }
```

##### csharp
```c# 

public class SampleData
{
    public string name = "Bob";
    public float score = 22.1;
}
```


Example of JSON in the wild:
https://openweathermap.org/current
# Serialization and Deserialization of Complex 
![SerializationandDeserialization.excalidraw](Excalidraw/SerializationandDeserialization.excalidraw.md)
objects

```c#
[System.Serializable]
public class SampleDataComplex
{
    public string name;
    public Address address;
    public book[] books;
}

[System.Serializable]
public class Address
{
    public int unit;
    public string road;
    public string city;
}

[System.Serializable]
public class book
{
    public string name;
    public bool isDigital;
    public string author;
}
```

```c#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class JSONExampleComplex : MonoBehaviour
{
    
    void Start()
    {
        //Serializing a data object
        SampleDataComplex sample = new SampleDataComplex();

        sample.name = "Joe";

        sample.address = new Address();
        sample.address.unit = 1;
        sample.address.road = "2nd avenue";
        sample.address.city = "New York";

        sample.books = new book[2]; //creating the array
        sample.books[0] = new book(); //creating an object to add to the array
        sample.books[0].name = "Intro to Game Dev";
        sample.books[0].isDigital = true;
        sample.books[0].author = "John Doe";

        sample.books[1] = new book();
        sample.books[1].name = "Hatty Porrer";
        sample.books[1].isDigital = false;
        sample.books[1].author = "Just Kidding Rolling";


        string data = JsonUtility.ToJson(sample);
        Debug.Log(data);

        //Deserializing the same, use an example as before

    }
}
```


# PlayerPrefs in Unity

# Scriptable Objects in Unity
```c#
```
# Saving and Loading the High Score
```c#

```
# Setup the UI


##### Next Lesson
[Module2 Lesson3](Module2%20Lesson7.md)
