# SOLID Principles

**Reference Links:**
1. https://team-coder.com/solid-principles/

2. http://blog.gauffin.org/2012/05/solid-principles-with-real-world-examples/

3. https://dzone.com/articles/solid-principles-by-examples-single-responsability

4. https://dzone.com/articles/solid-principles-by-examples-openclosed

5. https://dzone.com/articles/solid-principles-by-examples-liskov-substitution-p

6. https://dzone.com/articles/solid-principles-by-example-interface-segregation

7. https://dzone.com/articles/solid-principles-by-example-dependency-inversion




# 1. Single Responsibility Principle

**A class should have one, and only one, reason to change.**

**Description:**

Every class is responsible for exactly one thing. That means it has only one reason to change. If you change anything in that class, it will effect only one particular behavior of the software. That makes the code more robust because there will be less side effects. If a class had two responsibilities and you changed anything, the risk would be high that you also break the logic for the second behavior.

**Example:**

A ScoreCounter class is only responsible for counting the score of a game according to the scoring rules. This class should only change if the scoring rules change.


# 2. Open-Closed Principle

**You should be able to extend a classes behavior, without modifying it.**

**Description:**

The classes you use should be open for extension but closed for modification. This can be achieved with inheritance. You don’t have to touch the class you want to extend if you create a subclass of it. The original class is closed for modification but you can add custom code to your subclass to add new behavior.

Inheritance may be the most popular way to implement the Open-Closed Principle but it is not the only one. Objective-C, for example, offers categories which can be used to add methods to a class, without touching the original class and without subclassing it.

**Example:**

Imagine you use an external library which contains a class Car. The Car has a method brake. In its base implementation, this method only slows down the car but you also want to turn on the brake lights. You would create a subclass of Car and override the method brake. After calling the original method of the super class, you can call your own turnOnBrakeLights method. This way you have extended the Car‘s behavior without touching the original class from the library.

# 3. Liskov Substitution Principle

**Derived classes must be substitutable for their base classes.**

**Make small and specific interfaces so the client who implements them does not depend on methods it does not need.**

**Description:**

Assume we have a class B which is a subclass of A. If your program works with an object a of class A you can replace it with an object b of class B without changing the behavior of the program.

The implementation of this principle can be a little bit tricky if you combine it with the Open-Closed Principle. Even if you extend the behavior of your class in a subclass, you must make sure that you could still exchange the base class with the derived class without breaking anything.

**Example:**

You have an instance of the class Car which your program uses to perform a drive action. This instance could be replaced by an instance of the class Tesla if Tesla is a subclass of Car.

# 4. Interface Segregation Principle

**Make fine grained interfaces that are client specific.**

**Description:**

Classes should be as specialized as possible. You do not want any god classes that contain the whole application logic. The source code should be modular and every class should contain only the minimum necessary logic to achieve the desired behavior. The same goes for interfaces. Make small and specific interfaces so the client who implements them does not depend on methods it does not need. Instead of one class that can handle three special cases it is better to have three classes, one for each special case.

**Example:**

In an adventure game, you have a class for your main character. The player can either be a warrior or an archer or a wizard. Instead of a class which can perform all the actions, like strike, shoot and heal, you would create three different classes, one for each character type. In the end, you would not only have a Character class but also a Warrior, an Archer and a Wizard, all inheriting from Character and implementing their specific actions.

# 5. Dependency Inversion Principle

**Depend on abstractions, not on concretions.**


The principle states:


    High-level modules should not depend on low-level modules. Both should depend on abstractions.
    

    Abstractions should not depend on details. Details should depend on abstractions.


**Description:**

Classes should not depend on concrete details of other classes. Even classes from a high domain level should not handle the specific details of components from a lower level. Both low and high level classes should depend on the same abstractions. To create specific behavior you can use techniques like inheritance or interfaces.

**Example:**

Imagine we have a class Distributer which is able to share a blog post on different platforms. According to the Interface Segregation Principle the distributer uses a composition of several instances, like a TwitterShareAction and a FacebookShareAction. Now the goal of the Dependency Inversion Principle is to not depend on concrete methods of the share action classes, like sharePostOnTwitter and sharePostOnFacebook. Instead the Distributer class would define an interface called Sharing which is implemented by TwitterShareAction and FacebookShareAction. It declares the abstract method sharePost. The Distributer class doesn’t have to know the details of the concrete share actions. It just calls the sharePost method.
