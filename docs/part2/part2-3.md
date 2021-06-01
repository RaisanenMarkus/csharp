---
title: "The Basics of Methods"
parent: "Part 2 - Problem Solving"
permalink: /part2/3/
nav_order: 3
published: true
---

# The Basics of Methods

Printing to the screen has been done with the statement **Console.WriteLine()** and reading numbers with the statement **Console.ReadLine()**. Conditional statements have used **if** and repeat statements **while** and **for**. We notice that printing and reading differ from **if**, **while**, and **for**. The printing and reading commands are followed by parentheses and sometimes there also are parameters given to the command between the parentheses. These statements "ending with parentheses" are strictly speaking not commands but rather methods.

Technically speaking **a method** is a named set of statements, a part of the program that can be called from elsewhere in the program code by using the method's name. 

```cs
Console.WriteLine("I am a parameter given to a method!");
``` 

In this example the line of code calls a method that handles printing to the screen. The internal implementation of the method is hidden and the programmer need not concern themselves with it when using the method.

Thus far all the methods we have used have been premade C# methods. Next we will learn to create our own methods.

## Own Methods

A method means a named set consisting of statements that can be called from elsewhere in the program code by its name. Programming languages offer premade methods but programmers can also write their own. It is actually quite exceptional if a program does not use methods written by a programmer, because methods help in structuring the program. From this point onward nearly every program on the course will contain custom created methods.

In the code methods are written outside of the curly bracets of the Main method, yet inside out the outermost curly bracets. They can be located above or below the Main method.

```cs
using System;

public class Program 
{  
  public static void Main(string[] args) 
  {  
      // Add your statements here  
  }  

  // Your own methods are here
}   
```

Let's observe how to create a new method. We'll create the method **Greet()**.

```cs
using System;

public class Program 
{  
    public static void Main(string[] args) 
    {  
        // Add your statements here  
    }  

    // Your own methods are here
    public static void Greet() 
    {
      Console.WriteLine("Greetings from the method world!");
    } 
}   
```

The definition of the method consists of two parts. The first line of the definition includes the name of the method, here it is Greet(). On the left side of the name are the keywords **public static void**. Beneath the row containing the name of the method is a code block surrounded by the curly brackets. Inside of the code block is the code of the method, the commands that are executed when it is called. The only thing our method does is write a line of text on the screen.

Calling a custom method is simple. Write the name of the methods followed by a set of parentheses and the semicolon. In the following the Main program calls the greet method four times in total.

```cs
using System;

public class Program 
{  
  public static void Main(string[] args) 
  {  
    // Add your statements here
    Console.WriteLine("Let's try if we can travel to the method world:");
    Greet();

    Console.WriteLine("Looks like we can, let's try again:");
    Greet();
    Greet();
    Greet();
  }  

  // Your own methods are here
  public static void Greet() 
  {
    Console.WriteLine("Greetings from the method world!");
  } 
}   
```

The execution of the program produces the following output.

```console
Let's try if we can travel to the method world: 
Greetings from the method world!  
Looks like we can, let's try again: 
Greetings from the method world!   
Greetings from the method world!   
Greetings from the method world!
```

The order of execution is worth noticing. The execution of the program happens by executing the lines of the Main method in order from top to bottom, one at a time. When the encountered statement is a method call, the execution of the program moves inside the method in question. The statements of the method are executed one at a time from top to bottom. After this the execution returns to the place where the method call occured and then proceeds to the next statement in the program.

Strictly speaking the Main program itself is a method. When the program starts the operating system calls the Main method. The Main method is the starting point for the program since the execution begins from its first row. The execution of a program ends at the end of the Main method.

## Naming of Methods

We discussed variable naming in the previous part. There are rules for method naming as well. For methods we use **PascalCase**. It is very similar to the camelCase used for variables. The major difference is that with PascalCase method names start with a capital letter.

```cs
public static void ThisMethodSaysWoof() 
{
  Console.WriteLine("woof");
}
```

In the example above the method name begins with a capital letter and the words are joined together with the PascalCase style. Meaning that each word begins with an uppercase letter. The parentheses sit next to one another and the contents are correctly indented.

