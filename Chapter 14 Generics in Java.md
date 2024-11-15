### In-depth Study Material for Chapter 14: Generics in Java

#### Introduction to Generics

- **Generics** (parameterized types) in Java allow you to write code that can work with different types of data without having to specify those types explicitly at compile time. They are essentially placeholders for concrete types that are determined when the code is used.
    
- **Benefits of Generics:**
    
    - **Type safety:** Generics eliminate the need for explicit type casting, reducing the risk of runtime errors. The compiler can verify the type compatibility at compile time, enhancing code reliability.
    - **Code reusability:** You can write more generic algorithms and data structures that can operate on a variety of types without the need to create separate versions for each type.

#### Generic Classes

- **Definition:** A generic class is defined with one or more type parameters enclosed in angle brackets (e.g., `<T>`). These type parameters act as placeholders for actual types that will be specified when an instance of the class is created.
    
- **General Form:**
    
    ```java
    class class-name<type-param-list> {
        // ...
    }
    ```
    
- **Example:** A Generic Stack Class
    
    ```java
    class Stack<T> {
        private int size;
        private T[] stackArray;
        private int top;
    
        public Stack(int s) {
            size = s;
            stackArray = (T[]) new Object[size]; // Type casting required
            top = -1;
        }
    
        public void push(T item) {
            stackArray[++top] = item;
        }
    
        public T pop() {
            return stackArray[top--];
        }
    
        public boolean isEmpty() {
            return (top == -1);
        }
    
        public boolean isFull() {
            return (top == size - 1);
        }
    }
    ```
    

#### Bounded Type Parameters

- **Purpose:** You can restrict the types that can be used as type arguments for a generic class or method by using bounded type parameters.
    
- **Syntax:**
    
    ```java
    <T extends upperbound>
    ```
    
    - `T` is the type parameter.
    - `upperbound` is the upper bound, which can be a class or an interface.
- **Example:** A generic class that operates only on numbers or their subclasses:
    
    ```java
    class Stats<T extends Number> {
        T[] nums;
    
        Stats(T[] nums) {
            this.nums = nums;
        }
    
        double average() {
            double sum = 0.0;
            for(int i=0; i < nums.length; i++)
                sum += nums[i].doubleValue(); // Using Number class methods
            return sum / nums.length;
        }
    }
    ```
    
- **Explanation:** In the `Stats` class, the type parameter `T` is bounded by `Number`, meaning that only types that are `Number` or its subclasses (like `Integer`, `Double`, etc.) can be used as type arguments. The code uses the `doubleValue()` method from the `Number` class.
    

#### Bounded Wildcards

- **Purpose:** Bounded wildcards provide flexibility when you need to work with generic types where the specific type argument is not known in advance.
    
- **Syntax:**
    
    ```java
    <? extends upperbound>  // Upper bounded wildcard
    <? super lowerbound>     // Lower bounded wildcard
    ```
    
- **Example:**
    
    ```java
    class Gen<T> {
        T ob;
    
        Gen(T o) {
            ob = o;
        }
    
        // Return ob.
        T getOb() {
            return ob;
        }
    }
    
    class GenDemo {
        //  Method that operates on Gen objects with type arguments
        //  bounded by A or a subclass of A.
        static void test(Gen<? extends A> o) {
            // ...
        }
    }
    ```
    
    - **Explanation:** The `test()` method accepts a `Gen` object whose type argument is `A` or a subclass of `A`. The wildcard `? extends A` ensures that the method can handle a range of `Gen` objects with compatible type arguments.

#### Generic Methods

- **Definition:** A generic method is a method that has its own type parameters, separate from the type parameters of the class it might belong to.
    
- **Purpose:** Allows you to write methods that can operate on different types of data without needing to be part of a generic class.
    
- **Syntax:**
    
    ```java
    <type-param-list> return-type method-name(parameter-list) {
        // ...
    }
    ```
    
- **Example:** A Generic Method to Print an Array
    
    ```java
    // Generic method printArray
    public static <E> void printArray(E[] inputArray ) {
        // Display array elements
        for ( E element : inputArray ){
            System.out.print(" " + element);
        }
        System.out.println();
    }
    ```
    
    - **Explanation:** The `printArray()` method uses the type parameter `E` to represent the type of the array elements. This allows the method to work with arrays of any type (Integer, Double, Character, etc.). The code iterates through the array using an enhanced for loop and prints each element.

#### Generic Interfaces

- **Definition:** A generic interface is an interface that is declared with type parameters.
    
- **Purpose:** Generic interfaces allow you to define contracts that can be implemented by classes with different type parameters.
    
- **Syntax:**
    
    ```java
    interface interface-name<type-param-list> {
        // ...
    }
    ```
    
- **Example:** A Containment Interface
    
    ```java
    // Generic interface Containment
    interface Containment<T> {
        boolean contains(T o);
    }
    ```
    
    - **Explanation:** The `Containment` interface is declared with a type parameter `T`. Any class that implements this interface must provide an implementation for the `contains()` method, which determines whether the object contains a given value of type `T`.

#### Key Points about Implementing Generic Interfaces

- **Generic Implementation:** A class implementing a generic interface must also be generic, providing its own type parameter that matches the interface's type parameter.
- **Specific Type Implementation:** If a class implements a specific type of a generic interface (e.g., `Containment<Double>`), the implementing class does not need to be generic.

#### Example: Implementing the Containment Interface

```java
// Implement Containment using a generic class.
class MyClass<T> implements Containment<T> {
    T[] arrayRef;

    MyClass(T[] o) {
        arrayRef = o;
    }

    // Implement contains().
    public boolean contains(T o) {
        for(T x : arrayRef)
        if(x.equals(o))
            return true;
        return false;
    }
}
```

- **Explanation:** The `MyClass` class is generic and implements the `Containment` interface. It uses the type parameter `T` to specify the type of elements in the array `arrayRef`. The `contains()` method iterates through the array and checks if the given object `o` is present.

#### Conclusion

Generics are a powerful feature in Java that enhance type safety, code reusability, and overall code quality. This in-depth study material has covered the fundamental aspects of generics, including generic classes, bounded type parameters, wildcards, generic methods, and generic interfaces. Understanding these concepts is crucial for writing robust and flexible Java code.