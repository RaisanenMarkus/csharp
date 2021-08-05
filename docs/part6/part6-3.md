---
title: "Exercises"
parent: "Part 6 - User Interfaces"
permalink: /part6/3/
nav_order: 3
published: true
---

# Part 6 - Exercises

## User Interfaces

### EXERCISE 6-1: Grade Register

The exercise base contains the **GradeRegister** from the material. In this exercise you will further develop the program, so that it can calculate the average of grades and exam results.

#### Section 1 - Average grade

create the method **public double AverageOfGrades()** for the class **GradeRegister**. It should return the average of the grades, rounded to 2 decimals. If the register contains no grades, the method should return **-1**. Use the **grades** list to calculate the average. Example:

```cs
GradeRegister register = new GradeRegister();
register.AddGradeBasedOnPoints(93);
register.AddGradeBasedOnPoints(91);
register.AddGradeBasedOnPoints(92);
register.AddGradeBasedOnPoints(88);

Console.WriteLine(register.AverageOfGrades());
```

```console
4.75
```

#### Section 2 - Average points

Give the class GradeRegister a new object variable: a list where you will store the exam points every time that the method **AddGradeBasedOnPoints** is called. After this addition, create a method **public double AverageOfPoints()** that calculates and returns the average of the exam points, rounded to 2 decimals. If there are no points added to the register, the method should return the number -1. Example:

```cs
GradeRegister register = new GradeRegister();
register.AddGradeBasedOnPoints(93);
register.AddGradeBasedOnPoints(91);
register.AddGradeBasedOnPoints(92);

Console.WriteLine(register.AverageOfPoints());
```

```console
92
```

#### Section 3 - Prints in the user interface

As a final step, add the methods implemented above as parts of the user interface. When the program prints the grade distribution, it should also print the averages of the points and the grades.

```console
Points:
> 82 
Points:
> 83
Points:
> 96 
Points: 
> 51 
Points:
> 48 
Points:
> 56 
Points:
> 61 
Points:
>

5: * 
4: ** 
3: 
2: * 
1: ** 
0: * 
The average of points: 68.14
The average of grades: 2.43
```

### EXERCISE 6-2: Joke Manager

NOTICE! This exercise does **NOT HAVE TESTS**. It is up to you to decide, when the exercise is ready. **I WILL CHECK THEM, SO DON'T CHEat.**

NOTICE 2! This is worth double the points, so 4 in total (2 per section).

The exercise base contains the following program that has been written "in the main".

```cs
using System;
using System.Collections.Generic;

namespace exercise_135
{
  class Program
  {
    public static void Main(string[] args)
    {
      List<string> jokes = new List<string>();
      Console.WriteLine("What a joke!");

      while (true)
      {
        Console.WriteLine("Commands:");
        Console.WriteLine(" 1 - add a joke");
        Console.WriteLine(" 2 - draw a joke");
        Console.WriteLine(" 3 - list jokes");
        Console.WriteLine(" X - stop");

        string command = Console.ReadLine();

        if (command == "X")
        {
          break;
        }

        if (command == "1")
        {
          Console.WriteLine("Write the joke to be added:");
          string joke = Console.ReadLine();
          jokes.Add(joke);
        }
        else if (command == "2")
        {
          Console.WriteLine("Drawing a joke.");

          if (jokes.Count == 0)
          {
            Console.WriteLine("Jokes are in short supply.");
          }
          else
          {
            Random draw = new Random();
            int index = draw.Next(0, jokes.Count);
            Console.WriteLine(jokes[index]);
          }

        }
        else if (command == "3")
        {
          Console.WriteLine("Printing the jokes.");
          foreach (string joke in jokes)
          {
            Console.WriteLine(joke);
          }
        }
      }
    }
  }
}
```

The application is in practice a storage for jokes. You can add jokes, get a randomized joke, and the stored jokes can be printed. In this exercise the program is divided into parts in a guided manner.

#### Section 1 - Joke manager

Create a class called **JokeManager** and move the functionality to manage jokes in it. The class must have a parameter-free constructor, and the following methods:

