### Chapter 4: Introducing Classes, Objects, and Methods

**Chapter 4 introduces the foundational concepts of object-oriented programming (OOP) in Java, focusing on classes, objects, methods, and constructors.**

#### Class Fundamentals

- **Classes as Blueprints**: Classes serve as templates or blueprints for creating objects. They define the structure and behavior of objects.
- **Objects as Instances**: Objects are concrete realizations of a class. A class can be used to create multiple objects, each with its own unique data.
- **Encapsulation**: Well-designed classes group data (instance variables) and the methods that operate on that data, promoting modularity and data protection.

#### Class Structure

The sources provide a general form for defining a class:

```java
class ClassName {
    // Instance Variable Declarations
    type variableName1;
    type variableName2;
    // ...

    // Constructor Declarations
    ClassName(parameters) {
        // Constructor body (initializes the object)
    }

    // Method Declarations
    returnType methodName(parameters) {
        // Method body (code to be executed)
    }
    // ... more methods
}
```

- **Instance Variables**: Variables declared within a class, but outside any method. Each object of the class has its own copy of these variables.
- **Constructors**: Special methods used to initialize objects when they are created using the `new` keyword. A constructor has the same name as the class and does not have a return type (not even `void`).
- **Methods**: Functions defined within a class that operate on the object's data. Methods have a return type (which can be `void` if the method doesn't return a value) and may take parameters (input values).

#### Example: The `Vehicle` Class

The sources use a `Vehicle` class as an example to illustrate these concepts:

```java
class Vehicle {
    int passengers;  // Number of passengers
    int fuelCap;     // Fuel capacity in gallons
    int mpg;         // Miles per gallon

    // Constructor (initializes a Vehicle object)
    Vehicle(int p, int f, int m) {
        passengers = p;
        fuelCap = f;
        mpg = m;
    }

    // Method to calculate the range
    void range() {
        System.out.println("Range: " + fuelCap * mpg);
    }
}
```

To create and use objects of the `Vehicle` class:

```java
class VehicleDemo {
    public static void main(String[] args) {
        // Create a Vehicle object named 'car'
        Vehicle car = new Vehicle(5, 12, 25);

        // Create another Vehicle object named 'van'
        Vehicle van = new Vehicle(7, 24, 21);

        // Call the range() method on the 'car' object
        car.range();  // Output: "Range: 300"

        // Access instance variables
        System.out.println("Van's fuel capacity: " + van.fuelCap); // Output: "Van's fuel capacity: 24"
    }
}
```

#### Key Concepts

- **Object Creation (`new`)**: The `new` operator allocates memory for an object and calls the constructor to initialize it, returning a reference to the newly created object.
- **Methods and Parameters**: Methods can take parameters, which are variables used to pass values into the method.
- **Return Values**: Methods can return values to the caller. The return type of the method specifies the type of value that will be returned.
- **The `this` Keyword**: The `this` keyword refers to the current object within a method. It's useful for disambiguating instance variables from parameters or local variables with the same name.

#### Additional Topics

- **Garbage Collection**: Java automatically reclaims memory occupied by objects that are no longer in use, simplifying memory management.
- **Exercises**: The chapter includes exercises that encourage you to practice defining classes, creating objects, and using methods and constructors.

Please let me know if you have any further questions or if you'd like me to elaborate on any specific aspects of Chapter 4.