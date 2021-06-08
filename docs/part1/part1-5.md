---
title: "Repetition"
parent: "Part 1 - The Beginning"
permalink: /part1/5/
nav_order: 5
published: true
---

# Repetition

We now can do simple commands one at a time. But what if we want to do something more than once? Let's make a program which asks the user for a number 4 times and sums them up.

```cs
int sum = 0;

Console.Write("Give integer value: ");
string userInput = Convert.ToInt32(Console.ReadLine());
sum = sum + userInput;
Console.WriteLine("Sum is " + intValue);

Console.Write("Give integer value: ");
userInput = Convert.ToInt32(Console.ReadLine());
sum = sum + userInput;
Console.WriteLine("Sum is " + sum);

Console.Write("Give integer value: ");
userInput = Convert.ToInt32(Console.ReadLine());
sum = sum + userInput;
Console.WriteLine("Sum is " + sum);

Console.Write("Give integer value: ");
userInput = Convert.ToInt32(Console.ReadLine());
sum = sum + userInput;
Console.WriteLine("Sum is " + sum);

``` 

This will get the job done, but as you can see there is plenty of repetition and many lines of code for such a simple task. What if we wanted to ask the user 10 numbers or 1000? The easier and nicer way to solve this problem is with loops especially the while loop. 

```cs
int sum = 0;
int readNumbers = 0;

while (true) 
{
    if (readNumbers == 7) {
        break;
    }

    Console.WriteLine("Give a number");
    sum = sum + Convert.ToInt32(Console.ReadLine());
    readNumbers = readNumbers + 1;
}
Console.WriteLine("Sum is " + sum);
```

## While Looping Forever and Ever

Let's look deeper into the while loops.

```cs
while (expression)
{
    // Your code is here
    // Here can be any amount of code
}
```

For now we shall be using the boolean value of true as our expression. This can lead us to a neverending loop. Once the code block has been run the value of the expression is checked. As it is always true it will always start running the code again.

## Ending a While Loop

We did manage to create a program in the previous example that is not looping forever. We did that with the keyword **break**. As the name suggests it breaks the loop. Technically it stops the current code block from running and jumps ahead to the next code block.

Usually a break is used when the user gives a certain kind of input or when the loop calculation has reached a certain point.

```cs
int number = 1;

while (true) 
{
    Console.WriteLine(number);
    if (number >= 5) {
        break;
    }
    number = number + 1;
}
Console.WriteLine("All done!");
```

```console
1
2
3
4
5
All done!
```

Notice that we created the original number variable outside of the loop. If we would create it in the while loop code block it would be recreated every time the loop starts again.

```cs
while (true) 
{
    int number = 1;
    Console.WriteLine(number);
    if (number >= 5) {
        break;
    }
    number = number + 1;
}
Console.WriteLine("All done!");
```

```console
1
1
1
1
1
... 
(This keeps going forever)
```

You can also ask user input in a while loop. In the following example we will ask the user if they want to continue the program.

```cs
while (true) 
{
    Console.WriteLine("Do you want to continue?");
    string input = Console.ReadLine();
    if (input = "no") 
    {
        break;
    }
    Console.WriteLine("Let's keep going!");
}
Console.WriteLine("All done!");
```

```console
Do you want to continue?
> yes
Let's keep going!
Do you want to continue?
> totally
Let's keep going!
Do you want to continue?
> no
All done!
```

In the previous example we asked the user for string input. Other types of variable work just as well.

```cs
while (true) 
{
    Console.WriteLine("Input an integer, 0 quits");
    int command = Convert.ToInt32(Console.ReadLine());
    if (command == 0) 
    {
        break;
    }

    Console.WriteLine("You gave " + command);
}

Console.WriteLine("All done!");
```

```console
Input an integer, 0 quits
> 5
You gave 5
Input an integer, 0 quits
> -2
You gave -2
Input an integer, 0 quits
> 0
All done!
```

