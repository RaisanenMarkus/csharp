---
title: "Exercises"
parent: "Part 2 - Problem Solving"
permalink: /part2/5/
nav_order: 5
published: true
---

# Part 2 - Exercises

## Subproblems

### EXERCISE 2-1: Second Power

* Write a program that reads an integer from the user input and then prints the second power of the given integer i.e. the integer multiplied by itself.

```console
> 4
16
```

```console
> 5
25
```

```console
> -3
9
```

### EXERCISE 2-2: Square Root of Sum

* Write a program that reads two integers from the user and prints the square root of the sum of these integers. The program does not need to work with negative values.
* You can get the square root of an integer with the Math.Sqrt method like this.

```cs
int number = 42;
double squareRoot = Math.Sqrt(number);
Console.WriteLine(squareRoot);
```

```console
> 1 
> 0 
1
```

```console
> 5 
> 4 
3
```

```console
> 1 
> 35 
6
```

### EXERCISE 2-3: Absolute Value

* Write a program that reads an integer from the user. If the number is less than 0 it prints the number multiplied by -1. Otherwise the program prints the number itself. A few examples of the expected function below.

```console
> -3
3
```

```console
> 1
1
```

```console
> 0
0
```
### EXERCISE 2-4: Comparison

* Write a program that reads two integers from the user input. If the first number is greater than the second the program prints "(first) is greater than (second)." If the first number is less than the second the program prints "(first) is less than (second)." Otherwise the program prints "(first) is equal to (second)." The (first) and (second) should always be replaced with the actual numbers given by the user.

A few examples of the expected behaviour.

```console
> 8 
> 4 
8 is grEater than 4.
```

```console
> -3 
> 5 
-3 is less than 5.
```

```console
> 1 
> 1 
1 is equal to 1.
```

## More Loops

### EXERCISE 2-5: Iterating to Input

* Write a program that reads an integer from the user. Then the program prints numbers from 0 to the number given by the user. You can assume that the user always gives a positive number. Below is some examples of the wanted functionality. **You can use either a while-loop or a for-loop.**

```console
> 4
0
1
2
3
4
```

```console
> 1
0
1
```

### EXERCISE 2-6: Iterating to Hundred

* Write a program which reads an integer from the user. Then the program prints numbers from that number to 100. You can assume that the user always gives a number less than 100. Below are some examples of the wanted functionality.

```console
> 99
99
100
```

```console
> -4
-4
-3
-2
-1
0
1
... (lots of numbers in between) ...
98
99
100
```

### NOTICE!
* From now on the exercises might be as multiple section instructions. In the end you should still have **only one program per exercise** to return.  All sections are needed to count exercise as DONE.

### EXERCISE 2-7: Where to and From

#### Section 1
* Write a program which prints integers from 1 to a number given by the user.

```console
Where to? 
>3 
1 
2 
3
```

```console
Where to? 
>5 
1 
2 
3 
4 
5
```

Hint: the number read from the user is now the upper limit of the condition. Remember that **a <= b** means a is smaller or equal to b.

#### Section 2

* Ask the user for the starting point as well.

```console
Where to? 
>8 
Where from? 
>5
5 
6 
7 
8
```

* If the upper limit is larger than the starting point nothing is printed.

```
Where to? 
> 12 
Where from? 
> 16
```

Hint: Remember that the lower and the upper limits can be negative!

### EXERCISE 2-8: Numbers and Calculations

#### Section 1

* Implement a program that asks the user for numbers. The program first prints "Give numbers: " and then reads numbers until the user gives the number -1. When the user writes -1 the program prints "Thx! Bye!" and ends.

```console
Give numbers: 
> 5 
> 2 
> 4 
> -1 
Thx! Bye!
```

#### Section 2

* Extend the program so that it prints the sum of the numbers the user has written. Not including the -1. 

```console
Give numbers: 
> 5 
> 2 
> 4 
> -1 
Thx! Bye! 
Sum: 11
```

#### Section 3 
* Extend the program so that it also prints the number of numbers the user has written. Not including the -1. 

