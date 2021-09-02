---
title: "Exercises"
parent: "Part 1 - The Beginning"
permalink: /part1/6/
nav_order: 6
published: true
---

# Part 1 - Exercises

## Printing and Reading

The basic structure of the program is given in the exercises.

```cs
using System;

namespace exercise_01
{
    class Program
    {
        public static void Main(string[] args)
        {
            // Add your code here:
            
        }
    }
}
```

### EXERCISE 1-1: Hello World
* Create a program that writes the text **Hello World!** into the console. The program contains the basic structure pictured above.

### EXERCISE 1-2: Bonnie Tyler
* Let's write some more. Bonnie Tyler once sang about feelings. Create a program using 3 Console.WriteLine's that print these lyrics.
  
**Once upon a time**  
**I was falling in love**  
**Now I'm only falling apart**
’ ' 
**Now I'm only falling apart**

### EXERCISE 1-3: Bonnie Tyler Line Change
* Let's refine our program. Print the same message. This time use only one Console.WriteLine method. 
  
**Once upon a time**  
**I was falling in love**  
**Now I'm only falling apart**  

### EXERCISE 1-4: First Variable
* The exercise has following structure.

```cs
using System;

namespace exercise_04
{
    class Program
    {
        public static void Main(string[] args)
        {
            string message = "Passport and floss!";
            Console.WriteLine(message);
        }
    }
}
```

* Change it so that it prints **Passport and a toothbrush!** Do not change the line containing Console.WriteLine. Only change the content of the variable!

### EXERCISE 1-5: Ada Lovelace
* You will find following structure in the exercise.
  
```cs
using System;

namespace exercise_05
{
    class Program
    {
        public static void Main(string[] args)
        {
            string name = "Ada Lovelace";
            // Write your code here:
            
        }
    }
}
```

* Modify the code so that it prints **Hello Ada LoveLace!** Do not modify the variable content!

### EXERCISE 1-6: Print Input
* Create a program that asks user for a string. After the user has given the string, the program will print the given line. Example output with **Hello** as input. Input is marked with **>** for clarification.

```console
Give input!
> Hello
Hello
```

### EXERCISE 1-7: Triple Hello
* Create a program that asks user for a string. After the user has given the string the program will print the given line 3 times. Example output with **Hello** as input.

```console
Give input!
> Hello
Hello
Hello
Hello
```

### EXERCISE 1-8: Greeting
* Create a program that asks user for their name and greets them. Example output with **Ada** as input.

```console
What is your name?
> Ada
Hello Ada!
```
* Notice the exclamation mark!

### EXERCISE 1-9: Conversation
* Create a program that simulates a small conversation. The program will tell three lines and expects two user inputs.

```console
Hello, how are you?
> Fine, thanks.
That's interesting, tell me more
> I learn coding
Thank you for sharing!
```

### EXERCISE 1-10: Name Profession
* Create a program that asks the user for a name and a profession. Then make the program to write a little story with this information. Here is an example story with inputs **Ada** and **Data Scientist**.

* Notice every **Ada** and **Data Scientist** in the story are the inputs by the user. Remember to save the **Console.ReadLine's** into variables and use them as parts of the story!

```console
I will tell a story, but I need some information.
Give a name for main character:
> Ada
Give the character a profession:
> Data Scientist
Here is the story:
Once upon a time there was a Data Scientist called Ada
On her way to work, Ada often pondered what being Data Scientist meant to them.
When you work as a Data Scientist you meet interesting people.
Ada enjoys their work as Data Scientist, The end.
```

## Variables

### EXERCISE 1-11: Print Variables
* The exercise comes with a template that prints the following.

```console
Days to summer:
100
Hours to lunch:
1
Coding is fun:
Are you sure?
```

* Change the values of the variables so the program will print.

```console
Days to summer:
200
Hours to lunch:
3.5
Coding is fun:
It sure is!
```

### EXERCISE 1-12: Print Integer
* Create a program that asks the user for an integer. After user input the program will print the integer.

```console
Give a number!
> 11
You gave 11
```

```console
Give a number!
> 42
You gave 42
```

### EXERCISE 1-13: Print Double
* Create a program that asks the user for a double. After user input the program will print the double.

```console
Give a number!
> 11.11
You gave 11.11
```

