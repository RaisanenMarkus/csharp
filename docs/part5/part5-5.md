---
title: "Exercises"
parent: "Part 5 - Deeper into Objects"
permalink: /part5/5/
nav_order: 5
published: true
---

# Part 5 - Exercises

## Object Oriented Revision

### EXERCISE 5-1: One Minute

The exercise template comes with the **ClockHand** class described in the course material. Implement a **Timer** class based on the material's Clock class.

The timer has two hands, one for hundredths of a second and one for seconds. As it progresses the number of hundredths of a second grows by one. When the hand corresponding to hundredths of a second reaches a value of 100 its value is set to zero and the number of seconds grows by one. In the same way when the value of the hand corresponding to seconds reaches the value of sixty its value is set to zero.

* Constructor **public Timer()** for creating a new timer object.
* **public override string ToString()** returns a string representation of the timer. The string representation should be in the form "seconds: hundredths of a second", where both the seconds and the hundredths of a second are represented by two numbers. For example **"19:83"** would represent the time 19 seconds, 83 hundredths of a second.
* **public void Advance()** moves the timer forward by a hundredth of a second.

You can test out the timer's functionality in the main program. The example code below provides you with a program where the timer is printed and it advances once every hundredth of a second.

```cs
static void Main(string[] args)
{
  // Create new timer
  Timer timer = new Timer();
  // Loop until you cancel the loop.
  // You can cancel with the CTRL + C
  while (true)
  {
    Console.WriteLine(timer);
    timer.Advance();
    // Some error proving, we'll talk about this later.
    // Known as try-catch.
    try
    {
      // Wait 100th of a second. 
      // Sleep(1000) waits one second, if you want to test at slower pace.
      System.Threading.Thread.Sleep(10);
    }
    // Other half of try-catch pair. 
    catch (Exception e)
    {
      Console.WriteLine("Error happened: +" + e);
    }
  }
}
```

### EXERCISE 5-2: Cube

Create a **Cube** class that represents a cube. 

* Create a **public Cube (int edgeLength)** constructor for the class that takes the length of the cube's edge as its parameter.
* Make a **public int Volume()** method for the cube, which calculates and returns the cube's volume. The volume of the cube is calculated with the formula **edgeLength * edgeLength * edgeLength**. 
* Moreover make a **public override string ToString()** method for the cube, which returns a string representation of it. The string representation should take the form **"The length of the edge is l and the volume v"**. Where l is the length and v the volume. Both the length and volume must be represented as integers.

### EXERCISE 5-3: Fitbyte

