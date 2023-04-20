# Unit Testing

- Introduction
    - Unit testing is all about separating your system into units (Classes, methods, etc.) and test each unit to check if that unit does what it’s supposed to do.
    - It has become mandatory in most companies to do unit testing.
    - In current systems, testing code is predominating the whole codebase of a system. So the ratio between a production code to a test code is 1 : 1 or 1 : 3 or maybe may reach 1 : 10.
    - Initially, the the unit testing was an essential part as the production code, so the discussion has shifted from “should we write unit tests” to “What does it mean to write good unit tests?”.
- Growth of projects with and without tests, and the affect of good and bad tests on a project.
    - When you first start with building a system from scratch, you might think that adding unit tests at the beginning is a waste of time and you just want to launch an MVP (Minimum Viable Product) quickly.
    - But it turns out when you start to make your system more bigger with a chunk of features, the development time would increase hence the progress is slowed down. So at some point, you’d make no progress to the project in case you’ve decided to not go with adding unit tests along the development process.
    - However, adding unit tests from the beginning might take time to deploy an initial release of your software, but you’re making your software more robust and ready for changes and new features.
    - As you can see from the graph, with unit tests, you’re able to sustain a development pace thanks to the unit tests that you’re writing.
        
        ![Untitled](Unit%20Testing%20f961323acc5c4c3ab1f71eb7a7b5d523/Untitled.png)
        
    - You should also notice that writing bad tests may end up with the same result as of without writing tests.
        
         
        
        ![Untitled](Unit%20Testing%20f961323acc5c4c3ab1f71eb7a7b5d523/Untitled%201.png)
        
- How to test a function ?
    - Say you have a function called isPermutationOf that is used to test whether a string is a permutation of other string (which basically means both strings have the same characters but in different order).
    - Initially, this function has no implementation and returns false.
    - So your test function should compare the value returned by isPermutationOf to the expected value you’ve manually passed to the test function for comparison. A third parameter is used to name each test so you can identify which one has passed and which one hasn’t.
    - Each call to our test function should cover a usage case for our function. Each function call is called test case, and a set of test cases are called test suite.
        
        ```c
        	test(TRUE, isPermutationOf("a", "a"), "a");
          test(TRUE, isPermutationOf("abc", "abc"), "abc");
          test(TRUE, isPermutationOf("cab", "bac"), "cab=>bac");
          test(FALSE, isPermutationOf("c", "b"), "c=>b");
          test(TRUE, isPermutationOf("abcdefg", "gfedcba"), "abcdefg");
        
        // PASSED a
        // PASSED abc
        // PASSED cab=>bac
        // PASSED c=>b
        // PASSED abcdefg
        // PASSED 1 is empty
        // PASSED 2 is empty
        // PASSED 1 and 2 are empty
        // PASSED abc=>ab
        // PASSED 123456789
        ```
        
        [demo_unit_test_C.cpp](Unit%20Testing%20f961323acc5c4c3ab1f71eb7a7b5d523/demo_unit_test_C.cpp)
        
    
    - After you write your test cases, you start working on the implementation of isPermutationOf function. After finishing working on that function, you can validate its functionality by running the test cases. What we did is called TDD or Test-Driven Development, in which you’re writing the test cases for the function before the implementation of that function.
    - Whenever you change the function, so for example optimizing the algorithm used, you can still assure that the function maintains the same functionality by running the tests you’ve written.
