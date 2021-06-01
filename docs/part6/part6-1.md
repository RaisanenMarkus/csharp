---
title: "User Interfaces"
parent: "Part 6 - User Interfaces"
permalink: /part6/1/
nav_order: 1
published: true
---

# Separating the User Interface from Program Logic

Let's examine the process of implementing a program and separating different areas of responsibility from each other. The program asks the user to write words until they write the same word twice.


```console
Write a word:
> carrot 
Write a word:
> turnip 
Write a word:
> potato 
Write a word:
> celery 
Write a word:
> potato 
You wrote the same word twice!
```

Let's build this program piece by piece. One of the challenges is that it is difficult to decide how to approach the problem, or how to split the problem into smaller subproblems, and from which subproblem to start. There is no one clear answer -- sometimes it is good to start from the problem domain and its concepts and their connections, sometimes it is better to start from the user interface.

We could start implementing the user interface by creating a class UserInterface. 

```cs
public class UserInterface
{
  public UserInterface() 
  {

  }

  public void Start()
  {
    // Do something...
  }
}
```

Creating and starting up a user interface can be done as follows.

```cs
public static void Main(string[] args) 
{  
  UserInterface userinterface = new UserInterface();
  userinterface.Start();
}
```  

## Looping and Quitting

This program has (at least) two "sub-problems". The first problem is continuously reading words from the user until a certain condition is reached. We can outline this as follows.


```cs
public class UserInterface
{
  public UserInterface() 
  {

  }

  public void Start()
  {
    while(true)
    {
      Console.WriteLine("Enter a word:");
      string word = Console.ReadLine();

      if(/*stop condition here*/) {
        break;
      }
    }
    Console.WriteLine("You gave the same word twice!");
  }
}
```

The program continues to ask for words until the user enters a word that has already been entered before. Let us modify the program so that it checks whether the word has been entered or not. We don't know yet how to implement this functionality, so let us first build an outline for it.

```cs
public class UserInterface
{
  public UserInterface() 
  {

  }

  public void Start()
  {
    while(true)
    {
      Console.WriteLine("Enter a word:");
      string word = Console.ReadLine();
      if(AlreadyEntered(word)) {
        break;
      }
    }
    Console.WriteLine("You gave the same word twice!");
  }
}

  public bool AlreadyEntered(string word) 
  {
    // do something here
    return false;
  }
}
```

It's a good idea to test the program continuously, so let's make a test version of the method:

```cs
public bool AlreadyEntered(string word) 
{
  if (word == "end") 
  {
    return true;
  }
  return false;
}
```

Now the loop continues until the input equals the word "end":

```console
Write a word:
> carrot 
Write a word:
> turnip 
Write a word:
> potato 
Write a word:
> celery 
Write a word:
> end
You wrote the same word twice!
```

The program doesn't completely work yet, but the first sub-problem - quitting the loop when a certain condition has been reached - has now been implemented.

## Storing Relevant Information

Another sub-problem is remembering the words that have already been entered. A list is a good structure for this purpose.

```cs
public class UserInterface
{
  private List<string> words;

  public UserInterface() 
  {
    this.words = new List<string>();
  }

  public void Start()
  {
    while(true)
    {
      Console.WriteLine("Enter a word:");
      string word = Console.ReadLine();

      if(AlreadyEntered(word)) {
        break;
      }
    }
    Console.WriteLine("You gave the same word twice!");
  }
  public bool AlreadyEntered(string word) 
  {
    if (word == "end") 
    {
      return true;
    }
    return false;
  }
}
```

When a new word is entered, it has to be added to the list of words that have been entered before. This is done by adding a line that updates our list to the while-loop:

```cs
while(true)
{
  Console.WriteLine("Enter a word:");
  string word = Console.ReadLine();

  if (AlreadyEntered(word))
  {
    break;
  }
  // adding the word to the list of previous words
  this.words.Add(word);
}
```

The whole user interface now looks as follows.

```cs
public class UserInterface
{
  private List<string> words;

  public UserInterface() 
  {
    this.words = new List<string>();
  }

  public void Start()
  {
    while(true)
    {
      Console.WriteLine("Enter a word:");
      string word = Console.ReadLine();

      if (AlreadyEntered(word))
      {
        break;
      }
      // adding the word to the list of previous words
      this.words.Add(word);
    }
    Console.WriteLine("You gave the same word twice!");
  }

  public bool AlreadyEntered(string word) 
  {
    if (word == "end") 
    {
      return true;
    }
    return false;
  }
}
```

Again, it is a good idea to test that the program still works. For example, it might be useful to add a test print to the end of the start-method to make sure that the entered words have really been added to the list.

```cs
// test print to check that everything still works
words.ForEach(Console.WriteLine);
```

## Combining the Solutions to Sub Problems

