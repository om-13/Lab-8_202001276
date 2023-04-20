# Lab-8_202001276
## **Name:** *Om Chalodiya*
## **ID:** *202001276*
## **Objective:** *JUnit Testing in Eclipse*
---

## Creating Java Package and Boa Class

A package _202001276_Lab-8_ is created for the _Boa_ class implementation. The **.java** code for the same is as follows:

```java
package tests;

public class Boa {
	private String name; 
	private int length; // the length of the boa, in feet 
	private String favoriteFood; 
	public Boa (String name, int length, String favoriteFood){
		this.name = name; 
		this.length = length; 
		this.favoriteFood = favoriteFood; 
	} 
	 // returns true if this Boa constructor is healthy 
	public boolean isHealthy(){ 
		return this.favoriteFood.equals("granola bars");
	} 
	// returns true if the length of this boa constrictor is 
	// less than the given cage length 
	public boolean fitsInCage(int cageLength){
		return this.length < cageLength; 
	}
}
```

## Creating a JUnit Test Class in Eclipse

We can create a JUnit test case for any **.java** file by right-clicking on the file, selecting _new_ and then clicking on _JUnit Test Case_. We create a test case file **BoaTest.java** for **Boa.java** file.

After configuring the test case file, we define the _setUp()_ function as follows

```java
package tests;
import org.junit.Before;
import org.junit.Test;
public class BoaTest {
	Boa jen,ken;
	
	@Before
	public void setUp() throws Exception { 
		jen = new Boa("Jennifer", 2, "grapes");
		ken = new Boa ("Kenneth", 3, "granola bars");
	} 
}
```

> Note that the methods _testIsHealthy()_ and _testFitsInCage()_ will contain code to test the _Boa_ class methods. These functions along with _tearDown()_ are yet to be implemented.
