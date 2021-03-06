# Summary
As mentioned the use cases in the assignment is implemented in a generic way such that discounts can easily be created and applied to bills. The main test cases are in
[BillTest](https://github.com/raghuveersinghtank/Java-Assignment---Xebia-IT-Architect/blob/master/BillTest.java) where explained each test case through comments. The discounts in the assignment are created in [DiscountServiceImpl](https://github.com/raghuveersinghtank/Java-Assignment---Xebia-IT-Architect/blob/master/DiscountServiceImplTest.java). Below is a summary of my approach, rationale, logical and completed activities.

# Coding exercise:

On a retail website, the following discounts apply: 
1. If the user is an employee of the store, he gets a 30% discount 
2. If the user is an affiliate of the store, he gets a 10% discount 
3. If the user has been a customer for over 2 years, he gets a 5% discount. 
4. For every $100 on the bill, there would be a $ 5 discount (e.g. for $ 990, you get $ 45 as a discount). 
5. The percentage based discounts do not apply on groceries. 
6. A user can get only one of the percentage based discounts on a bill. 

Write a program with test cases such that given a bill, it finds the net payable amount. Please note the stress is on object oriented approach and test coverage. What we care about: 


* object oriented programming approach 
* unit test (may be using xUnit) and code coverage 
* code to be generic and simple 
* leverage today's best coding practices 
* clear README.md that explains how the code and the test can be run.

# Getting Started
Requirements:

- Apache Maven 3.3
- Java 1.7 

Clone and build the project

```bash
    https://github.com/raghuveersinghtank/Java-Assignment---Xebia-IT-Architect.git
    cd bill-discounts-master
    mvn install
    mvn compile
    mvn test
    
    Project inside Java-Assignment---Xebia-IT-Architect-master\Java-Assignment---Xebia-IT-Architect-master\bill-discounts-master.zip\bill-discounts-master
```    

# Assumptions
- When applying multiple discounts, first discount is applied to the net, second discount is applied to the discounted net, etc…
- Mutually exclusive discounts are applied first, for example the percentage based ones
- Mentioned use test case as well ae method in Bill Test java class for discounted and without discounted.
- An entire bill can only be for one category, for example one bill can be groceries, another bill might be for clothing, etc...

# Object Oriented Approach
A high level class diagram of my approach is shown below. I've followed an OO approach to implementing the requirements, here is my rationale:
- I felt that User and Bill do not need multiple classes as there is not much business logic related to a specific type of user or bill. Instead I used enums to differentiate between the types of users and bills.
- I felt there is a great deal of business logic related to discounts so implemented them in a generic way such that different discounts can be created. I've used a common discounts super class [GenericDiscount](https://github.com/raghuveersinghtank/Java-Assignment---Xebia-IT-Architect/blob/master/GenericDiscount.java) for the common functionality with subclasses implementing the logic related to the applicability of the discount. 
- I've modelled and created subclasses to represent each type of discount (e.g. user type, customer period or multiples of the net) and ensured this is done in an OO way.
- I've used interfaces where possible to reduce coupling.
https://github.com/raghuveersinghtank/Java-Assignment---Xebia-IT-Architect/blob/master/class_diagram.png
![Alt text](https://github.com/raghuveersinghtank/Java-Assignment---Xebia-IT-Architect/blob/master/class_diagram.png "Class Diagram")


# Generic & Simple Code

I've implemented the requirements in a generic way such that developers can easily create new discounts. The code is well commented and easy to understand.

# Leverage Today’s Best Coding Practices

To ensure the code follows the best practices and standards, I’ve used the [Checkstyle](https://github.com/checkstyle/checkstyle) maven plugin with the [Google Checkstyle](https://github.com/checkstyle/checkstyle/blob/master/src/main/resources/google_checks.xml) settings. Using the plugin I've double checked the code to ensure all style issues are fixed.

To run the checkstyle report:

```bash
    mvn checkstyle:checkstyle
```

I've also followed the Java coding standards and defensive programming, i.e. validation, checking for nulls and invalid values where possible. And where appropriate comments are added to the code to ensure other developers can also understand and easily work on the code.

To run FindBugs plugin:

```bash
    mvn findbugs:check
```

To run the PMD plugin:

```bash
    mvn pmd:check
```