Let's change the method 'AlreadyEntered' so that it checks whether the entered word is contained in our list of words that have been already entered.

```cs
public bool AlreadyEntered(string word) 
{
  return this.words.Contains(word);
}
```

Now the application works as intended.

## Objects as a Natural Part of Problem Solving

We just built a solution to a problem where the program reads words from a user until the user enters a word that has already been entered before. Our example input was as follows:


```console
Write a word:
> carrot 
Write a word:
> turnip 
Write a word:
> potato 
Write a word:
> celery 
Write a word:
> potato 
You wrote the same word twice!
```

We came up with the following solution:


```cs
public class UserInterface
{
  private List<string> words;

  public UserInterface() 
  {
    this.words = new List<string>();
  }

  public void Start()
  {
    while(true)
    {
      Console.WriteLine("Enter a word:");
      string word = Console.ReadLine();

      if (AlreadyEntered(word))
      {
        break;
      }
      // adding the word to the list of previous words
      this.words.Add(word);
    }
    Console.WriteLine("You gave the same word twice!");
  }

  public bool AlreadyEntered(string word) 
  {
    return this.words.Contains(word);
  }
}
```

From the point of view of the user interface, the support variable 'words' is just a detail. The main thing is that the user interface remembers the set of words that have been entered before. The set is a clear distinct "concept" or an abstraction. Distinct concepts like this are all potential objects: when we notice that we have an abstraction like this in our code, we can think about separating the concept into a class of its own.

## WordSet

Let's make a class called 'WordSet'. After implenting the class, the user interface's start method looks like this:

```cs
while(true)
{
  if (words.Contains(word))
  {
    break;
  }
  wordSet.Add(word);
}
Console.WriteLine("You gave the same word twice!");
```

From the point of view of the user interface, the class WordSet should contain the method **bool Contains(string word)**, that checks whether the given word is contained in our set of words, and the method **void Add(String word)**, that adds the given word into the set.

We notice that the readability of the user interface is greatly improved when it's written like this.

The outline for the class 'WordSet' looks like this:

```cs
public class WordSet 
{
  // object variable(s)

  public WordSet() 
  {
    // constructor
  }

  public bool Contains(string word) 
  {
    // implementation of the contains method
    return false;
  }

  public void Add(string word) 
  {
    // implementation of the add method
  }
}
```

## Earlier Solution as Part of Implementation

We can implement the set of words by making our earlier solution, the list, into an object variable:

```cs
public class WordSet 
{
  private List<string> words;

  public WordSet() 
  {
    this.words = new List<string>();
  }

  public bool Contains(string word) 
  {
    return this.words.Contains(word);
  }

  public void Add(string word) 
  {
    this.words.Add(word);
  }
}
```

Now our solution is quite elegant. We have separated a distinct concept into a class of its own, and our user interface looks clean. All the "dirty details" have been encapsulated neatly inside an object.

Let's now edit the user interface so that it uses the class WordSet. The class is given to the user interface as a parameter.

```cs
public class UserInterface
{
  private WordSet wordSet;

  public UserInterface(WordSet wordSet) 
  {
    this.wordSet = wordSet;
  }

  public void Start()
  {
    while(true)
    {
      Console.WriteLine("Enter a word:");
      string word = Console.ReadLine();

      if (this.wordSet.Contains(word))
      {
        break;
      }
      // adding the word to the list of previous words
      this.wordSet.Add(word);
    }
    Console.WriteLine("You gave the same word twice!");
  }
}
```

Starting the program is now done as follows:

```cs
public static void Main(string[] args) 
{  
  WordSet set = new WordSet();
  UserInterface userinterface = new UserInterface(set);
  userinterface.Start();
}  
```

## Changing the Implementation of a Class

We have arrived at a situation where the class 'WordSet' "encapsulates" a List. Is this reasonable? Perhaps. This is because we can make other changes to the class if we so desire, and before long we might arrive into a situation where the word set has to be, for example, saved into a file. If we make all these changes inside the class WordSet without changing the names of the methods that the user interface uses, we don't have to modify the actual user interface at all.

The main point here is that changes made inside the class WordSet don't affect the class UserInterface. This is because the user interface uses WordSet through the methods that it provides -- these are called its public interfaces.

## Implementing New Functionality: Palindromes

In the future, we might want to augment the program so that the class 'WordSet' offers some new functionalities. If, for example, we wanted to know how many of the entered words were palindromes, we could add a method called **Palindromes** into the program.

```cs
public void Start()
{
  while(true)
  {
    Console.WriteLine("Enter a word:");
    string word = Console.ReadLine();

    if (this.wordSet.Contains(word))
    {
      break;
    }
    // adding the word to the list of previous words
    this.wordSet.Add(word);
  }
  Console.WriteLine("You gave the same word twice!");
  Console.WriteLine(this.wordSet.Palindromes() + " of the words were palindromes.");
}
```