* **public void AddJoke(string joke)** - adds a joke to the manager.
* **public string DrawJoke()** - chooses one joke at random and returns it. It there are no jokes stored in the joke manager, the method should return the string "Jokes are in short supply.".
* **public void PrintJokes()** - prints all the jokes stored in the joke manager.

An example of how to use the class:

```cs
JokeManager manager = new JokeManager();
manager.AddJoke("What is red and smells of blue paint? - Red paint.");
manager.AddJoke("What is blue and smells of red paint? - Blue paint.");

Console.WriteLine("Drawing jokes:");
for (int i = 0; i < 5; i++)
{
  Console.WriteLine(manager.DrawJoke());
}

Console.WriteLine("");
Console.WriteLine("Printing jokes:");
manager.PrintJokes();
```

Below is a possible output of the program. Notice that the jokes will probably not be drawn as in this example.

```console
Drawing jokes: 
What is blue and smells of red paint? - Blue paint. 
What is red and smells of blue paint? - Red paint. 
What is blue and smells of red paint? - Blue paint. 
What is blue and smells of red paint? - Blue paint. 
What is blue and smells of red paint? - Blue paint.

Printing jokes: 
What is red and smells of blue paint? - Red paint. 
What is blue and smells of red paint? - Blue paint.
```

#### Section 2 - User Interface

Create a class called **UserInterface** and move the UI functionality of the program there. The class must have a constructor with one parameter: an instance of the JokeManager class. In addition, the class should have the method **public void Start()** that can be used to start the user interface.

The user interface should provide the user with the following commands:

* X - ending: exits the method start.
* 1 - adding: asks the user for the joke to be added to the joke manager, and then adds it.
* 2 - drawing: chooses a random joke from the joke manager and prints it. If there are no jokes in the manager, thi string "Jokes are in short supply." will be printed.
* 3 - printing: prints all the jokes stored in the joke manager.

An example of how to use the UI:

```cs
JokeManager manager = new JokeManager();
UserInterface ui = new UserInterface(manager);
ui.Start();
```

```console
Commands: 
 1 - add a joke 
 2 - draw a joke 
 3 - list jokes
  X - stop 
> 1 
Write the joke to be added:
> Did you hear about the claustrophobic astronaut? -- He just needed a little space. 
Commands:
 1 - add a joke
 2 - draw a joke
 3 - list jokes 
 X - stop 
> 3 
Printing the jokes. 
Did you hear about the claustrophobic astronaut? -- He just needed a little space. 
Commands:
 1 - add a joke
 2 - draw a joke
 3 - list jokes 
 X - stop 
> X
```

## Static

### EXERCISE 6-3: How Many Names

Our template has the **Person** class and some use for it in Main. create a **public static void HowManyNames(Person person)** for the **Main Program**, which prints the name and the amount of names as follows:

```cs
public static void Main(string[] args)
{
  Person ada = new Person("Ada Lovelace");
  Person jack = new Person("Jack The Ripper");
  Person mike = new Person("Mike The Incredible Magic Mouse");

  HowManyNames(ada);
  HowManyNames(jack);
  HowManyNames(mike);
}
```

```console
Ada Lovelace has 2 names.
Jack The Ripper has 3 names.
Mike The Incredible Magic Mouse has 5 names.
```

NOTICE! The **Console.WriteLine** is called from inside the method this time!

### EXERCISE 6-4: How Many Names in Person

Our template has the **Person class** and some use for it in Main. create a **public int HowManyNames()** in the **Person class**, which returns the amount of names a person has, like follows:

```cs
public static void Main(string[] args)
{
  Person ada = new Person("Ada Lovelace");
  Person jack = new Person("Jack The Ripper");
  Person mike = new Person("Mike The Incredible Magic Mouse");

  Console.WriteLine(ada + " has " ada.HowManyNames() + " names.");
  Console.WriteLine(jack + " has " jack.HowManyNames() + " names.");
  Console.WriteLine(mike + " has " mike.HowManyNames() + " names.");
}
```