```console
Give numbers: 
> 5 
> 2 
> 4 
> -1 
Thx! Bye! 
Sum: 11
Numbers: 3
```

#### Section 4

* Extend the program so that it prints the average of the numbers the user has written. Not including the -1. 

```console
Give numbers: 
> 5 
> 2 
> 4 
> -1 
Thx! Bye! 
Sum: 11
Numbers: 3
Average: 3.666666666666
```

#### Section 5

* Extend the program so that it prints the number of even and odd numbers. Not including the -1.

```console
Give numbers: 
> 5 
> 2 
> 4 
> -1 
Thx! Bye! 
Sum: 11
Numbers: 3
Average: 3.666666666666
Even: 2
Odd: 1
```

### NOTICE!
* When you are writing a program whether it's an exercise or a personal project, figure out the types of parts the program needs to function and proceed by implementing them one part at a time. Make sure to test the program right after implementing each part.

* Never try solving the whole problem at once, because that makes running and testing the program in the middle of the problem solving process difficult. Start with something easy that you know you can do. When one part works you can move on to the next.

* Some of the exercises are already split into parts. However it's often the case in programming that these parts need to be split into even smaller parts. By running the program in smaller parts you ensures that the solution is moving in the right direction.

## Methods

* In these exercises we practice making and calling our own methods. 
* If the exercise template says **// Call your method here:"** call it once. Usually this is in the Main class.

### EXERCISE 2-9: Print Phrase

* Create a method called **PrintPhrase()** which prints the phrase "In a hole in the ground there lived a method." and a newline. Use WriteLine() and not just Write().

```cs
public static void Main(string[] args)
{
  // Call your method here:
  PrintPhrase();

}

// Write your method here:
public static void PrintPhrase() 
{

}
```

```console
In a hole in the ground there lived a method.
```
### EXERCISE 2-10: How Many Times

* Expand the previous program so that the main program asks the user for the number of times the phrase will be printed.

```cs
public static void Main(string[] args)
{
  // ask the user for the number of times that the phrase will be printed
  // use the while command to call the method a suitable number of times

}

// Write your method here:
public static void PrintPhrase() 
{

}
```

```console
How many times?
> 3
In a hole in the ground there lived a method.
In a hole in the ground there lived a method.
In a hole in the ground there lived a method.
```

## NOTICE!
* From now on when introducing methods we might not explicitly mention they must be located in the correct place. Methods cannot be defined e.g. inside other methods.

### EXERCISE 2-11: Print Until Number

* Create the following method in the exercise template **public static void PrintUntilNumber(int number)**. It should print the numbers from one to the number passed as a parameter. Two examples of the method's usage are given below.

```cs
public static void Main(string[] args) 
{
  PrintUntilNumber(5);
}
```

```console
1
2
3
4
5
```

```cs
public static void Main(string[] args) 
{
  PrintUntilNumber(3);
}
```

```console
1
2
3
```
### EXERCISE 2-12: From Number to One

* Create the following method in the exercise template **public static void PrintFromNumberToOne(int number)**. It should print the numbers from the number passed as a parameter down to one. Two examples of the method's usage are given below.

```cs
public static void Main(string[] args) 
{
  PrintFromNumberToOne(5);
}
```

```console
5
4
3
2
1
```

```cs
public static void Main(string[] args) 
{
  PrintFromNumberToOne(2);
}
```

```console
2
1
```

### EXERCISE 2-13: Division

* Write a method **public static void Division(int numerator, int denominator)** that prints the result of the division of the numerator by the denominator. Keep in mind that the result of the division of the integers is an integer. In this case we want the result to be a double.

### EXERCISE 2-14: Divisible in Range

* Write a method **public static void DivisibleByThreeInRange(int beginning, int end)** that prints all the numbers divisible by three in the given range. The numbers are to be printed in order from the smallest to the greatest.

```cs
public static void Main(string[] args) 
{
  DivisibleByThreeInRange(3, 6);
}
```

```console
3
6
```

```cs
public static void Main(string[] args) 
{
  DivisibleByThreeInRange(2, 10);
}
```

```console
3
6
9
```

### EXERCISE 2-15: Number Uno

