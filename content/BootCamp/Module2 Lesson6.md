---
title: "Lesson 6"
---
##### Previous Lesson
[Module2 Lesson3](Module2%20Lesson3.md)


# Objects! Shooting and Damaging
# Game Manager/Singleton
Singleton is a creational design pattern that lets you ensure that a class has only one instance, while providing a global access point to this instance.![](image/singleton.png)
```c# 
private static GameManager instance;  
  
public static GameManager GetInstance()  
{  
    return instance;  
}  
  
void SetSingleton()  
{  
    if (instance != null && instance != this)  
    {  
        Destroy(this);  
    }  
  
    instance = this;  
}
```
# Objects! Spawning Enemies
# Coroutines
A coroutine is a function that can suspend its execution (yield) until the given [YieldInstruction](https://docs.unity3d.com/ScriptReference/YieldInstruction.html) finishes.
```c#
float secondsCounter;


void Start()
    {
		secondsCounter = 0;
        StartCoroutine(Timer());
    }
IEnumerator Timer()
    {
        while (true)
        {
			secondsCounter++;
            yield return new WaitForSecondsRealtime(1.0f);
            Debug.Log(Time.time);
        }
```
# Actions and Events
Actions and events all methods to subscribe to events without necessarily being aware of each other.
![ActionsandEvents.excalidraw](Excalidraw/ActionsandEvents.excalidraw.md)

# Exception Handling 
```c#
try
        {
            target = GameObject.FindWithTag("Player").transform;
        }catch(NullReferenceException e)
        {
            Debug.Log("There is no player in the scene, destroying myself" + e);
            Destroy(gameObject);
        }
```
##### Next Lesson
[Module2 Lesson3](Module2%20Lesson7.md)
