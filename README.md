# JAVA Object Oriented Concepts

## Content

1. [Usage](#1-usage)
2. [Abstraction](#2-abstraction)
3. [Class](#3-class)
4. [Object](#4-object-an-instance-of-a-class)
5. [Package](#5-packages)

---

### 1. Usage

- It becomes apparent in the development and maintenance of large-scale programs
- Allow users to manage scale by partitioning the problem and hiding irrelevant details
- Allow programs to evolve without disrupting applications that already depend on them

### 2. Abstraction

> Hiding implementation details and capture and represent only those details that are relevant to the current perspective

- Application
  - Abstraction by specification
  - Abstracution thourgh parameters
  - Procedural abstraction
  - Data abstraction
  - Iteration abstraction
  - Type hierarchies

### 3. Class

> A template that defines states and behavious.

- Variables
  - Fields: variables declared in a class (class/global variable)
  - Local variables: variables passed to a method and part of a method's signature
  - Paramenters: variables passed to a method and part of method's signature
- Overloading methods: **_same_** method name, **_different_** parameters
- Constructor methods: **_same_** name as the class, **_no return type_**

- **this** keyword
  - `this()` invokes the constructor
  - `this.field` accesses an instance field (variable)
  - `this.method()` calls an instance method
- **static** keyword
  - It means only one copy exists of the field or method
  - No need to create an instance of the class
  - Useful for constants, cases where creating an instance doesn't make sense

```Java
class BankAccount{
  // fields
  private int age;
  private String name;

  // constructor
  public BankAccount(int age, String name){
    this.age = age;
    this.name = name;
  }

  // method
  public void myMethod(){}

}
```

### 4. Object: An instance of a class

```Java
BankAccount myAccount = new BankAccount();
```

### 5. Packages

- Java packages are containers for functionally-related classes
- Each package has its own scope and name space

```Java
import mypackage.foo;
import mypackage.*;
```

- Packages can be placed in sub-packages
- Dots uses to indicate subpackages

### 6. Encapsulation

> A design principle that separates the specification from implementation (hiding implementation from others)

- Specification
  - what the class/method does
  - how to interact with it
- Implementation:
  - how the class/method performs (actual code)
- Advantages
  - unimportant details are hidden away, so make programs easier to understand
  - implementation can be changed without affecting the interface, so make programs easier to modify
  - ensure the publichsed API for the class states **_what_** the class will do but not how
- Important principles
  - make fields **_private_**
  - make getters and setters **_public_**
  - make helper (utility) methods **_private_** (unless there is utilities class)

### 7. Inheritance

> The inheritance relationship is an "**_is a_**" relationship

- `extends` keyword for inheriting from superclass
- A superclass' constructor is called with `super()` and its methods with `super.method()`
- `super()` not needed if implementing a no parameter constructor

### 8. Concrete and other classes

| Concrete classes                 | Interface     | Abstract Classes                        |
| -------------------------------- | ------------- | --------------------------------------- |
| **_may_** have fields            | No fields     | **_may_** have fields                   |
| specification and implementation | specification | at least one with is just specification |

#### 8.1 Interface

- Abstract methods only
- Abstract methods are **_specifications_** consisting of a signature but no body
- Cannot be instantiated as objects (cannot be executed)
- `implements` keyword for inheriting from interfaces
- All methods within an interface are `public` by default

```Java
public interface GraphicalEntity{
  // get the shape's area
  public float getArea();

  // get the shape's perimeter
  public float getPerimeter();
}

public class Rectangle implements GraphicalEntity{
  private float length;
  private float width;

  public Rectangle(float l, float w){
    this.length = l;
    this.width = w;
  }

  public float getArea(){
    return length * width;
  }
  public float getPerimeter(){
    return length + width * 2;
  }
}
```