- Code coverage.
    - When each test case is executed, the function you’re testing is executed and may trigger different scenarios in the function code (going through an if condition for example) depending on the input given to the function.
    - So when your test suite (set of tests) execute every single line in the function you want to test, it’s said that the code is fully covered.
    - So it can be formally defined that it’s the ratio of number of code lines executed by at least one test and the total number of lines in the production codebase.
        
        ![Untitled](Unit%20Testing%20f961323acc5c4c3ab1f71eb7a7b5d523/Untitled%202.png)
        
    - Important Example of code and branch coverage.
        - The following code snippet shows a function that checks if a string is long (larger than 5 characters). This function is followed by a test case that passes “abc” as an input to the function.
        - You notice that this test case executes only 4 lines out of 5 of the function (the open and closing braces are included).
        - It’s said that the tests has covered 80% of the production code → 4 / 5 = 0.8.
        
        ```csharp
        public static bool IsStringLong(string input)
        {
        	if(input.Length > 5)
        		return true;
        	// new line is not counted.
        	return false;
        }
        
        // Test case
        public void Test()
        {
        	bool result = IsStringLong("abc");
        	Assert.Equal(false, result);
        }
        ```
        
        - You have two options of increasing the code coverage percentage. First you may add more test cases, or you might do some refactoring to the production code such that the existing test cases cover all lines of code.
        
        ```csharp
        public static bool IsStringLong(string input)
        {
        	return input.Length > 5;
        }
        
        // Test case
        public void Test()
        {
        	bool result = IsStringLong("abc");
        	Assert.Equal(false, result);
        }
        ```
        
        - You may think at first that this test case is sufficient as it covers 100% of the production code. Unfortunately, having a percentage of 100% is not actually a metric of covering all the cases. So in our refactored version of the isStringLong function, you may notice that we haven’t actually cover the case in which a string of more than 5 characters is passed. So you shouldn’t be deceived by the code coverage percentage.
        - In this case, we might use branch coverage is a metric of code coverage. So in case of the optimized version, we know that this Boolean expression would result in two values hence two branches (which is totally equivalent to the if-else version) that are needed to be covered. So in the previous code snippet, the branch coverage is 50% because we only covered the case in which a false value has been returned.
            
            ![Untitled](Unit%20Testing%20f961323acc5c4c3ab1f71eb7a7b5d523/Untitled%203.png)
            
        
        - The branch coverage may be also misleading in case you’re using an external libraries.
            
            ```csharp
            public static int Parse(string value)
            {
            	return int.Parse(value);
            }
            
            public void Test(){
            	bool result = Parse("1");
            	Assert.Equal(1, result);
            }
            ```
            
        - In the previous code snippet, you might think at first that we have only one possible branch in which you pass a string of an integer and an integer value would be returned. You might’ve not realized the internal work done by the method, so you’d have to dig into the source code to check for the different types of strings that might be passed as an argument to the method.
            
            ![Untitled](Unit%20Testing%20f961323acc5c4c3ab1f71eb7a7b5d523/Untitled%204.png)
            
        - So the method would act differently depending on the input given, so it’s not a one branch anymore.
    - Summary
        
        ![Untitled](Unit%20Testing%20f961323acc5c4c3ab1f71eb7a7b5d523/Untitled%205.png)
        
- Choosing test cases.
    - The main goal of unit tests is to expose as much anomalous behavior that caused by inputs as possible.
        
        ![Untitled](Unit%20Testing%20f961323acc5c4c3ab1f71eb7a7b5d523/Untitled%206.png)
        
    - It’s practically infeasible to test all possible inputs to a unit, so writing many unit tests doesn’t indicate that our unit is immune to odd behaviors.
    - You should probably pick a useful set of inputs that indicate how your unit behaves with various inputs. Choosing inputs that are similar that may result in similar output/behavior is pointless.
    - Each set of similar inputs is called **equivalence partitions.** So each test case should cover a partition of these equivalence partitions, thus this type of testing is called **partition testing**.
    
