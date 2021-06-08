---
title: "Lists"
parent: "Part 3 - Data Structures"
permalink: /part3/1/
nav_order: 1
published: true
---

# Lists

In programming we often encounter situations where we want to handle lots of data. The method we've used so far is to define a separate variable for storing each value. This is not practical.

```cs
string word1;
string word2;
string word3;
// ...
string word10;
```

Programming languages offer tools to assist in storing a large quantity of data. We will next take a peek at the List, which is used for storing many values that are of the same type.

List is a premade tool in C# language that helps dealing with data in a list. It offers various methods including ones for adding values to the list, removing values from it and retrieving a value from a specific place in the list. The implementations have beed abstracted behind the List methods.

## Creating and Using Lists

For a List to be used it first needs be imported into the program. This is achieved by including the command **using System.Collections.Generic** at the top of the program. Below is an example program where an List is imported into the program.

To use a List it also has to be initialized. Below is an example where we create a List that holds integers called numbers.

```cs
using System.Collections.Generic;

public class Program 
{
    public static void Main(string[] args) 
    {
      List<int> numbers = new List<int>();
      // Rest of the code...
    }
}

```

Creating a new list is done with the command List\<type\> list = new List\<type\>() where type is the type of the values to be stored in the list. We create a list for storing strings in the example below.

```cs
List<string> strings = new List<string>();
```

The type of the List variable is List. When a list variable is initialized the type of the values to be stored is also defined. All the variables stored in a given list are of the same type. As such the type of a List that stores strings is **List\<string\>**. A new list is created with the command **new List<>()**.

## Defining the Type of Values That a List Can Contain

When defining the type of values that a list can include, the type is written the same way as when declaring variables. A list that includes int-type variables has to be defined in the form **List\<int\>** and a list that includes double-type variables is defined in the form **List\<double\>**.

You'll find examples below of creating lists that contain different types of values.

```cs
List<int> list = new List<int>();
list.Add(1);
```

```cs
List<double> list = new List<double>();
list.Add(4.2);
```

```cs
List<bool> list = new List<bool>();
list.Add(true);
```

```cs
List<string> list = new List<string>();
lista.Add("String is text");
```

Once a List has been created it assumes that all the variables are of the correct type. When storing the variables with a value the value of the said variable is stored.

```cs
List<int> integers = new List<int>();
int integer = 1;
integers.Add(integer);

List<double> doubles = new List<double>();
double d = 4.2;
doubles.Add(d);
```

## Adding to a List and Retrieving a Value from a Specific Place

The next example demonstrates the addition of a strings into a List containing strings. Addition is done with the list method **Add**, which takes the value to be added as a parameter. We then print the value at position zero.

```cs
public class WordListExample 
{
  public static void Main(string[] args) 
  {
    // create the word list for storing strings
    List<string> wordList = new List<string>();

    // add two values to the word list
    wordList.Add("First");
    wordList.Add("Second");

    // retrieve the value from position 0 of the word list, and print it
    Console.WriteLine(wordList[0]);
  }
}
```

Program writes the following.

```console
First
```

As can be seen the latter method retrieves the first value from the list when it is given the parameter 0. This is because list positions are counted starting from zero. The first value is found by wordList[0], the second value by wordList[1] and so on.

## Retrieving Information from a "Non-Existent" Place

If you try to retrieve information from a place that does not exist on the list the program will print a **ArgumentOutOfRangeException** error. In the example below two values are added to a list, then there is an attempt to print the value at place 2 on the list.

```cs
public class WordListExample 
{
  public static void Main(string[] args) 
  {
    // create the word list for storing strings
    List<string> wordList = new List<string>();

    // add two values to the word list
    wordList.Add("First");
    wordList.Add("Second");

    // retrieve the value from position 0 of the word list, and print it
    Console.WriteLine(wordList[2]);
  }
}
```

Since the indexing of the list elements starts with zero the program isn't able to find anything at place 2 and its execution ends with an error. Below is a description of the error message caused by the program.

