---
title: "Deeper into Methods"
parent: "Part 2 - Problem Solving"
permalink: /part2/4/
nav_order: 4
published: true
---

# Deeper into Methods

Methods are important part of an object oriented programming of which we will learn more later. Lets now get deeper into methods.

## Methods Can Return Values

The definition of a method indicates whether that method returns a value. If a method does return a value, the method definition is to express the type of the return value. Otherwise the keyword **void** is used in the definition. The methods we've created thus far have been defined with the keyword void so they have returned no values.

```cs
public static void IncrementByThree() 
{
  ...
}
```

The keyword **void** indicates that the method returns nothing. If we want the method to return a value, the keyword must be replaced with the type of the return variable. In the following example there is a method called **AlwaysReturnsTen()** which returns an integer type variable. In this case the value 10.

Returning the value happens with the command **return** followed by the value to be returned or the name of the variable whose value is to be returned.

```cs
public static int AlwaysReturnsTen() 
{
  return 10;
}
```

The method defined above returns an **int** type value **10** when it is called. The return value must be stored if it is to be used. This is done the same way as normal assignment of a variable value.

```cs
public static void Main(String[] args) 
{
  int number = AlwaysReturnsTen();

  Console.WriteLine("The method returned the number " + number);
}
```

The return value of the method is placed in an **int** type variable as any other int value. The return value can also used as a part of any expression.

```cs
double number = 4 * AlwaysReturnsTen() + (alwaysReturnsTen() / 2.0) - 8;

Console.WriteLine("The result of the calculation " + number);
```

All the variable types seen so far can be returned from a method.

| Type of return value | Example |
|----------------------|---------|
| Method returns nothing | public static void ReturnsNothing() |
| Method returns **int** type variable | public static int ReturnsInt() |
| Method returns **double** type variable | public static double ReturnsDouble() |
| Method returns **bool** type variable | public static bool ReturnsBool() |
| Method returns **varible type** | public static "variable type" NameOfMethod() |


The lines of source code following the command **return** are never executed. Should the programmer add source code in a place after the return command a compiler will produce an error message. Method like the following is faulty.

```cs
public static int FaultyMethod() 
{
  return 10;
  Console.WriteLine("I claim to return an integer, but I won't.");
}
```

The next method works since it is possible to reach every statement in it.

```cs
public static int FunctioningMethod(int parameter) 
{
  if (parameter > 10) {
      return 10;
  }
  Console.WriteLine("The number received as parameter is ten or lesser.");

  return parameter;
}
```

If the method is of the form **public static void NameOfMethod()** it is possible to return from it by using the command return without following it by any value.

```cs
public static void PrintEmptyLines(int parameter) 
{
  if (parameter > 10)
  {
    return;
  }
  for (int i = 0; i < parameter; i++)
    Console.WriteLine("");
}
```

This would print up to 10 empty lines, but if the **parameter** is more than 10, the method will return and not print any lines.

## Defining Variables Inside Methods

Defining variables inside methods is done in the same manner as in the Main program. 

Following method calculates the average of the numbers it receives as parameters. 

```cs
public static double Average(int number1, int number2, int number3) 
{
  int sum = number1 + number2 + number3;
  double avg = sum / 3.0;

  return avg;
}
```

One way to call the method is the following.

```cs
public static void Main(String[] args) 
{
  Console.Write("Enter the first number: ");
  int first = Convert.ToInt32(Console.WriteLine());

  Console.Write("Enter the second number: ");
  int second = Convert.ToInt32(Console.WriteLine());

  Console.Write("Enter the third number: ");
  int third = Convert.ToInt32(Console.WriteLine());

  double averageResult = Average(first, second, third);

  Console.Write("The average of the numbers: " + averageResult);
}
```

Variables defined in a method are only visible inside that method. In the example above this means that the variables **sum** and **avg** defined inside the method **Average(int, int, int)** are not visible in the Main program. Next some common mistakes. 

```cs
public static void Main(String[] args) 
{
  int first = 3;
  int second = 8;
  int third = 4;

  Average(first, second, third);

  // Trying to use a method's internal variable, DOES NOT WORK!
  Console.Write("The average of the numbers: " + avg);
  
  // Trying to use the method name only, DOES NOT WORK!
  Console.Write("The average of the numbers: " + Average);
}
```
Typical mistakes for a learning programmer is to try and use a method in the way shown above.

## Calculating the Return Value Inside a Method

Return command that returns a value from a method can also be given an expression that is evaluated before the returning.

In the following example we'll define the method Sum(int, int) that adds together the values of two variables and returns the sum. The values of the variables that are summed are received as method parameters.

```cs
public static int Sum(int first, int second) 
{
  return first + second;
}
```

When the execution of the method reaches the statement **return first + second** the expression **first + second** is evaluated and its value will be returned.

The method is called in the following manner.

```cs
int sumOfNumbers = Sum(2, 7);
// sumOfNumbers is now 9
```

Let's expand the previous example so that the numbers are entered by the user.

```cs
public static void Main(String[] args) 
{
  Console.Write("Enter the first number: ");
  int first = Convert.ToInt32(Console.ReadLine());

  Console.Write("Enter the second number: ");
  int second = Convert.ToInt32(Console.ReadLine());

  Console.Write("The combined sum of the numbers is: " + Sum(first, second));
}

public static int Sum(int first, int second) 
{
  return first + second;
}
```

In the example above the return value of the method is not stored in a variable but rather is directly used as part of the print.

## Execution of a Method and the Call Stack

How does the computer remember where to return after the execution of a method? The execution environment of C# source code keeps track of the method being executed in the call stack. 
 
