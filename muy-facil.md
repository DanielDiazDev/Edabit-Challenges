
Return the Sum of Two Numbers
Create a function that takes two numbers as arguments and returns their sum.

Examples
addition(3, 2) ➞ 5

addition(-3, -6) ➞ -9

addition(7, 3) ➞ 10
Notes
Don't forget to return the result.
If you get stuck on a challenge, find help in the Resources tab.
If you're really stuck, unlock solutions in the Solutions tab.

--------------------

public class Program
{
    public static int Sum(int a, int b)
    {
        int result = a + b;
        return result;
    }
}

-----------------------------

using System;
using NUnit.Framework;

[TestFixture]
public class Tests
{
    [Test]
    [TestCase(2, 3, Result=5)]
    [TestCase(-3, -6, Result=-9)]
  	[TestCase(7, 3, Result=10)]
    public static int FixedTest(int a, int b)
    {
				Console.WriteLine($"Input: {a}, {b}");
        return Program.Sum(a, b);
    }
}

---------------------
estimación: 4 minutos
Tiempo real: 2 minutos

##########################
Convert Age to Days
Create a function that takes the age in years and returns the age in days.

Examples
calcAge(65) ➞ 23725

calcAge(0) ➞ 0

calcAge(20) ➞ 7300

Notes
Use 365 days as the length of a year for this challenge.
Ignore leap years and days between last birthday and now.
Expect only positive integer inputs.


-----------------

public class Program 
{
    public static int CalcAge(int age) 
    {
			return age * 365;
    }
}

-------------------------
using System;
using NUnit.Framework;

[TestFixture]
public class Tests {
	[Test]
	[TestCase(10, Result=3650)]
	[TestCase(0, Result=0)]
	[TestCase(73, Result=26645)]
	public static int CalcAge(int age)
	{
		Console.WriteLine($"Input: {age}");
		return Program.CalcAge(age);
	}
}

------------------------------

estimación: 4 minutos 
Tiempo real: 1 minutos

################################

Convert Minutes into Seconds
Write a function that takes an integer minutes and converts it to seconds.

Examples
convert(5) ➞ 300

convert(3) ➞ 180

convert(2) ➞ 120
Notes
Don't forget to return the result.
If you get stuck on a challenge, find help in the Resources tab.
If you're really stuck, unlock solutions in the Solutions tab.
------------
public class Program {
	public static int convert(int minutes) {
		return minutes * 60;
	}
}
---------------------------------

using System;
using NUnit.Framework;

[TestFixture]
public class Tests {
	[Test]
	[TestCase(6, Result=360)]
	[TestCase(4, Result=240)]
	[TestCase(8, Result=480)]
	[TestCase(60, Result=3600)]
	public static int FixedTest(int a) {
		Console.WriteLine($"Input: {a}");
		return Program.convert(a);
	}
}

-------------------------------

estimación: 4 minutos
tiempo real: 1 minuto
