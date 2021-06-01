---
title: "Discovering Errors"
parent: "Part 3 - Data Structures"
permalink: /part3/5/
nav_order: 5
published: true
---

# Discovering Errors

We have practiced the fundamentals of variables, conditionals, loops, methods, lists and arrays. Let's now think about the clarity of programs and how errors are found.

## Code Blindness

Programmers often becomes blind to their own code. Let's familiarize ourselves with this with the aid of a short video. Count how many times the white shirted players pass the ball between each other.

<iframe width="560" height="315" 
src="https://www.youtube.com/embed/Ahg6qcgoay4" 
title="YouTube video player" frameborder="0" 
allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; 
picture-in-picture" allowfullscreen></iframe>

Something else happens in the video that may go unnoticed at first. This effect is known as perceptual blindness. It is explained by the fact that as we focus on a specific task our brains tend to filter out information that is irrelevant to that task. However we don't always know what information is essential and what is not. For example when we study for an exam concentrating on a specific part of a study, leaving relevant information out.

Applying oneself to a given task lessens the occurrence of perceptual blindness. In other words, practice develops one's ability to distinguish between relevant and irrelevant information.

One way in which perceptual blindness manifests itself in programming practice is when concentrating on a specific part of a program draws attention away from seemingly correct, but yet erroneous parts. For instance, while inspecting the correctness of a program's output a programmer may fixate on the print statements and mistakenly neglect some aspects of the logic.

Likewise a programmer may focus on the most complicated aspect of a program featuring a loop when in fact the error lies somewhere else. An example of this is the program below, which is used to calculate the average of user inputted values. It contains an error and when searching for it the loop is typically the first target of focus.


```cs

int values = 0;
int sum = 0;

while (true) 
{
  Console.WriteLine("Provide a value, a negative value ends the program");
  int value = Convert.ToInt32(Console.ReadLine());
  if (value < 0) 
  {
    break;
  }

  values = values + 1;
  sum = sum + value;
}

if (sum == 0) 
{
  Console.WriteLine("The average of the values could not be calculated.");
} 
else 
{
  Console.WriteLine("Average of values: " + (1.0 * sum / value));
}
```

**Question:** Can you spot what is wrong with the code above? 

We will find the error later on in this part. The answer is also at the bottom of the page. DON'T SPOIL YOURSELF, read the whole part first!

Perceptual blindness is something that one cannot be eliminated completely. However there are ways by which a programmer can lessen its effect. 

1) Taking breaks, which requires that work is begun early. 
2) Code comments, proper naming of things. 
3) "Debugging" prints are example of things that are also helpful.

## Commenting the Source Code

Comments have many purposes and one of them is explaining how the code works to oneself. The execution of a relatively simple program is described below through the use of comments.

```cs
/*
 Prints the numbers from ten to one. Each number is printed on its own line.
*/

// We create an integer variable named value,
// assigning the value 10 to it.

int value = 10;

// The loop execution continues until
// the value of the variable named value is less than or equal to zero. 

while (value > 0) {
    // We print out the value in the variable and a new line.
    Console.WriteLine(value);
    // We decrement the value by one.
    value = value - 1;
}
```

Comments have no impact on the execution of the program. The program works in the same way with the comments as it does without them.

In real development the goal is for the source code to be self documenting. This means that the functionality of the program should be evident from the way classes, methods and variables are named.

The example can be "commented out" by encapsulating the code into an appropriately named method. Below are two examples of methods that do this. 

```cs
public static void PrintValuesFromTenToOne() 
{
  int value = 10;
  while (value > 0) 
  {
    Console.WriteLine(value);
    value = value - 1;
  }
}
```

```cs
public static void PrintValuesFromLargestToSmallest(int start, int end) 
{
  while (start >= end) {
    Console.WriteLine(start);
    start = start - 1;
  }
}
```

## Searching for Errors with Print Debugging

One skill in programming is the ability to test and debug when searching for errors. The simplest way to search for errors is to use so called print debugging, which in practice involves adding messages to certain lines of code. These messages are used to follow the program's execution and can contain values of variables in the program.

Let's inspect the program used to calculate the average of non negative values.


```cs

int values = 0;
int sum = 0;

while (true) 
{
  Console.WriteLine("Provide a value, a negative value ends the program");
  int value = Convert.ToInt32(Console.ReadLine());
  if (value < 0) 
  {
    break;
  }

  values = values + 1;
  sum = sum + value;
}

if (sum == 0) 
{
  Console.WriteLine("The average of the values could not be calculated.");
} 
else 
{
  Console.WriteLine("Average of values: " + (1.0 * sum / value));
}
```

Had the program contained an error. Print debugging could have been used to unravel its functionality by adding print statements in the appropriate places. The example below contains one possible example of a program containing print debug statements.

```cs

int values = 0;
int sum = 0;

while (true) 
{
  Console.WriteLine("-- values: " + values + ", sum: " + sum);

  Console.WriteLine("Provide a value, a negative value ends the program");
  int value = Convert.ToInt32(Console.ReadLine());
  if (value < 0) 
  {
    Console.WriteLine("-- value is negative, exiting loop");
    break;
  }

  values = values + 1;
  sum = sum + value;
}

Console.WriteLine("-- loop exited");
Console.WriteLine("-- values: " + values + ", sum: " + sum);

if (sum == 0) 
{
  Console.WriteLine("The average of the values could not be calculated.");
} 
else 
{
  Console.WriteLine("Average of values: " + (1.0 * sum / value));
}
```

When a program is executed multiple times with appropriate inputs the hidden error is often found. Coming up with relevant inputs is a skill in its own. It's essential to test the circumstances where the program execution could be exceptional. 

**There are no exercises. Move along.**

**Answer:** The last variable in the code is called **value** when it should be called **values**. We are calling for a variable which was defined inside the loop rather than the one we want.
