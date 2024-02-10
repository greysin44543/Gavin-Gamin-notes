
# What is a constant?

constants are immutable variables which you can use to rename other things blah blah blah Ill finish this later

# referencing a script from a different gameobject

If you’re referencing a script from a different GameObject, you much reference the GameObject first, then reference the script.
```cs
	// reference the gameobject with the script
    public GameObject player;
    //reference the script
    refrencedscript refscript;
	    q
    
    void Awake()
    {
        refrencedscript = refscript.GetComponent<refrencedscript>();
    }

    void Update()
    {
        if (refrencedscript.whateverthingyoutrynnacall == whatever you wanna do)
 ```
# what is a static variable/function?

essentially, putting the keyword "Static"  in front of a variable or function means it can be accessed from any script across the game. Makes it seem like you dont have to do the whole "reference a script from a different gameobject" to use a function/variable from another gameobject, HOWEVER using static variables/functions take up a ton of memory, so using them willy nilly is not advised.


# [range] stuff

essentially if you put  

[range(0.5f,1f)]
the serialized float below it becomes a slider in the inspector, which has a maximum and a minimum. in this example, you could set the sliders lowest value to 0.5, and the highest to 1. Really good for testing fire rates and stuff.