- Partition testing.
    - In partition testing, you divide your inputs into equivalence partitions such that each partition has similar inputs.
    - Your tests cases should cover each partition.
    - So you may consider small positive values (1, 2, 4, 5) as a partition, large positive values (1000, 20000) as a partition, or negative values as a partition (-1, -2, -3, .. ).
        
        ![Untitled](Unit%20Testing%20f961323acc5c4c3ab1f71eb7a7b5d523/Untitled%207.png)
        
    
    - Example of partitioning.
        
        ![Untitled](Unit%20Testing%20f961323acc5c4c3ab1f71eb7a7b5d523/Untitled%208.png)
        
         
        
    - The values that you pick from the partition may reside at the boundaries and the middle of that partition.
    - So if you partition ranges from 1 to 20, you can pick 1, 20 and 10 as your inputs, and these values represents the whole partition.
    - An example of testing a program.
        - Consider a program that accepts four to ten inputs.
        - Each input is five-digit integer greater than or equal 10k.
        - So you first need to test two things, the first specification which is the number of input, and the value of the input.
        - You may start with partitioning the number of inputs. So you want to see how your system behaves when passing three inputs (less than the required), passing number of inputs that resides in the allowed range (4 to 10), or passing more than 10 inputs.
        - Each kind of input should trigger different behavior of the program. So for example your program should throw an exception in case of passing only 3 inputs or more than 10, and should work properly if passing, for example, 7 inputs.
        - Same steps are followed when partitioning the input values, you can split the values into three partitions in which you can pass 9999 to represent a value less than 10k, a value that resides in the range 10k to 99999 (you can pick 50k which satisfies this partition), or 100k that represents a value more than 99999.
            
            ![Untitled](Unit%20Testing%20f961323acc5c4c3ab1f71eb7a7b5d523/Untitled%209.png)
            
- Black-box vs. White-box testing.
    - Black-box testing → Using the system specifications (like user stories) to define the test cases.
    - White-box testing → Using the source code of a system to define its test cases.
    - The last example in partition testing is an example of black-box. In that example, we specify our test cases with the help of system specifications (number of inputs and the value of each input).
    - Logically, in TDD you always have to use black-box testing as you haven’t written any implementation yet.
- Structure of unit test code.
    - Typically, developers tend to use frameworks to write unit tests such as JUnit or xUnit. Most frameworks are used similarly.
    - You have to define a class for each unit, and each class should have separate method for each test case.
    - Inside each method (test case), the code should be composed of three components following AAA pattern (Arrange, Act, Assert).
    - Example.
        - Consider you have a system that is a calculator, and you wish to test one of its methods which is the **sum** method.
        
        ```csharp
        public class Calculator {
        
        	public double Sum(double first, double second) {
        		return first + second;
        	}
        
        }
        ```
        
        - You’d need to have a class that covers all your test cases as methods of that class. The code written here is in xUnit but other frameworks would have a similar construction
        
        ```csharp
        public class CalculatorTests{
        	
        	[Fact] // xUnit attribute to indicate a test case.
        	public void Sum_of_two_numbers(){
        		
        		// Arrange.
        		double firstNumber = 1;
        		double secondNumber = 2;
        		var calculator = new Calculator();
        		
        		// Act.
        		double result = calculator.Sum(firstNumber, secondNumber);
        
        		// Assert
        
        		Assert.Equal(3, result);
        
        	}
        
        }
        ```
        
        - So as we previously discussed, we have three main steps which are **arrange**, **act**, and **assert**. These steps are used to structure our test case. At the first step, you start with initializing your parameters and the object you’re going to test its method. The second you start to call the method you’re intended to test. Lastly, we make sure that we got the correct result by using the Assert.Equal method.
        - The three components may be called **Give-When-Then** (like in JUnit) or **Set-Call -Assertion**, these are all synonymous to AAA.
        - Also note that it’s fine that your method name (test case) can be long, however, it must be descriptive of what you’re trying to test.
        - An example of JUnit in Java.
            
            ```java
            @Test // JUnit attribute to indicate a test case.
            
            // Long name but it's very descriptive of what it should test.
            // So this method should checks if you run out of coffee
            // then you should stop serving coffee.
            public void shouldNeverServeCoffeeIfNoRemaining(){
            	
            	// Given
            	var cafe = new Cafe();
            	cafe.setCoffeesRemaining(1);
            
            	// When
            	cafe.serveCoffee();
            
            	// Then
            	assertFalse(cafe.canServeCoffee());
            
            }
            ```
            
        
    - Tips for unit testing.
        - Each test case must be simple and shouldn’t take much time to execute (coming back to this point in stubbing).
        - You should avoid multiple arrange, act, and assert in a single test case.
        - Avoid if statements in a test code. This implies that you’re testing two behaviors (test code) instead of one. A test should be a simple sequence of steps with no branching, hence you should avoid branching in unit tests as well as integration tests.
        - Try to avoid multiple lines of act sections. Check here to see an example.
            - Consider a store class that has a method called AddInventory in which you can add a product and its inventory, and another method called GetInventory to know the inventory of a product.
            - There’s also another class called customer that is able to purchase products using Purchase method.
            
            ```csharp
            [Fact]
            public void PurchaseSucceedsWhenEnoughInventory(){
            	
            	// Arrange
            	var store = new Store();
            	store.AddInventory(Product.Shampoo, 10);
            	var customer = new Customer();
            
            	// Act
            	bool success = customer.Purchase(store, Product.Shampoo, 5);
            	store.RemoveInventory(Product.Shampoo, 5);
            
            	// Asssert
            	Assert.True(success);
            	Assert.Equals(5, store.GetInventory(Product.Shampoo));
            }
            ```
            
            - You notice from the previous code snippet that you have to remove the amount of shampoo purchased by the customer from the inventory. That puts extra effort on the developer to memorize calling the RemoveInventory method after calling the Purchase method.
            - Multiple lines of act sections indicates a problem in the class’ API.
            - The RemoveInvetory method must have been called inside the Purchase method of the customer, so you don’t have to call it in your test case.
        - It’s common to call the objects that you want to test their methods as SUT (system under test). So with that you have the ability to differentiate the objects that you want to test from the objects that just helping in the test process. So in the previous example, we wanted to test the Customer object not the Store object, so it should have been called as **SUT**.
        - You can separate your AAA sections with empty lines rather than code comments.
            
            ![Untitled](Unit%20Testing%20f961323acc5c4c3ab1f71eb7a7b5d523/Untitled%2010.png)
            
