---
description: 0430-0506
---

# Core Java APIs

### Exam objectives

1. Using Operators and Decision Constructs
   * Test equality between Strings and objects using == and equals\(\).
2. Creating and Using Arrays
   * Declare, instantiate, initialize and use a one-dimensional array.
   * Declare, instantiate, initialize and use a multi-dimensional array.
3. Working with Selected classes from the Java API
   * Creating and manipulating Strings.
   * Manipulate data using the StringBuilder class and its methods.
   * Declare and use an ArrayList of a given type.
   * Create and manipulate calendar data using classes from java.time.LocalDateTime, java.time.LocalDate, java.time.Local-Time, java.time.format.DateTimeFormatter, java.time.Period.
4. Working with Java Data Types
   * Develop code that uses wrapper classes such as Boolean, Double, and Integer.

### Notes

#### Creating and Manipulating Strings

* A string is basically a sequence of characters.
* String class is a special class, doesn't need to be instantiated with new.
  * `String name = "Fluffy";`
  * `String name = new String("Fluffy");`

**Concatenation**

* Placing String before the other String and combining them together is called string concatenating. The + operator can be used in two ways within the same line of code:
* If both operands are numeric, + means numeric addition.
* If either operand is a String, + means concatenation.
* The expression is evaluated left to right.

ie.

```java
  System.out.println(1 + 2); // 2
  System.out.println("a" + "b"); // ab
  System.out.println("a" + "b" + 3); // ab3
  System.out.println(1 + 2 + "c"); // 3c
```

**Immutability**

* **String objects are immutable**, once they are created, they can not be made larger or smaller, and you cannot change one of the characters inside them.

**The String Pool**

* Strings are everywhere in Java, they use up a lot of memory, Java solves this issue by reusing common ones. The `string pool`, also known as the intern pool, is a location in the JVM that collects all these strings.
* The string pool contains literal values that appear in your program. Strings not in the string pool are garbage collected just like any other object.

```java
String name = "Fluffy"; // this is a literal string.
String name = new String("Fluffy"); // this is not a literal string.
```

* The second way is less efficient than the first way, however, it is allowed.

**Important String Methods**

* A string is a sequence of characters and zero-indexed.

**length\(\)**

```java
String string = "animals";
System.out.println(string.length()); // 7
```

* Returns the number of characters in the String.

**charAt\(\)**

```java
String string = "animals";
System.out.println(string.charAt(0)); // a
System.out.println(string.charAt(6)); // s
System.out.println(string.charAt(7)); // throws exception
```

* Lets you query the string to find out what character is at a specific index.
* **Indexes start counting with 0**.

**indexOf\(\)**

