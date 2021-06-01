---
title: "Part 1 - The Beginning"
permalink: /part1/
nav_order: 3
published: true
has_children: true
has_toc: true
---

# Part 1 - The Beginning

During this course you will learn how to do basic programs. The course starts from the very beginning and goes deeper as we progress. Before we start programming we have to know exactly what programming is.  

Programming is designing and creating software also know as programs. The programs are usually written in human readable language known as programming languages. There are hundreds of programming languages available, but in this course we concentrate on C#. More information about [**the C# programming language**](https://docs.microsoft.com/en-us/dotnet/csharp/tour-of-csharp/).

Programming languages offer multiple methods and commands as built-in. Thus we do not implement everything ourselves. Large part of programming is using the built-in methods for problem solving. 

The written code is called the source code and is comprised of statements and expressions. The code is read just like any other written text, from left to right, top to bottom.

C# programs require a certain type of body to function.

```cs  
public class Program {  
    public static void Main(string[] args)  
    {  
        // Add your statements here  
    }  
}   
```
    
There are many parts to this body of which many are automatically created. For now it is enough to know that in a program there is always code that is not written by the coder. There are some features in all programming languages that are required for the program to run.

## Running a Program

When trying if a source code works you run your program. This means basically two steps.  

1) The source code is compiled into a program. 

2) The compiled program is run as planned. 

The compilation and running can usually be done quite automatically with a dedicated compiler. With modern development tools compilation and running are done with one command or even a click of a button.

## The Assembly and Machine Instructions

When you compile your program the C# compiler compiles the source code into a module which is converted into an assembly. The assembly is a intermediate code of the program. 

The Common Language Runtime (CLR) manages the execution of the C# program using the assembly. CLR converts the assembly into machine instructions which are executed on the Central Processing Unit (CPU). The machine instructions are executed by the operating system and the output will shows according to requirement.

The compiling process is quite a complicated task, where the human readable code is transferred into more machine readable. We concentrate on the human-readable side of code.