```console
Give a number!
> 41.999999
You gave 41.999999
```

### EXERCISE 1-14: Print Truth
* Create a program that asks the user for a boolean. After user input the program will print the boolean.

```console
Give me the truth!
> tRuE
True
```

```console
Give me the truth!
> false
False
```

### EXERCISE 1-15: Asking Multiple Inputs
* Let's combine everything you know so far. Create program that asks the user for a string, an integer, a double and a boolean and prints them as following.

```console
Give a string:
> This is a masterpiece!
Give an integer:
> 42
Give a double:
> 3.1415
Give a boolean:
> True
Your string: This is a masterpiece!
Your integer: 42
Your double: 3.1415
Your boolean: True
```

## Calculations

### EXERCISE 1-16: Seconds In Days
* Create a program which asks user for amount of days and prints the total amount of seconds for that amount of days.

Example print:
```console
How many days?
> 2
172800
```
```console
How many days?
> 7
604800
```

### EXERCISE 1-17: Input Two Integers
* Create a program which asks the user for two integers and calculates their sum.  
* Remember that the input is a string so you have to convert it to integer!

```console
Give the first number!
> 8
Give the second number!
> 3
The sum is 11
```

```console
Give the first number!
> 3
Give the second number!
> -1
The sum is 2
```

### EXERCISE 1-18: Input Three Integers
* Expand a little on the previous exercise. Now create a program which asks for three integers and calculates their sum.

```console
Give the first number!
> 3
Give the second number!
> -1
Give the third number!
> 2
The sum is 4
```

### EXERCISE 1-19: Sum of Two
* Create a program which asks the user for two integers and counts their sum. This time also print the equation to the user.

```console
Give the first number!
> 3
Give the second number!
> 1
3 + 1 = 4
```

```console
Give the first number!
> 5
Give the second number!
> -1
3 + -1 = 2
```

### EXERCISE 1-20: Multiply Two
* Create a program which asks the user for two integers and multiplies them with each other.

```console
Give the first number!
> 3
Give the second number!
> 2
3 * 2 = 6
```

```console
Give the first number!
> 50
Give the second number!
> -2
50  * -2 = -100
```

### EXERCISE 1-21: Average of Two
* Create a program which asks the user for two **integers** and calculates their **average** as a **double**.

```console
Give the first number!
> 3
Give the second number!
> 2
The average is 2.5
```
### EXERCISE 1-22: Average of Three
* Create a program which asks the user for three **integers** and calculates their **average** as a **double**.

```console
Give the first number!
> 3
Give the second number!
> 2
Give the third number!
> 1
The average is 2.0
```

### EXERCISE 1-23: Tiny Calculator
* Let's create a program that does all the basic calculations from user input. Ask for two integers and do the calculations with them.

```console
Give the first number!
> 3
Give the second number!
> 2
3 + 2 = 5
3 - 2 = 1
3 * 2 = 6
3 / 2 = 1.5
```

## Conditionals and Comparison

### EXERCISE 1-24: Speeding
* Create a program which asks the user for an integer. If the given integer is larger than 120 output "Speeding!".

