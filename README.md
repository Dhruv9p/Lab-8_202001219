# IT314 - Software Engineering LAB - 8
# Dhruv Prajapati
# 202001219

Goal - To learn how to use JUnit to write unit tests for Java programs.

1. Creating a new Eclipse project, and within the project create a package and defining the class

![image](https://user-images.githubusercontent.com/82575404/233334354-e579ee1f-ef35-4847-a14f-6bbef9eebc9a.png)

2. Test method to test the behaviour of the Boa class :

![image](https://user-images.githubusercontent.com/82575404/233335022-5ad4a53e-abf1-452e-a946-c255cadc9740.png)

3. Modified setUp() method in the BoaTest class :

![image](https://user-images.githubusercontent.com/82575404/233335311-48262807-9964-42b3-ad06-99918cffc348.png)

4. Running test cases

![image](https://user-images.githubusercontent.com/82575404/233335735-5fa0ecea-2d8c-49b9-9706-b923697d6fb6.png)

5. Modified Boa class with the new lengthInInches() method:

![image](https://user-images.githubusercontent.com/82575404/233336014-bb00380d-887a-4445-a0c4-8d7c6f38abb0.png)

# Boa.java file -

package Testing;

public class Boa {

	private String name;
  
	private int length; // the length of the boa, in feet
  
	private String favoriteFood;
  
	public Boa (String name, int length, String favoriteFood)
  
	{
  
		this.name = name;
    
		this.length = length;
    
		this.favoriteFood = favoriteFood;
    
	}
  
	// returns true if this boa constrictor is healthy
  
	public boolean isHealthy()
  
	{
  
		return this.favoriteFood.equals("granola bars");
    
	}
  
	// returns true if the length of this boa constrictor is
  
	// less than the given cage length
  
	public boolean fitsInCage(int cageLength)
  
	{
  
		return this.length < cageLength;
    
	}
	
	public int lengthInInches()
  
	{
  
		return this.length*12;
    
	}
  
}

# BoaTest.java file - 

package Testing;

import static org.junit.Assert.*;

import org.junit.Before;

import org.junit.Test;

public class BoaTest {

	private Boa jen;
  
	private Boa ken;
	
	@Before
  
	public void setUp() throws Exception {
  
		jen = new Boa("Jennifer", 2, "grapes");
    
		ken = new Boa ("Kenneth", 3, "granola bars");
    
	}
  
	@Test
  
	public void testIsHealthy_1() {
  
		boolean output = ken.isHealthy();
    
		assertEquals(output,true);
    
	}
  
	@Test
  
	public void testIsHealthy_2() {
  
		boolean output = jen.isHealthy();
    
		assertEquals(output,false);
    
	}
  
	@Test
  
	public void testFitsInCage_1() {
		
		int cage = 2;
    
		boolean output = jen.fitsInCage(cage);
    
		assertEquals(output,false);
    
	}
  
	@Test
  
	public void testFitsInCage_2() {
		
		int cage = 1;
    
		boolean output = ken.fitsInCage(cage);
    
		assertEquals(output,false);
    
	}
  
	@Test
  
	public void testFitsInCage_3() {
		
		int cage = 10;
    
		boolean output = ken.fitsInCage(cage);
    
		assertEquals(output,true);
    
	}
  
	@Test
  
	public void testFitsInCage_4() {
		
		int cage = 3;
    
		boolean output = ken.fitsInCage(cage);
    
		assertEquals(output,false);
    
	}
  
	@Test
  
	public void lengthInInches_1() {
		
		int output = jen.lengthInInches();
    
		assertEquals(output,24);
    
	}
  
	@Test
  
	public void lengthInInches_2() {
		
		int output = ken.lengthInInches();
    
		assertEquals(output,36);
    
	}
  
}



