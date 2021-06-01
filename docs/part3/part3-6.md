---
title: "Exercises"
parent: "Part 3 - Data Structures"
permalink: /part3/6/
nav_order: 6
published: true
---

# Part 3 - Exercises

## Lists

### EXERCISE_62:

* This exercise contains a base that asks the user for strings and adds them to a list. The program stops reading input when the user enters an empty string. The program then prints the first element of the list.
* Your assignment is to modify the program so that instead of the first value the third value on the list is printed. Remember that programmers start counting from zero! The program is allowed to malfunction if there are fewer than three entries on the list.

```console
> Tom 
> Emma 
> Alex 
> Mary
>
Alex
```

```console
> Emma 
> Alex 
> Mary
>

Mary
```

### EXERCISE_63:

* In the exercise template there is a program that reads integers from the user and adds them to a list. This ends when the user enters 0. The program then prints the first value on the list.
* Modify the program so that instead of the first value the program prints the sum of the second and third numbers. The program is allowed to malfunction if there are fewer than three entries on the list, so you don't need to prepare for such an event at all.

```console
> 1 
> 3 
> 5 
> 7 
> 0 
8
```

```console
> 2 
> 3 
> 4 
> 0 
7
```

### EXERCISE_64:

* There is a program that uses a list in the exercise template. Modify it so that its execution always produces the error **ArgumentOutRangeException**. The user should not have to give any inputs to the program.

### EXERCISE_65:

* In the exercise template there is a program that reads input from the user. Modify its working so that when the program quits reading, with an empty line, the program prints the number of values on the list.

```console
> Tom 
> Emma 
> Alex 
> Mary
>
In total: 4
```

```console
> Juno 
> Elizabeth 
> Mason 
> Irene
> Olivia
> Liam
> Ida
> Christopher
> Mark
> Sylvester
> Oscar
>
In total: 11
```

**NOTICE!** Be sure to use the **Count property** of the list.

* The next exercises are meant for learning to use lists and indices. Even if you could complete the execises without a list concentrate on training to use lists. The functionality in the exercises is to be implemented after reading the inputs.

### EXERCISE_66:

* In the exercise template there is a program that reads inputs from the user and adds them to a list. Reading is stopped once the user enters an empty string.
* Your task is to modify the method to print the last read value after it stops reading. Print the value that was read last from the list. Use the Count to help you. You do not have to take into consideration empty lists. You can assume that the user always gives at least one input.

```console
> Tom 
> Emma 
> Alex 
> Mary
>
Mary
```

```console
> Juno 
> Elizabeth 
> Mason 
> Irene
> Olivia
> Liam
> Ida
> Christopher
> Mark
> Sylvester
> Oscar
>
Oscar
```

### EXERCISE_67:

* In the exercise template there is a program that reads inputs from the user and adds them to a list. Reading is stopped once the user enters an empty string.
* Modify the program to print both the first and the last values after the reading ends. You may suppose that at least two values are read into the list.

```console
> Tom 
> Emma 
> Alex 
> Mary
>
Tom
Mary
```

```console
> Juno 
> Elizabeth 
> Mason 
> Irene
> Olivia
> Liam
> Ida
> Christopher
> Mark
> Sylvester
> Oscar
>
Juno
Oscar
```

```console
> Tom 
> Mary
>
Tom
Mary
```

### EXERCISE_68:

* The exercise template contains a base that reads numbers from the user and adds them to a list. Reading is stopped once the user enters the number -1.
* Expand the functionality of the program so that after reading the numbers it prints all the numbers received from the user. The number used to indicate stopping should not be printed.

```console
> 72
> 2
> 8
> 11
> -1 
72
2
8
11
```

### EXERCISE_69:

* The exercise template contains a base that reads numbers from the user and adds them to a list. Reading is stopped once the user enters the number -1.
* Expand the program to ask for a start and end indices once it has finished asking for numbers. After this the program shall prints all the numbers in the list that fall in the specified range. Inclusively all the numbers between the indices given by the user. You may assume that the user gives indices that match some numbers in the list.

```console
> 72
> 2
> 8
> 11
> -1 
From where?
> 1
Where to?
> 9 
2 
8
```

```console
> 72
> 2
> 8
> 11
> -1 
From where?
> 0 
Where to?
> 20  
2
8
11 
```

### EXERCISE_70:

* The exercise template contains a base that reads numbers from the user and adds them to a list. Reading is stopped once the user enters the number -1.
* Continue developing the program so that it finds the greatest number in the list and prints its value after reading all the numbers. The programming should work in the following manner.

```console
> 72
> 2
> 8
> 93
> 11
> -1
The grEatest number: 93
```
* You can assume that user always gives atleast one viable number.
* You can use the source code below as an inspitation. It is used to find the smallest number.

```cs
// assume we have a list that contains integers

int smallest = list[0];

for(int i = 0; i < list.Count; i++) {
    int number = list[i];
    if (smallest > number) {
        smallest = number;
    }
}

Console.WriteLine("The smallest number: " + smallest);
```

### EXERCISE_71:

