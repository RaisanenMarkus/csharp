---
title: "Subproblems"
parent: "Part 2 - Problem Solving"
permalink: /part2/1/
nav_order: 1
published: true
---

# Subproblems

## Reading User Input

The solution pattern for programming tasks involving reading user input is straightforward. We can use the **System.Console.ReadLine()** method for this task. In most cases we want to use the method more than once or use other methods from the **System** library as well. For this we will have **using System;** in our program structure.

```cs
using System;

public class Program 
{  
  public static void Main(string[] args) 
  {  
    Console.ReadLine();
    // More code...
  }  
}   

```

## Calculating

We quite often need to calculate something in a program such as an average or a sum. The solution patter to solve such problems is as follows.

- Define the inputs required for the calculation and declare variables for them.
- Identify the operation needed and declare a variable for the result of the calculation. 
- Perform the calculation using the inputs and assign the result to the variable that was reserved for it.
- Once the calculation is done do something with its result. 

For example the solution pattern for the problem 'Create a program to calculate the sum of two integers' is the following.

```cs
// Identifying the input values and declaring the variables for them
int first = 1;
int second = 2;

// Identifying the operation and declaring a variable for the result
int sum = first + second;

// printing the result of the calculation
Console.WriteLine("The sum of " + first + " and " + second + " is " + sum);
```

A program that both reads and calculates combines both of these patterns. Variable declaration and the reading of values into them can be combined into one.

```cs
int first = Convert.ToInt32(Console.ReadLine());
int second = Convert.ToInt32(Console.ReadLine());

int product = first * second;

Console.WriteLine("The product of " + first + " and " + second + " is " + product);

```

## Some Alternative Functionality

Problems often contain some alternative functionality and in such case we use conditional statements. A Conditional statement starts with an 'if' statement followed by an expression in parentheses. The expression evaluates to either true or false. If it evaluates true the following block delimited by curly brackets gets executed.

A program that prints "ok" if the value of the variable is greater than 42, and otherwise prints "not ok" looks like this.

```cs
int value = 15;
if (value > 42) 
{
    Console.WriteLine("ok");
} 
else 
{
    Console.WriteLine("not ok");
}
```

You can also chain together multiple conditions. In such a case, the problem takes the form "if a, then b; else if c, then d; else if e, then f; otherwise g". The chain consists of an if-statement followed by else if-statements each containing its own expression and a block.

```cs
// if the value is greater than five
if (value > 5) 
{
    // functionality when value is greater than five
} 
else if (value < 0)
{ 
    // functionality when value is less than zero
    // and the value IS NOT larger than five
} 
else // otherwise
{  
    // functionality otherwise
}
```

Conditional functionality can be combined with other solution patterns. Let's look into a problem: 'Read two integers from the user. If the sum of the integers is over 100, print too much. If the sum is less than 0, print too little. Otherwise, print ok.' 

The program below combines reading, calculating and conditional functionality.

```cs
 // Declaring the variables and assigning user input to them
int first = Convert.ToInt32(Console.ReadLine());
int second = Convert.ToInt32(Console.ReadLine());

// Identifying the operation and declaring variable for the result
int sum = first + second;

// Doing something with the result. In this case
// the result is used in the conditional operations.

if (sum > 100) // if the sum is over 100
{ 
    Console.WriteLine("too much");
} 
else if (sum < 0) // if the sum is less than 0
{ 
    Console.WriteLine("too little");
} 
else // otherwise
{ 
    Console.WriteLine("ok");
}
```

**You can now do the exercises for subproblems.**
