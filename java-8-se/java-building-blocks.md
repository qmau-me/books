# Java Building Blocks

## Exam objectives

1. Java Basics
   * Define the scope of variables
   * Define the structure of a Java class
   * Create executable Java applications with a main method, run a Java program from the command line, including console output
   * Import other Java packages to make them accessible in your code
   * Compare and contrast the features and components of Java such as platforms independence, object orientation, encapsulation, etc.
2. Working with Java Data Types
   * Declare and initialize variables \(including casting or primitive types\)
   * Differentiate between object reference variables and primitive variables
   * Know how to read or write to object fields
   * Explain an Object's Lifecycle \(creation, "dereference by reassignment" and garbage collection\)

## Notes:

### Methods and Fields

* Object is a runtime instance of a class in memory.
* Java classes have two primary element: methods and fields.
* Example class:

```java
public class Animal {
  // field
  String name; // field

  // method
  public String getName() {
    return name;
  }

  public void setName(newName){
    name = newName;
  }
}
```

* Method: access modifier, static \(binds method to the class\), return type, method name, parameters.
* A file can have 2 or more classes but just one of them is a public class and have the name matches the file's name.
* `main()` class is a gate way between the startup of a Java process managed by JVM and the beginning of the programmer's code.

```java
// main() class
public static void main(String args[]){
}
```

* All command line arguments are String objects.

### Packages and Imports

* Java puts classes in packages \(which are folders\).
* Import statement tells the compiler which package to look in to find a class.

#### Wildcards

* Class in the same package are often imported together.

```java
import java.util.*; // imports java.util.Random among other thing

public class ImportExample {
   public static void main(String[] args) {
   Random r = new Random();
   System.out.println(r.nextInt(10));
   }
}
```

* Including wildcards DO NOT slow the program down, it also help shorten the import list.

#### Redundant Imports

* `java.lang` is automatically imported.
* Redundant Imports example:

  ```java
  import java.nio.file.*;
  ```

  or

  ```java
  import java.nio.file.Files;
  import java.nio.file.Paths;
  ```

  not

  ```java
  import java.nio.*; // NO GOOD – a wildcard only matches
  //class names, not "file.*Files"
  import java.nio.*.*; // NO GOOD – you can only have one wildcard
  //and it must be at the end
  import java.nio.files.Paths.*; // NO GOOD – you cannot import methods
  //only class names
  ```

  **Naming conflicts**

* Different packages' classes can have the same name
* Using 2 wildcard import for packages that have same used class ends up compiler error

  ie:

```java
import java.util.*;
import java.sql.*; // DOES NOT COMPILE
// ↓ this will work
import java.util.Date;
import java.sql.*;

public class Conflicts {
 Date date;
 // some more code
}
```

* If You Really Need to Use Two Classes with the Same Name…

```java
import java.util.Date;
public class Conflicts {
 Date date;
 java.sql.Date sqlDate;
}
// Or you could have neither with an import and always use the fully qualifi ed class name:
public class Conflicts {
 java.util.Date date;
 java.sql.Date sqlDate;
}
```

### Code Formatting on the Exam

* If the code begins with line 1 or not?

### Creating objects

#### Constructors

* To create an object declare the type + variable name = new constructor;

```java
Random r = new Random();
```

```java
public class Chick {
  // constructor
   public Chick() {
     System.out.println("in constructor");
   }
}
```

* constructor is to initialize fields, 2 ways of doing this:

```java
public class Chicken {
   int numEggs = 0;// initialize on line
   String name;
   public Chicken() {
     name = "Duke";// initialize in constructor
   }
}
```

#### Reading and Writing Object Fields

```java
public class Swan {
   int numberEggs;// instance variable
   public static void main(String[] args) {
     Swan mother = new Swan();
     mother.numberEggs = 1; // set variable
     System.out.println(mother.numberEggs); // read variable
  }
}
```

#### Instance Initializer Blocks

* The code between the braces\({}\) is called a code block.
* Other times, code blocks appear outside a method. These are called **instance initializers**.

#### Order of Initialization

* Fields and instance initializer blocks are run in the order in which they appear in the file.
* The constructor runs after all fields and instance initializer blocks have run.

### Distinguishing Between Object References and Primitives

* 2 types of data:
  * primitive types
  * reference types

    **Primitive Types**

| Keyword | Type | Example |
| :---: | :---: | :---: |
| boolean | true of false | true |
| byte | 8-bit integral value | 123 |
| short | 16-bit integral value | 123 |
| int | 32-bit integral value | 123 |
| long | 64-bit integral value | 123 |
| float | 32-bit integral value | 123.45f |
| double | 64-bit integral value | 123.456 |
| char | 16-bit integral value | "a" |

* float and double are used for floating-point \(decimal\) values.
* A float requires the letter f following the number so Java knows it is a float.
* byte, short, int, and long are used for numbers without decimal points.
* Each numeric type uses twice as many bits as the smaller similar type. For example, short uses twice as many bits as byte does.
* number is called literal.
* Java allows you to specify digits in several other formats:
  * octal \(digits 0–7\), which uses the number 0 as a prefix—for example, 017
  * hexadecimal \(digits 0–9 and letters A–F\), which uses the number 0 followed by x or X as a prefix—for example, 0xFF
  * binary \(digits 0–1\), which uses the number 0 followed by b or B as a prefix—for example, 0b10
