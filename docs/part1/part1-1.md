---
title: "Printing and Reading"
parent: "Part 1 - The Beginning"
permalink: /part1/1/
nav_order: 1
published: true
---

# Printing and Reading

The basic structure of a C# program is the following.

```cs  
using System;

public class Program 
{  
    public static void Main(string[] args) 
    {  
        // Add your statements here  
    }  
}   
```

The program execution starts from the first line after **public static void Main(string[] args) {** and ends at the closing curly bracket **}**. 

Everything in between is run one row at a time. For example the most common first program of any programmer would go like this.

```cs  
public class Program {  
    public static void Main(string[] args) 
    {  
        Console.WriteLine("Hello World");  
    }  
}   
```

In this example the only runnable statement is **Console.WriteLine("Hello World")** which prints to the console. 

```console
Hello World!
```

We will later focus on the terms **public class** and **public static void**. 

In the material the whole structure might not be shown unless purposefully needed. The example above could be represented.

```cs  
Console.WriteLine("Hello World");  
```

In the first exercises the basic structure is given so you do not have to worry about memorising it.

## Printing

As mentioned programming languages have build in methods. **Console.WriteLine()** is one of them. The statement is quite self explanatory. It tells the computer to write a line to the console. You can change the **Hello World** to any text you wish as long as the method itself is not changed.

The requirements in the exercises are very precise. For example the line needs to end with a semicolon **;**.

Programs are created and read command by command. Every command has to be on their own line. In the next example we are calling **Console.WriteLine()** twice which means the print command is executed twice.

```cs  
public class Program {  
    public static void Main(string[] args) 
    {  
        Console.WriteLine("Hello World!");
        Console.WriteLine("... and Helsinki!"); 
    }  
}   
```

This would print.

```console
Hello World!
... and Helsinki!
```

To be precise the command **Console.WriteLine("example text")** prints the text **example text** and a line change. The line change can also be handled with special new line character **\n** which is written as a part of the printable text. The example could be written.

```cs  
public class Program {  
    public static void Main(string[] args) 
    {  
        Console.WriteLine("Hello World!\n... and Helsinki!"); 
    }  
}   
```

Notice there is no empty space around the new line character **\n**. In a text every character even the empty ones are part of the text. If you would put space around the line change the first line would end with an empty character and the second one would start with one.

Sometimes the texts can be quite long and reading them from a single line can become quite difficult. It is possible to split the string into multiple pieces and then concatenate them together with the addition operator **+**. The example above could be done.

```cs  
public class Program {  
    public static void Main(string[] args) 
    {  
        Console.WriteLine("Hello World!\n" + 
        "... and Helsinki!"); 
    }  
}   
```

This will print exactly the same information as previously. Compared to the first solution this is more efficient as we have to call the print command only once.

So far everything we have printed have ended in a line change. To print something, but not change the line in the end we would use **Console.Write("I do not change line")**.

Thus there are two statements for printing:  
* **Console.WriteLine()** prints the text and changes line,
* **Console.Write()** prints the text but stays on the same line.   

