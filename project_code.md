




# want to make the players guns go point at the camera?

this code involves a ton of math that I really dont understand, so Ill past the code below and hoepfully you learn it at some point.

```cs
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
public class shooting : MonoBehaviour
{

    private Camera maincam;
    private Vector3 mousepos;
    
    void Start()
    {
        maincam = GameObject.FindGameObjectWithTag("MainCamera").GetComponent<Camera>();
    }
```

and then create a function like below:

```cs
private void HandleAiming()
{
    mousepos = maincam.ScreenToWorldPoint(Input.mousePosition);

    Vector3 rotation = (mousepos - transform.position).normalized;



    float rotZ = Mathf.Atan2(rotation.y, rotation.x) * Mathf.Rad2Deg;


    transform.rotation = Quaternion.Euler(0, 0, rotZ);
}
```
# wanna make the player shoot using the code above?

well first you gotta make the bullet, give it a rigidbody 2d and a 2d collider, then put the following code in it; 

```cs
[SerializeField] private float speed = 200f;

[Range(1, 10)]
[SerializeField] private float lifeTime = 3f;



Rigidbody2D rb;


private void Start()
{
    rb = GetComponent<Rigidbody2D>();
    Destroy(gameObject, lifeTime);


   

}

private void FixedUpdate()
{
    rb.velocity = transform.right * speed  * Time.Deltatime; 
}

//(yeah idk why but the `code` stuff doesnt work for certain pages, really any formatting at all)
```

first assign the rigidbody variable, make sure its a rigidbody2D and not just a rigidbody. fun fact the second parameter in the destroy function actually is the time before it gets destroyed, so you can set a timer for the bullets t despawn after awhile.

rb.velocity affects the speed and movement of the rigidbody, so you wanna set that to transform.right and multiply it by speed

now you have a bullet that moves and kills itself after awhile, now you wanna make it shoot outta the gun.

first create these varibles and label them 

```cs
//gun variables
[SerializeField] private GameObject bulletPrefab;
[SerializeField] private Transform firingPoint;
[SerializeField] private float fireRate = 0.5f;
private float fireTimer;
```

The bulletPrefab stores the bullets prefab (no shit). make sure you drag it in the inspector. the firing point is a empty gameobject youll place near the guns barrel, which is where the bullet fires from //(make sure its under the gun gameobject so it rotates with it). 
the fire rate is the timer between each bullet, well get to that in a sec
and the firetimer is what we set equal to the firerate, and what actually counts down using Time.Delta time, see below

Here is the function:
private void FireGunFunc()


```cs
{
    if (Input.GetMouseButtonDown(0) && fireTimer < 0f)
    {
        Instantiate(bulletPrefab, firingPoint.position, firingPoint.rotation);
        fireTimer = fireRate;
    }
    else
    {
        fireTimer = fireTimer -= Time.deltaTime;
    }
}

//(yeah Idk why the colors are buggin out)
```
