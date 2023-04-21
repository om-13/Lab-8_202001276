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

## Testing _Boa_ class methods

### _isHealthy()_ method

It is important to note that the _isHealthy()_ function does not take any parameters. Due to this, the only test cases possible are to call the method on _Boa_ objects _"jen"_ and _"ken"_.  
Thus, the test cases defined in the _testIsHealthy()_ test function is as follows:

```java
  @Test
  public void testIsHealthy() {
      assertEquals("Error in isHealthy()",false, jen.isHealthy());
      assertEquals("Error in isHealthy()",true, ken.isHealthy());
  }
```

> The cases are defined such that _jen_ does not have favoriteFood as _"granola bars"_ which is necessary for boa object to be healthy while _ken_ has favoriteFood as _"granola bars"_.

### _FitsInCage()_ method

The _FitsInCage()_ function takes an integer parameter as input and hence can have a range of test-cases possible.  
Although _jen_ and _ken_ both will be executing the same function definition for _FitsInCage(<cage_length>)_ function call, it is better to call methods from both the instances to ensure independency of the function definition from the instance.

The test-cases defined can thus go as follows:

```java
@Test
public void testFitsInCage() {
    assertEquals("Error in fitsInCage()",true,jen.fitsInCage(3));  // For length of cage greater than jen's boa
    assertEquals("Error in fitsInCage()",false,jen.fitsInCage(2)); // For length of cage equal to jen's boa
    assertEquals("Error in fitsInCage()",false,jen.fitsInCage(1)); // For length of cage less than jen's boa
    assertEquals("Error in fitsInCage()",true,ken.fitsInCage(4)); // For length of cage greater than ken's boa
    assertEquals("Error in fitsInCage()",false,ken.fitsInCage(3)); // For length of cage equal to ken's boa
    assertEquals("Error in fitsInCage()",false,ken.fitsInCage(2));  // For length of cage less than ken's boa
}
```

> Here, according to the _"Equivalence class partitioning"_ and _"Boundary value analysis"_, the test-cases will be broadly divided into three partitions, corresponding to cage length less than _Boa_, cage length greater than _Boa_ and cage length equal to _Boa_.

## Running the Test Cases

To run the test cases, we simply right-click on the file(_BoaTest.java_ here), click on _Coverage As_, and then _1 JUnit Test_.

![image](https://user-images.githubusercontent.com/77343775/233540323-2ab61303-762a-4861-8824-6b7c5aaa3706.png)

> Here, the last two test cases gets failed indicating an error in the code. The error occurs in the _fitsInCage()_ function which is defined as follows:

```java
public boolean fitsInCage(int cageLength){
    return this.length < cageLength; 
}
```

To correct this error, the actual definition of the function should be as shown below to account for the fact that the boa can fit in a cage with length greater than or equal to its length.

```java
public boolean fitsInCage(int cageLength){
    return this.length <= cageLength; 
}
```

Modifying the code, we can see that all the test-cases gets successfully passed now

![image](https://user-images.githubusercontent.com/77343775/233540355-c35e59e3-f5a4-4e4f-9800-0d689fb58a2a.png)
