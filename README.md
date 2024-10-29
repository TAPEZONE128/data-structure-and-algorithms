# Data Structure And Algorithm

Submission Compilation <br>
1. [Activity01](https://github.com/TAPEZONE128/intermediate-programming/blob/main/Activity01.ipynb) // python
2. [Activity02](https://github.com/TAPEZONE128/data-structure-and-algorithms/blob/main/Hworld.java) // avg
3. [Activity03](https://github.com/TAPEZONE128/data-structure-and-algorithms/blob/main/ATM.java) // atm

---

## Contents
- [Stacks](#stacks)
  - Array vs. Linked List
  - Recursion

---


## Stacks
- A **stack** is a linear data structure that operates on a **Last In, First Out (LIFO)** principle. This means that the most recently added item is the first to be removed, with all operations (insertion and deletion) occurring at one end, referred to as the **top** of the stack.

### Key Characteristics
- **LIFO Order**: Elements are added and removed from the same end; the last element added is the first to be removed.
- **Single Access Point**: Operations are performed only at the top.
- **Common Use Cases**: Ideal for scenarios where elements must be stored and retrieved in reverse order, such as a stack of plates, browser history, or undo functionality.

## Stack as an Abstract Data Type (ADT)
Stacks support specific operations, represented in the table below:

| Operation        | Description                                                                                  |
|------------------|----------------------------------------------------------------------------------------------|
| `CreateEmptyStack(S)` | Initializes `S` as an empty stack.                                                      |
| `Push(S, x)`     | Adds element `x` to the top of the stack `S`.                                               |
| `Pop(S)`         | Removes the element at the top of `S`.                                                      |
| `Top(S)`         | Returns the top element of the stack without removing it.                                   |
| `IsFull(S)`      | Checks if `S` is full (only applicable if stack has a maximum capacity).                    |
| `IsEmpty(S)`     | Checks if `S` is empty.                                                                     |

### Stack Overflow and Underflow
- **Stack Overflow**: Occurs when trying to push an element onto a full stack.
- **Stack Underflow**: Happens when attempting to pop an element from an empty stack.

## Implementing a Stack Using Linked Lists
Stacks can be implemented as **linked lists**, where each node contains:
- **Data**: Holds the value of the element.
- **Pointer**: Points to the next element in the list.

### Array vs. Linked List Implementation
| Feature                    | Array-based Stack          | Linked List-based Stack               |
|----------------------------|----------------------------|---------------------------------------|
| **Size Limit**             | Fixed size                 | Dynamic, grows as needed              |
| **Memory Usage**           | Pre-allocated              | Allocated as elements are added       |
| **Performance**            | Faster access time        | Slower due to pointer traversal       |
| **Complexity**             | Simpler to implement      | More complex due to pointers          |

## Applications of Stacks
1. **Expression Evaluation**: Stacks are helpful in evaluating arithmetic expressions, especially those in **prefix** (Polish notation) and **postfix** (Reverse Polish Notation) formats.
2. **Function Call Management**: Stacks manage function calls, especially for **recursive** functions.
3. **Undo Mechanisms**: Used in applications like text editors, where the last action can be undone.
4. **Syntax Parsing**: Compilers use stacks for syntax analysis in expressions with nested operations.

## Expression Conversion Using Stacks
### Infix to Postfix Conversion
Infix expressions (e.g., `A + B * C`) are converted to postfix (RPN) for easier evaluation by computers. Conversion is done based on operator precedence.

#### Steps in the Algorithm
1. **Initialize two stacks**: `opstack` for operators and `poststack` for the postfix output.
2. **Scan each character** of the infix expression from left to right.
3. Handle each character based on its type:
   - **'('**: Push to `opstack`.
   - **Operand**: Push directly to `poststack`.
   - **Operator**: Pop operators from `opstack` to `poststack` until an operator with lower precedence is found, then push the current operator.
   - **')'**: Pop from `opstack` to `poststack` until '(' is found.
4. **End of Expression**: Pop any remaining operators from `opstack` to `poststack`.

#### Example Conversions

| Infix Expression | Postfix Expression | Explanation                                                                                         |
|------------------|--------------------|-----------------------------------------------------------------------------------------------------|
| `A * B + C`      | `A B * C +`       | `*` has higher precedence than `+`, so `A B *` is evaluated first, followed by `C +`.              |
| `A * (B + C)`    | `A B C + *`       | Parentheses change precedence, so `B + C` is evaluated first, then `A *` with the result.          |

### Example Conversion Table for `A * B + C`
| Current Symbol | `opstack` | `poststack` |
|----------------|-----------|-------------|
| A              |           | A           |
| *              | *         | A           |
| B              | *         | AB          |
| +              | +         | AB*         |
| C              | +         | AB*C        |
| End            |           | AB*C+       |

## Recursion and Stacks
**Recursion** is a process where a function calls itself until a base condition is met. Stacks are essential for managing recursive calls, storing each function call until it completes.

### Requirements for Recursive Solutions
1. **Recursive Definition**: The problem should be defined in terms of smaller instances of itself.
2. **Base Condition**: Specifies the stopping point to prevent infinite recursion.

### Factorial of an Integer Using Recursive Function
- A **factorial** of a non-negative integer `n` (denoted as `n!`) is the product of all positive integers less than or equal to `n`. For example, `5!` (factorial of 5) is calculated as `5 * 4 * 3 * 2 * 1 = 120`.

## Recursive Approach to Calculate Factorial

The recursive definition of a factorial is:
- **Base Case**: `factorial(0) = 1`
- **Recursive Case**: `factorial(n) = n * factorial(n - 1)`

Below is a Java implementation of a recursive factorial function, alongside a breakdown of the recursive calls for `factorial(5)`.


| Code                                       | Factorial Recursive Function Breakdown         |
|--------------------------------------------|------------------------------------------------|
| int factorial(int n) {                     | factorial(5) = 5 * factorial(4)                |
|    if (n == 0) {                           |            = 5 * (4 * factorial(3))            |
|      return 1;                             |            = 5 * (4 * (3 * factorial(2)))      |
|    } else {                                |            = 5 * (4 * (3 * (2 * factorial(1))))|
|      return n * factorial(n - 1);          |            = 5 * (4 * (3 * (2 * (1 * factorial(0)))))|
|    }                                       |            = 5 * 4 * 3 * 2 * 1                 |
|  }                                         |            = 120                               |



### Pros and Cons of Recursion
- **Pros**:
  - Simplifies code for certain problems, such as the **Tower of Hanoi** or tree traversals.
- **Cons**:
  - Generally slower than iterative solutions due to function call overhead.
  - Uses more memory as it requires stack space for each call.

### Recursive vs. Iterative Approach
| Approach      | Pros                        | Cons                                           |
|---------------|-----------------------------|------------------------------------------------|
| **Recursive** | Cleaner, easier to implement| Higher memory usage, slower for large problems |
| **Iterative** | Faster, more memory-efficient | More complex for some problems                |