The user interface remains clean, because counting the palindromes is done inside the 'WordSet' object. The following is an example implementation of the method.

```cs
public int Palindromes() 
{
  int count = 0;

  foreach (string word in this.words)) 
  {
    if (IsPalindrome(word)) 
    {
      count++;
    }
  }

  return count;
}

public bool IsPalindrome(string word) 
{
  int length = word.Length;
  int end = word.Length - 1;
  for (int i = 0; i < length / 2; i++)
  {
      if (word[i] != word[end - i])
          return false;
  }
  return true;
}
```

The method **Palindromes** uses the helper method **IsPalindrome** to check whether the word that's given to it as a parameter is, in fact, a palindrome.

When concepts have been separated into different classes in the code, recycling them and reusing them in other projects becomes easy. For example, the class 'WordSet' could be well be used in a graphical user interface, and it could also part of a mobile phone application. In addition, testing the program is much easier when it has been divided into several concepts, each of which has its own separate logic and can function alone as a unit.

## Programming Tips

In the larger example above, we were following the advice given here.

* Proceed with small steps
  * Try to separate the program into several sub-problems and work on only one sub-problem at a time
  * Always test that the program code is advancing in the right direction, in other words: test that the solution to the sub-problem is correct
  * Recognize the conditions that require the program to work differently. In the example above, we needed a different functionality to test whether a word had been already entered before.

* Write as "clean" code as possible
  * Indent your code
  * Use descriptive method and variable names
  * Don't make your methods too long, not even the main method
  * Do only one thing inside one method
  * **Remove all copy-paste code**
  * Replace the "bad" and unclean parts of your code with clean code

* If needed, take a step back and assess the program as a whole. If it doesn't work, it might be a good idea to return into a previous state where the code still worked. As a corollary, we might say that a program that's broken is rarely fixed by adding more code to it.

Programmers follow these conventions so that programming can be made easier. Following them also makes it easier to read programs, to keep them up, and to edit them in teams.


## From One Entity to Many Parts

Let's examine a program that asks the user to enter exam points and turns them into grades. Finally, the program prints the distribution of the grades as stars. The program stops reading inputs when the user inputs an empty string. An example program looks as follows:

```console
Points:
> 91 
Points:
> 98 
Points:
> 103 
Impossible number. 
Points:
> 90 
Points:
> 89 
Points:
> 89 
Points:
> 88 
Points:
> 72 
Points:
> 54 
Points:
> 55 
Points: 
51 
Points:
> 49 
Points:
> 48 
Points:
>

5: *** 
4: *** 
3: * 
2: 
1: *** 
0: **
```

As almost all programs, this program can be written into main as one entity. Here is one possibility.

```cs
public class Program 
{
  public static void Main(string[] args) 
  {
    List<int> grades = new List<int>();

    while (true) {
      Console.WriteLine("Points:");
      string input = Console.ReadLine();
      if (input =0 "") 
      {
          break;
      }
      int score = Conver.ToInt32(input);

      if (score < 0 || score > 100) 
      {
        Console.WriteLine("Impossible number.");
        continue;
      }

      int grade = 0;
      if (score < 50) 
      {
        grade = 0;
      } 
      else if (score < 60) 
      {
        grade = 1;
      } 
      else if (score < 70) 
      {
        grade = 2;
      } 
      else if (score < 80) 
      {
        grade = 3;
      } 
      else if (score < 90) 
      {
        grade = 4;
      } 
      else 
      {
        grade = 5;
      }

      grades.Add(grade);
    }

    Console.WriteLine("");
    int grade = 5;
    while (grade >= 0) 
    {
      int stars = 0;
      foreach(int received in grades) 
      {
        if (received == grade) 
        {
          stars++;
        }
      }

      Console.Write(grade + ": ");
      while (stars > 0) 
      {
        Console.Write("*");
        stars--;
      }
      Console.WriteLine("");
      grade = grade - 1;
    }
  }
}
```

Let's separate the program into smaller chunks. This can be done by identifying several discrete areas of responsibility within the program. Keeping track of grades, including converting scores into grades, could be done inside a different class. In addition, we could create a new class for the user interface.

## Program Logic

Program logic includes parts that are crucial for the execution of the program, like functionalities that store information. From the previous example, we can separate the parts that store grade information. From these we can make a class called 'GradeRegister', which is responsible for keeping track of the numbers of different grades students have received. In the register, we can add grades according to scores. In addition, we can use the register to ask how many people have received a certain grade.

An example class follows.

