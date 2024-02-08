

This is my notes concerning how to manage and type the proper syntax of code that moves things in the game.


3D and 2D versions of unity have different syntax for moving stuff, since I'm mainly focused on producing a 2D game I'm gonna list the syntax for that stuff here:

To move a 2D sprite you have to use Unity's built in input manager, accessed via edit>Project settings>Input manager and you can see all the Terms you gotta call in a string within the function.

Before anything though, make sure you call it in the start function using:
```cs

        rb = GetComponent<Rigidbody2D>(); 
```
rb is the name of the rigidbody2D you assign towards the top.

also make sure you ad the  Player Input component to the player sprite before you do any coding.

you gotta have your player input detected in the update() function, and the actual moving of the player has to occur in the FixedUpdate() function.

In the update function, the following code is entered
```cs

        movementInput = new Vector2(Input.GetAxis("Horizontal"), Input.GetAxis("Vertical"));

```
movementInput is a Vector2 private float variable that store a X and a Y, with the Input.GetAxis("") thing returing a 1 or -1, depending on the WASD input given by the player.


input.method is a class that handles input in various ways

if your trying to detect a certain key being pressed you gotta do the GetKeyDown and GetButtonDown, but even those can be handled in the inputmanger list as viewed above.








