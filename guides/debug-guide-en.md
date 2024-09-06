# Debugging and Fixing Code in Java

## Introduction

Debugging is a crucial skill for any programmer. Being able to debug your code autonomously allows you to efficiently identify and fix issues without relying on others. This skill not only improves your problem-solving capabilities but also enhances your understanding of how your code operates. In this guide, we will explore various types of errors, strategies for diagnosing and fixing issues, and tools available in IntelliJ IDEA.

## Compilation Errors

### Understanding Compilation Errors

Compilation errors occur when the Java compiler encounters issues with your code that prevent it from converting your source code into bytecode. These errors are often syntax-related or involve incorrect use of language features.

#### Common Compilation Errors

1. **Syntax Errors**: These occur when the code does not follow the correct syntax. For example:
    ```java
    public class Main {
        public static void main(String[] args) {
            System.out.println("Hello, World!")
        }
    }
    ```
    *Error*: Missing semicolon at the end of the `println` statement.
    
    **Compiler Message**:
    ```
    Main.java:4: error: ';' expected
        System.out.println("Hello, World!")
                                        ^
    1 error
    ```

2. **Type Mismatch**: Occurs when there is an attempt to assign or use a variable of the wrong type.
    ```java
    int number = "string";
    ```
    *Error*: Incompatible type.

    **Compiler Message**:
    ```
    Main.java:2: error: incompatible types: String cannot be converted to int
        int number = "string";
                       ^
    1 error
    ```

3. **Non-static Method Call from Static Context**: Occurs when a non-static method is called from a static context.
    ```java
    public class Main {
        public void display() {
            System.out.println("Hello");
        }
        
        public static void main(String[] args) {
            display(); // Error here
        }
    }
    ```
    *Error*: Non-static method display() cannot be referenced from a static context.

    **Compiler Message**:
    ```
    Main.java:7: error: non-static method display() cannot be referenced from a static context
        display(); // Error here
        ^
    1 error
    ```

Thankfully compiler messages are usually very descriptive so **be sure to use them to your advantage!**

## Runtime Errors

### Common Runtime Errors

Runtime errors occur while the program is running. These can be harder to detect because they do not stop the compilation process but cause the program to behave unexpectedly.

#### Examples of Runtime Errors

1. **Null Pointer Exception**: This occurs when you try to use an object reference that has not been initialized.
    ```java
    String str = null;
    System.out.println(str.length());
    ```
    *Error*: `NullPointerException`

2. **ArrayIndexOutOfBoundsException**: Occurs when accessing an array with an invalid index.
    ```java
    int[] arr = new int[5];
    System.out.println(arr[10]);
    ```
    *Error*: `ArrayIndexOutOfBoundsException`

3. **ArithmeticException**: Happens during arithmetic operations, such as division by zero.
    ```java
    int result = 10 / 0;
    ```
    *Error*: `ArithmeticException`

4. **ClassCastException**: Occurs when trying to cast an object to a type that it isn't an instance of.
    ```java
    Object obj = "Hello";
    Integer num = (Integer) obj;
    ```
    *Error*: `ClassCastException`

### Identifying and Fixing Runtime Errors

- **Use Exception Stack Traces**: The stack trace provides information about where the error occurred. For example:
    ```
    Exception in thread "main" java.lang.NullPointerException
        at Main.main(Main.java:4)
    ```
    *Usage*: The line `Main.java:4` indicates that the error occurred at line 4 of `Main.java`. Check this line for potential issues, such as using an uninitialized variable.

- **Check Input Values**: Validate inputs to avoid invalid operations.
- **Add Debug Statements**: Print statements can help track the flow and values of variables.

Similar to Compiler messages, Exception Stack Traces are very useful in allowing you to diagnose and fix your code quickly.

## Diagnosing and Fixing Buggy Code

### Strategies for Debugging

1. **Use Debugger Tools**: Set breakpoints and step through your code to observe its execution. 

   **IntelliJ IDEA Debugging Tutorial**:
   - **Set Breakpoints**: Click in the left margin next to the line numbers in the editor to set breakpoints.
     
     ![Set Breakpoints](../images/image1.png "Setting a breakpoint")
     
   - **Start Debugging**: Click on the Debug icon (a bug) in the top-right corner of the IDE.

     ![Start Debugging](../images/image2.png)

   - **Use Debug Tool Window**: Inspect variables, step over lines, and evaluate expressions using the Debug tool window.
     
     ![Debug Tool Window](../images/image3.png)
     

2. **Print Statements**: Add print statements to check the values of variables and program flow.
    ```java
    System.out.println("Value of x: " + x);
    ```

3. **Explain Code to Someone**: Explaining your code to someone else can help you realize what the error might be.

### Improving Bug Hunting Skills

- **Develop a Systematic Approach**: Follow a step-by-step method to track down bugs, starting from reproducing the issue to identifying the root cause.
- **Keep a Debugging Checklist**: Maintain a checklist of common issues and solutions to streamline your debugging process.

## Reproducing Crash Situations in Games

When programming, you might need to quickly reproduce crash situations to debug issues -especially if the issue takes a while to reproduce normally (e.g. Having to play through the entirety of a game when the bug occurs at the end)-.

### Techniques for Reproducing Crashes

1. **Create Test Cases**: Write specific scenarios or test cases that simulate the conditions leading to the crash.
2. **Use Debugging Tools**: Employ IntelliJ’s debugging features to simulate different game states and interactions.
3. **Isolate Problematic Code**: Identify and isolate the parts of the code related to the crash and test them independently.
4. **Hard Code Variables**: Set relevant variables in order to expedite the process of reproducing the bug.

By following these techniques, you can quickly locate and address crashes, making your debugging process more efficient.

## Conclusion

Being proficient in debugging and fixing code is essential for any developer. By understanding common errors, utilizing effective strategies, and leveraging the tools available in IntelliJ IDEA, you can become a more efficient and autonomous programmer. Practice these skills regularly to improve your debugging capabilities and handle issues with confidence.

## footnote

There might be oversights or mistakes, feel free to contact me at mehdi.alaoui@epfl.ch if there are any corrections or relevant additions to be made :-)