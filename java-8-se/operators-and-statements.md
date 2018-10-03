---
description: 0422-0430
---

# Operators and Statements

## Exam objectives

1. Using Operators and Decision Constructs
   * Use Java operators; including parentheses to override operator precedence
   * Create if and if/else and ternary constructs
   * Use a switch statement
2. Using Loop Constructs
   * Create and use while loops 
   * Create and use for loops including the enhanced for loop
   * Create and use do/while loops
   * Compare loop constructs
   * Use break and continue

## Notes

### Understanding Java Operators

* Java _operator_ is a special symbol that can be applied to a set of variables, values, of literals - referred to as operands and that return a result.
* Types:
  * Unary
  * Binary
  * Ternary
* Operators are not necessarily evaluated from left-to-right order. 
* Unless overridden with parentheses, operators follow _order of operation_ by decreasing order of operator precedence. If two operators have the same level of precedence, Java guarantees left-to-right evaluation.

| Operator | Symbols and examples |
| :--- | :--- |
| Other unary operators | +, -, ! |
| Multiplication/Division/Modulus | \*,/,% |
| Addition/Subtraction | +,- |
| Shift operators | &lt;&lt;,&gt;&gt;,&gt;&gt;&gt; |
| Relational operators | &lt;,&gt;,&lt;=,&gt;=,instanceof |
| Equal to/ not equal to | ==, != |
| Logical operators | &,^,\| |
| Short-circuit logical operators | &&,\|\| |
| Ternary operators | boolean expression ? expression1 : expresssion2 |
| Assignment operators | =, +=, -=., \*=, /=, %=, &=, ^=, !=, &lt;&lt;=, &gt;&gt;=, &gt;&gt;&gt;= |

### Working with Binary Arithmetic Operators

#### Arithmetic Operators

* Often encountered in early mathematics and include +,-,\*,/, %, ++, --.
* All of the arithmetic operators may be applied to any Java primitives, excepts boolean and String. Furthermore, only the addition operators + and += may be applied to String values, which results in String concatenation.

  **String is a Java primitive?**

#### Numeric Promotion

* Numeric Promotion rules:
  1. If two values have different data types, Java will automatically promote one of the values to the larger of the two data types \(ie. int → long, float → double\).
  2. If one of the values is integral and the other is floating-point, Java will automatically promote the integral value to the floating-point value's data type.
  3. Smaller data types, namely byte, short, and char, are first promoted to in any time they are used with a Java binary arithmetic operator, even if neither of the operands is int.
  4. After all promotion has occured and the operands have the same data types, the resulting value will have the same data type as its promoted operands.

### Working with Unary Operators

* Unary operator is one that requires exactly one operand, or variable, to function

| Unary operator | Description |
| :--- | :--- |
| + | Indicates a number is positive, although numbers are assumed to be positive in Java unless accompanied by a negative unary operator |
| - | Indicates a literal number is negative of negates an expression |
| ++ | Increments a value by 1 |
| -- | Decrements a value by 1 |
| ! | Inverts a Boolean's logical value |

#### Logical Complement and Negation Operators

* Logical complement operator, !, flips the value of a boolean expression. 
* Negation operator, -, reverses the sign of a numeric expression.

```java
boolean x = false;
System.out.println(x); // false
x = !x;
System.out println(x); // true

double x = 1.21;
System.out.println(x); // 1.21
x = -x;
System.out.println(x); // -1.21
x = -x;
System.out.println(x); // 1.21
```

* **You can not apply a negation operator \(-\) to a boolean expression, nor can you apply a logical complement operator \(!\) to a numeric expression**

#### Increment and Decrement Operators

* Increment and decrement operator \(++, --\), can be applied to numeric operands and have the higher order of precedence. 
* _Pre-increment_ of decrement operator is applied first and the value return is the new value of the expression, the _post-increment_ and decrement operators are applied after the value returned.

### Using Additional Binary Operators

#### Assignment Operators

* Automatically promote from smaller to larger data types, but it will tthrow a compiler exception if it detects you are trying to convert from larger to smaller data types.

#### Casting Primitive Values

* We can cast the results to a smaller data type. Casting primitives is required any time you are going from a larger numerical data type to a smaller data type, or converting from a floating-point number to an integral value.

```java
int x = (int)1.0;
short y = (short) 1921222; // stored as 20678
int z = (int)9l;
long t = 123124124124124L;
```

#### Compound Assignment Operators

* Comples operators are really just glorified forms of the simple assignment operator, with a built-in arithmetic or logical operation that applies the left-and right-hand side of the statement and stores the resulting value in a variable in the left-hand side of the statement.
* The result of the assignment is an expression in and of itself, equal to the value of the assignment.

```java
long x = 5;
long y = (x=3);
System.out.println(x); // Outputs 3
System.out.println(y); // Also, outputs 3
```

#### Relational Operators

* Compares two expressions and return a boolean value. The first four relational operators are applied to numeric primitive data types only.