* The exercise template contains a base that reads numbers from the user and adds them to a list. Reading is stopped once the user enters the number -1.
* Expand the program that then asks the user for a number, and reports that number's index in the list. If the number is not found, the program should not print anything.

```console
> 72 
> 2 
> 8 
> 8 
> 11 
> -1
Search for? 
> 2 
2 is at index 1
```

```console
> 72 
> 2 
> 8 
> 8 
> 11 
> -1
Search for? 
> 8 
8 is at index 2
8 is at index 3
```

### EXERCISE_72:

* Write a program that reads numbers from the user. When number 9999 is entered the reading process stops. After this the program will print the smallest number in the list and also the indices where that number is found. The smallest number can appear multiple times in the list.

```console
> 72
> 2
> 8
> 8
> 11
> 9999
Smallest number: 2 
Found at index: 1
```

```console
> 72
> 44
> 8
> 8
> 11
> 9999
Smallest number: 8 
Found at index: 2 
Found at index: 3
```

**HINT:** Combine the programs you wrote for the exercises "Greatest number in the list" and "Index of the requested number". First find the smalleest number and then find the index of that number.

### EXERCISE_73:

* The exercise template contains a base that reads numbers from the user and adds them to a list. Reading is stopped once the user enters the number -1.
* Modify the program so that after reading the numbers it calculates and prints the sum of the numbers in the list.

```console
> 72
> 2
> 8
> 11
> -1
Sum: 93
```

### EXERCISE_74:

* In the exercise template there is a program that reads inputs from the user until an empty string is entered. 
* Add the following functionality to it. After reading the inputs one more string is requested from the user. The program then tell whether that string was found in the list or not.

```
> Tom
> Emma
> Alex
> Mary
Search for?
> Mary
Mary was found!
```

```
> Tom
> Emma
> Alex
> Mary
Search for?
> Logan
Logan was not found!
```

### EXERCISE_75:

* Create the method **public static void PrintNumbersInRange(List\<int\> numbers, int lowerLimit, int upperLimit)** in the exercise template. The method prints the numbers in the given list whose values are in the range [lowerLimit, upperLimit]. A few examples of using the method are supplied below.

```cs
List<int> numbers = new List<int>();
numbers.Add(3);
numbers.Add(2);
numbers.Add(6);
numbers.Add(-1);
numbers.Add(5);
numnbers.Add(1);

Console.WriteLine("The numbers in the range [0, 5]");
PrintNumbersInRange(numbers, 0, 5);

Console.WriteLine("The numbers in the range [3, 10]");
PrintNumbersInRange(numbers, 3, 10);
```

```console
The numbers in the range [0, 5] 
3 
2 
5 
1 
The numbers in the range [3, 10] 
3 
6 
5
```

### EXERCISE_76:

* Create the method **public static int Sum(List\<int\> numbers)** in the exercise template. The method is to **return** the sum of the numbers in the parameter list.

```cs
List<int> numbers = new List<int>();
numbers.Add(3);
numbers.Add(2);
numbers.Add(6);
numbers.Add(-1);
Console.WriteLine(Sum(numbers));

numbers.Add(5);
numbers.Add(1);
Console.WriteLine(Sum(numbers));
```

```console
10
16
```

### EXERCISE_77:

* Create the method **public static void RemoveLast(List\<string\> strings)** in the exercise template. The method should remove the last value in the list it receives as a parameter. If the list is empty the method does nothing.

```cs
List<string> strings = new List<string>();

strings.Add("First");
strings.Add("Second");
strings.Add("Third");

// Remember, this is how you print all the items in a list
strings.ForEach(Console.WriteLine);

RemoveLast(strings);
RemoveLast(strings);

strings.ForEach(Console.WriteLine);
```

```console
First
Second
Third
First
```

## Arrays

### EXERCISE_78:

* The exercise template already contains a program that creates an array and prints the values of the array twice. 
* Modify the program to do following: After the first printing the program should ask for two indices from the user. The values in these two indices should be swapped and in the end the values of the array should be printed once again.

```console
1 
3 
5 
7 
9

Give two indices to swap: 
> 2 
> 4

1 
3 
9 
7 
5
```

```console
1 
3 
5 
7 
9

Give two indices to swap: 
> 0 
> 1

3 
1 
5 
7 
9
```

You can assume the array to contain the given indices.   

**Tip!** You'll need an additional variable to store one of the values for little while.

### EXERCISE_79:

* The exercise template has already an array containing numbers. 
* Complete the program to ask the user for a number to search in the array. If the array contains the given number the program tells the index containing the number. If the array doesn't contain the given number the program will tell the number wasn't found.

```console
Search for? 
> 3 
3 is at index 4.
```

```console
Search for? 
> 7 
7 is at index 7.
```

```console
Search for? 
> 22 
22 was not found.
```

### EXERCISE_80:

* The template has a method **public static int SumOfNumbersInArray(int[] array)**. Complete the method so that it computes and returns the sum of the numbers in the array it receives as parameter.
* You can try out the computation of the sum with this example.

```cs
int[] numbers = {5, 1, 3, 4, 2};
int sum = SumOfNumbersInArray(numbers);
Console.WriteLine(sum);
```

