### In-depth Study Material for Chapter 7: Inheritance in Java

#### Inheritance Fundamentals

- **Concept:** Inheritance is a fundamental principle of object-oriented programming (OOP) that enables you to create new classes (subclasses) based on existing classes (superclasses). Subclasses inherit the characteristics (variables and methods) of their superclasses, promoting code reusability and a hierarchical organization of classes.
    
- **Key Terminology:**
    
    - **Superclass (Base Class, Parent Class):** The class being inherited from.
    - **Subclass (Derived Class, Child Class):** The class that inherits from the superclass.
    - **`extends` Keyword:** Used to indicate that a subclass inherits from a superclass.
- **Benefits of Inheritance:**
    
    - **Code Reusability:** Subclasses inherit the functionality of superclasses, reducing code duplication.
    - **Hierarchical Organization:** Inheritance creates a clear relationship between classes, making code easier to understand and maintain.
    - **Polymorphism:** Enables you to use objects of different classes in a uniform way.
- **Basic Syntax:**
    
    ```java
    class Subclass extends Superclass {
        // Subclass members (variables and methods)
    }
    ```
    

#### Example: Inheritance in Action

```java
class OneDimPoint {
    int x = 3;
    int getX() { return x; }
}

class TwoDimPoint extends OneDimPoint {
    int y = 4;
    int getY() { return y; }
}

class TestInherit {
    public static void main(String[] args) {
        TwoDimPoint pt = new TwoDimPoint();
        System.out.println(pt.getX() + "," + pt.getY()); // Output: 3,4
    }
}
```

- **Explanation:**
    
    - `OneDimPoint` represents a point in one dimension (with an `x` coordinate).
    - `TwoDimPoint` extends `OneDimPoint`, inheriting the `x` variable and `getX()` method. It adds the `y` variable and `getY()` method to represent a point in two dimensions.
    - In `TestInherit`, a `TwoDimPoint` object `pt` can access both `getX()` and `getY()`.

#### Member Access and Inheritance

- **Private Members:** Private members of a superclass are not directly accessible to its subclasses. Inheritance does not override private access restrictions.
- **Accessing Private Members:** Subclasses can access private members of the superclass indirectly through public or protected methods provided by the superclass.

#### Constructors and Inheritance

- **Constructor Execution Order:** When a subclass object is created, both the superclass and subclass constructors are executed. The superclass constructor is executed first.
    
- **`super` Keyword:**
    
    - Used to call a superclass constructor from within a subclass constructor.
    - Must be the first statement inside a subclass constructor if used.
- **Syntax for Calling Superclass Constructor:**
    
    ```java
    super(parameter-list);
    ```
    
- **Example:**
    
    ```java
    class TwoDShape {
        private double width;
        private double height;
    
        TwoDShape() { // Default constructor
            width = height = 0.0;
        }
    
        TwoDShape(double w, double h) { // Parameterized constructor
            width = w;
            height = h;
        }
    }
    
    class Triangle extends TwoDShape {
        String style;
    
        Triangle(String s, double w, double h) {
            super(w, h); // Call superclass constructor
            style = s;
        }
    }
    ```
    

#### Using `super` to Access Hidden Superclass Members

- **Name Hiding:** When a subclass member has the same name as a superclass member, the subclass member "hides" the superclass member.
    
- **`super.member`:** You can use `super.member` to access the hidden superclass member (method or variable).
    
- **Example:**
    
    ```java
    class A {
        int i;
    }
    
    class B extends A {
        int i; // Hides 'i' in class A
    
        B(int a, int b) {
            super.i = a; // 'i' in class A
            i = b;       // 'i' in class B
        }
    
        void show() {
            System.out.println("i in superclass: " + super.i);
            System.out.println("i in subclass: " + i);
        }
    }
    ```
    

#### Creating a Multilevel Hierarchy

- Inheritance can be extended to multiple levels, forming a hierarchy of classes.
- Constructors in a class hierarchy execute from superclass to subclass.

#### Superclass References and Subclass Objects

- **Key Concept:** A reference variable of a superclass type can refer to an object of any of its subclasses. This is a fundamental concept related to polymorphism.
    
- **Example:**
    
    ```java
    class X {
        int a;
        X(int i) { a = i; }
    }
    
    class Y extends X {
        int b;
        Y(int i, int j) {
            super(j);
            b = i;
        }
    }
    
    class SupSubRef {
        public static void main(String args[]) {
            X x = new X(10);
            X x2;
            Y y = new Y(5, 6);
    
            x2 = x;  // OK, both are of type X
            x2 = y;  // Still OK because Y is a subclass of X
        }
    }
    ```
    

#### Method Overriding

- **Concept:** Method overriding allows a subclass to provide a specific implementation for a method that is already defined in its superclass. The subclass method "overrides" the superclass method.
    
- **Key Points:**
    
    - The overriding method must have the same name, return type, and parameters as the superclass method.
    - It provides a way to specialize the behavior of inherited methods.
- **Example:**
    
    ```java
    class A {
        int i, j;
        A(int a, int b) {
            i = a;
            j = b;
        }
    
        void show() {
            System.out.println("i and j: " + i + " " + j);
        }
    }
    
    class B extends A {
        int k;
        B(int a, int b, int c) {
            super(a, b);
            k = c;
        }
    
        // Override show() in A
        void show() {
            System.out.println("k: " + k);
        }
    }
    ```
    

#### Method Overriding and Polymorphism

- **Dynamic Method Dispatch:** When an overridden method is called through a superclass reference, the JVM determines at runtime which version of the method to execute based on the actual object type (subclass). This is known as dynamic method dispatch.
- **Polymorphism:** Method overriding, along with dynamic method dispatch, is a key mechanism for achieving polymorphism, allowing you to use objects of different classes in a uniform way.

#### Abstract Classes

- **Concept:** An abstract class is a class that cannot be instantiated (you can't create objects of an abstract class). It serves as a blueprint for subclasses, defining common methods and variables that subclasses must implement or override.
    
- **`abstract` Keyword:** Used to declare abstract classes and methods.
    
- **Abstract Methods:** Abstract methods are declared without a body (implementation). Subclasses must provide concrete implementations for abstract methods.
    
- **Example:**
    
    ```java
    abstract class Figure {
        double dim1;
        double dim2;
    
        Figure(double a, double b) {
            dim1 = a;
            dim2 = b;
        }
    
        // Area is abstract.
        abstract double area();
    }
    
    class Rectangle extends Figure {
        Rectangle(double a, double b) {
            super(a, b);
        }
    
        // Override area() for Rectangle
        double area() {
            System.out.println("Inside Area for Rectangle.");
            return dim1 * dim2;
        }
    }
    ```
    

#### The `final` Keyword

- **`final` Classes:** A `final` class cannot be subclassed.
- **`final` Methods:** A `final` method cannot be overridden by subclasses.
- **`final` Variables:** A `final` variable is a constant (its value cannot be changed).

The sources you provided don't go into detail on some advanced OOP concepts related to Chapter 7, such as:

- **Covariant return types:** Allowing an overriding method to return a more specific type than the overridden method.
- **Using `super` in a constructor's parameter list:** Passing values directly to the superclass constructor from the subclass constructor.

If you're looking for deeper coverage of these advanced topics, you might need to consult additional Java programming resources.