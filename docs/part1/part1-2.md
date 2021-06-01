---
title: "Variables"
parent: "Part 1 - The Beginning"
permalink: /part1/2/
nav_order: 2
published: true
---

# Variables

In the previous section we introduced the string variable. String is not the only variable in coding. Variables are the basic storages of information in programming. 

Some example variables are string for text, int for integers, double for decimal numbers and boolean for truth value. As mentioned earlier the value for a variable is set with the equals sign **=**.

```cs
int truth = 42;
```

In the example above we declare a variable called **truth** and assign it the value **42**.

This integer can be concatenated to a string in our program.

```cs
int truth = 42;
double pie = 3.141592653;
bool valid = true;
string magic = "The magic number: ";
Console.WriteLine(magic + truth);
Console.WriteLine("Life of " + pie);
Console.WriteLine("This is awesome: " + valid);
```

```console
The magic number: 42
Life of 3.141592653
This is awesome: true
```

The variable names must be unique inside a code block. You can declare each variable only once. But as the name variable suggests you can change their value.

```cs
int number = 42;
Console.WriteLine(number);
number = 21;
Console.WriteLine(number);
```

```console
42
21
```

## Assigning Value to a Variable

Let us take a closer look at our previous example. In the first line we declare the variable and assign it a value. With this information the compiler creates the **int** variable and stores the value.

In the second line we use the variable to access the stored information. It could be said that the variable name is a reference to the value. Once we have gained the value the command prints it as requested.

Earlier it was mentioned that you can declare a variable only once. This time we do not declare the value. The difference is the **int** on the first line. As we did on the second line while we printed the value on the third line we once again reference to the number rather than declare it again. With the **=** sign we assign a new value to the variable.

## Variable Typing

The variables in C# programming are statically typed. This means that once a variable is declared into a certain type the type does not change*.

(* There is nowadays a keyword **dynamic** in C# programming, but that is not relevant for basic programming. For our purposes we treat the variables as static typing.)

For example this works.

```cs
int magic = 42;
magic = 41;
```

This does not work.

```cs
int magic = 42;
magic = "Magic";
```

There are exceptions of course. For example you can assign an integer to a double.

```cs
double decimal = 10; // Works fine

int number = 20;
decimal = number; // Also works
```

But not the other way around.

```cs
int number = 4.2; // Does not work

double decimal = 4.2;
number = decimal // Does not work either
```

## Naming Variables

Previously we discussed about the quality of code and its readibility.

```cs
double a = 3.14;
double b = 22.0;
double c = a * b * b;

Console.WriteLine(c);
```

```console
1519.76
```
Both these programs produce the same result. How ever the second one is much easier to read and its functionality is easier to understand. Both calculate the area of a circle. First we define the value of pi, then the radius and finally we calculate the area.

```cs
double pi = 3.14;
double radius = 22.0;
double area = pi * radius * radius;

Console.WriteLine(area);
```

```console
1519.76
```

There are certain restrictions to naming variables as well as conventions. The variable names:
* cannot contain special characters such as **!**, **?**, **å** or **ö**, 
* cannot contain empty spaces also called **whitespace**,
* should start with **a lowercase letter**,
* **shouldBeWrittenInCamelCase**.

The variables in C# are usually written with [**camelCase**](https://en.wikipedia.org/wiki/Camel_case). This means the variable name starts with a small letter. They contains no other characters than letters and numbers, and contains no punctuation or spaces. 

Even though 'snake_case' with underscore would be a valid variable name such naming convention is not recommended and should not be used during this course.

```cs
int 9var = 42; // Does not work
int var9 = 42; // Works, but does not describe the variable well
```

The variables can only be declared once.

```cs
string camelCase = "Camels are fun!";
string camelCase = "Camels are nice"; // Does not compile, the variable name is already in use
```

## Reading Different Kinds of Variables from User

In the previous part we learned how to read a string variable from the user.

```cs  
public class Program 
{
   public static void Main() 
   {  
      Console.Write("Give a message: ");
      string message = Console.ReadLine();
      Console.WriteLine(message);
   }
}
```

```console
Give a message: I want to print this
I want to print this  
```

All the other variables such as integers, doubles or booleans are also read from the user as strings. We have to convert them to the correct type with built in methods.

```cs
Console.Write("Give integer value: ");
string userInput = Console.ReadLine();             // Declare and assign the input as string
int intValue = Convert.ToInt32(userInput);         // Convert string to integer type
Console.WriteLine("You gave " + intValue);

Console.Write("Give double value: ");
userInput = Console.ReadLine();                    // Assign new value to userInput
double doubleValue = Convert.ToDouble(userInput);  // Convert string to double type
Console.WriteLine("You gave " + doubleValue);
```

```console
Give integer value: 42
You gave: 42
Give double value: 4.2
You gave: 4.2
```

In the example above we read both an integer and a double. There is no large difference between the methods only the method name is different.

If we want to convert a truth value from a string, are two options: **True** and **False**.

```cs
string truth = "True";
bool booleanValue = System.Convert.ToBoolean(truth);
Console.WriteLine(booleanValue);

truth = "False";
booleanValue = System.Convert.ToBoolean(truth);
Console.WriteLine(booleanValue);
```

```console
True
False
```

Convert Class is used to convert strings into multiple other types of variables. The full list is [**found here**](https://docs.microsoft.com/en-us/dotnet/api/system.convert?view=netframework-4.8).

**You can now do the exercises for variables.**
