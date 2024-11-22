Design Patterns in JUnit 4

1. Template Method Pattern
org.junit.runners.BlockJUnit4ClassRunner`

Roles:  
Abstract Class: ParentRunner  
Defines the structure of the testing execution process, such as run() and runChild().  
Concrete Class: BlockJUnit4ClassRunner`  
Implements the runChild() method to execute individual test cases.  

Functionality:  
ParentRunner provides a generic template for running test cases. The specific logic of executing test cases, such as handling test annotations and running methods, is implemented by the BlockJUnit4ClassRunner.  

Extensibility:  
  To create a custom runner, a developer can subclass ParentRunner and provide their own implementation of runChild() to modify the test execution flow.

2. Strategy Pattern
Location: org.junit.runners.model.Statement

Roles:  
Context: BlockJUnit4ClassRunner  
Uses various `Statement` implementations to execute specific parts of the test process.  
Strategies:  
InvokeMethod: Executes the test method.  
RunBefores and RunAfters: Handle @Before and @After annotated methods.  

Functionality:  
The BlockJUnit4ClassRunner delegates the execution of test-related logic to different Statement implementations. This decouples the test runner from the specific logic of handling annotations and method execution.  

Extensibility:  
Developers can add a new Statement subclass to introduce custom behavior during test execution, such as logging or performance monitoring.

3. Factory Pattern
Location: org.junit.rules.RuleChain

Roles:  
Factory: RuleChain
Dynamically creates a chain of TestRule objects.  
Product: Various TestRule implementations, such as Timeout and TemporaryFolder.  

Functionality:  
The RuleChain provides a fluent interface to compose multiple rules for a test case. Each rule is applied in the specified order, ensuring that resources are managed and tests are configured properly.  

Extensibility:  
 Developers can create a custom TestRule implementation and integrate it into the RuleChain to provide additional test configurations or behaviors.
