So a renderer is a component you will probably have to call pretty often, to get things like the length of the object, or to flip a object, or to even change the color of the freaking thing.

In order to reference the sprite render in your scripts, you got first put this code at the top Start()
```cs

SpriteRenderer renderervariablename
```
then put this in the Start() function:
```cs
RendererVariableName = GetComponent(<SpriteRenderer>();  
```

**If you wanna flip the Sprites horizontal movement, your gonna have to use and reference the Render for the sprite, then use:**

```cs
RendererVariableName.flipx = true;
```
