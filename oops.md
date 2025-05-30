# Object-Oriented Programming (OOP) Interview Questions for Freshers

---

## 🟢 Easy-Level Questions

1. **What is Object-Oriented Programming? Can you name its main principles?**  
   - **Expected Answer**: Object-Oriented Programming (OOP) is a programming paradigm based on the concept of objects. Main principles include Encapsulation, Abstraction, Inheritance, and Polymorphism.

2. **Can you explain what a class and an object are, in your own words?**  
   - **Expected Answer**: A class is a blueprint for creating objects. An object is an instance of a class.

3. **Why do we use constructors in OOP? What happens if we don’t define one?**  
   - **Expected Answer**: Constructors initialize objects. If we don't define one, most languages provide a default constructor.

4. **What is the difference between method overloading and method overriding?**  
   - **Expected Answer**: Overloading means same method name with different parameters; overriding means redefining a base class method in a derived class.  
   - **Example**:
     ```java
     class Example {
         void show(int a) {}
         void show(String s) {} // Overloading
     }

     class Parent {
         void display() { System.out.println("Parent"); }
     }

     class Child extends Parent {
         @Override
         void display() { System.out.println("Child"); } // Overriding
     }
     ```

5. **What is the difference between a class and a structure (in languages like C++)?**  
   - **Expected Answer**: In C++, structures have public members by default while classes have private. Classes support full OOP features.

6. **What is encapsulation in simple terms, and why is it useful?**  
   - **Expected Answer**: Encapsulation means hiding the internal state and requiring all interaction to be performed through an object’s methods. It improves security and modularity.

7. **Can you name a real-world object and explain how it maps to a class and object?**  
   - **Expected Answer**: A car can be a class. A specific car (e.g., red Honda Civic) is an object. Class defines attributes (color, speed) and behaviors (drive, brake).

8. **What is the ‘this’ keyword used for?**  
   - **Expected Answer**: 'this' refers to the current object. It helps distinguish between instance variables and parameters with the same name.

9. **What are default and parameterized constructors?**  
   - **Expected Answer**: Default constructors take no parameters. Parameterized constructors take arguments to initialize objects.

10. **Can two different classes have methods with the same name? If yes, how does the compiler know which one to call?**  
    - **Expected Answer**: Yes. It depends on the object’s class that calls the method. Compiler uses the reference type and runtime type accordingly.

---

## 🟡 Medium-Level Questions

11. **Can you explain the concept of inheritance? Also, what are the types of inheritance?**  
    - **Expected Answer**: Inheritance allows a class to acquire properties of another class. Types: Single, Multiple, Multilevel, Hierarchical, Hybrid.

12. **How does encapsulation help with data security? Can you give an example?**  
    - **Expected Answer**: It hides internal state and allows controlled access via methods, reducing risk of unintended interference.

13. **What is abstraction? How is it different from encapsulation?**  
    - **Expected Answer**: Abstraction hides complexity by showing only relevant data. Encapsulation hides data through access modifiers.

14. **What is polymorphism? Can you give a real-life example or a code snippet?**  
    - **Expected Answer**: Polymorphism allows one interface to be used for different data types.  
    - **Example**:
      ```java
      class Animal {
          void sound() { System.out.println("Animal sound"); }
      }

      class Dog extends Animal {
          @Override
          void sound() { System.out.println("Bark"); }
      }

      Animal a = new Dog();
      a.sound(); // Output: Bark
      ```

15. **What is an interface, and how is it different from an abstract class?**  
    - **Expected Answer**: Interface defines a contract with no implementation. Abstract classes can have both abstract and concrete methods.  
    - **Example**:
      ```java
      interface Flyable {
          void fly();
      }

      abstract class Bird {
          void eat() { System.out.println("Eating"); }
          abstract void makeSound();
      }

      class Sparrow extends Bird implements Flyable {
          public void fly() { System.out.println("Flying"); }
          void makeSound() { System.out.println("Chirp"); }
      }
      ```

16. **What is the use of the final keyword in OOP?**  
    - **Expected Answer**: It prevents method overriding, variable reassignment, or class inheritance depending on where it's used.

17. **What are constructors and destructors? Do all OOP languages have both?**  
    - **Expected Answer**: Constructors initialize objects. Destructors clean up resources. Java has finalizers (deprecated); C++ uses destructors.

18. **What is the difference between shallow copy and deep copy?**  
    - **Expected Answer**: Shallow copy copies references; deep copy copies actual objects recursively.

19. **What happens if you override equals() and not hashCode()?**  
    - **Expected Answer**: It can break hash-based collections like HashMap. Both must be overridden to maintain consistency.

20. **Can a constructor be private? If yes, why and when would you use it?**  
    - **Expected Answer**: Yes, to implement Singleton pattern or prevent instantiation.

---

## 🔴 Hard-Level Questions

21. **Explain the Liskov Substitution Principle with an example.**  
    - **Expected Answer**: Objects of a superclass should be replaceable with objects of its subclasses without breaking the application.  
    - **Example**: If class Bird has a fly() method, then a subclass Penguin should not override it in a way that breaks functionality.

22. **How would you implement multiple inheritance in a language that doesn’t support it directly (like Java)?**  
    - **Expected Answer**: Use interfaces to simulate multiple inheritance.

23. **What is dynamic dispatch? How does it work?**  
    - **Expected Answer**: Runtime selection of the appropriate method when an overridden method is called through a superclass reference.

24. **What are design patterns? Can you explain a few commonly used ones?**  
    - **Expected Answer**: Design patterns are best practices for solving common design problems. Examples: Singleton, Factory, Observer.  
    - **Example (Singleton)**:
      ```java
      class Singleton {
          private static Singleton instance;
          private Singleton() {}
          public static Singleton getInstance() {
              if (instance == null) {
                  instance = new Singleton();
              }
              return instance;
          }
      }
      ```

25. **Can you describe the differences between association, aggregation, and composition?**  
    - **Expected Answer**: Association is a general relationship. Aggregation is a weak 'has-a' (can exist independently). Composition is a strong 'has-a' (cannot exist independently).

---

## 🤔 Tricky Questions

26. **Can a class be both abstract and final? Why or why not?**  
    - **Expected Answer**: No. Abstract means it needs subclassing; final means it cannot be subclassed. They contradict each other.

27. **What will happen if you call a method on a null object reference in Java?**  
    - **Expected Answer**: A NullPointerException will be thrown at runtime.

28. **Is it possible to override a static method? Why or why not?**  
    - **Expected Answer**: No. Static methods belong to the class, not the instance.

29. **Can you instantiate an abstract class? How can it be used then?**  
    - **Expected Answer**: No, but you can use it as a reference type and instantiate subclasses.

30. **How can you implement method chaining in OOP?**  
    - **Expected Answer**: Return 'this' from each method.  
    - **Example**:
      ```java
      class Person {
          Person setName(String name) { ... return this; }
          Person setAge(int age) { ... return this; }
      }
      ```

---