```console
15
```

### EXERCISE_81:

* Complete the method **public static void PrintNeatly(int[] array)** in the template to make it print the numbers of the array it receives more neatly. There should be a whitespace and a comma between each number. Don't put a comma after the last number.
* Print the numbers on one line using **Console.Write()**.
* You can try out your printing with this example.

```cs
int[] array = {5, 1, 3, 4, 2};
PrintNeatly(array);
```

```console
5, 1, 3, 4, 2
```

### EXERCISE_82:

* Complete the method **public static void PrintArrayInStars(int[] array)** in the template to make it print a row of stars for each number in the array. The amount of stars on each row is defined by the corresponding number in the array.

* You can try out the printing with this example.

```cs
int[] array = {5, 1, 3, 4, 2};
PrintArrayInStars(array);
```

```
***** 
* 
*** 
**** 
**
```

* The 0th element of the array is 5 so the first line has 5 stars. The next one has 1 etc.

## Strings

### EXERCISE_83:

* Write a program that reads a string from the user and then prints it three times.

```console
Give a word: cake

cakecakecake
```

**NOTICE!** The program should ask for only one string. Don't use a loop here.

### EXERCISE_84:

* Write a program that asks the user for a string. If the user writes the string "true" the program prints "You got it right!" otherwise it prints "Try again!".

```console
Give a string: true 
You got it right!
```

```console
Give a string: trueish 
Try again!
```

### EXERCISE_85:

* Write a program that recognizes the following users.

|username	|password|
|--|--|
|alex|	sunshine|
|emma|	haskell|

The program either shows a login message or informs of incorrect username or password.

```console
Enter username: 
>alex 
Enter password: 
> sunshine 
You have successfully logged in!
```

```console
Enter username: 
> emma 
Enter password: 
> haskell 
You have successfully logged in!
```

```console
Enter username: 
> alex 
Enter password: 
> haskell 
Incorrect username or password!
```

**NOTICE!** In real life login should not be implemented like this! This is just an exercise.

### EXERCISE_86:

* Write a program that reads strings from the user. If the input is empty the program stops reading input and halts. For each non empty input it splits the string input by whitespaces and prints each part of the string on a new line.

```console
> once upon a time 
once 
upon 
a 
time 
> a little program 
a 
little 
program 
> halted 
halted
>
```

### EXERCISE_87:

* Write a program that reads user input until an empty line. For each non empty string the program splits the string by spaces and then prints the pieces that contain **av** each on a new line.

```console
> navy blue shirt
navy
> Do you have a favourite flavour
have
favourite
flavour
> was that a cat
>
```

**Tip!** Strings have a Contains() method which tells if a string contains another string. It works like this.

```cs
string text = "volcanologist";

if (text.Contains("can")) 
{
  Console.WriteLine("can was found");
}

if (!text.Contains("tin")) 
{
  Console.WriteLine("tin wasn't found");
}
```

```console
can was found 
tin wasn't found
```

### EXERCISE_88:

* Write a program that reads user input until an empty line. For each non empty line the program splits the string by spaces and prints the first part of the string.

```console
> one two three four 
one 
> this is a very important message 
this
>
```

### EXERCISE_89:

* Write a program that reads user input until an empty line. For each non empty line the program splits the string by spaces and prints the last part of the string.

```console
> one two three four 
four 
> this is a very important message 
message
>
```

**Tip!** You can find out the length of the array like this.

```cs
string[] parts = {"one", "two", "three"};
Console.WriteLine("Number of parts: " + parts.Length);
```

```console
Number of parts: 3
```

### EXERCISE_90:

* Write a program that reads names and ages from the user until an empty line is entered. The name and age are separed by a comma.
* After reading the program prints the age of the oldest person. 
* You can assume that the user enters at least one person and that one of the users is older than the others.

```console
> sebastian,2 
> lucas,2
> lily,1
> hanna,5
> gabriel,10
>
Age of the oldest: 10
```

### EXERCISE_91:

* Write a program that reads names and ages from the user until an empty line is entered. The name and age are separed by a comma.
* After reading the program prints the name of the oldest person. 
* You can assume that the user enters at least one person and that one of the users is older than the others.

```console
> sebastian,2 
> lucas,2
> lily,1
> hanna,5
> gabriel,10
>
Name of the oldest: gabriel
```

### EXERCISE_92:

* In this exercise you'll be asked for the length of the names. You can find out the length of a string with Length property.

```cs
string word = "equisterian";
int length = word.Length;
Console.WriteLine("The length of the word " + word + " is " + length);
```

```console
The length of the word equisterian is 11
```

* Write a program that reads names and birth years from the user until an empty line is entered. The name and birth year are separed by a comma.
* After that the program prints the longest name and the highest age. 
* If multiple names are equally longest you can print any of them. 
* You can assume the user to enter at least one person and the current year to be 2020.

```console
> sebastian,2017 
> lucas,2017 
> lily,2017 
> hanna,2014 
> gabriel,2009
>
Longest name: sebastian 
Highest age: 11
```
