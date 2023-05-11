---
title: "Lesson "
---
##### Previous Lesson
[Module2 Lesson3](Module2%20Lesson3.md)


# JSON (JavaScript Object Notation)
JSON (JavaScript Object Notation) is a lightweight data-interchange format. It is easy for humans to read and write. It is easy for machines to parse and generate.

JSON is built on two structures:

-   A collection of name/value pairs. (C#)
-   An ordered list of values.(C#)

```JSON
 {  "name": "Bob",
		 age: 22,	
		 "favorite books": []
		 "canfly" : false 
		 }


```
```c# 
[System.Serializable]
public class SampleData
{
    public string name;
    public float score;
}
```

```c#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class JSONExample : MonoBehaviour
{
    
    void Start()
    {
        //Serielizing data to JSON

        SampleData sample = new SampleData();
        sample.name = "Mike";
        sample.score = 10.0f;

        string data = JsonUtility.ToJson(sample);
        Debug.Log(data);

        // Deserializing JSON to data
        string JSON = "{\n\t\"name\": \"Alice\",\n\t\"score\": 90.34\n}";
        SampleData sample2 = JsonUtility.FromJson<SampleData>(JSON);

        Debug.Log($"Deserialized {sample2.name} - Score : {sample2.score}");
    }
}
```

Example of JSON in the wild:
https://openweathermap.org/current
# Serialization and Deserialization of Complex objects
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

        sample.name = "Indi";

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
```c#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using TMPro;

public class PlayerPrefExample : MonoBehaviour
{
    [SerializeField] private TMP_InputField input;
    [SerializeField] private TMP_Text txtDisplay;

    // Try this with Int and Float as well.

    public void SaveData()
    {
        PlayerPrefs.SetString("SAVE_DATA", input.text);
    }

    public void LoadData()
    {
        if(PlayerPrefs.HasKey("SAVE_DATA"))
        {
            txtDisplay.SetText(PlayerPrefs.GetString("SAVE_DATA"));
        }else
        {
            Debug.Log("No data to load");
        }
    }

    public void ClearData()
    {
        PlayerPrefs.DeleteKey("SAVE_DATA");

        // Can delete all data
        //PlayerPrefs.DeleteAll();
    }
}
```
# Scriptable Objects in Unity
```c#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

[CreateAssetMenu(fileName = "DataSample", menuName ="CircuitStream/Create Sample ScriptableObject", order =1)]
public class ScriptableObjectSample : ScriptableObject
{
    public string objectName;
    public string score;
    public Vector2 startPosition;
}
```

```c#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class ScriptableObjectTest : MonoBehaviour
{

    public ScriptableObjectSample sample;
    
    void Start()
    {
        if (!sample)
            return;

        Debug.Log($"Loaded the object, Name :{sample.objectName}, Score:{sample.score}, Position:{sample.startPosition}");
    }
}

```
# Objects! Spawning Pickups
```c#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class PickupSpawner : MonoBehaviour
{
    [SerializeField]private PickupSpawn[] pickups;

    [Range(0,1)]
    [SerializeField]private float pickupProbability;

    List<Pickup> pickupPool = new List<Pickup>();
    Pickup chosenPickup;

    private void Start()
    {
        // Populate a pool of pickups
        foreach (PickupSpawn spawn in pickups)
        {
            for (int i = 0; i < spawn.spawnWeight; i++)
            {
                pickupPool.Add(spawn.pickup);
            }
        }
    }

    public void SpawnPickup(Vector2 position)
    {
        if (pickupPool.Count <= 0)
            return;

        if (Random.Range(0.0f, 1.0f) < pickupProbability)
        {
            chosenPickup = pickupPool[Random.Range(0, pickupPool.Count)];
            Instantiate(chosenPickup, position, Quaternion.identity);
        }
    }
}

[System.Serializable]
public struct PickupSpawn
{
    public Pickup pickup;
    public int spawnWeight;
}
```

```c#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class HealthPickup : Pickup, IDamageable
{
    [SerializeField] private float healthMin;
    [SerializeField] private float healthMax;


    public override void OnPicked()
    {
        base.OnPicked();
        // Increase Health here
        float health = Random.Range(healthMin, healthMax);

        var player = GameManager.GetInstance().GetPlayer();

        player.health.AddHealth(health);

        Debug.Log($"Added {health} health to player");

    }

    public void GetDamage(float damage)
    {
        // Add health to player (this pickup must be collided with the player or shot at it to be picked up
        OnPicked();
    }
}
```

```c#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class GunPickup : Pickup
{
    public override void OnPicked()
    {
        base.OnPicked();

        // Add a gun to player here
    }
}
```
# Saving and Loading the High Score
```c#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.Events;

public class ScoreManager : MonoBehaviour
{
    private int score;
    private int highScore;

    // To demonstrate Unity Events
    public UnityEvent OnScoreUpdated;
    public UnityEvent OnHighScoreUpdated;

    private void Start()
    {
        highScore = PlayerPrefs.GetInt("HighScore");
    }

    public int GetScore()
    {
        return score;
    }
    public int GetHighScore()
    {
        return highScore;
    }

    public void IncrementScore()
    {
        score++;
        OnScoreUpdated?.Invoke();

        if(score > highScore)
        {
            highScore = score;
            OnHighScoreUpdated?.Invoke();
        }
    }

    public void SetHighScore()
    {
        PlayerPrefs.SetInt("HighScore", highScore);
    }
}

```
---
```c#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using TMPro;

public class UIManager : MonoBehaviour
{
    [SerializeField] private TMP_Text txtHealth;
    [SerializeField] private TMP_Text txtScore;
    [SerializeField] private TMP_Text txtHighScore;
    [SerializeField] Player player;

    private ScoreManager scoreManager;

    private void Start()
    {
        scoreManager = GameManager.GetInstance().scoreManager;

        // Subscribing to actions
        player.health.OnHealthUpdate += UpdateHealth;
    }

    private void OnDisable()
    {
        // Unsubscribe from actions
        player.health.OnHealthUpdate -= UpdateHealth;
    }

    public void UpdateHealth(float currentHealth)
    {
        txtHealth.SetText(currentHealth.ToString());
    }

    public void UpdateScore()
    {
        //Only to test UnityEvent
        txtScore.SetText(scoreManager.GetScore().ToString());
    }

    public void UpdateHighScore()
    {
        txtHighScore.SetText(scoreManager.GetHighScore().ToString());
    }
}
```
# Setup the UI


##### Next Lesson
[Module2 Lesson3](Module2%20Lesson7.md)
