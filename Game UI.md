
Step 1. Create a canvas

In the canvas object, under the canvas component, your probably gonna use  "screen space" as your render mode. 

**CANVAS SCALER**

just scales the UI with the resolution with the computer being used. make sure it matches your resolution or else it will look funky. In order to make it so the UI of the cade custom fits to any and all resolutions, you gotta  use the square thing in the inspector when your UI element is selected. Using that will align your UI to that part of the screen. HOLD DOWN BOTH SHIFT + ALT AND SELECT YOUR SQUARE TO ALIGN IT.

You may notice that the UI box is like 100x bigger than the game, thats normal you just gotta deal with it.


# Making text reappear and disappear

example on how to use Text Mesh Pro and the .enable method:

```cs
using System.Collections;
using System.Collections.Generic;
using TMPro;
using UnityEngine;

public class The_text : MonoBehaviour
{
    public TMP_Text Text;


    void Start()
    {
        Text.enabled = false;
    }

    // Update is called once per frame
    void Update()
    {
        
    }
```