```console
Unhandled exception. System.ArgumentOutOfRangeException: Index was out of range. 
    Must be non-negative and less than the size of the collection. (Parameter 'index')
    at System.Collections.Generic.List`1.get_Item(Int32 index)
    at WordListExample.Program.Main(String[] args) in ... Program.cs:line 13
```

The error message tells exactly what and where happened. First the error contains the error type **ArgumentOutOfRangeException**. Then it gives a possible correction. Next the error contains which method caused the error. In this case it would be the **get_Item(Int32 index)**. Last the error tells us which part of our code triggered the error.

When calling for List[index] we are actually calling method **System.Collections.Generic.List --> get_Item(Int32 index)**, which is a already built in method. 

## Indexing

In C# programming indexing always begins with zero. The list's first value is located at index 0, the second value at index 1, the third value at index 2, and so on. In programs an index is denoted with a variable called **i**.

Example list called **numbers** could contain something like this.

|i|0|1|2|3|4|
|-:|:-:|:-:|:-:|:-:|:-:|
|value|6|1|2|4||

In the list above the first value is 6 and the second value 1. If a new value was added to the list by calling the **Add** method with 8 as parameter the number 8 would be placed at index 4. It would be the fifth number in the list.

```cs
numbers.Add(8);
```

|i|0|1|2|3|4|
|-:|:-:|:-:|:-:|:-:|:-:|
|value|6|1|2|4|8|

Similarly by calling the method **numbers[index]** with the parameter 3 the fourth number in the list would retrieve the value 4.

## Iterating Over a List

Next we will examine methods that are used for going through the values on a list. Let's start with a simple example where we print a list containing four values.

```cs
List<string> teachers = new List<string>();

teachers.Add("Simon");
teachers.Add("Samuel");
teachers.Add("Ann");
teachers.Add("Anna");

Console.WriteLine(teachers[0]);
Console.WriteLine(teachers[1]);
Console.WriteLine(teachers[2]);
Console.WriteLine(teachers[3]);
```

```console
Simon
Samuel
Ann
Anna
```

What if there were more values on the list? What if we didn't know the number of values on the list?

The number of values on a list is provided with the list's **Count** property, which returns the number of elements the list contains. The number is an integer.

```cs
List<string> list = new List<string>();
Console.WriteLine("Number of values on the list: " + list.Count);
lista.add("First");
Console.WriteLine("Number of values on the list: " + list.Count);
lista.add("Second");
int values = list.Count;
Console.WriteLine("Number of values on the list: " + values);
```

```console
Number of values on the list: 0 
Number of values on the list: 1 
Number of values on the list: 2
```

**NOTICE!** The Count is not a method but a property. This means that when calling Count we do not add the round brackets in the end!

Let's make a new program that prints each index manually using a while loop. The printing works regardless of the number of elements.

```cs
List<string> teachers = new List<string>();

teachers.Add("Simon");
teachers.Add("Samuel");
teachers.Add("Ann");
teachers.Add("Anna");

int index = 0;
// Repeat when the variable `index` is smaller than the list size.
while (index < teachers.Count) 
{
  Console.WriteLine(teachers[index]);
  index = index + 1;
}
```

The for loop is extremely handy here. We can convert the loop above to a for loop.

```cs
List<string> teachers = new List<string>();

teachers.Add("Simon");
teachers.Add("Samuel");
teachers.Add("Ann");
teachers.Add("Anna");

for (int index = 0; index < teachers.Count; index++) 
{
    Console.WriteLine(teachers[index]);
}
```

```console
Simon
Samuel
Ann
Anna
```

Let's consider using a list to store integers.

```cs
List<int> numbers = new List<int>();

numbers.Add(1);
numbers.Add(2);
numbers.Add(3);
numbers.Add(4);

for (int i = 0; i < numbers.Count; i++) 
{
    int number = numbers[i];
    Console.WriteLine(number);
    // alternatively: Console.WriteLine(numbers[i]);
}
```

```console
1
2
3
4
```

Consider the difference of List index and its integer value. 
