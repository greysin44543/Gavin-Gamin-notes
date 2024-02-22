
animation sucks but you gotta thug it out

Theres two screens, the animator window, and the animation window.

**NOTICE: while writing this I actually learned of a better and easier way to animate 2D sprite, so all of this only really applies to 3d sprites, but Im gonna leave in in anyways. Also below  all this crap im gonna have my better 2D animation method linked here: **
# Animation window


The animation window is where you construct the individual animation, via dragging and dropping individual key frames onto a timeline, where you can create your separate animations.

the way you should organize your animations is by putting each individual character/objects animations into a separate folder where you can have all of them together.

when naming a animation, make sure you use the format  (charactert/object)action for better organization. 

remember you can shift click in order to select multiple key frames, so use that to your advantage when dragging in multiple keyframes into the animation window.


# animator window

The animator window has a bunch of blocks, parameters, and layers. Whenever your create a animation in the animation window, it pops up as a block in the animator window, where you can create transitions from one animation to the next.

**!Organize your blocks so you can easily understand and view the transitions between animations!**

In order for a transition to occur, you have to a have a parameter  that gets triggered for the transition into that animation to happen. By clicking on the arrow lines in between the blocks, we can set parameters for those transitions to occur. Sometimes you gotta go into your custom component scripts in order to trigger that parameter.

**To reference a parameter in your script, make sure you use the following code:**
```cs

Animator Variablename;
```

then in start assign your variable name to your animator by using the 
```cs

VariableName = GetComponentAnimatorr>();
```


### parameters

There are four different types of Parameters,

Float
Int 
Bool
Trigger

Use the specific paramter for your sitution(fill in later)

To set a parameter, click on a transition and down in the conditions bar, hit plus, select your parameter, and the condition for that parameter.
For Bool its either gonna be true of false. The Syntax to Check if  a bool parameter is triggered or not is as follows:
```cs
animator.SetBool("parameter_name",true);
```
So for player movement, you can use the  Input.GetAxis thing (See[[Physics and Transform]]) and detect if that number is a 1 or a -1, and return true or false based off that. Create a function and have that run in Update() to handle all those animations.



## The Better Method for animating sprites


So the previous stuff utuilizes transitions between animation blocks in the animator, HOWEVER that can get messy and tedious very quickly, so instead we can simply trigger the animations, in the scripts code, which simplifies a lot of stuff and once you get good at it (apparently) makes stuff roll a lot smoother.


first off, your gonna wanna store your animations in constants (see [[basics]]), so That you can easily type them out and have the AI finish your code thing suggest them. This helps prevent typoes and such. Do it as follows:
```cs
const string NEW_NAME = "Actual_Animation_Name";
```
So in order to reference animations, you have to of course call it, which is still the same as above.
then you can use the the following code to actually make the animation play. You want to have these in if statements, like if a player isnt moving, play the idle animation, ect ect.

Then you have to actually create the Function that changes the animations First step is to create a string called currentState by using:

private string currentState;

Then make the function. Call it ChangeAnimationState and write it like its listed below:
```cs

void ChangeAnimationState(string newState)
{
	//stop the same animation from interupting itself`
	if (currentState == newState) return;`


	//plays the animation`
	animator.Play(newState);`
	//reassign the current state
	currentState = newState;
}
```



```cs
animator.ChangeAnimationState(NEW_NAME);
```

there is a catch you gotta very carefully code around. Sometimes you gotta have if statements in order to prevent animations from overlapping. Heres an example of a carefully nested animation if statement thing that makes sure nothing else is playing, so that its own animation plays without getting overlapped or overlapping itself.



### If you wanna change the layer of the players weapon so when they turn around it goes behind the player


The following code is what im tlaking about. First make sure you refernece the player object so you can can the animation specifics, see [[basics]] on how to reference variables or functions from other scripts. then create a SpriteRenderer variable to store the
GetComponent\<SpriteRenderer>(); thing. then just do as seen below in the update() in order to reference it.


```cs
public GameObject player;
player_controller controller;
private SpriteRenderer sprite;
// Start is called before the first frame update
void Awake()
{
	controller = player.GetComponent<player_controller>();
	sprite = GetComponent<SpriteRenderer>();
}

// Update is called once per frame
void Update()
{
	if (controller.playerstate == "player_walkback")
	{
		sprite.sortingOrder = -1;
	}
	else
	{
		sprite.sortingOrder = 1;
	}
}
```