- Isolation.
    - An important attribute in unit testing is **isolation**, and there’s a conflict in that manner but that would be discussed in the next point.
    - Let’s recall the previous example of Customer unit testing.
    
    ```csharp
    [Fact]
    public void PurchaseSucceedsWhenEnoughInventory(){
    	
    	// Arrange
    	var store = new Store();
    	store.AddInventory(Product.Shampoo, 10);
    	var customer = new Customer();
    
    	// Act
    	bool success = customer.Purchase(store, Product.Shampoo, 5);
    	store.RemoveInventory, Product.Shampoo, 5);
    
    	// Asssert
    	Assert.True(success);
    	Assert.Equals(5, store.GetInventory(Product.Shampoo));
    }
    ```
    
    - There’s an argument that the pervious snippet has a problem. The problem is that our test case which tests a method in the customer object needs a store object to validate the test case. The disadvantage here is that the GetInventory method may fail for some reason and thus interrupt the test.
- Schools of unit testing.
    - We have two main schools that define the isolation, the first is London school and the second is Classical school.
    - Classical school is fine with the Customer test case in which we initiate a Store object with it. So this school defines a unit as just a class or maybe a set of classes (customer and store objects).
    - However, in London school, you can only use a single class and all other dependencies or objects must be mocked (use test doubles, which basically means create a fake object that you can control its operations).
    
    ![Untitled](Unit%20Testing%20f961323acc5c4c3ab1f71eb7a7b5d523/Untitled%2011.png)
    
- Test Doubles.
    - When you have dependencies in your test case (like the store object) you may face three main issues :
        - Your team mate have not done working on the dependency object that you need for your test case, in other words, it’s not implemented yet.
        - The dependency requires long time to execute (connecting to a database, calling a web service, etc.).
        - The dependency may have its own bugs or issues, but we want to test the SUT not the dependency.
        
    - To overcome these issues, hence emphasize the isolation principle we talked about earlier, we can use **test doubles**.
    - **Test doubles** are objects that replace real objects in unit testing to facilitate the isolation. They’re only used to mimic the dependencies so your SUT can be tested without any need of real dependencies.
    - Categories of test doubles.
        - Test doubles are divided into two categories:
            - Mocks
            - Stubs
