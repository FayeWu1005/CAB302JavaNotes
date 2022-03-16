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

- Importance
  1. each implementation is very different
  1. act as contract
     - each implementing clas **HAS** to provide implementation
     - calling class knows that method is being implemented
  1. multiple inheritance: a Java class can only **extend** one class, while you can implement any number of interfaces

#### 8.2 Abstract class

> Abstract class is a class that implements some **member fields** and **methods** but leaves others abstract

- `abstract` keyword
- child class **must** implement abstract classes but don't have to implement non-abstract classes
- cannot be instantiated

```Java
public abstract class FileReader{
  private String filename;

  public Filereader(String fn){
    this.filename = fn;

    public String getFilename(){
      return filename;
    }

    public abstract void readFile();
  }
}

public class CSVReader extends FileReader{
  public CSVReader(String fn){
    super(fn);
  }

  public void readFile(){
    /* code for read CSV file */
  }
}

```

- Importance
  1. shred fields and methods
  2. benefits of OOP
  3. no need for subclasses to implement non-abstract method

### 9. Polymorphism

- Apply the same operation on different types with common ancestor in the type hierarchy
- making common operations available in an identical form in other different classes
- `override`

### 10. Enumerate

- A special class type whose fields are **constants**
- `enum` keyword

```Java
public class EnumExample{
  public enum Day{
  SUNDAY,
  MONDAY,
  TUESDAY,
  WEDNESDAY,
  THURSDAY,
  FRIDAY,
  SATURDAY
}

public static void printDayGreeting(Day day){
  if(day == Day.FRIDAY){
    System.out.println("It's Friday!");
  }else{
    System.out.println("Some other day");
  }
}

public static void main(String[] agrs){
  Day myDay = Day.THURSDAY;

  printDayGreeting(myDay);
}
}

// output: Some other day

```

- `values` method can be used in **for** loops

```Java
for(Day d: Day.values()){
  printDayGreeting(d);
}
```

- `enum` classes can have other fields and methods
- each constant can have a value(s) associated with it when it is declared
- the value is passed to the constructor when an `enum` object is created

```Java
public enum Planet{
  MERCURY (3.7),
  VENUS (8.87),
  EARTH (9.799);

  private double gravity;

  public Planet(double gravity){
    this.gravity = gravity;
  }
  public double getGravity(){
    return gravity;
  }
  public static void main(String[] args){
    for(Planet p: Planet.values()){
      System.out.println(p.getGravity());
    }
  }
}
```