## Returning to the Beginning of a While Loop

We return to the beginning of a while loop when all the code inside the code block has been run. It is possible to return to the beginning from other parts of code as well. That is done with the keyword **continue**.

Below we ask the user for positive integers. If the user gives a negative integer we print out a message 'Not a positive integer' and return to the beginning of the loop. If the user gives a zero the program ends.

```cs
while (true) 
{
    Console.WriteLine("Input a positive integer, 0 quits");
    int number = Convert.ToInt32(Console.ReadLine());
    if (number == 0) 
    {
        break;
    }
    else if  (number < 0)
    {
        Console.WriteLine("Not a positive integer!");
        continue;
    }
    else 
    {
        Console.WriteLine("You gave " + number);
    }
}

Console.WriteLine("All done!");
```

```console
Input a positive integer, 0 quits
> 12
You gave 12
Input a positive integer, 0 quits
> -2
Not a positive integer!
Input a positive integer, 0 quits
> 0
All done!
```

Let us comment the code. All the lines and inner code blocks have a simple meaningful task to perform.

```cs
// Repeat until the block has been exited.
while (true) 
{
    Console.WriteLine("Input a positive integer, 0 quits");     // Ask user for input
    int number = Convert.ToInt32(Console.ReadLine());           // Read the input

    // if-else-if-else is one code block with multiple functions.    
    // Check if number is too small.
    if  (number < 0)
    {
        Console.WriteLine("Not a positive integer!");
    }
    // Check if the user wants to exit the loop.
    else if (number == 0) 
    {
        break;
    }
    // Print the positive outcome.
    else 
    {
        Console.WriteLine("You gave " + number);
    }
}
// Confirm exit with print.
Console.WriteLine("All done!");
```

As you can see the if-else-if-else block has quite a huge task and defining it takes few steps. When you design your programs you should aim for simple tasks for all the code blocks.

## Calculations with While Loops

While loops are often used for calculations. Programs that handle undetermined amounts of user inputs are based on while structrure. 

If the variable for data storage is introduced inside the block dedicated for the loop the variable is accessible only inside the block. Let's demonstrate that with commented code.

```cs
// Repeat until the block has been exited
while (true) 
{
    int countOnes = 0;      // Create a variable as storage for counting 1s.
    Console.WriteLine("Input an integer, 0 quits");     // Ask for integers
    int number = Convert.ToInt32(Console.ReadLine());   // Read user input
    
    // If the input is 0, exit the loop.
    if (number == 0) 
    {
        break;
    }
    // If the input is 1, add to count.
    if  (number == 1)
    {
        // Increase the value of countOnes by 1.
        countOnes = countOnes + 1;
    }
}

// Here we cannot access the variable "countOnes" because it was defined in the inner block.
// Our code does not compile.
Console.WriteLine("Amount of ones: " + countOnes);
```

All the variables are visible to the code block they are in. If we want the program to work we have to create the variable before the loop. The next example works as intended.

```cs
// Create a variable as storage for counting 1s
int countOnes = 0;

// Repeat until the block has been exited
while (true) 
{
    Console.WriteLine("Input an integer, 0 quits");     // Ask for integers
    int number = Convert.ToInt32(Console.ReadLine());   // Read user input
    
    // If the input is 0, exit the loop.
    if (number == 0) 
    {
        break;
    }
    // If the input is 1, add to count.
    if  (number == 1)
    {
        // Increase the value of countOnes by 1.
        countOnes = countOnes + 1;
    }
}

// Print the amount of 1s from input.
Console.WriteLine("Amount of ones: " + countOnes);
```

```console
Input an integer, 0 quits
> 5
Input an integer, 0 quits
> 1
Input an integer, 0 quits
> 1
Input an integer, 0 quits
> -1
Input an integer, 0 quits
> 0
Amount of ones: 2
```

**You can now do the exercises for Repetition.**