|  |  |
| :--- | :--- |
| &lt; | Strictly less than |
| &lt;= | Less than or equal to |
| &gt; | Strictly greater than |
| &gt;= | Greater than or equal to |

* The fifth relational operator is applied to object references and classes or interfaces.

|  |  |
| :--- | :--- |
| a instanceof b | True if the reference that a points to is an instance of a class, subclass or class that implements a particular interface, as named in b |

#### Logical Operators

* The _logical operators_ \(&,\|,^\) may be applied to both numeric and boolean data types. When they are applied to boolean data types, they are referred to as logical operators, otherwise they are bitwise operators. 
  * & AND is only true if both operands are true.
  * \| Inclusive OR is only false if both operands are false.
  * ^ Exclusive OR is only true if the operands are different.
* Short-circuit operators are nearly identical to the logical operators, & and \|, respectively, except that the right-hand side of the expression may never be evaluated if the final result can be determined by the left-hand side of the expression.

```java
if (x!= null && x.getValue() < 5){
  // do something
} // no exception

if (x!= null & x.getValue() < 5){ // throw an exception if x is null
  // do something
}
```

#### Equality Operators

* The equality operators are used in one of three scenarios: 1. Comparing two numeric primitive types. If the numeric values are of different data types, the values are automatically promoted as previously described. 2. Comparing two boolean value 3. Comparing two objects, including null and String values.
* For objects comparison, the equality operator is applied to the references to the objects, not the objects they point to. Two references are equal if and only if they point to the same object, or both point to null.

### Understanding Java Statements

#### The if-then statement

