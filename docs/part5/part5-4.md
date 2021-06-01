---
title: "Objects and References"
parent: "Part 5 - Deeper into Objects"
permalink: /part5/4/
nav_order: 4
published: true
---


# Objects and References

Let's continue working with objects and references. Assume we can use the class that represents a person, shown below. 

Person has object variables name, age, weight, and height; additionally, it offers methods to calculate the body mass index, among other things. 

```cs
namespace sandbox
{

  public class Person
  {
    private string name;
    private int age;
    private int weight;
    private int height;

    // Constructor which only sets the name
    public Person(string name) : this(name, 0, 0, 0)
    {
    }

    // Constructor to set name and age
    public Person(string name, int age) :this(name, age, 0, 0)
    {
    }

    // Constructor to set all the variables.
    // The two constructors above call this when they are used.
    public Person(string name, int age, int weight, int height)
    {
      this.name = name;
      this.age = age;
      this.weight = weight;
      this.height = height;
    }

    public double BodyMassIndex()
    {
      double heigthPerHundred = this.height / 100.0;
      return this.weight / (heigthPerHundred * heigthPerHundred);
    }

    public double MaximumHeartRate()
    {
      return 206.3 - (0.711 * this.age);
    }
    
    public bool IsAdult()
    {
      if (this.age < 18)
      {
        return false;
      }
      return true;
    }

    public void GrowOlder()
    {
      this.GrowOlder(1);
    }

    public void GrowOlder(int years)
    {
      this.age += years;
    }

    public override string ToString()
    {
      return this.name + ", age " + this.age + " years";
    }


  }
}
```

Precisely what happens when a new object is created?

```cs
Person joan = new Person("Joan Ball");
```

Calling a constructor with the command new causes several things to happen. 
* First, space is reserved in the computer memory for storing object variables. 
* Then default or initial values are set to object variables (e.g. an int type variable receives an initial value of 0). 
* Lastly, the source code in the constructor is executed.

A constructor call returns a reference to an object. A **reference** is information about the location of object data.

So the value of the variable is set to be a reference, i.e. knowledge about the location of related object data. The image above also reveals that strings -- the name of our example person, for instance -- are objects, too.

## Assigning a Reference Type Variable Copies the Reference

Let's add a Person type variable called **ball** into the program, and assign joan as its initial value. What happens then?

```cs
Person joan = new Person("Joan Ball");
Console.WriteLine(joan);

Person ball = joan;
```

The statement **Person ball = joan;** creates a new Person variable call, and copies the value of the variable joan as its value. As a result, ball refers to the same object as joan.

Let's inspect the same example a little more thoroughly.

```cs
Person joan = new Person("Joan Ball");
Console.WriteLine(joan);

Person ball = joan;
ball.GrowOlder();
ball.GrowOlder();

Console.WriteLine(joan);
```

```console
Joan Ball, age: 0
Joan Ball, age: 2
```

**Joan Ball** -- i.e. the Person object that the reference in the **joan** variable points at -- starts as 0 years old. After this the value of the joan variable is assigned (so copied) to the **ball** variable. The **Person object ball** is aged by two years, and Joan Ball ages as a consequence!

An object's internal state is not copied when a variable's value is assigned. A new object is not being created in the statement **Person ball = joan;** -- the value of the variable ball is assigned to be the copy of joan's value, i.e. a reference to an object.

Next, the example is continued so that a new object is created for the **joan** variable, and a reference to it is assigned as the value of the variable. The variable **ball** still refers to the object that we created earlier.

```cs
Person joan = new Person("Joan Ball");
Console.WriteLine(joan);

Person ball = joan;
ball.GrowOlder();
ball.GrowOlder();

Console.WriteLine(joan);

joan = new Person("Joan B.");
Console.WriteLine(joan);
```
The following is printed:


```console
Joan Ball, age: 0
Joan Ball, age: 2
Joan B., age: 0
```

So in the beginning the variable **joan** contains a reference to one object, but in the end a reference to another object has been copied as its value.

## NULL Value of a Reference Variable

