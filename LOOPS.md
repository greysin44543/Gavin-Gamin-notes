

## While loops

While loops repeat until a certain condition is met, or during a certain condition. for example:

```cs

int cupsinsink = 4

void Start()
{
	while (cupsinsink > 0)
	{
		cupsinsink -= 1;
		//subtracts 1 cup every loop
	
	}
	
	// repeats 4 times until cupsinsink = 0 then it stops looping


}

```

## do while loops

Do while loops run once, check if the while is true, then runs for however many times the while loops runs. This way the loop always runs once regardless if while should be running or not.

```cs

void Start()
{
	int cupsinsink = 4
	do
	{
		print("hello world")
		cupsinsink -= 1;
	}
	while (cupsinsink > 0);
	

}
```

## for loops

For loops are tricky. They repeat as long as a certain condition is met within the parameters of the for loop:

```cs

int numEnemies = 3;


void Start()
{
	for (int i = 0; i < numEnemies; i++)
	{
		print("enemy number" + i)
	}


}
```
The first paramter sets the value of i, the second is the condition for the loop to take place, and the third adds/subtracts to i for everyloop. In this loopit adds 1 every loop, until it is equal to 3, starting at 0.