* Write a method **public static int NumberUno()** that returns the value 1.

### EXERCISE 2-16: Word

* Write a method **public static string Word()**. The method must return a string of your choice.

### EXERCISE 2-17: Sum

* Expand the method **Sum(int, int, int, int)** in the exercise template so that it calculates and returns the sum of the numbers that are given as the parameters.
* Create the method using the following structure.

```cs
public static int Sum(int number1, int number2, int number3, int number4) 
{
  // write your code here
  // remember to include return (at the end)!
}

public static void Main(string[] args) 
{
    int answer = Sum(4, 3, 6, 1);
    Console.WriteLine("Sum: " + answer);
}
```
Output of the example.

```console
Sum: 14
```

### EXERCISE 2-18: Smallest

* Define a two-parameter method **Smallest(int, int)** that returns the smaller of the two numbers passed to it as parameters.

```cs
public static int Smallest(int number1, int number2) 
{
  // write your code here
  // do not print anything inside the method

  // there must be a return command at the end
}

public static void Main(string[] args) 
{
  int answer =  Smallest(2, 7);
  Console.WriteLine("Smallest: " + answer);
}
```

The output of the program.

```console
Smallest: 2
```

### EXERCISE 2-19: Greatest

* Define a three parameter method **Greatest(int, int, int)** that returns the greatest of the three numbers passed to it as parameters.

```cs
public static int Greatest(int number1, int number2, int number3) 
{
  // write your code here
  // do not print anything inside the method

  // there must be a return command at the end
}

public static void Main(string[] args) 
{
  int answer =  Greatest(2, 7, 3);
  Console.WriteLine("Greatest: " + answer);
}
```

The output of the program.

```console
Greatest: 7
```

### EXERCISE 2-20: Stars

#### Section 1

* Define a method called **PrintStars(int)** that prints the given number of stars and a line break.

Write the method in the following template.

```cs
public static void PrintStars(int number)
{
  // You can print one star with the command.
  // Console.Write("*");
  // Call the print command n times.
  // In the end print a line break with the comand.
  // Console.WriteLine("");
}

public static void Main(string[] args) 
{
  PrintStars(5);
  PrintStars(3);
  PrintStars(9);
}
```

The output of the program.

```console
***** 
*** 
*********
```

#### Section 2

* Define a method called **PrintSquare(int size)** that prints a suitable square with the help of the printStars(int) method. The method call PrintSquare(4) results in the following output.

```console
****
****
****
****
```

#### Section 3

* Write a method called PrintRectangle(int width, int height) that prints the correct rectangle by using the method PrintStars(int). The method call PrintRectangle(17, 3) should produce the following output.

```console
***************** 
***************** 
*****************
```

#### Section 4

* Create a method called PrintTriangle(int size) that prints a triangle by using the PrintStars(int) method. The call PrintTriangle(4) should print the following.

```console
*
**
***
****
```


### EXERCISE 2-21: Christmas Tree

#### Section 1
* Define a method called **PrintSpaces(int number)** that produces the number of spaces specified by number. The method **does not print the line break**.

You will also have to either copy the PrintStars(int) method from your previous answer or reimplement it in this exercise template.

#### Section 2

* Create a method called **PrintRightTriangle(int size)** that uses PrintSpaces and PrintStars to print the correct triangle. The method call PrintRightTriangle(4) should print the following.

```console
   *
  **
 ***
****
```

#### Section 3

* Define a method called **ChristmasTree(int height)** that prints the correct Christmas tree. The Christmas tree consists of a triangle with the specified height and the base. The base is two stars high and three stars wide and is placed at the center of the triangle's bottom. The tree is to be constructed by using the methods PrintSpaces(int) and PrintStars(int).

The call **ChristmasTree(4)** should print the following:

```console
   * 
  *** 
 *****
******* 
  *** 
  ***
```
The call **christmasTree(10)** should print:

```console
         * 
        *** 
       ***** 
      ******* 
     ********* 
    *********** 
   ************* 
  *************** 
 ***************** 
******************* 
        *** 
        ***
```
NOTICE! Heights shorter that 3 don't have to work correctly!