```console
Your speed:
> 5
````

```console
Your speed:
125
Speeding!
```

### EXERCISE 1-25: Orwell
* Create a program which asks for an integer. If the integer is 1984 output "Orwell".

```console
Give a number:
>1985
```

```console
Give a number:
> 1984
Orwell
```

### EXERCISE 1-26: Too Old
* Create a program which asks for a year as an integer. If the integer is less than 1900 output "You're old".

```console
Give your age:
>1985
```

```console
Give your age:
> 1899
You're old
```

### EXERCISE 1-27: Stay Positive
* Create a program which tells if the given number is positive or not.

```console
Give a number:
> 5
It is positive
```

```console
Give a number:
-2
It is not positive
```

### EXERCISE 1-28: Over Eighteen
* Create a program which tell if the given person is legally adult, in Finland over 18 or not.

```console
How old are you?
> 5
You're under age!
```

```console
How old are you?
> 18
You're an adult!
```

### EXERCISE 1-29: Larger Number
* Create a program which asks for two integers. The program should tell which of them is greater. If they are equal that should be noted.

```console
Give the first number!
> 3
Give the second number!
> 2
The larger number is 3!
```

```console
Give the first number!
> 3
Give the second number!
> 4
The larger number is 4!
```

```console
Give the first number!
> 3
Give the second number!
> 3
They are equal!
```
### EXERCISE 1-30: Course Grading
* Here is the grading for this course.

| Percent | Grade|
|---|---|
| < 0 | Impossible |
| 0 - 49  | Fail |
| 50 - 59 | 1 |
| 60 - 69 | 2 |
| 70 - 79 | 3 |
| 80 - 89 | 4 |
| 90 - 100 | 5 |
| > 100 | Outstanding! |

* Create a program which asks the user for their percent and gives them their score.

```console
Give your percent [0 - 100]:
> -2
Impossible
```

```console
Give your percent [0 - 100]:
> 49
Fail
```

```console
Give your percent [0 - 100]:
> 75
Grade: 3
```

```console
Give your percent [0 - 100]:
> 9001
Outstanding!
```

### EXERCISE 1-31: Even or Odd
* Create a program which asks for an integer and tells the user if it is even or not.

```console
Give a number:
> 2
It is even.
```

````console
Give a number
> 5
It is odd.
````

* Hint: You might want to use the **%** operator to get the remainder after a division with 2.

### EXERCISE 1-32: Enter Friend
* Create a program which asks for a string. If the string is "Mellon" print "Welcome, friend" otherwise print "They've got a cave troll!".

```console
Speak, friend, and enter!
> Let meeeee in!
They've got a cave troll!
```

```console
Speak, friend, and enter!
> Mellon
Welcome, friend
```

### EXERCISE 1-33: Echo
* Create a program which asks for two string. If the strings are equal print "Echo" otherwise print "Nope".

```console
Give the first string:
> Potato
Give the second string:
> Potato
Echo!
```

```console
Give the first string:
> Potato
Give the second string:
> Tomato
Nope!
```

## Repetition

### EXERCISE 1-34: Continue
* Create a program which asks the user if they want to continue. If the user answers "no" then quit the program. Otherwise ask again.

```console
Do you want to continue?
> Yes
Do you want to continue?
> Hot potato
Do you want to continue?
> no
```

* Hint: Use a while loop!

### EXERCISE 1-35: Answer to Life
* Create a program which asks the user for integers until the user give the number "42".

```console
Give a number:
> 41
Give a number:
> 68
Give a number:
-42
Give a number:
42
```

### EXERCISE 1-36: Power of Positivity
* Create a program which asks the user for integers. If the number is zero exit the program. If the number is negative give the user message "That is negative". If the number is positive output the number raised to its second power.

```console
Give a number:
> 5
25
Give a number:
> -2
That is negative
Give a number:
> 4
16
Give a number:
0
```

### EXERCISE 1-37: Counting Numbers
* Create a program which asks the user for integers. If the integer is 0 quit. In the end output "Total amount of numbers:" and the amount. Do not count the 0 into the amount.

```console
Give a number:
> 5
Give a number:
> -2
Give a number:
> 22
Give a number:
> 0
Total amount of numbers: 3
```

### EXERCISE 1-38: Counting Negatives
* Create a program which asks the user for integers. If the integer is 0 quit. In the end output the total amount of **negative numbers** with "Total amount of negative numbers:" and the amount. Do not count the 0 into the amount.

```console
Give a number:
> 5
Give a number:
> -2
Give a number:
> 22
Give a number:
> 0
Total amount of negative numbers: 1
```

### EXERCISE 1-39: Sum of Numbers
* Create a program which asks the user for integers. If the integer is 0 quit. In the end output the total **sum** of the numbers with "Total sum of numbers:" and the sum. Do not count the 0 into the sum.

```console
Give a number:
> 5
Give a number:
> -2
Give a number:
> 22
Give a number:
> 0
Total sum of numbers: 25
```

### EXERCISE 1-40: Amount and Sum
* Create a program which asks the user for integers. Exit with 0. In the end output both the amount and the sum. Do not count 0 to either.

```console
Give a number:
> 5
Give a number:
> -2
Give a number:
> 22
Give a number:
> 0
Total sum of numbers: 25
Total amount of numbers: 3
```


* Hint: You will need two variables to store the data. One for the sum and one for the amount.
