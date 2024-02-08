So to start off, you gotta create three variables, a public gameobject player, so the enemy script knows what its trying to follow,  a float speed so you can change the enemies speed from the inspector,  and a private float distance, which, in update() we set equal to Vector2.Distance(transform.position, player.transform.position), which returns the distance between two objects, in this cast transform.position(the enemys position) and player.transform.position (the players position).

next we gotta move the enemy towards the player, to do that we use the Vector2.MoveTowards() function, which, you guessed it, moves stuff towards something else. The first parameter is the the current gameobject, which you can refer to by using this.transform.position. The second is the target, which is gonna be player.transform.position, and the final is the speed, which is our speed float we make public before.

**Now we have a object that moves towards the player!**


# Advanced enemy ai stuff (like pathfinding)

First import this ai pathfinding package into the project:
![[astarpathfindingproject_master_free_4_2_17_c030646a.unitypackage]]
thats the name of it your gonna have to find it yourself.

Now we have access to a new  component, which you add to a empty gameobject to layout the pathfinding mesh. in the pathfinding component, click on graphs , and check the 2D box. Below that you can adjust and expand the amount and size of the nodes. Its ideal to have a lot of little nodes (but not too many) so that the enemies have a lot of room to move around.
next check the "use 2D physics" box and make sure the collider type is set to circle.

NEXT you wanna create a new layer called "enviroment", and set the collision object tiles to that layer, this way the pathfinder knows which tiles have colliders, so the enemies can go around them. Make sure anything else you want the enemies to go around are in this layer as well. Lastly, set the "obstacle layer mask" in your pathfinder component to the new enviroment layer, and hit scan at the very bottom of the component. This will highlight all the areas where enemies can go in blue, and where they cant in red. keep in mind you can adjuct the diameter of the nodes as well.

next, go to your enemy you want to chase down the player, and give it the "ai path" component. in that component, you want to set the orientation to "YaxisForward(for2Dgames)" . Then adjust the radius of your ai to match its size, and unless you want the enemy to rotate towrads you character, uncheck "enable rotation" under movement.

Now in order for there to be a target for your enemy, you gotta add another component to the enemy called "AI destination center", and drag the player character into the Target field.

keep in mind, if you want you enemy to slowdown as it gets closer to the player, you can tweak the slowdown distance and the end reached distance(the distance where the enemy will stop from the player) in order to achieve that goal.