![](https://i.imgur.com/dDXF3l5.png)

```java
if(hourOfDay < 11) {
  System.out.println("Good Morning");
  morningGreetingCount++;
}
```

#### The if-then-else statement

![](https://i.imgur.com/5cAcA76.png)

```java
if(hourOfDay < 11) {
  System.out.println("Good Morning");
} else {
  System.out.println("Good Afternoon");
}
```

```java
if(hourOfDay < 11) {
  System.out.println("Good Morning");
} else if(hourOfDay < 15) {
  System.out.println("Good Afternoon");
} else {
  System.out.println("Good Evening");
}
```

#### Ternary Operator

`boolean expression ? expression1:expression2`

```java
System.out.println((y > 5) ? 21 : "Zebra");
int animal = (y < 91) ? 9 : "Horse"; // DOES NOT COMPILE
```

#### The switch statement

![](https://i.imgur.com/IVZ1RKt.png)

* A switch statement is a complex desicion-making structure in which a single value is evaluated and flow is redirected to the first matching branch, known as a case statement, if no such case statement is found that matches the value, an optional default statement will be called. If no such default option is available, the entire switch statement will be skipped.

**Supported data types**

* Data types supported by switch statement include the following:
  * int and Integer
  * byte and Byte
  * short and Short
  * char and Character
  * String
  * enum values
* long and boolean and their associated wrapper classes are not supported by switch statements.

**Compile-time Constant values**

* The default case is not required to be at the last of switch case, however do not forget the break at the end of each case.

#### The while statement

![](https://i.imgur.com/HuvGlBQ.png)

* During execution, the boolean expression is evaluated before each iteration of the loop and exits if the evaluation returns false. **a while loop may terminate after its first evaluation of the boolean expression**

#### The do-while statement

![](https://i.imgur.com/9LvR1Q8.png)

* Like the while loop but guarantees that **the statement or block will be executed at least once**.
* The while loop purposely orders the statement of block of statements before the conditional expression, in order to reinforce that the statement will be executed before the expression is ever evaluated.

#### The for statement

**The basic for statement**

![](https://i.imgur.com/f7KaaHz.png)

* Variables declared in the initialization block of a for loop have limited scope and are only accesible within the for loop.

Some examples for illustrative purposes: 1. Creating an Infinite Loop:

```java
for( ; ; ){ 
  System.out.println("Hello World");
} // compile
```

* The semicolons separating the three sections are required, as for\( \) will not compile.
* Adding Multiple terms to the for statement

```java
int x = 0;
for (long y = 0, z = 4; x <5 && y< 10; x++, y++){
  System.out.println(y + '');
}
System.out.println(x); // compile
```

* You can declare a variable before the loop begins and use it after it completes. 
* Your initialization block, boolean expression, and update statements can include extra variables that may not reference each other.
* The update statement can modify multiple variables.
* Redeclaring a Variable in the Initialization Block

```java
int x = 0;
for (long y = 0, x = 4; x < 5 && y < 10; x++, y++){
  System.out.println(x + ""); // does not compile
}
```

```java
int x = 0;
long y = 10;
for(y = 0, x = 4; x < 5 && y < 10; x++, y++) {
  System.out.print(x + " ");
} // compile
```

* Can not repeat a declared variable in the initialization block.
* Using Incompatible Data Types in the Initialization Block

```java
for (long y = 0, int x = 4; x < 5 && y < 10; x++,y++){
 System.out.print(x + " ");
} // does not compile
```

* The variables in the initialization block must all be of the same type.
* Using loop variables outside the loop

```java
for(long y = 0, x = 4; x < 5 && y < 10; x++, y++) {
  System.out.print(y + " ");
}
System.out.print(x); // DOES NOT COMPILE
```

**The for-each statement**

![](https://i.imgur.com/xt8KXjq.png)

* The right-hand side of the for-each loop statement must be a built-in Java array or an object whose class implements `java.lang.Iterable`, which includes most of the Java `Collection` framework.
* The left-hand side of the for-each loop must include a declaration for an instance of variable, whose type matches the type of a member of the array or collection in the right-hand side of the statement.
* Java actually convert a for-each loop into a for loop:

ie:

```java
for(int value : values) {
  System.out.print(value + ", ");
}
for(java.util.Iterator<Integer> i = values.iterator(); i.hasNext(); ) {
  int value = i.next();
  System.out.print(value + ", ");
}
```

### Understanding Java Advanced Flow Control

#### Nested Loop

```java
int[][] myComplexArray = {{5,2,1,3},{3,9,8,9},{5,7,12,7}};
for(int[] mySimpleArray : myComplexArray) {
  for(int i=0; i<mySimpleArray.length; i++) {
    System.out.print(mySimpleArray[i]+"\t");
  }
  System.out.println();
}
```

result:

```java
5 2 1 3
3 9 8 9
5 7 12  7
```

#### Adding Optional Labels

* A label is an optional pointer to the head of a statement that allows the application flow to jump to it or break down from it. It is a single word that is proceeded by a colon \(:\).

```java
int[][] myComplexArray = {{5,2,1,3},{3,9,8,9},{5,7,12,7}};
OUTER_LOOP: for (int[] mySimpleArray : myComplexArray){
  INNER_LOOP: for (int i=0; i<mySimpleArray.length; i++) {
    System.out.println(mySimpleArray[i]+"\t");
  }
  System.out.println();
}
```

* It is possible to add optional labels to control and block structures. However, it is rarely considered good coding practice to do so.
* For formatting, labels follow the same rules for identifiers. For readability, they are commonly expressed in uppercase, with underscores between words, to distinguish them from regular variables.

#### The break statement

![](https://i.imgur.com/Eo6WHA3.png)

* The break statements that appear inside of while, do-while, and for loop will end the loop early.
* Without a label, the break statement will terminate the nearest inner loop it is currently in the process of executing. The optional label parameter allows us to break out of a higher level outer loop. 

```java
public class SearchSample {
  public static void main(String[] args) {
    int[][] list = {{1,13,5},{1,2,5},{2,7,2}};
    int searchValue = 2;
    int positionX = -1;
    int positionY = -1;
    PARENT_LOOP: for(int i=0; i<list.length; i++) {
      for(int j=0; j<list[i].length; j++) {
        if(list[i][j]==searchValue) {
          positionX = i;
          positionY = j;
          break PARENT_LOOP;
        }
      }
    }
    if(positionX==-1 || positionY==-1) {
      System.out.println("Value "+searchValue+" not found");
    } else {
      System.out.println("Value "+searchValue+" found at: " +
        "("+positionX+","+positionY+")");
    }
  }
}
```

#### The continue statement

![](https://i.imgur.com/BLwAZDX.png)

* The continue statement transfers control to the boolean expression that determines if the loop should continue. It ends the current iteration of the loop.
* Applied to the nearest inner loop under execution using optional label statements to override this behavior.

Advanced flow control usage

|  | Allows optional labels | Allows break statement | Allows continue statement |
| :--- | :--- | :--- | :--- |
| if | Yes\* | No | No |
| while | Yes | Yes | Yes |
| do while | Yes | Yes | Yes |
| for | Yes | Yes | Yes |
| switch | Yes | Yes | No |

* Labels are allowed for any block statement, including those that are preceded with an if-then statement.

### Summary

* For statement, there are two types of control structures:
  * Decision-making control structures: if-then, if-then-else, and switch  
  * Repetition control structures: for, for-each, while, and do-while.
* Most of these structures require the evaluation of a particular boolean expression either for branching decisions or once per repetition. The switch statement is the only one that supports a variety of data types, including String variables as of Java 7.
* For-each statement does not need to explicitly write a boolean expression, since the compiler builds them implicitly. For clarity, we referred to an enhanced for loop as a for-each loop, but syntactically they are written as a for statement.
* Flow can be enhanced through nested loops, break statements, continue statements, and optional labels.

### Exam Essentials

* Be able to write code that uses Java operators.
* Be able to recognize which operators are associated with which datatypes.
* Understand Java operator precedence.
* Be able to write code that uses parentheses to override operator precedence.
* Understand if and switch decision control statements.
* Understand loop statements.
* Understand how break and continue can change flow control.