## Method Parameters

**Parameters** are values given to a method that can be used in its execution. The parameters of a method are defined on the uppermost row of the method within the round brackets following its name. The values of the parameters that the method can use are copied from the values given to the method when it is executed.

In the following example a parameterized method **Greet(int)** is defined. It has an int type parameter called **numOfTimes**.

```cs
public static void Greet(int numOfTimes) 
{
    int i = 0;
    while (i < numOfTimes) 
    {
      Console.WriteLine("Greetings!");
      i++;
    }
}
```

We will call the method Greet(int) with different values. The parameter **numOfTimes** is assigned the value **1** on the first call, and **3** on the second.

```cs
  public static void Main(string[] args) 
  {
    Greet(1);
    Console.WriteLine("");
    Greet(3);
  }
```  

```console
Greetings!

Greetings!
Greetings!
Greetings!
```

Just like when calling the predefined method **Console.WriteLine()** you can pass an expression as a parameter.

```cs
  public static void Main(string[] args) 
  {
    Greet(1 + 2);
  }
```  

```console
Greetings!
Greetings!
Greetings!
```

If an expression is used as a parameter for a method that expression is evaluated prior to the method call. Above the expression **evaluates to 3** and the final method call is of the form Greet(3).

## Multiple Parameters

A method can be defined with multiple parameters. When calling such a method the parameters are passed in the same order.

```cs
public static void Sum(int first, int second) 
{
  Console.WriteLine("The sum of numbers " + first + " and " + second + " is " + (first + second));
}
```

```cs
Sum(3, 5);

int number1 = 2;
int number2 = 4;

Sum(number1, number2);
```

```console
The sum of numbers 3 and 5 is 8
The sum of numbers 2 and 4 is 6
```

## The Values of the Parameters

When calling a method **the values of the parameters are copied**. In practice this means that both the Main method and the method to be called can use similarly named variables. Changing the value of the parameter inside the method does not affect the value of the variable with the same name in the Main method. Let's examine this behavior with the following program.

```cs
public class Example {
  public static void Main(string[] args) 
  {
      int min = 5;
      int max = 10;

      PrintNumbers(min, max);
      Console.WriteLine();

      max = 8;

      PrintNumbers(min, max);
  }

  public static void PrintNumbers(int min, int max) 
  {
      while (min < max) {
          Console.WriteLine(min);
          min++;
      }
  }
}
```
The output of the program.

```console
5
6
7
8
9

5
6
7
```

Changing the values of the variables in the method PrintNumbers(int, int) does not affect the values in the Main method even though they have the same exact names.

So even if the variables have the same exact name, the method parameters are distinct from the variables or parameters of different methods. When during a method call a variable is passed to a method the value of that variable is copied to be used as the value of the parameter variable that is declared in the method definition. The variables in different methods are different from each other.

Let's consider the following example. We define a variable called **number** in the Main method. That variable is passed as a parameter to the method **IncrementByThree(int)**.

```cs
// Main program
public static void Main(String[] args) 
{
  int number = 1;
  Console.WriteLine("The value of the variable 'number' in the Main program: " + number);
  IncrementByThree(number);
  Console.WriteLine("The value of the variable 'number' in the Main program: " + number);
}

// method
public static void IncrementByThree(int number) 
{
  Console.WriteLine("The value of the method parameter 'number': " + number);
  number = number + 3;
  Console.WriteLine("The value of the method parameter 'number': " + number);
}
```

The execution of the program produces the following output.

```console
The value of the variable 'number' in the Main program: 1 
The value of the method parameter 'number': 1 
The value of the method parameter 'number': 4 
The value of the variable 'number' in the Main program: 1
````

Incrementing the variable inside the method poses no problem. This does not cause changes in the variable inside the Main program. This latter **number** variable residing in the Main is different from the one in the method.

The parameter is copied for the method to us. In other words a new variable called **number** is created for the **incrementByThree(int)** method and the value of the variable in the Main program is copied as its value when the method is called. The variable **number** inside the method **incrementByThree(int)** exists only for the duration of the method execution and it has no relation to the similarly named variable in the Main program.
