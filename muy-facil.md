
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

Test.assertEquals(addition(2, 3), 5)
Test.assertEquals(addition(-3, -6), -9)
Test.assertEquals(addition(7, 3), 10)
Test.assertEquals(addition(88, 2), 90)

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

Test.assertEquals(convert(6), 360)
Test.assertEquals(convert(4), 240)
Test.assertEquals(convert(8), 480)
Test.assertEquals(convert(60), 3600)

-------------------------------

estimación: 4 minutos
tiempo real: 1 minuto