* Can have underscore to make them easier to read:

  ```java
  int million1 = 1000000;
  int million2 = 1_000_000;
  ```

* Be careful

```java
double notAtStart = _1000.00; // DOES NOT COMPILE
double notAtEnd = 1000.00_; // DOES NOT COMPILE
double notByDecimal = 1000_.00; // DOES NOT COMPILE
double annoyingButLegal = 1_00_0.0_0; // this one compiles
```

#### Reference Types

* Referenced object is not stored on memory, we use **pointer** to address them.
* A value is assigned to a reference in one of two ways:
  * A reference can be assigned to another object of the same type.
  * A reference can be assigned to a new object using the new keyword.

```java
today = new java.util.Date();
greeting = "How are you?";
```

![](https://scontent-nrt1-1.xx.fbcdn.net/v/t1.0-9/30698599_10214056330476578_1540331506075959296_n.jpg?_nc_cat=0&oh=ea1aeda997169f7f1a3b84e879470378&oe=5B62FCC8)

#### Key Differences

* Reference types can be assigned null, which means they do not currently refer

  to an object. Primitive types will give you a compiler error if you attempt to assign them null.

```java
int value = null; // DOES NOT COMPILE
String s = null;
```

* Reference types can be used to call methods when they do not point to null.

  Primitives do not have methods declared on them. Primitives do not have methods.

```java
String reference = "hello";
int len = reference.length();
int bad = len.length(); // DOES NOT COMPILE
```

* All the primitive types have lowercase type names. All classes that

  come with Java begin with uppercase.

#### Declaring and Initializing Variables

```java
String zooName;
int numberAnimals;
zooName = "The Best Zoo";
numberAnimals = 100;

// or

String zooName = "The Best Zoo";
int numberAnimals = 100;
```

#### Declaring Multiple Variables

```java
String s1, s2;
String s3 = "yes", s4 = "no";
int num, String value; // DOES NOT COMPILE
```

#### Identifiers

* There are only three rules to remember for legal identifiers:
  * The name must begin with a letter or the symbol $ or \_.
  * Subsequent characters may also be numbers.
  * You cannot use the same name as a Java _reserved word_. Java is case sensitive, so you can use versions of the keywords that only differ in case. Please don’t, though.
* Reserved words are

> abstract assert boolean break byte case catch char class const continue default do double else enum extends false final finally float for goto if implements import instanceof int interface long native new null package private protected public return short static strictfp super switch synchronized this throw throws transient true try void volatile while

* ie:
  * The following examples are legal:
    * okidentifier
    * $OK2Identifier
    * \_alsoOK1d3ntifi3r
    * \_\_SStillOkbutKnotsonice$
  * These examples are not legal:
    * 3DPointClass // identifiers cannot begin with a number
    * hollywood@vine // @ is not a letter, digit, $ or \_
    * \*$coffee // \* is not a letter, digit, $ or \_
    * public // public is a reserved word
* Most Java developers follow these conventions for identifier names:
  * Method and variables names begin with a lowercase letter followed by CamelCase.
  * Class names begin with an uppercase letter followed by CamelCase. Don’t start any identifiers with $. The compiler uses this symbol for some files.

### Understanding Default Initialization of Variables

#### Local Variables

* A local variable is a variable defined within a method. Local variables must be initialized before use.

#### Instance and Class Variables

* Variables that are not local variables are known as instance variables or class variables. Instance variables are also called fields.
* You can tell a variable is a class variable because it has the keyword static before it.
* Instance and class variables do not require you to initialize them. As soon as you declare these variables, they are given a default value.

| Variable type | Default initialization value |
| :--- | :--- |
| boolean | false |
| byte, short, int, long | 0 \(in the type’s bit-length\) |
| float, double | 0.0 \(in the type’s bit-length\) |
| char | '\u0000' \(NUL\) |
| All object references \(everything else\) | null |

#### Understanding Variable Scope

* These smaller contained blocks can reference variables defined in the larger scoped blocks, but not vice versa.
* Local variables - in scope from declaration to end of block
* Instance variables - in scope from declaration until object garbage collected
* Class variables - in scope from declaration until program ends

ie:

```java
11: public void eatMore(boolean hungry, int amountOfFood) {
12:   int roomInBelly = 5;
13:   if (hungry) {
14:     boolean timeToEat = true;
15:     while (amountOfFood > 0) {
16:       int amountEaten = 2;
17:       roomInBelly = roomInBelly - amountEaten;
18:       amountOfFood = amountOfFood - amountEaten;
19:     }
20:   }
21:   System.out.println(amountOfFood);
22: }
```

Block for scope

| Line | First line in block | Last line in block |
| :--- | :--- | :--- |
| while | 15 | 19 |
| if | 13 | 20 |
| Method | 11 | 22 |

### Ordering Elements in a Class

| Element | Example | Required? | Where does it go? |
| :--- | :--- | :--- | :--- |
| Package | package abc; | No | First line in the file |
| Import statements | import java.util.\*; | No | Immediately after the package |
| Class declaration | public class C | Yes | Immediately after the import |
| Field declaration | int value; | No | Anywhere inside a class |
| Method declarations | void method\(\) | No | Anywhere inside a class |

```java
package structure; // package must be first non-comment
import java.util.*; // import must come after package
public class Meerkat { // then comes the class
   double weight; // fields and methods can go in either order
   public double getWeight() {
   return weight; }
   double height; // another field – they don't need to be together
}
```

* **Multi classes can be in a file but just one class can be public**

### Destroying Objects

* Java objects are stored in your program memory's heap. The heap is quite large but there is always a limit to its size.

#### Garbage Collection

* Refers to the process of automatically freeing memory on the heap by deleting objects that are no longer reachable in your program.
* Java provides a method called `System.gc()`. Now might be a good time for Java to kick off a garbage collection run. Java is free to ignore the request.
* An object will remain on the heap until it is no longer reachable. An object is no longer reachable when one of two situations occurs:
  * The object no longer has any references pointing to it.
  * All references to the object have gone out of scope.

![](https://scontent-nrt1-1.xx.fbcdn.net/v/t1.0-9/30689087_10214056473000141_5917426007068901376_n.jpg?_nc_cat=0&oh=7081ee224f027c59a6c7293b4959176b&oe=5B75243E)

#### finalize\(\)

* This method gets called if the garbage collector tries to collect the object. If the garbage collector doesn’t run, the method doesn’t get called.
* The lesson is that the finalize\(\) call could run zero or one time.

### Benefits of Java

* **Object Oriented:** all code is defined in classes and most of those classes can be instantiated into objects. Java allows functional programming within a class, but objects oriented is still the main organization of code.
* **Encapsulation:** Java support access modifier to protect data from unintended access and modification.
* **Platform Independent:** Java is an interpreted language because it gets compiled to bytecode. This is known as **"write once, run everywhere"**.
* **Robust:** Java over C++ in preventing memory leaks. Java manages memory on its own and does garbage collection automatically.
* **Simple:** Java was intended to be simpler than C++. In addition to eliminating pointers, it got rid of operator overloading.
* **Secure:** Java code runs inside the JVM. This creates a sandbox that makes it hard for Java code to do evil things to the computer it is running on.

### Summary

* In this chapter, you saw that Java classes consist of members called fields and methods. An object is an instance of a Java class. There are three styles of comment: a single-line comment \(//\), a multiline comment \(/\* \\*/\), and a Javadoc comment \(/\*\* \\*/\).
* Java begins program execution with a main\(\) method. The most common signature for this method run from the command line is `public static void main(String[] args)`. Arguments are passed in after the class name, as in java NameOfClass firstArgument. Arguments are indexed starting with 0.
* Java code is organized into folders called packages. To reference classes in other packages, you use an import statement. A wildcard ending an import statement means you want to import all classes in that package. It does not include packages that are inside that one.
* java.lang is a special package that does not need to be imported.
* Constructors create Java objects. A constructor is a method matching the class name and omitting the return type. When an object is instantiated, fields and blocks of code are initialized first. Then the constructor is run. Primitive types are the basic building blocks of Java types. They are assembled into reference types. Reference types can have methods and be assigned to null. In addition to “normal” numbers, numeric literals are allowed to begin with 0 \(octal\), 0x \(hex\), 0X \(hex\), 0b \(binary\), or 0B \(binary\). Numeric literals are also allowed to contain underscores as long as they are directly between two other numbers.
* Declaring a variable involves stating the data type and giving the variable a name. Variables that represent fields in a class are automatically initialized to their corresponding “zero” or null value during object instantiation. Local variables must be specifically initialized. Identifiers may contain letters, numbers, $, or \_. Identifiers may not begin with numbers.
* Scope refers to that portion of code where a variable can be accessed. There are three kinds of variables in Java, depending on their scope: instance variables, class variables, and local variables. Instance variables are the non-static fields of your class. Class variables are the static fields within a class. Local variables are declared within a method.
* For some class elements, order matters within the file. The package statement comes first if present. Then comes the import statements if present. Then comes the class declaration. Fields and methods are allowed to be in any order within the class.
* Garbage collection is responsible for removing objects from memory when they can never be used again. An object becomes eligible for garbage collection when there are no more references to it or its references have all gone out of scope. The finalize\(\) method will run once for each object if/when it is first garbage collected.
* Java code is object oriented, meaning all code is defined in classes. Access modifiers allow classes to encapsulate data. Java is platform independent, compiling to bytecode. It is robust and simple by not providing pointers or operator overloading. Finally, Java is secure because it runs inside a virtual machine.

### Exam Essentials

* Be able to write code using a `main()` method.
* Understand the effect of using packages and Imports.
* Be able to recognize a constructor.
* Be able to identify legal and illegal declarations and initialization.
* Be able to determine where variables go into and out of scope.
* Be able to recognize misplaced statements in a class.
* Know how to identify when an object is eligible for garbage collection.