In the printed text there can be special characters such as the new line **\n**. You might want to get familiar with [**other special characters**](https://en.wikipedia.org/wiki/Escape_character).

## Parameters for a Command

When we want to print something we have to give that information as a parameter to our print command. Parameters are given to the command inside the round brakets **()**. For example to print **I like coding** we give the parameter inside quotes: Console.Write("I like coding").

## Semicolon Separates Commands

The semicolon **;** is used to seperate the commands from each other. One line code would not be very readable.

```cs
Console.Write("Hello "); Console.Write("World!"); Console.Write("\n");  
```

This would print out.

```console
Hello World!
```

## Code Blocks

Code consists of code blocks. Code block is part of the code separated with the curly brackets **{}**. There are usually multiple of these in a single program.

For example the line **public static void Main(string[] args)** defines where to start the program. It defines a block of what to run when the program is started.

```cs
public class Program 
{  // Here starts block for the class

  public static void Main(string[] args) 
  {  // Here starts block for the main

  // Your code would be here

  } // The main block ends
 
} // The class block ends
```

The example shows a block inside another block. Blocks can be used to define the structure of a program. The block for the class contains the whole program structure, whereas the block for the Main method contains the source code that is run when the program is started.

The block is always opened with the left curly bracket **{** and closed with the right curly bracket **}**. If either of them is missing the code will not compile and thus will not run.

## Comments

As you might have noticed we already have comments in our code. Comments are text that are not compiled and thus are not run. Comments can be used for example to comment certain elements in the code or to temporarily comment out part of a code for debugging purposes. There are two types of comments:
* **// single line comment**
* **/* multiple line comment */**

The single line comment is started with a double slash **//** but does not have an ending delimeter. Multiline comment starts with a slash and star **/*** and ends with a star and slash ***/**. Everything between these are considered as a comment by the compiler.

## Code Style

Even though there is no style restraint from computer or the language we have chosen there is great advantage in keeping the code neat and easy to read. 

For every language there are widely spread [**coding conventions**](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/inside-a-program/coding-conventions). Indentation and variable naming conventions are the most useful ones to keep in mind. We could write our program.

```cs  
public class Program 
{  
    public static void Main(string[] args) 
    {  
        Console.WriteLine("Hello World!\n" + 
        "... and Helsinki!"); 
    }  
}   
```

Other way to do this. 

```cs  
public class Program { public static void Main(string[] args) { Console.WriteLine("Hello World!\n" + 
"... and Helsinki!");  }  
                                        }   
```

The latter is not as easy to read and understanding the code blocks is harder. 

**Keep your code neat and clean!**

## Printing a String

Now that we have the tools for programming let's go a bit deeper. The simple lines of text we have printed are actually string literals. These literals can be saved into string variables. 

When we introduce a variable into a program we usually give it a value. A value is given by following the variable with a assignment sign **=** the value and ending the line again with a semicolon **;**. For example if we want a string variable called **message** with a value of **I am learning** we would assign it as following.

```cs
string message = "I am learning";
```

Creating a variable gives us an opportunity to reference to the variable inside the program.

```cs
string message = "Print me";
Console.WriteLine(message);
```

```console
Print me
```

If we now would use quotes around our variable name we would print it as a string literal.

```cs
string message = "Print me";
Console.WriteLine("message");
```

```console
message
```

As combined multiple lines of text the string variables can also be concatenated as a part of printing. 

```cs
string name = "Doctor Octopus";
Console.WriteLine("We meet again, " + name);
```

```console
We meet again, Doctor Octopus
```

Same can be done with multiple parts.

```cs
string name = "Doctor Octopus";
string greeting = "We meet again, ";
Console.WriteLine(greeting + name + "!");
```

```console
We meet again, Doctor Octopus!
```

We could also create a string variable from multiple literals.

```cs
string counting = "One" + "\n" + "Two" + "\n" + "Three";
Console.WriteLine(counting);
```

```console
One
Two
Three
```

## Reading Strings from User

So far we have used strings that are written directly to the source code. It would be nice if we could tell our program what we want to print each time. This can be done with another built in method **Console.ReadLine()**. 

```cs  
public class Program 
{
    public static void Main() 
    {  
    // Print a request for message.
    Console.Write("Give a message: ");

    // Assign a new string variable. The value is the command we want to use.
    string message = Console.ReadLine();

    // Print out the message we gave.
    Console.WriteLine(message);
    }
}
```

This will look something like this with input **I want to print this**.

```console
Give a message: I want to print this
I want to print this  
```
  
This is the same example, but with concatenating the input message with **Your message was:**.

```cs  
public class Program 
{
   public static void Main() 
   {  
    // Print a request for message.
    Console.Write("Give a message: ");
    
    // Assign a new string variable. The value is the method we want to use.
    string message = Console.ReadLine();

    // Print out the message we gave.
    Console.WriteLine("Your message was: " + message);
   }
}
```

This will look something like this with input **I want to print this**.

```console
Give a message: I want to print this
Your message was: I want to print this  
```

**You can now do the exercises for Printing and Reading.**

