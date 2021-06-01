---
title: "Arrays"
parent: "Part 3 - Data Structures"
permalink: /part3/3/
nav_order: 3
published: true
---

# Arrays

Earlier we got familiar with a List. From the view point of a programmer the size of List is unlimited. But when you actually create the List a limited space is reserved in the memory of computer. When the List runs out of space a larger space is reserved and the data from previous space is copied to the new one.

Even though a List is simple to use sometimes we need the ancestor of the List, which is an array.

An array contains a limited amount of numbered spots or indices for values. The length or size of an array is the amount of these spots. The values in an array are called elements.

## Creating an Array

There are two ways to create an array. In the first one you have to explicitly define the size upon the creating. This is how you create an array to hold three integers.

```cs
int[] numbers = new int[3];
```

An array is declared by adding square brackets after the type of the elements it contains. A new Array is created by calling **new** followed by the type of the elements, square brackets and the number of the elements.

An array to hold 5 strings can be created like this.

```cs
string[] strings = new string[5];
```

## Assigning and Accessing Elements

An element of an array is referred to by its index. In the example below we create an array to hold 3 integers and then assigning values to the indices 0 and 2. After that we print the values.

```cs
int[] numbers = new int[3];
numbers[0] = 2;
numbers[2] = 5;
// numbers[1] is empty

Console.WriteLine(numbers[0]);
Console.WriteLine(numbers[2]);
```

Assigning a value to a specific spot of an array works much like assigning a value in a normal variable, but in the array you must specify the index. The index is an integer and it's value is between [0, length of the array - 1]. For example an array to hold 5 elements has indices 0, 1, 2, 3, and 4.

```cs
int[] numbers = new int[5];
numbers[0] = 42;
numbers[1] = 13;
numbers[2] = 12;
numbers[3] = 7;
numbers[4] = 1;

Console.WriteLine("Which index should we access? ");
int index = Convert.ToInt32(Console.ReadLine());

Console.WriteLine(numbers[index]);
```

## Size of an Array and Iterating

You can find out the size of an array through the property **Length**. Note that this is not a method call, so numbers.Length() doesn't work.

```cs
int[] numbers = new int[4];

numbers[0] = 12;
numbers[1] = 42;
numbers[2] = 37;
numbers[3] = 9;

Console.WriteLine("The array has " + numbers.Length + " elements:");
for (int i = 0; i < numbers.Length; i++)
{
  Console.WriteLine(numbers[i]);
}
```

```console
The array has 4 elements:
12
42
37
9
```

If the index is pointing outside the array we get an **IndexOutOfRangeException**. This error tells that the array doesn't contain the given index. 

The next example is a program that first asks the user to enter how many numbers and then enter the number values. Finally it prints back the numbers in the same order. The numbers are stored in an array.

```cs
Console.WriteLine("How many numbers? ");
int howMany = Convert.ToInt32(Console.ReadLine());

int[] numbers = new int[howMany];

Console.WriteLine("Enter the numbers:");

int index = 0;
while (index < numbers.length) {
    numbers[index] = Convert.ToInt32(Console.ReadLine());
    index = index + 1;
}


Console.WriteLine("Here are the numbers again:");

index = 0;
while (index < numbers.length) {
    Console.WriteLine(numbers[index]);
    index = index + 1;
}
```
An execution of the program might look like this.

```console
How many numbers? 
> 4 
Enter the numbers: 
> 4 
> 8
> 2 
> 1 
Here are the numbers again: 
4 
8 
2 
1
```

## Type of the Elements

You can create an array stating the type of the elements of the array followed by square brackets. Therefore the elements of the array can be of any type.

```cs
string[] months = new string[12];
double[] approximations = new double[100];

months[0] = "January";
approximations[0] = 3.14;
```

Every programmer should know a bit about the structure of the memory used by a computer program. Each variable, let it be primitive or reference type, is saved in the memory. Each variable has a size of defined number of bits (zeros and ones). The value of the variable is also represented in bits.

The reference of the array object is actually information about the location of the data. By stating **array[0]** we refer to the first element of the array. The statement **array[0]** can also be read: *"Go to the beginning of the array and move forward the size of variable. Return the variable chunk of data."*

The size of an integer variable in C# is 32 bits. One bit is reserved for the plus or minus sign, so the largest possible number to present in int is 2^31 - 1. When you create an integer array of 4 elements, 4 * 32 bits of memory is allocated to hold the integers. When you access **array[2]** 32 bits are read starting from beginning of the array + 2 * 32 bits.

Some programming languages try to make sure the programmer don't go "in the wrong area". If compiler doesn't cause the exception when we say **array[-1]** we would find out the data located just before the array in the memory of the program. In such case there wouldn't be anything preventing us from writing a program using the whole memory.

## Array as a Parameter of a Method

You can also use arrays as a parameter of a method.

```cs
public static void ListElements(int[] integerArray)
{
  Console.WriteLine("The elements of the array are: ");
  int index = 0;
  while (index < integerArray.Length)
  {
    int number = integerArray[index];
    Console.Write(number + " ");
    index = index + 1;
  }

  Console.WriteLine("");
}
```

The method in action.

```cs
int[] numbers = new int[3];
numbers[0] = 1;
numbers[1] = 2;
numbers[2] = 3;

ListElements(numbers);
```

```console
The elements of the array are: 
1 2 3 
```

Because an array is a reference type its value is a reference to the information contained. When you use an array as a parameter of a method the method receives a copy of reference to the array.

## Shorter Way to Create an Array

There's also a shortcut to create an array. Here we create an array to hold 3 integers, and initiate it with values 100, 1 and 42 in it:

```cs
int[] numbers = {100, 1, 42};
```

Apart from calling for **new** we can initialize an array with a block that contains comma separated values to be assigned in the array. This works for all the types. Below we initialize an array of strings and an array of floating point numbers. Finally the values are printed.

```cs
string[] arrayOfStrings = {"Mike L.", "Mike P.", "Mike V."};
double[] arrayOfFloatingpoints = {1.20, 3.14, 100.0, 0.6666666667};

for (int i = 0; i < arrayOfStrings.Length; i++) {
    Console.WriteLine(arrayOfStrings[i] + " " +  arrayOfFloatingpoints[i]);
}
```

```console
Mike L. 1.2
Mike P. 3.14
Mike V. 100
```

When you initialize an array with a block the length of the array is precisely the number of the values specified in the block. The values of the block are assigned to the array in the order specified. 

```cs
// index           0   1    2    3   4   5     6     7
int[] numbers = {100,  1,  42,  23,  1,  1, 3200, 3201};

// prints the number at index 0
Console.WriteLine(numbers[0]);
// prints the number at index 2
Console.WriteLine(luvut[2]);
```

Just like in Lists you can't access an index outside of the array.

**You can now do the exercises for arrays.**
