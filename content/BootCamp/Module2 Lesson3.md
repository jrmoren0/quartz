---
title: "Lesson 3"
---
##### Previous Lesson
[Module2 Lesson2](Module2%20Lesson2.md)

# Virtual Methods
A virtual method will allow you to create a method that can be inherited by multiple classes and have its own implementation of that method.(Utilized when you [override](Module2%20Lesson2.md) a method from the parent class) 


# Abstraction
Modeling the relevant attributes and interactions of entities as classes to define an abstract representation of a system. ()
![AbstractionDrawing](BootCamp/image/AbstractionDrawing.md)

###### Examples
car
map
tv remote

# Encapsulation
Hiding the internal state and functionality of an object and only allowing access through a public set of functions


###### Examples
bank account 
laundry machine 
car 
	-Manual vs Automatic




# Abstract Classes and Methods
Use the abstract modifier in a class declaration to indicate that a class is intended only to be a base class of other classes, not instantiated on its own. Members marked as abstract must be implemented by non-abstract classes that derive from the abstract class.
![Abstract Classes](BootCamp/image/Abstract%20Classes.md)

###### Example
 ```C#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

// Abstract class example
public abstract class PlayableObject : MonoBehaviour, IDamageable
{
    public Health health = new Health();
    public Weapon weapon;

    public abstract void Move(Vector2 direction, Vector2 target);

    public abstract void Shoot();

    public abstract void Attack(float interval);

    public abstract void Die();

    public abstract void GetDamage(float damage);
}
```
# Interfaces 
Interfaces can be thought of as a contract on functionality. Any class that implements an interface must have all of its methods and properties. In exchange, the implementing class can be treated like the interface by other classes, using polymorphism. It is important to note, that interfaces are not classes, and cannot have their own instances.


*Creating an Interface*
```C# 
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public interface IDamageable
{
    void GetDamage(float damage);
}
```

*Using an interface*
```C#
using System.Collections.Generic;
using UnityEngine;

// Abstract use with and Interface
public abstract class PlayableObject : MonoBehaviour, IDamageable
{
```

# Choice of Application of Abstraction
Abstract classes are for shared behavior  but interfaces are for similar interactions.


![](BootCamp/image/AbstractVsInterface.png)

# Customize Player Input
###### code
```c#
using UnityEngine;


public class Player : PlayableObject
{
    [SerializeField] private Camera cam;
    [SerializeField] private float speed;

    private Rigidbody2D playerRB;

    private void Start()
    {
        health = new Health(100, 0.5f, 100);
        playerRB = GetComponent<Rigidbody2D>();
    }

    public override void Move(Vector2 direction, Vector2 target)
    {
        playerRB.velocity = direction * speed * Time.deltaTime;

        var playerScreenPos = cam.WorldToScreenPoint(transform.position);
        target.x -= playerScreenPos.x;
        target.y -= playerScreenPos.y;

        float angle = Mathf.Atan2(target.y, target.x) * Mathf.Rad2Deg;
        transform.rotation = Quaternion.Euler(0,0,angle);
    }

    public override void Shoot()
    {
        Debug.Log($"Shooting a bullet");
    }

    public override void Die()
    {
        Debug.Log("Player died!");
    }

    public override void Attack(float interval)
    {
        
    }

    public override void GetDamage(float damage)
    {
        
    }
}

```



```C#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class PlayerInput : MonoBehaviour
{
    private Player player;
    private float horizontal, vertical;
    private Vector2 lookTarget;

    void Start()
    {
        player = GetComponent<Player>();
    }

    void Update()
    {
        horizontal = Input.GetAxis("Horizontal");
        vertical = Input.GetAxis("Vertical");
        lookTarget = Input.mousePosition;

        if(Input.GetMouseButton(0))
        {
            player.Shoot();
        }
    }

    void FixedUpdate()
    {
        player.Move(new Vector2(horizontal, vertical), lookTarget);
    }
}

```