The call stack contains frames each of which includes information about a specific method. Its internal variables and their values. When a method is called a new frame containing its variables is created in the call stack. When the execution of a method ends the frame relating to that method is removed from the call stack which leads to execution resuming to the previous method of the stack.

When a method is called the execution of the calling method await the execution of the called method. This can be visualized with the call stack. The call stack refers to the stack formed by the method calls. The method that is currently being executed is always on the top of the stack. On ending the method execution the turn is resumed in the method that is next on the stack. Let's examine the following program.

```cs
public static void Main(String[] args) 
{
  Console.WriteLine("Hello world!");
  PrintNumber();
  Console.WriteLine("Bye bye world!");
}

public static void PrintNumber() {
  Console.WriteLine("Number");
}
```

The execution begins from the first line of the Main method when the program is started. The text "Hello world!" is printed with the command on this line. The call stack of the program looks like this.

```console
Main
```

Once the print command has been executed the next line that calls the method **PrintNumber()** is in turn. Calling that method moves the execution of the program to the beginning of the method PrintNumber(). Meanwhile the Main method will wait until the execution of the method PrintNumber() ends. While inside the method PrintNumber() the call stack looks like this.

```console
PrintNumber 
Main
```

Once the method PrintNumber() completes we return to the method that is immediately below the method PrintNumber() in the call stack. In this case the Main method. PrintNumber() is removed from the call stack and the execution continues on the line after the PrintNumber() method call in the Main method. The state of the call stack is now the following.

```console
Main
```

Once the execution reaches the end of the Main method the execution of the program ends and the call stack is cleared.

## Call Stack and Method Parameters

Let's examine the call stack in a situation where there are parameters defined for the method.

```cs
public static void Main(String[] args) 
{
  int beginning = 1;
  int end = 5;

  PrintStarts(beginning, end);
}

public static void PrintStars(int beginning, int end) {
  while (beginning < end) {
      Console.Write("*");
      beginning++;    // equal to beginning = beginning + 1
  }
}
```

The execution of the program begins on the first line of the **Main** method. The next two lines create the variables beginning and end and place values to them. The state of the program prior to calling the method PrintStars(int, int).

```console 
Main beginning = 1 end = 5
```

When **PrintStars(int, int)** is called the Main method enters waiting state. The method call causes new variables **beginning** and **end** to be created for the method PrintStars(int, int) and the values passed as parameters are assigned to them. These values are copied from the variables beginning and end of the Main method. The state of the program on the first line of the execution of the method PrintStars(int, int) is illustrated below.

```console
PrintStars beginning = 1 end = 5 
Main beginning = 1 end = 5
```

When the command beginning++ is executed within the repeat statement the value of the variable beginning that belongs to the method currently being executed is altered.

```console
PrintStars beginning = 2 end = 5 
Main beginning = 1 end = 5
````

So the values of the variables in the method Main remain unchanged. The execution of the method printStars(int, int) would continue for some time after this. When the execution of that method ends the execution resumes inside the Main method.

```console
Main beginning = 1 end = 5
````

Once the execution reaches the end of the Main method the execution of the program ends and the call stack is cleared.

## Call Stack and Returning a Value from a Method

Let's next study an example where the method returns a value. The Main method of the program calls a separate **Start()** method inside of which two variables are created. When the method **Sum(int, int)** is called the the value returned by the Sum(int, int) method is printed.


```cs
public static void Main(String[] args) 
{
  Start();
}

public static void Start() 
{
  int first = 5;
  int second = 6;

  int sum = Sum(first, second);

  Console.WriteLine("Sum: " + sum);
}

public static int Sum(int number1, int number2) {
  return number1 + number2;
}
```

At the beginning of executing the method **Start()** the call stack looks like the following illustration.

```console
Start 
Main
````

When variables first and second have been created in the Start() method the situation resembles the following.

```console
Start first = 5 second = 6 
Main
````

The command **int sum = Sum(first, second)** creates the variable sum with the method Start(int, int) and calls the method Sum(int, int). The method Start() enters a waiting state. Since the parameters number1 and number2 are defined in the method Sum(int,int) they are created right at the beginning of the method's execution and then the values of the variables given as parametes are copied into them.

```console
Sum number1 = 5 number2 = 6 
Start first = 5 second = 6 
sum // no value 
Main
```

The execution of the method Sum(int, int) adds together the values of the variables number1 and number2. The command **return** returns the sum of the numbers to the method that is one lower in the call stack. In this case the method Start(). The returned value is set as the value of the variable sum.

```console
Start first = 5 second = 6 sum = 11 
Main
```

After that the print command is executed and we return to the Main method. 

Once the execution reaches the end of the Main method the execution of the program ends and the call stack is cleared.

## Method Calling Another Method

As we noticed before you can call an other method from inside a method. An additional example of this technique is given below. 

We'll create the method MultiplicationTable(int) that prints the multiplication table of the given number. The multiplication table prints the rows with the help of the method PrintMultiplicationTableRow(int, int).

```cs
public static void MultiplicationTable(int max) 
{
  int number = 1;

  while (number <= max) 
  {
    PrintMultiplicationTableRow(number, max);
    number++;
  }
}

public static void PrintMultiplicationTableRow(int number, int coefficient) 
{
  int printable = number;
  while (printable <= number * coefficient) 
  {
    Console.Write("  " + printable);
    printable += number;
  }
  Console.WriteLine("");
}
```

The output of the method call **MultiplicationTable(3)** looks like this.

```console
 1 2 3
 2 4 6
 3 6 9
```

**You can now do the exercises for Methods.**