```cs
public class GradeRegister 
{
  private List<int> grades;
  
  public GradeRegister() 
  {
    this.grades = new List<int>();
  }

  public void AddGradeBasedOnPoints(int points) 
  {
    this.grades.add(PointsToGrades(points));
  }

  public int NumberOfGrades(int grade) 
  {
    int count = 0;
    foreach(int received in this.grades) 
    {
      if (received == grade) 
      {
          count++;
      }
    }
    return count;
  }
  
  public static int PointsToGrades(int points) 
  {
    int grade = 0;
    if (points < 50) 
    {
      grade = 0;
    } 
    else if (points < 60) 
    {
      grade = 1;
    } 
    else if (points < 70) 
    {
      grade = 2;
    } 
    else if (points < 80) 
    {
      grade = 3;
    } 
    else if (points < 90) 
    {
      grade = 4;
    } 
    else 
    {
      grade = 5;
    }
    return grade;
    }
  }
}
```

When the grade register has been separated into a class, we can remove the functionality associated with it from our main program. The main program now looks like this.


```cs
public class Program 
{
  public static void Main(string[] args) 
  {
    GradeRegister register = new GradeRegister();

    while (true) {
      Console.WriteLine("Points:");
      string input = Console.ReadLine();
      if (input == "") 
      {
          break;
      }
      int score = Conver.ToInt32(input);

      if (score < 0 || score > 100) 
      {
        Console.WriteLine("Impossible number.");
        continue;
      }
      register.AddGradeBasedOnPoints(score);
    }

    Console.WriteLine("");
    int grade = 5;
    while (grade >= 0) 
    {
      int stars = register.NumberOfGrades(grade);
      Console.Write(grade + ": ");
      while (stars > 0) 
      {
        Console.Write("*");
        stars--;
      }
      Console.WriteLine("");

      grade = grade - 1;
    }
  }
}
```

Separating the program logic is a major benefit for the maintenance of the program. Since the program logic -- in this case the GradeRegister -- is its own class, it can also be tested separately from the other parts of the program. If you wanted to, you could copy the class GradeRegister and use it in your other programs. Below is an example of simple manual testing -- this experiment only concerns itself with a small part of the register's functionality.

```cs
GradeRegister register = new GradeRegister();
register.AddGradeBasedOnPoints(51);
register.AddGradeBasedOnPoints(50);
register.AddGradeBasedOnPoints(49);

Console.WriteLine("Number of students with grade 0 (should be 1): " + register.NumberOfGrades(0));
Console.WriteLine("Number of students with grade 1 (should be 2): " + register.NumberOfGrades(1));
```

## User Interface

Typically each program has its own user interface. We will create the class UserInterface and separate it from the main program. The user interface receives a grade register for storing the grades as a parameter for the constructor.

When we now have a separate user interface at our disposal, the main program that initializes the whole program becomes very clear.

```cs
public class Program 
{
  public static void Main(String[] args) 
  {
    GradeRegister register = new GradeRegister();

    UserInterface userInterface = new UserInterface(register);
    userInterface.Start();
  }
}
```

Let's have a look at how the user interface is implemented. There are two essential parts to the UI: reading the points, and printing the grade distribution.

```cs
public class UserInterface 
{
  private GradeRegister register;

  public UserInterface(GradeRegister register) 
  {
    this.register = register;
  }

  public void Start() 
  {
    ReadPoints();
    Console.WriteLine("");
    PrintGradeDistribution();
  }

  public void ReadPoints() 
  {
  }

  public void PrintGradeDistribution() 
  {
  }
}
```

We can copy the code for reading exam points and printing grade distribution nearly as is from the previous main program. In the program below, parts of the code have indeed been copied from the earlier main program, and new method for printing stars has also been created -- this clarifies the method that is used for printing the grade distribution.

```cs
public class UserInterface 
{
  private GradeRegister register;

  public UserInterface(GradeRegister register) 
  {
    this.register = register;
  }

  public void Start() 
  {
    ReadPoints();
    Console.WriteLine("");
    PrintGradeDistribution();
  }

  public void ReadPoints() 
  {
    while (true) 
    {
      Console.WriteLine("Points:");
      string input = Console.ReadLine();
      if (input =0 "") 
      {
        break;
      }
      int score = Conver.ToInt32(input);

      if (score < 0 || score > 100) 
      {
        Console.WriteLine("Impossible number.");
        continue;
      }
      register.AddGradeBasedOnPoints(score);
    }
  }

  public void PrintGradeDistribution() 
  {
    int grade = 5;
    while (grade >= 0) 
    {
      int stars = register.NumberOfGrades(grade);
      Console.Write(grade + ": ");
      PrintStars(stars);
      Console.WriteLine();

      grade = grade - 1;
    }

  public static void PrintStars(int stars) 
  {
    while (stars > 0) 
    {
      Console.Write("*");
      stars--;
    }
  }
  }
}
```