- Mocks vs. Stubs.
    
    ![Untitled](Unit%20Testing%20f961323acc5c4c3ab1f71eb7a7b5d523/Untitled%2012.png)
    
    - Mocks help to emulate and examine outcoming interactions. These interactions are calls the SUT makes to its dependencies to change their state. Mocks should track how many times have you called a method, or the inputs that you passed to a method. So in this example, we notice that the mock object is used to keep record of the number of times that SendGreetingsEmail method was invoked. Also the **verify** method used to verify that the SUT has interacted with the mock object.
        
        ![Untitled](Unit%20Testing%20f961323acc5c4c3ab1f71eb7a7b5d523/Untitled%2013.png)
        
    - Stubs help to emulate incoming interactions. These interactions are calls the SUT makes to its dependencies to get input data. In this one, we create a stub object and then changed the operation of the GetNumberOfUsers method such that it just returns 10 rather than connecting to a real database and waste time. After that, the CreateReport method in our SUT calls that method (GetNumberOfUsers) internally.
        
        ![Untitled](Unit%20Testing%20f961323acc5c4c3ab1f71eb7a7b5d523/Untitled%2014.png)
        
    - Consider the following class and its test case:
        
        ```csharp
        public class Customer{
        
        	// Has two methods, AddInventory and RemoveInventory.
        	private Store store;
        	
        	public Customer(Store store){
        		this.store = store;
        	}
        
        	public bool Purchase(Product product, int numOfItems){
        		// Assume that this methods does some work...
        		
        		// This method may access a DB or web service to remove the product. Which
        		// takes some time.
        		bool success = store.RemoveInventory(product, numOfItems); 
        
        		return success; 
        	}
        
        }
        ```
        
        ```csharp
        [Fact]
        public void Purchase_succeeds_when_enough_inventory(){
        	
        	// This object is a mocked version of the real Store object.
        	// It may has attributes or fields to track method calls. We
        	// may use the help of the framework (xUnit) to create the
        	// mock class.
        	var storeMock = new Mock<IStore>();
        	var customer = new Customer(storeMock.Object);
          storeMock.Setup(x => x.RemoveInventory(Product.Shampoo, 5)).Returns(true);
        
        	// Internally, this method calls store.RemoveInventory method.
        
        	bool success = customer.Purchase(Product.Shampoo, 5);
        	
        	
        	Assert.True(success);
        	
        	storeMock.Verify(x => x.RemoveInventory(Product.Shampoo, 5),Times.Once),
        	
        }
        ```
        
    - So the mock object we created here is the store, and it’s outcoming interaction was the RemoveInventory method.
    - The stubbing is the input data or incoming interaction when we assigned the **success** variable’s value in the Purchase method to be true whenever RemoveInventory is called with these parameters.
    - The previous example represents a test double that can be both mock and stub (call it **mock** for short). The same goes with this example, but we have verified the number of times we called RemoveInventory method.
        
        ![Untitled](Unit%20Testing%20f961323acc5c4c3ab1f71eb7a7b5d523/Untitled%2015.png)
        
    - Question
        
        ![Untitled](Unit%20Testing%20f961323acc5c4c3ab1f71eb7a7b5d523/Untitled%2016.png)
        
        - This is a stub as you can see there’re setups to change the returned value of methods inside the mock, and there’s no verify method called to verify the number of times a specific method has been called.
- Mocks vs. Spies.
    - Both are playing the same role.
    - Mocks are created with the help of a mocking framework like Mockito (Java), Mock (Python).
    - Spies are written manually without the help of any framework, also known as **handwritten mocks**.
- Decoupling interface from the concrete implementation.
    - It’s common to decouple the signature of a class’ methods to a separate interface.
    - This interface is used by the mocking framework to create mock objects so the framework is capable of add its own implementation to methods in the interface.
        
        ![Untitled](Unit%20Testing%20f961323acc5c4c3ab1f71eb7a7b5d523/Untitled%2017.png)
        
        ![Untitled](Unit%20Testing%20f961323acc5c4c3ab1f71eb7a7b5d523/Untitled%2018.png)