[**The Karvonen method**](https://en.wikipedia.org/wiki/Heart_rate#Karvonen_method) allows you to calculate your target heart rate for physical exercise. The target heart rate is calculated with the formula **(maximum heart rate - resting heart rate) * (target heart rate percentage) + resting heart rate** where the target heart rate is given as a percentage of the maximum heart rate.

For example if a person has a maximum heart rate of 200 a resting heart rate of 50 and a target heart rate of 75% of the maximum heart rate. The target heart rate should be about ((200-50) * (0.75) + 50) = 162.5 beats per minute.

Create an "exercise assistant" class called **Fitbyte**. Its constructor takes both an age and a resting heart rate as its parameters. The exercise assistant should provide a method **TargetHeartRate**, which is passed a number of type double as a parameter that represents a percentual portion of the maximum heart rate. The proportion is given as a number between zero and one. 

The class should have:
* A constructor **public Fitbyte(int age, int restingHeartRate)**
* A method **public double TargetHeartRate(double percentageOfMaximum)** that calculates and returns the target heart rate.

Use the formula **206.3 - (0.711 * age)** to calculate the maximum heart rate.
Use the formula **(maxHeartRate - restingHeartRate) * percentageOfMaximum + restingHeartRate** to calculate the target heart rate.

See a use case example below.

```cs
public static void Main(string[] args)
{
  Fitbyte assistant = new Fitbyte(30, 60);
  double percentage = 0.5;

  while (percentage < 1.0)
  {
    double target = assistant.TargetHeartRate(percentage);
    Console.WriteLine("Target " + (percentage * 100) + "% of maximum: " + target);
    percentage = percentage + 0.1;
  }
}
```

```console
Target 50% of maximum: 122.48500000000001
Target 60% of maximum: 134.98200000000003
Target 70% of maximum: 147.479
Target 80% of maximum: 159.976
Target 89.99999999999999% of maximum: 172.473
Target 99.99999999999999% of maximum: 184.97000000000003
```


## Overloading

### EXERCISE 5-4: Constructor Overload

The exercise template has a **Product** class, which represents a product in a shop. Every product has a name, location and weight.

Add the following three constructors to the Product class.

* **public Product(string name)** creates a product with the given name. Its location is set to "shelf" and its weight is set to 1.
* **public Product(string name, string location)** creates a product with the given name and the given location. Its weight is set to 1.
* **public Product(string name, int weight)** creates a product with the given name and the given weight. Its location is set to "warehouse".

You can test your program with the following code.

```cs
Product tapeMeasure = new Product("Tape measure");
Product plaster = new Product("Plaster", "home improvement section");
Product tyre = new Product("Tyre", 5);

Console.WriteLine(tapeMeasure);
Console.WriteLine(plaster);
Console.WriteLine(tyre);
```

```console
Tape measure (1 kg) can be found from the shelf. 
Plaster (1 kg) can be found from the home improvement section. 
Tyre (5 kg) can be found from the warehouse.
```

### EXERCISE 5-5: Overloaded Counter

Implement a class called **Counter**. The class contains a number, whichs value can be increased and decreased. The class must have the following constructors.

* **public Counter(int startValue)** sets the start value of the counter to startValue.
* **public Counter()** sets the start value of the counter to 0.

And the following methods and properties.

* **public int value { get; set; }**
* **public void Increase()** increases the value by 1
* **public void Decrease()** decreases the value by 1
* **public void Increase(int increaseBy)** increases the value of the counter by the value of increaseBy. If the value of increaseBy is negative, the value of the counter does not change.
* **public void Decrease(int decreaseBy)** decreases the value of the counter by the value of decreaseBy. If the value of decreaseBy is negative, the value of the counter does not change.

## Objects and References

#### EXERCISE 5-6: Null Reference Exception

Implement a program that causes the **NullReferenceException** error. The error should occur directly after starting the program -- don't wait to read input from the user, for instance.

HINT! Change an object into null, and try to use it.

### EXERCISE 5-7: Health Station

In the exercise base there is the class **Person**, which we are already quite familiar with. There is also an outline for the class **HealthStation**. Health station objects process people in different ways, they e.g. weigh and feed people. In this exercise we will construct a health station. The code of the Person class should not be modified in this exercise!


##### Section 1 - Weighing people

The **Weigh** method receives a person as a parameter, and it is meant to return to its caller the weight of that person. The weight information can be found by calling a suitable property of the Person person. So your task is to complete the code of the method!

##### Section 2 - Feeding people

It is possible to modify the state of the object that is received as a parameter. Fill in the method called **public void Feed(Person person)** for the health station. It should increase the weight of the parameter person by one.

##### Section 3 - Counting weighings

Use the variable **public int weighings { get; private set; }** to count weighings - That is, when ever the method **Weigh** is called, the variable should increase by one.

Here's a Main class to test all of the sections:

```cs
public static void Main(string[] args)
{
  // create new Station
  HealthStation childrensHospital = new HealthStation();

  // create two new persons
  Person ethan = new Person("Ethan", 1, 110, 7);
  Person peter = new Person("Peter", 33, 176, 85);

  // Try out the Persons and method Weigh
  Console.WriteLine(ethan.name + " weight: " + childrensHospital.Weigh(ethan) + " kilos");
  Console.WriteLine(peter.name + " weight: " + childrensHospital.Weigh(peter) + " kilos");

  // Test feeding the persons
  childrensHospital.Feed(ethan);
  childrensHospital.Feed(peter);

  // See that the weights have changed
  Console.WriteLine(ethan.name + " weight: " + childrensHospital.Weigh(ethan) + " kilos");
  Console.WriteLine(peter.name + " weight: " + childrensHospital.Weigh(peter) + " kilos");

  // Keep weighing to increase the 'int weighings'
  childrensHospital.Weigh(ethan);
  childrensHospital.Weigh(ethan);
  childrensHospital.Weigh(ethan);
  childrensHospital.Weigh(ethan);

  // See that the variable has increased to 8
  Console.WriteLine("weighings performed: " + childrensHospital.weighings);
}
```

Should print out 

```console
Ethan weight: 110 kilos
Peter weight: 176 kilos
Ethan weight: 111 kilos
Peter weight: 177 kilos
weighings performed: 8
```

### EXERCISE 5-8: Card Payments

In a previous exercises part we created a class called **PaymentCard**. The card had methods for Eating a lunch and drinking coffee, and also for adding money to the card.

However, there was a problem with the **PaymentCard** class that is implemented in this fashion. The card knew the prices of the different payments, and therefore was able to decrease the balance by the proper amount. What about if the prices are raised? Or new items are added to the list of offered products? A change in the pricing would mean that all the existing cards would have to be replaced with new cards that are aware of the new prices.

An improved solution is to make the cards "dumb"; unaware of the prices and products that are sold, and only keeping track of their balance. All the intelligence is better placed in separate objects, payment terminals.


##### Section 1

Let's first implement the **"dumb" version of the PaymentCard**. The card only has ability for asking for the balance, adding money, and taking money. Complete the method **public bool TakeMoney(double amount)** in the class below (and found in the exercise template), using the following as a guide:

```cs
namespace exercise_126
{
  public class PaymentCard
  {
    public double balance { get; private set; }

    public PaymentCard(double balance)
    {
      this.balance = balance;
    }

    public void AddMoney(double increase)
    {
      this.balance = this.balance + increase;
    }

    public bool TakeMoney(double amount)
    {
      // implement the method so that it only takes money from the card if
      // the balance is at least the amount parameter.
      // returns true if successful and false otherwise

      return false;
    }
  }
}
```

```cs
static void Main(string[] args)
{
  PaymentCard petesCard = new PaymentCard(10);

  Console.WriteLine("money " + petesCard.balance);
  bool wasSuccessful = petesCard.takeMoney(8);
  Console.WriteLine("successfully withdrew: " + wasSuccessful);
  Console.WriteLine("money " + petesCard.balance);

  wasSuccessful = petesCard.takeMoney(4);
  Console.WriteLine("successfully withdrew: " + wasSuccessful);
  Console.WriteLine("money " + petesCard.balance);

}
```

Should print like this:

```console
money 10
successfully withdrew: True
money 2
successfully withdrew: False
money 2
```

##### Section 2

When visiting a student cafeteria, the customer pays either with cash or with a payment card. The cashier uses a payment terminal to charge the card or to process the cash payment. First, let's create a terminal that's suitable for cash payments.

The outline of the payment terminal. The comments inside the methods tell the wanted functionality:

```cs
namespace exercise_126
{
  public class PaymentTerminal
  {
    private double money;  // amount of cash
    private int coffeeAmount; // number of sold coffees
    private int lunchAmount;  // number of sold lunches

    public PaymentTerminal()
    {
      // register initially has 1000 euros of money
    }

    public double DrinkCoffee(double payment)
    {
      // an coffee now costs 2.50 euros
      // increase the amount of cash by the price of an coffee mean and return the change
      // if the payment parameter is not large enough, no coffee is sold and the method should return the whole payment
    }

    public double EatLunch(double payment)
    {
      // a lunch now costs 10.30 euros
      // increase the amount of cash by the price of a lunch and return the change
      // if the payment parameter is not large enough, no lunch is sold and the method should return the whole payment
    }

    public override string ToString()
    {
      return "money: " + money + ", number of sold coffees: " + coffeeAmount + ", number of sold lunches: " + lunchAmount;
    }
  }
}
```

The terminal starts with 1000 euros in it. Implement the methods so they work correctly, using the basis above and the example prints of the main program below.

```cs
PaymentTerminal lunchCafeteria = new PaymentTerminal();

double change = lunchCafeteria.DrinkCoffee(10);
Console.WriteLine("remaining change " + change);

change = lunchCafeteria.DrinkCoffee(5);
Console.WriteLine("remaining change " + change);

change = lunchCafeteria.EatLunch(20);
Console.WriteLine("remaining change " + change);

Console.WriteLine(lunchCafeteria);
```

```console
remaining change 7.5
remaining change 2.5
remaining change 13
money: 1015.3, number of sold coffees: 2, number of sold lunches: 1
```

##### Section 3

Let's extend our payment terminal to also support card payments. We are going to create new methods for the terminal. It receives a payment card as a parameter, and decreases its balance by the price of the meal that was purchased. Here are the outlines for the methods, and instructions for completing them.

```cs
public bool DrinkCoffee(PaymentCard card)
{
  // a coffee costs 2.50 euros
  // if the payment card has enough money, the balance of the card is decreased by the price, and the method returns true
  // otherwise false is returned
}

public bool EatLunch(PaymentCard card)
{
  // a lunch costs 10.30 euros
  // if the payment card has enough money, the balance of the card is decreased by the price, and the method returns true
  // otherwise false is returned
}
```

Notice! Card payments do not increase the cash in the register.

```cs
PaymentTerminal lunchCafeteria = new PaymentTerminal();

double change = lunchCafeteria.DrinkCoffee(10);
Console.WriteLine("remaining change: " + change);

PaymentCard annesCard = new PaymentCard(15);

bool wasSuccessful = lunchCafeteria.EatLunch(annesCard);
Console.WriteLine("there was enough money: " + wasSuccessful);
wasSuccessful = lunchCafeteria.EatLunch(annesCard);
Console.WriteLine("there was enough money: " + wasSuccessful);
wasSuccessful = lunchCafeteria.DrinkCoffee(annesCard);
Console.WriteLine("there was enough money: " + wasSuccessful);

Console.WriteLine(lunchCafeteria);
```

```console
remaining change: 7.5
there was enough money: True
there was enough money: False
there was enough money: True
money: 1002.5, number of sold coffees: 2, number of sold lunches: 1
```

##### Section 4

Let's create a method for the terminal that can be used to add money to a payment card. Recall that the payment that is received when adding money to the card is stored in the register (adding cash). The basis for the method:

```cs
public void AddMoneyToCard(PaymentCard card, double sum)
{
  // ...
}
```

A main program to illustrate:


```cs
public static void Main(string[] args)
{
  // Try your code here, if you want

  PaymentTerminal lunchCafeteria = new PaymentTerminal();
  Console.WriteLine(lunchCafeteria);

  PaymentCard annesCard = new PaymentCard(2);

  Console.WriteLine("amount of money on the card is " + annesCard.balance + " euros");

  bool wasSuccessful = lunchCafeteria.EatLunch(annesCard);
  Console.WriteLine("there was enough money: " + wasSuccessful);

  lunchCafeteria.AddMoneyToCard(annesCard, 100);

  wasSuccessful = lunchCafeteria.EatLunch(annesCard);
  Console.WriteLine("there was enough money: " + wasSuccessful);

  Console.WriteLine("amount of money on the card is " + annesCard.balance + " euros");

  Console.WriteLine(lunchCafeteria);
}
```

```console
money: 1000, number of sold coffees: 0, number of sold lunches: 0
amount of money on the card is 2 euros
there was enough money: False
there was enough money: True
amount of money on the card is 91.7 euros
money: 1100, number of sold coffees: 0, number of sold lunches: 1
```

#### EXERCISE 5-9: Biggest Pet Shop

Two classes, Person and Pet, are included in the exercise template. Each person has one pet. Modify the **public override string ToString** method of the **Person class** so that the string it returns tells the pet's name and breed in addition to the person's own name.

```cs
public static void Main(string[] args)
{

  Pet lucy = new Pet("Lucy", "golden retriever");
  Person leo = new Person("Leo", lucy);
  Console.WriteLine(leo);

  Person mike = new Person("Mike");
  Console.WriteLine(mike);
  
  Person lilo = new Person();
  Console.WriteLine(lilo);
}
```

```console
Leo, has a friend called Lucy (golden retriever)
Lilo, has a friend called Stitch (blue alien)
Mike, has a friend called Toothless (dragon)
```

#### EXERCISE 5-10: Comparing Apartments

Fill in the method **public bool LargerThan(Apartment compared)** that returns true if the apartment object whose method is called has a larger total area than the apartment object that is being compared.

An example of how the method should work:

```cs
public static void Main(string[] args)
{
  Apartment manhattanStudioApt = new Apartment(1, 16, 5500);
  Apartment atlantaTwoBedroomApt = new Apartment(2, 38, 4200);
  Apartment bangorThreeBedroomApt = new Apartment(3, 78, 2500);

  Console.WriteLine(manhattanStudioApt.LargerThan(atlantaTwoBedroomApt));
  Console.WriteLine(bangorThreeBedroomApt.LargerThan(manhattanStudioApt));
}
```

```console
False
True
```

Fill in the method **public int PriceDifference(Apartment compared)** that returns the price difference of the apartment object whose method was called and the apartment object received as the parameter. The price difference is the absolute value of the difference of the prices (price can be calculated by multiplying the price per square by the number of squares). Use the method **private int Price()** to calculate the price for the apartments.

An example of how the method should work:

```cs
Apartment manhattanStudioApt = new Apartment(1, 16, 5500);
Apartment atlantaTwoBedroomApt = new Apartment(2, 38, 4200);
Apartment bangorThreeBedroomApt = new Apartment(3, 78, 2500);
Console.WriteLine(manhattanStudioApt.PriceDifference(atlantaTwoBedroomApt));
Console.WriteLine(bangorThreeBedroomApt.PriceDifference(manhattanStudioApt));
```

```console
71600
107000
```

Fill in the method **public bool MoreExpensiveThan(Apartment compared)** that returns true if the apartment object whose method is called is more expensive than the apartment object being compared.

An example of how the method should work:

```cs
Apartment manhattanStudioApt = new Apartment(1, 16, 5500);
Apartment atlantaTwoBedroomApt = new Apartment(2, 38, 4200);
Apartment bangorThreeBedroomApt = new Apartment(3, 78, 2500);
Console.WriteLine(manhattanStudioApt.MoreExpensiveThan(atlantaTwoBedroomApt));
Console.WriteLine(bangorThreeBedroomApt.MoreExpensiveThan(manhattanStudioApt));
```

```console
False
True
```

#### EXERCISE 5-11: Song

In the exercise base there is a class called **Song** that can be used to create new objects that represent songs. Add to that class the **Equals** method so that the similarity of songs can be examined.

You can try your code with this:

```cs
public static void Main(string[] args)
{
  // Try your code here, if you want
  Song jackSparrow = new Song("The Lonely Island", "Jack Sparrow", 196);
  Song anotherSparrow = new Song("The Lonely Island", "Jack Sparrow", 196);

  if (jackSparrow.Equals(anotherSparrow))
  {
    Console.WriteLine("Songs are equal.");
  }

  if (jackSparrow.Equals("Another object"))
  {
    Console.WriteLine("Strange things are afoot.");
  }
}
```

#### EXERCISE 5-12: Books

There is a program in the exercise base that asks for books from the user and adds them to a list.

Modify the program so that books that are already on the list are not added to it again. Two books should be considered the same if they have the same name and publication year.

Example print:

```console
Name (empty will stop): 
> Bossypants 
Publication year: 
>2013 
Name (empty will stop):
> Seriously...I'm Kidding
Publication year:
> 2012 
Name (empty will stop):
> Seriously...I'm Kidding 
Publication year:
> 2012 
The book is already on the list. Let's not add the same book again. 
Name (empty will stop):
>

Thank you! Books added: 2
```

#### EXERCISE 5-13: Archive

The program should read items from the user. When all the items from the user have been read, the program prints the information of each item.

For each item, its identifier and name should be read. If the identifier or name is empty, the program stops asking for input, and prints all the item information.

Example print:

```console
Identifier? (empty will stop):
> B07H8ND8HH 
Name? (empty will stop):
> He-Man figure
Identifier? (empty will stop):
> B07H8ND8HH 
Name? (empty will stop):
> He-Man 
Identifier? (empty will stop):
> B07NQFMZYG 
Name? (empty will stop):
> He-Man figure 
Identifier? (empty will stop):
> B07NQFMZYG 
Name? (empty will stop):
> He-Man figure
Identifier? (empty will stop):
>

==Items== 
B07H8ND8HH: He-Man figure 
B07NQFMZYG: He-Man figure
```


The printing format of the items should be identifier: name.

After entering the items, each item is printed at most once. Two items should be considered the same if their identifiers are the same (there can be variation in their names in different countries, for instance).

If the user enters the same item multiple times, the print uses the item that was added first.

Hint! It is probably smart to add each item to the list at most once -- compare the equality of the objects based on their identifiers.

#### EXERCISE 5-14: Dating App

This exercise is worth 2.

With the exercise base the class SimpleDate is supplied. The date is stored with the help of the object variables year, month, and day. There are some methods that need fulfilling:

- **public void Advance()** advances the date by one day.  In this exercise we assume that each month has 30 day. Remember! In certain situations you need to change the values of month and year.
- **public void Advance(int howManyDays)** advances the date by the amount of days. Use the method Advance() that you implemented to help you in this.
- **public SimpleDate AfterNumberOfDays(int days)**  It creates a new SimpleDate object whose date is the specified number of days grEater than the object that the method was called on. You may still assume that each month has 30 days. Notice that the old date object must remain unchanged!

Since the last method must create a new object, the structure of the code should be somewhat similar to this:

```cs
SimpleDate newDate = new SimpleDate( ... );

// Do something here

return newDate;
```

The whole class template looks like this:

```cs
namespace exercise_132
{
  public class SimpleDate
  {
    private int day;
    private int month;
    private int year;

    public SimpleDate(int day, int month, int year)
    {
      this.day = day;
      this.month = month;
      this.year = year;
    }

    public void Advance() {
      // Do something here
    }

    public void Advance(int howManyDays) {
      // Do something here
    }

    public SimpleDate AfterNumberOfDays(int days) {
      SimpleDate newDate = new SimpleDate( ... );

      // Do something here

      return newDate;
    }

    
    public override string ToString()
    {
      return this.day + "." + this.month + "." + this.year;
    }

    // used to check if this date object (`this`) is before
    // the date object given as the parameter (`compared`)
    public bool Before(SimpleDate compared)
    {
      // first compare years
      if (this.year < compared.year)
      {
        return true;
      }

      // if the years are the same, compare months
      if (this.year == compared.year && this.month < compared.month)
      {
        return true;
      }

      // the years and the months are the same, compare days
      if (this.year == compared.year && this.month == compared.month &&
          this.day < compared.day)
      {
        return true;
      }

      return false;
    }
  }
}
```

Here's example use:
```cs
public static void Main(string[] args)
{
  SimpleDate date = new SimpleDate(13, 2, 2015);
  Console.WriteLine("Friday of the examined week is " + date);

  SimpleDate newDate = date.AfterNumberOfDays(7);
  int week = 1;
  while (week <= 7)
  {
    Console.WriteLine("Friday after " + week + " weeks is " + newDate);
    newDate = newDate.AfterNumberOfDays(7);

    week = week + 1;
  }

  Console.WriteLine("The date after 790 days from the examined Friday is ... try it out yourself!");
  // Console.WriteLine("Try " + date.AfterNumberOfDays(790));

}
```

```console
Friday of the examined week is 13.2.2015
Friday after 1 weeks is 20.2.2015
Friday after 2 weeks is 27.2.2015
Friday after 3 weeks is 4.3.2015
Friday after 4 weeks is 11.3.2015
Friday after 5 weeks is 18.3.2015
Friday after 6 weeks is 25.3.2015
Friday after 7 weeks is 2.4.2015
The date after 790 days from the examined Friday is ... try it out yourself!
```

NOTICE! Instead of modifying the state of the old object we return a new one with **AfterNumberOfDays**. Imagine that the SimpleDate class has a method Advance that works similarly to the method we programmed, but it modifies the state of the old object. In that case the next block of code would cause problems.

```cs
SimpleDate now = new SimpleDate(13, 2, 2015);
SimpleDate afterOneWeek = now;
afterOneWeek.Advance(7);

Console.WriteLine("Now: " + now);
Console.WriteLine("After one week: " + afterOneWeek);
```

```console
Now: 20.2.2015 
After one week: 20.2.2015
```

This is because a normal assignment only copies the reference to the object. So the objects now and afterOneWeek in the program now refer to the **one and same SimpleDate object**.

#### EXERCISE 5-15: Money

This exercise is worth 2.

In the Payment card exercise we used a double-type object variable to store the amount of money. In real applications this is not the approach you want to take, since as we have seen, calculating with doubles is not exact. A more reasonable way to handle amounts of money is create an own class for that purpose. Here is a layout for the class:

```cs
namespace exercise_133
{
  public class Money
  {

    private int euros;
    private int cents;

    public Money(int euros, int cents)
    {
      if (cents > 99)
      {
        euros = euros + cents / 100;
        cents = cents % 100;
      }

      this.euros = euros;
      this.cents = cents;
    }

    public Money Plus(Money addition)
    {
      Money newMoney = new Money(/* Do something here*/);
      // create a new Money object that has the correct worth

      // return the new Money object
      return newMoney;
    }

    public Money Minus(Money decreaser)
    {
      Money newMoney = new Money(/* Do something here*/);
      // create a new Money object that has the correct worth

      // return the new Money object
      return newMoney;
    }

    public bool LessThan(Money compared)
    {
      // Do something here
      return false;
    }

    public string toString()
    {
      string zero = "";
      if (cents <= 10)
      {
        zero = "0";
      }

      return euros + "." + zero + cents + "e";
    }
  }
}
```

Next we'll create a few operations for processing money.

- First create the method **public Money Plus(Money addition)** that returns a new money object that is worth the total amount of the object whose mehtod was called and the object that is received as the parameter.

The basis for the method is the following:

```cs
public Money Plus(Money addition)
{
  Money newMoney = new Money(/* Do something here*/);
  // create a new Money object that has the correct worth

  // return the new Money object
  return newMoney;
}
```
NOTICE! If the cents would go over 100, the euros should increase as well!

- create the method **public bool LessThan(Money compared)** that returns true if the money object whose method is called has a grEater worth than the money object that is received as the method parameter.

- Write the method **public Money Minus(Money decreaser)** that returns a new money object worth the difference of the object whose method was called and the object received as the parameter. If the difference would be negative, the worth of the created money object is set to 0.

NOTICE! If the cents would go under 0, the euros should decrease as well!

Example of all the methods:
```cs
Money money = new Money(100, 00);
Money moreMoney = new Money(500, 50);

Money combined = money.Plus(moreMoney);

Console.WriteLine(money);
Console.WriteLine(moreMoney);
Console.WriteLine(combined);

Money lessMoney = moreMoney.Minus(money);

Console.WriteLine(money);
Console.WriteLine(moreMoney);
Console.WriteLine(lessMoney);

lessMoney = lessMoney.Minus(money);

Console.WriteLine(money);
Console.WriteLine(moreMoney);
Console.WriteLine(lessMoney);

Console.WriteLine(lessMoney.LessThan(moreMoney));
Console.WriteLine(lessMoney.LessThan(money));

lessMoney = lessMoney.Minus(moreMoney);
Console.WriteLine(lessMoney);
```

Prints out

```console
100.00e
500.50e
600.50e
100.00e
500.50e
400.50e
100.00e
500.50e
300.50e
True
False
0.00e
```
