**Chapter 3 focuses on the statements that control the flow of execution in a Java program.**

#### Control Statements: Overview

The sources categorize Java's control statements into:

- **Selection Statements**: These statements allow you to choose different paths of execution based on conditions. Examples include:
    
    - `if`, `else if`, `else`: Used for conditional branching.
    - `switch`: Provides multi-way branching based on the value of an expression.
- **Iteration Statements**: These statements enable you to repeat blocks of code. Examples include:
    
    - `while`: Executes a block of code as long as a condition is true.
    - `do-while`: Similar to `while`, but the code block is executed at least once before the condition is checked.
    - `for`: A versatile loop structure commonly used for iterating a specific number of times.
    - `for-each`: A specialized loop designed for iterating over elements in arrays and collections.
- **Jump Statements**: These statements alter the flow of execution by transferring control to a different part of the program. Examples include:
    
    - `break`: Used to exit a loop prematurely.
    - `continue`: Skips the remaining statements in the current loop iteration and proceeds to the next iteration.
    - `return`: Exits a method, optionally returning a value.

#### Selection Statements

##### The `if` Statement

The `if` statement executes a block of code only if a specified condition is true. The sources detail the complete form of the `if` statement:

```java
if (condition) {
    statement1;
    // ...
} else {
    statement2;
    // ...
}
```

- `condition`: A boolean expression that determines whether the code block is executed.
- `statement1`: The code block that is executed if the condition is true.
- `statement2` (optional): The code block that is executed if the condition is false.

The `else` clause is optional. If it is omitted and the condition is false, the `if` statement does nothing.

You can chain multiple `if` statements together using `else if` clauses to create more complex decision structures:

```java
if (x > y) {
    System.out.println("x is greater than y");
} else if (y > z) {
    System.out.println("y is greater than z");
} else {
    System.out.println("Neither x nor y is greater than the other values");
}
```

##### The `switch` Statement

The `switch` statement allows you to select one block of code to execute from a set of multiple code blocks, based on the value of an expression. The general form of the `switch` statement is as follows:

```java
switch (expression) {
    case value1:
        // Code to be executed if expression equals value1
        break;
    case value2:
        // Code to be executed if expression equals value2
        break;
    // ... more cases
    default:
        // Code to be executed if expression does not match any case
}
```

- `expression`: An expression whose value is evaluated. The value of the expression must be of type `byte`, `short`, `char`, `int`, `String`, or an `enum` type.
- `case value1`, `case value2`, etc.: Each `case` label specifies a possible value that the `expression` might match.
- `break`: The `break` statement is crucial. It causes execution to exit the `switch` block after a matching case is found. If you omit the `break`, execution will "fall through" to the next case.
- `default` (optional): The `default` case is executed if none of the other cases match the expression.

#### Iteration Statements (Loops)

##### The `while` Loop

The `while` loop repeatedly executes a block of code as long as a specified condition remains true. The syntax is:

```java
while (condition) {
    // Code to be executed repeatedly
}
```

- `condition`: A boolean expression that is evaluated before each iteration. The loop continues to execute as long as the condition is true.

##### The `do-while` Loop

The `do-while` loop is similar to the `while` loop, but it ensures that the code block is executed at least once before the condition is checked. The syntax is:

```java
do {
    // Code to be executed repeatedly
} while (condition);
```

- `condition`: A boolean expression evaluated after each iteration. The loop continues as long as the condition is true.

##### The `for` Loop

The `for` loop is a powerful looping structure that is often used for iterating a specific number of times. The general syntax is:

```java
for (initialization; condition; iteration) {
    // Code to be executed repeatedly
}
```

- `initialization`: Executed only once, before the first iteration. Typically used to initialize a loop counter variable.
- `condition`: Evaluated before each iteration. The loop continues to execute as long as the condition is true.
- `iteration`: Executed after each iteration. Typically used to increment or decrement the loop counter variable.

##### The `for-each` Loop

The `for-each` loop is a simplified way to iterate over elements in arrays and collections. The syntax is:

```java
for (type element : collection) {
    // Code to be executed for each element
}
```

- `type`: The data type of the elements in the collection.
- `element`: A variable that receives each element of the collection in turn.
- `collection`: The array or collection to iterate over.

#### Jump Statements

##### `break` Statement

- The `break` statement is primarily used to exit loops prematurely. When `break` is encountered inside a loop, the loop terminates immediately, and execution resumes at the statement following the loop.
- The sources provide an example using `break` with nested loops to terminate the outer loop when a specific condition is met:

```java
outer: for (int i = 0; i < 3; i++) {
    System.out.print("Pass " + i + ": ");
    for (int j = 0; j < 100; j++) {
        if (j == 10) {
            break outer; // Exit both loops
        }
        System.out.print(j + " ");
    }
    System.out.println("This will not print"); // Not reached
}
System.out.println("Loops complete.");
```

##### `continue` Statement

- The `continue` statement skips the remaining statements in the current loop iteration and proceeds directly to the next iteration.

```java
int x = 0;
while (x < 10) {
    x++;
    if (x % 2 == 0) {
        continue; // Skip even numbers
    }
    System.out.println(x); // Print odd numbers
}
```

##### `return` Statement

- The `return` statement is used to exit a method. It can optionally return a value to the caller of the method. If a method has a non-void return type, you must use a `return` statement to return a value of that type.

#### Important Considerations

- **Nested Loops**: You can nest loops within each other to create more complex iteration patterns. When using `break` or `continue` in nested loops, you can use labels to specify which loop you want to affect.
- **Indentation**: Proper indentation is crucial for readability and understanding the structure of your code. Although the Java compiler does not require specific indentation, it is a good practice to indent code blocks to make the code more readable.
- **Exercises**: Practice is essential for mastering program control statements. The sources suggest exercises like finding the sum of natural numbers, calculating the greatest common divisor (GCD), checking for palindromes, and printing patterns of stars.

#### Key Takeaways

- **Control flow statements are fundamental to structuring the logic of your Java programs.**
- **Selection statements allow you to make decisions based on conditions.**
- **Iteration statements enable you to repeat blocks of code efficiently.**
- **Jump statements provide flexibility in controlling the flow of execution.**
- **Understanding how to use these statements effectively is essential for writing well-structured and maintainable Java programs.**