Let's extend the example further by setting the value of the reference variable **ball** to **null**, i.e. a reference "to nothing". The **null** reference can be set as the value of any reference type variable.

```cs
Person joan = new Person("Joan Ball");
Console.WriteLine(joan);

Person ball = joan;
ball.GrowOlder();
ball.GrowOlder();

Console.WriteLine(joan);

joan = new Person("Joan B.");
Console.WriteLine(joan);

ball = null;
```

```console
Joan Ball, age: 0
Joan Ball, age: 2
Joan B., age: 0
```

The object whose name is Joan Ball is referred to by nobody. In other words, the object has become "garbage". garbage collector manages the allocation and release of memory for your application. 

From [**C# Documentation on garbage collection**](https://docs.microsoft.com/en-us/dotnet/standard/garbage-collection/):

"Each time you create a new object, the common language runtime allocates memory for the object from the managed heap. As long as address space is available in the managed heap, the runtime continues to allocate space for new objects. 

However, memory is not infinite. Eventually the garbage collector must perform a collection in order to free some memory.  If the garbage collection did not happen, the garbage objects would reserve a memory location until the end of the program execution."

In other words, when an object is not needed anymore, it will be taken care of, so the memory space will be accesible for other use.

Let's see what happens when we try to print a variable that references "nothing" i.e. null.

```cs
Person joan = new Person("Joan Ball");
Console.WriteLine(joan);

Person ball = joan;
ball.GrowOlder();
ball.GrowOlder();

Console.WriteLine(joan);

joan = new Person("Joan B.");
Console.WriteLine(joan);

ball = null;
Console.WriteLine(ball);
```

```console
Joan Ball, age: 0
Joan Ball, age: 2
Joan B., age: 0

```

We cannot see anything in the last line of print: That's because **ball** now refers to **null**, or "nothing".

Let's see what happens if we grow our **ball** older.

```cs
Person joan = new Person("Joan Ball");
Console.WriteLine(joan);

Person ball = joan;
ball.GrowOlder();
ball.GrowOlder();

Console.WriteLine(joan);

joan = new Person("Joan B.");
Console.WriteLine(joan);

ball = null;
Console.WriteLine(ball);
ball.GrowOlder();
```

```console
Joan Ball, age: 0
Joan Ball, age: 2
Joan B., age: 0

Unhandled exception. System.NullReferenceException: Object reference not set to an instance of an object.
    in /.../coding-exercises/sandbox/Program.cs:line 24
```

Bad things happen. We get a **NullReferenceException**. The name for the exception is quite self-explanatory (as they aim to be). In the course of the program,there occured an error indicating that we called a method on a variable that refers to nothing.

We promise that this is not the last time you will encounter the previous error. When you do, the first step is to look for variables whose value could be **null**. Fortunately, the error message is useful: it tells which row caused the error. Try it out yourself!

## Object as a Method Parameter

We have seen both value and reference variables act as method parameters. Since objects are reference variables, any type of object can be defined to be a method parameter. Let's take a look at a practical demonstration.

Amusement park rides only permit people who are taller than a certain height. The limit is not the same for all attractions. Let's create a class representing an amusement park ride. When creating a new object, the constructor receives as parameters the name of the ride, and the smallest height that permits entry to the ride.

```cs
public class AmusementParkRide
{
  private string name;
  private int lowestHeight;

  public AmusementParkRide(string name, int lowestHeight)
  {
    this.name = name;
    this.lowestHeight = lowestHeight;
  }

  public override string ToString()
  {
    return this.name + ", minimum height: " + this.lowestHeight;
  }
}
```

Then let's write a method that can be used to check if a person is allowed to enter the ride, so if they are tall enough. The method returns true if the person given as the parameter is permitted access, and false otherwise.

We can safely assume our Person class now has the ability to tell the age outside the class (i.e. the variable **int age** is public).

```cs
public bool AllowedToRide(Person person)
{
  if (person.height < this.lowestHeight)
  {
    return false;
  }

  return true;
}
```

So the method AllowedToRide of an AmusementParkRide object is given a Person object as a parameter. Like earlier, the value of the variable -- in this case, a reference -- is copied for the method to use. The method handles a copied reference, and it calls the name property of the person passed as a parameter.

Below is an example main program where the amusement park ride method is called twice: first the supplied parameter is a person object **matt**, and then a person object **jasper**:

```cs
static void Main(string[] args)
{

  // Our constructor has name, age, weight, height
  Person matt = new Person("Matt", 15, 86, 180);

  Person jasper = new Person("Jasper", 8, 34, 132);

  AmusementParkRide waterTrack = new AmusementParkRide("Water track", 140);

  if (waterTrack.AllowedToRide(matt))
  {
    Console.WriteLine(matt.name + " may enter the ride");
  }
  else
  {
    Console.WriteLine(matt.name + " may not enter the ride");
  }

  if (waterTrack.AllowedToRide(jasper))
  {
    Console.WriteLine(jasper.name + " may enter the ride");
  }
  else
  {
    Console.WriteLine(jasper.name + " may not enter the ride");
  }

  Console.WriteLine(waterTrack);
}
```

```console
Matt may enter the ride
Jasper may not enter the ride
Water track, minimum height: 140
```

What if we wanted to know how many people have taken the ride?

Let's add an object variable to the amusement park ride. It keeps track of the number of people that were permitted to enter.

```cs
public class AmusementParkRide
{
  private string name;
  private int lowestHeight;
  private int visitors;

  public AmusementParkRide(string name, int lowestHeight)
  {
    this.name = name;
    this.lowestHeight = lowestHeight;
    this.visitors = 0;
  }

  public bool AllowedToRide(Person person)
  {
    if (person.height < this.lowestHeight)
    {
      return false;
    }
    this.visitors++;
    return true;
  }

  public override string ToString()
  {
    return this.name + ", minimum height: " + this.lowestHeight +
            ", visitors: " + this.visitors;
  }
}
```

Now the previously used example program also keeps track of the number of visitors who have experienced the ride.

```cs
static void Main(string[] args)
{

  // Our constructor has name, age, weight, height
  Person matt = new Person("Matt", 15, 86, 180);

  Person jasper = new Person("Jasper", 8, 34, 132);

  AmusementParkRide waterTrack = new AmusementParkRide("Water track", 140);

  if (waterTrack.AllowedToRide(matt))
  {
    Console.WriteLine(matt.name + " may enter the ride");
  }
  else
  {
    Console.WriteLine(matt.name + " may not enter the ride");
  }

  if (waterTrack.AllowedToRide(jasper))
  {
    Console.WriteLine(jasper.name + " may enter the ride");
  }
  else
  {
    Console.WriteLine(jasper.name + " may not enter the ride");
  }

  Console.WriteLine(waterTrack);
}
```

```console
Matt may enter the ride
Jasper may not enter the ride
Water track, minimum height: 140, visitors: 1
```

## Object as Object Variable

Objects may contain references to objects.

Let's keep working with people, and add a birthday to the person class. A natural way of representing a birthday is to use a **Date** class. We could use the classname Date, but for the sake of **avoiding confusion with the similarly named existing C# class**, we will use **SimpleDate** here.

```cs
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


  public override string ToString()
  {
    return this.day + "." + this.month + "." + this.year;
  }
}
```

Since we know the birthday, there is no need to store that age of a person as a separate object variable. The age of the person can be inferred from their birthday. Let's assume that the class Person now has the following variables.

```cs
public class Person
{
  public string name;
  private SimpleDate birthday;
  private int weight;
  public int height;

//  ...
```

Let's create a new Person constructor that allows for setting the birthday:

```cs
public Person(string name, SimpleDate date)
{
  this.name = name;
  this.birthday = date;
  this.weight = 0;
  this.height = 0;
}
```

Along with the constructor above, we could give Person another constructor where the birthday was given as integers.

```cs
public Person(string name, int day, int month, int year)
{
  this.name = name;
  this.birthday = new SimpleDate(day, month, year);
}
```

The constructor receives as parameters the different parts of the date (day, month, year). They are used to create a date object, and finally the reference to that date is copied as the value of the object variable birthday.

Let's modify the ToString method of the Person class so that instead of age, the method returns the birthday:

```cs
public override string ToString()
{
  return this.name + ", born on " + this.birthday;
}
```

Let's see how the updated Person class works.

```cs
SimpleDate date = new SimpleDate(1, 1, 780);
Person muhammad = new Person("Muhammad ibn Musa al-Khwarizmi", date);
Person pascal = new Person("Blaise Pascal", 19, 6, 1623);

Console.WriteLine(muhammad);
Console.WriteLine(pascal);
```

```console
Muhammad ibn Musa al-Khwarizmi, born on 1.1.780
Blaise Pascal, born on 19.6.1623
```

Now a person object has object variables name and birthday. The variable name is a string, which itself is an object; the variable birthday is a **SimpleDate object**.

Both variables contain a reference to an object. Therefore a person object contains two references. 

So the Main program has is connected to two Person objects by strands. A person has a name and a birthday. Since both variables are objects, these attributes exist at the other ends of the strands.

Birthday appears to be a good extension to the Person class. Earlier we noted that the object variable age can be calculated with birthday, so it was removed.

In the section above, we use our own class SimpleDate to represent date, because it is suitable for illustrating and practising the operation of objects. If we want to handle date (and time) in our own programs, we would most probably use [**C#'s DateTime**](https://docs.microsoft.com/en-us/dotnet/api/system.datetime?view=netframework-4.8) rather than code our own version.

```cs
DateTime now = DateTime.Now;
Console.WriteLine(now);
int year = now.Year;
int month = now.Month;
int day = now.Day;

Console.WriteLine("today is  " + day + "." + month + "." + year);
```

```console
2/13/2020 7:12:07 PM
today is  13.2.2020
```

NOTICE! With C# the output of the first line can differ, depending on the language setting of your environment. This is due to **culture** in C# environments. We will discuss this later.

## Object of Same Type as Method Parameter

We will continue working with the **Person** class. We recall that persons know their birthdays:

```cs
public class Person
{
  public string name;
  private SimpleDate birthday;
  private int weight;
  public int height;
  
// ...
```

We would like to compare the ages of two people. The comparison can be done in multiple ways. We could, for instance, implement a method called **public int AgeAsYears()** for the Person class; in that case, the comparison would happen in the following manner:

```cs
Person muhammad = new Person("Muhammad ibn Musa al-Khwarizmi", 1, 1, 780);
Person pascal = new Person("Blaise Pascal", 19, 6, 1623);

if (muhammad.AgeAsYears() > pascal.AgeAsYears()) {
    Console.WriteLine(muhammad.name + " is older than " + pascal.name);
}
```

We are now going to learn a more "object-oriented" way to compare the ages of people.

We are going to create a new method **public bool OlderThan(Person compared)** for the Person class. It can be used to compare a certain person object to the person supplied as the parameter based on their ages.

The method is meant to be used like this:

```cs
Person muhammad = new Person("Muhammad ibn Musa al-Khwarizmi", 1, 1, 780);
Person pascal = new Person("Blaise Pascal", 19, 6, 1623);

if (muhammad.OlderThan(pascal)) {  //  same as muhammad.OlderThan(pascal)==true
    Console.WriteLine(muhammad.name + " is older than " + pascal.name);
} else {
    Console.WriteLine(muhammad.name + " is not older than " + pascal.name);
}
```

The program above tells if al-Khwarizmi older than Pascal. The method **OlderThan** returns true if the object that is used to call the method **(object OlderThan(objectGivenAsParameter))** is older than the object given as the parameter, and false otherwise.

In practice, we call the **OlderThan** method of the object that matches "Muhammad ibn Musa al-Khwarizmi", which is referred to by the variable **muhammad**. The reference **pascal**, matching the object "Blaise Pascal", is given as the parameter to that method.

The program prints:

```console
Muhammad ibn Musa al-Khwarizmi is older than Blaise Pascal
```

The method OlderThan receives a **person object** as its parameter. More precisely, the variable that is defined as the method parameter receives a copy of the value contained by the given variable. That value is a reference to an object, in this case.

The implementation of the method is illustrated below. Note that the method may return a value in more than one place -- here the comparison has been divided into multiple parts based on the years, the months, and the days:

```cs
public bool OlderThan(Person compared)
{
  // 1. First compare years
  int ownYear = this.birthday.year;
  int comparedYear = compared.birthday.year;

  if (ownYear < comparedYear)
  {
    return true;
  }

  if (ownYear > comparedYear)
  {
    return false;
  }

  // 2. Same birthyear, compare months
  int ownMonth = this.birthday.month;
  int comparedMonth = compared.birthday.month;

  if (ownMonth < comparedMonth)
  {
    return true;
  }

  if (ownMonth > comparedMonth)
  {
    return false;
  }

  // 3. Same birth year and month, compare days
  int ownDay = this.birthday.day;
  int comparedDay = compared.birthday.day;

  if (ownDay < comparedDay)
  {
    return true;
  }

  return false;
}
```

Let's pause for a moment to consider abstraction, one of the principles of object-oriented programming. The idea behind abstraction is to conceptualize the programming code so that each concept has its own clear responsibilities. When viewing the solution above, however, we notice that the comparison functionality would be better placed inside the SimpleDate class instead of the **Person** class.

We'll create a method called **public boole Before(SimpleDate compared)** for the class SimpleDate. The method returns the value **true** if the date given as the parameter is after (or on the same day as) the date of the object whose method is called.

```cs
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

    if (this.year > compared.year)
    {
      return false;
    }

    // years are same, compare months
    if (this.month < compared.month)
    {
      return true;
    }

    if (this.month > compared.month)
    {
      return false;
    }

    // years and months are same, compare days
    if (this.day < compared.day)
    {
      return true;
    }

    return false;
  }
}
```

Even though the object variables year, month, and day are encapsulated (private) object variables, we can read their values by writing compared.**variableName** This is because private variable can be accessed from all the methods contained by that class. Notice that the syntax here matches calling some object method. Unlike when calling a method, we refer to a property or a field of an object, so the parentheses that indicate a method call are not written.

An example of how to use the method:

```cs
SimpleDate d1 = new SimpleDate(14, 2, 2011);
SimpleDate d2 = new SimpleDate(21, 2, 2011);
SimpleDate d3 = new SimpleDate(1, 3, 2011);
SimpleDate d4 = new SimpleDate(31, 12, 2010);

Console.WriteLine(d1 + " is earlier than " + d2 + ": " + d1.Before(d2));
Console.WriteLine(d2 + " is earlier than " + d1 + ": " + d2.Before(d1));

Console.WriteLine(d2 + " is earlier than " + d3 + ": " + d2.Before(d3));
Console.WriteLine(d3 + " is earlier than " + d2 + ": " + d3.Before(d2));

Console.WriteLine(d4 + " is earlier than " + d1 + ": " + d4.Before(d1));
Console.WriteLine(d1 + " is earlier than " + d4 + ": " + d1.Before(d4));
```

```console
14.2.2011 is earlier than 21.2.2011: True
21.2.2011 is earlier than 14.2.2011: False
21.2.2011 is earlier than 1.3.2011: True
1.3.2011 is earlier than 21.2.2011: False
31.12.2010 is earlier than 14.2.2011: True
14.2.2011 is earlier than 31.12.2010: False
```

Let's tweak the method OlderThan of the Person class so that from here on out, we take use of the comparison functionality that date objects provide.

```cs
public bool OlderThan(Person compared) {
    if (this.birthday.Before(compared.birthday)) {
        return true;
    }

    return false;

    // or return more directly:
    // return this.birthday.Before(compared.birthday);
}
```

Now the concrete comparison of dates is implemented in the class that it logically (based on the class names) belongs to.

## Equality

If we want to be able to compare two objects of our own design with the **Equals** method, that method must be defined in the class. The method equals is defined as a method that returns a boolean type value -- the return value indicates whether the objects are equal.

The method equals is implemented in a way that allows for using it to compare the current object with any other object. The method receives an Object type object as its single parameter -- all objects are Object type, in addition to their own type. The equals method first compares if the addresses are equal: if so, the objects are equal. After this, we examine if the types of the objects are the same: if not, the objects are not equal. Then the Object object passed as the parameter is converted to the type of the object that is being examined by using a type cast. Then the values of the object variables can be compared. Below the equality comparison has been implemented for the SimpleDate class.

```cs
namespace sandbox
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

    public override bool Equals(object compared)
    {
      // if the variables are located in the same position, they are equal
      if (this == compared)
      {
        return true;
      }

      // if the compared object is null, or
      // if the type of the compared object is not SimpleDate, the objects are not equal
      if ((compared == null) || !this.GetType().Equals(compared.GetType()))
      {
        return false;
      }

      // convert the Object type compared object
      // into an SimpleDate type object called comparedSimpleDate
      SimpleDate comparedSimpleDate = (SimpleDate)compared;

      // if the values of the object variables are the same, the objects are equal
      if (this.day == comparedSimpleDate.day &&
          this.month == comparedSimpleDate.month &&
          this.year == comparedSimpleDate.year)
      {
        return true;
      }

      // otherwise the objects are not equal
      return false;
    }


    public override string ToString()
    {
      return this.day + "." + this.month + "." + this.year;
    }
  }
}
```

Notice! So far we have compared only with **==**, but now we're also using **Equals**. They compare different things. Try out, what happens if you compare two identical SimpleDates with both:

```cs
static void Main(string[] args)
{
  SimpleDate date1 = new SimpleDate(1,2,2020);
  SimpleDate date2 = new SimpleDate(1,2,2020);
  Console.WriteLine(date1.Equals(date2));
  Console.WriteLine(date1 == date2);
}
```


## Some Inheritance

Every class we create (and every ready-made C# class) inherits the class Object, even though it is not specially visible in the program code. This is why an instance of any class can be passed as a parameter to a method that receives an Object type variable as its parameter. Inheriting the Object can be seen elsewhere, too: for instance, the **ToString** method exists even if you have not implemented it yourself, just as the equals method does.

To illustrate, the following source code compiles successfully: **Equals** method can be found in the Object class inherited by all classes.

```cs
namespace sandbox
{
  public class Bird
  {
    private string name;

    public Bird(string name)
    {
      this.name = name;
    }
  }
}
```

```cs
static void Main(string[] args)
{
  Bird red = new Bird("Red");
  // We're using GetHashCode to show they're unique
  // The method returns the exact runtime type of the current instance.
  Console.WriteLine(red.GetHashCode());

  Bird chuck = new Bird("Chuck");
  Console.WriteLine(chuck.GetHashCode());

  if (red.Equals(chuck))
  {
    Console.WriteLine(red + " equals " + chuck);
  }
  else
  {
    Console.WriteLine("They're not equal!");
  }
}
```

```console
58225482
54267293
They're not equal!
```

## Object Equality and Lists

Let's examine how the **Equals** method is used with Lists. Let's assume we have the previously described class **Bird** with only the default **Equals** method (not defined by us).

```cs
public class Bird
{
  private string name;

  public Bird(string name)
  {
    this.name = name;
  }
}
```

Let's create a list and add a bird to it. After this we'll check if that bird is contained in it.

```cs
static void Main(string[] args)
{
  List<Bird> birds = new List<Bird>();
  Bird red = new Bird("Red");

  if (birds.Contains(red))
  {
    Console.WriteLine("Red is on the list.");
  }
  else
  {
    Console.WriteLine("Red is not on the list.");
  }

  birds.Add(red);
  if (birds.Contains(red))
  {
    Console.WriteLine("Red is on the list.");
  }
  else
  {
    Console.WriteLine("Red is not on the list.");
  }


  Console.WriteLine("However!");

  red = new Bird("Red");
  if (birds.Contains(red))
  {
    Console.WriteLine("Red is on the list.");
  }
  else
  {
    Console.WriteLine("Red is not on the list.");
  }
}
```

```console
Red is not on the list.
Red is on the list.
However!
Red is not on the list.
```

We can notice in the example above that we can search a list for our own objects. First, when the bird had not been added to the list, it is not found -- and after adding it is found. When the program switches the **red** object into a new object, with exactly the same contents as before, it is no longer equal to the object on the list, and therefore cannot be found on the list.

The **Contains** method of a list uses the **Equals** method that is defined for the objects in its search for objects. In the example above, the **Bird** class has no definition for that method, so a bird with exactly the same contents -- but a different reference -- cannot be found on the list.

Let's implement the **Equals** method for the class **Bird**. The method examines if the names of the objects are equal -- if the names match, the birds are thought to be equal.

```cs
public override bool Equals(object compared)
{
  // if the variables are located in the same position, they are equal
  if (this == compared)
  {
    return true;
  }

  // if the compared object is null or not of type Bird, the objects are not equal
  if ((compared == null) || !this.GetType().Equals(compared.GetType()))
  {
    return false;
  }
  else
  {
    // convert the object to a Bird object
    Bird comparedBird = (Bird)compared;
    // if the values of the object variables are equal, the objects are, too
    return this.name.Equals(comparedBird.name);
  }
}
```

Now the Contains list method recognizes birds with identical contents.

```cs
static void Main(string[] args)
{
  List<Bird> birds = new List<Bird>();
  Bird red = new Bird("Red");

  if (birds.Contains(red))
  {
    Console.WriteLine("Red is on the list.");
  }
  else
  {
    Console.WriteLine("Red is not on the list.");
  }

  birds.Add(red);
  if (birds.Contains(red))
  {
    Console.WriteLine("Red is on the list.");
  }
  else
  {
    Console.WriteLine("Red is not on the list.");
  }


  Console.WriteLine("However!");

  red = new Bird("Red");
  if (birds.Contains(red))
  {
    Console.WriteLine("Red is on the list.");
  }
  else
  {
    Console.WriteLine("Red is not on the list.");
  }
}
```

```console
Red is not on the list.
Red is on the list.
However!
Red is on the list.
```

## Object as a Method's Return Value

We have seen methods return boolean values, numbers, and strings. Easy to guess, a method can return an object of any type.

In the next example we present a simple counter that has the method **Clone**. The method can be used to crete a clone of the counter; i.e. a new counter object that has the same value at the time of its creation as the counter that is being cloned.

```cs
namespace sandbox
{
  public class Counter
  {
    private int value;

    // example of using multiple constructors:
    // you can call another constructor from a constructor by calling this
    // notice that the this call must be on the first line of the constructor
    public Counter() : this(0)
    {
    }

    public Counter(int initialValue)
    {
      this.value = initialValue;
    }

    public void Increase()
    {
      this.value = this.value + 1;
    }

    public override string ToString()
    {
      return "value: " + value;
    }

    public Counter Clone()
    {
      // create a new counter object that receives the value of the cloned counter as its initial value
      Counter clone = new Counter(this.value);

      // return the clone to the caller
      return clone;
    }
  }
}
```

An example of using counters follows:

```cs
Counter counter = new Counter();
counter.Increase();
counter.Increase();

Console.WriteLine(counter);         // prints 2

Counter clone = counter.Clone();

Console.WriteLine(counter);         // prints 2
Console.WriteLine(clone);          // prints 2

counter.Increase();
counter.Increase();
counter.Increase();
counter.Increase();

Console.WriteLine(counter);         // prints 6
Console.WriteLine(clone);          // prints 2

clone.Increase();

Console.WriteLine(counter);         // prints 6
Console.WriteLine(clone);          // prints 3
```

```console
value: 2
value: 2
value: 2
value: 6
value: 2
value: 6
value: 3
```

Immediately after the cloning operation, the values contained by the clone and the cloned object are the same. However, they are two different objects, so increasing the value of one counter does not affect the value of the other in any way.

Similarly, a **Factory** object could also be used to create and return new Car objects. Below is a sketch of the outline of the factory -- the factory also knows the makes of the cars that are created.

```cs
public class Factory 
{
  private string make;

  public Factory(string make) 
  {
    this.make = make;
  }

  public Car ProcuceCar() 
  {
    return new Car(this.make);
  }
}
```

**You can now do the exercises for Objects and References.**
