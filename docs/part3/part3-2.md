---
title: "Deeper into Lists"
parent: "Part 3 - Data Structures"
permalink: /part3/2/
nav_order: 2
published: true
---

# Deeper into Lists

If you don't need to keep track of a List index you can make use of the **foreach()** loop. It differs from the previous loops in that it has no separate condition for incrementing.

## Foreach() Loop

```cs
List<string> teachers = new List<string>();

teachers.Add("Simon");
teachers.Add("Samuel");
teachers.Add("Ann");
teachers.Add("Anna");

foreach (string teacher in teachers)
{
  Console.WriteLine(teacher);
}
```

The foreach() loop described above hides some parts of the for loop we practiced earlier. It goes through the teachers List's string variables one at a time and prints them to the console. 

## Removing from a List

The List's **RemoveAt(index)** method removes the value that is located at the index that's given as the parameter. The parameter is an integer.

```cs
// Create the List for storing strings.
List<string> list = new List<string>();

// Add three values to the List.
list.Add("First");
list.Add("Second");
list.Add("Third");

// Remove from index 1
list.RemoveAt(1);

// Retrieve the value from positions 0 and 1 of the List, and print them.
Console.WriteLine(list[0]);
Console.WriteLine(list[1]);
```

```console
First
Third
```

We can also use the method **Remove()** if we know the value of the item we want to remove.

```cs
// Create the List for storing strings.
List<string> list = new List<string>();

// Add three values to the List.
list.Add("First");
list.Add("Second");
list.Add("Third");

// Remove with value "Second".
list.Remove("Second");

// Retrieve the value from positions 0 and 1 of the List, and print them.
Console.WriteLine(list[0]);
Console.WriteLine(list[1]);
```

```console
First
Third
```

The methods work exactly the same way with integers, so be careful which method you use!

**NOTICE!** The method Remove() removes the first match it finds. If your List would contain multiples of the same value only the first one would be removed!

## Checking the Existence of a Value

List method **Contains()** can be used to check the existence of a value in a List. The method receives the value to be searched as its parameter and it returns a boolean type value indicating whether that value is stored in the List (True or False).

```cs
// Create the List for storing strings.
List<string> list = new List<string>();

// Add three values to the List.
list.Add("First");
list.Add("Second");
list.Add("Third");

Console.WriteLine("Can we find First: " + list.Contains("First"));


if (list.Contains("Second"))
{
  Console.WriteLine("We found second!");
}
```

```console
Can we find First: True
We found second!
```

## List as a Method Parameter

Like other variables a List can be used as a parameter to a method. When the method is defined to take a List as a parameter, the type of the parameter is defined as the type of List and the type of values contained in that List. Below the method **Print(List&lt;string&gt;)** prints one by one the values from a List.

```cs
public static void Print(List<string> list)
{
  foreach (string value in list)
  {
    Console.WriteLine(value);
  }
}
```

In the example below we use the method that was implemented above.

```cs
List<string> strings = new List<string>();

strings.Add("First");
strings.Add("Second");
strings.Add("Third");

Print(strings);
```

```console
First
Second
Third
```

The List variable is not dependent on parameter in the method call. In the program above the name of the List variable is **strings** but inside the method the variable is called **list**.

It's also possible to define multiple variables for a method. In the next example the method receives two parameters: a list of numbers and a threshold integer. It then prints all the numbers in the List that are smaller than the treshold parameter.

```cs
public static void PrintSmallerThan(List<int> numbers, int threshold) 
{
  foreach(int number in numbers)
  {
    if (number < threshold) 
    {
      Console.WriteLine(number);
    }
  }
}
```

Here we see it in action.

```cs
List<int> list = new List<int>();

list.Add(1);
list.Add(2);
list.Add(3);
list.Add(2);
list.Add(1);

PrintSmallerThan(list, 3);
```

```console
1
2
2
1
```

As before a method can also return a value. The methods that return values have the type of the return value in place of the **void** keyword and the actual returning of the value is done by the **return** command. 

The method below returns the Count property of the List, hence we use void as return value.

```cs
public static void Count(List<string> list)
{
  return list.Count;
}
```

You can also define own return values for methods. The method below calculates the average of the numbers in a List. If the List is empty it returns -1.

```cs
public static double Average(List<int> numbers) 
{
  if (numbers.Count == 0) 
  {
      return -1.0;
  }

  int sum = 0;
  foreach(int number in numbers) 
  {
      sum = sum + number;
  }

  return 1.0 * sum / numbers.Count;
}
```
## Copying the List to a Method Parameter

When variables such as integer are used as method parameters the value of the variable is copied for the method's use. The same occurs in case the parameter is a List.

Lists are reference type variables. This means that the value of the variable is a reference that points to the location that contains the information.

When a List is copied for a method's use the method receives the value reference of the List variable. **Method receives a reference to the real value of a reference type variable** and the method is able to modify the value of the original reference type variable. The List that the method receives as a parameter is the same List that is used in the program that calls the method.

Let's look at this with the following method.

```cs
public static void RemoveFirst(List<int> numbers)
{
  if (numbers.Count == 0)
  {
    return;
  }
  
  numbers.RemoveAt(0);
}
```

```cs
List<int> numbers = new List<int>();
numbers.Add(3);
numbers.Add(2);
numbers.Add(6);
numbers.Add(-1);

Console.WriteLine("First print: ");
numbers.ForEach(Console.WriteLine);

RemoveFirst(numbers);

Console.WriteLine("Second print: ");
numbers.ForEach(Console.WriteLine);

RemoveFirst(numbers);
RemoveFirst(numbers);
RemoveFirst(numbers);

Console.WriteLine("Third print: ");
numbers.ForEach(Console.WriteLine);
```

```console
First print: 
3
2
6
-1
Second print: 
2
6
-1
Third print: 
```

As you can see the methor **RemoveFirst(List&lt;int&gt;)** directly affects the List it was given as a parameter.

**NOTICE!** Instead of doing **Console.WriteLine(numbers)** to get the values from the List the annotation is **numbers.ForEach(Console.WriteLine);**!

## Summary of List Methods and Properties

You can find all the information about [**Lists here**](https://docs.microsoft.com/en-us/dotnet/api/system.collections.generic.list-1?view=netframework-4.8). 

* Adding to a List is done with the method **Add()** with a value to be added as a parameter.

```cs
List<int> numbers = new List<int>();
numbers.Add(3);
```

* The number of elements in a List can be discovered with the property **Count** which returns an integer.

```cs
List<int> numbers = new List<int>();
int amount = numbers.Count;
Console.WriteLine("Amount of integers in numbers: " + amount);
```

* You can retrieve a value from a certain index with the method **list[index]**.

```cs
List<int> numbers = new List<int>();
numbers.Add(3);
Console.WriteLine(numbers[0]);
```

* Removing elements is done with either **Remove()** or **RemoveAt()** depending if we remove with value or index.

```cs
List<string> list = new List<string>();
list.Add("First");
list.Add("Second");
list.Add("Third");
list.RemoveAt(0);
list.Remove("Third");
```

* Checking for the existence of a value is done with the method **Contains()**. It's provided the value being searched for as a parameter and it returns a boolean value.

```cs
List<string> list = new List<string>();
list.Add("First");
list.Contains("First");
```

* To iterate a List you use **ForEach()**.

```cs
List<int> numbers = new List<int>();
numbers.Add(3);
numbers.Add(2);

numbers.ForEach(Console.WriteLine);
```

**You can now do the exercises for Lists.**
