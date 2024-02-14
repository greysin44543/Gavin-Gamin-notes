The syntax for a array is as follows:

```cs
public Vector3[] SpawnPos

public GameObject[] SpawnList

public bool[] waahterver

```

essentially after putting brackets after the variable type, it becomes a array which stores a array of whatever variable type that is. For example, if you want four different spawn locations for enemies, you can have a Vector3 array so you can randomize the locations. Just make sure you assign the objects in the array via the inspector.


# random Stuff 

For picking a random variable from a array, heres a example below:
```cs
void spawnrandomanimal()
{
    int animalindex = Random.Range(0, animalprefabs.Length);
    Vector3 spawnpos = new Vector3(Random.Range(-spawnrangex, spawnrangex), 0, spawnrangez);

    Instantiate(animalprefabs[animalindex], spawnpos, animalprefabs[animalindex].transform.rotation);

}
```

Random.Range() chooses a random variable from within the array. The variables are listed from 0-infinity, 0 being the first in the list, and it can be as big or as little as you want. animalprefabs is a gameobject list, and the .Length grabs the amount of variables in the list, and turns it into a int for Random.Range to choose a random number from, therefore creating a random spawn list with no predictable order