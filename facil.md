*****Find the Smallest and Biggest Numbers********
Create a function that takes an array of numbers and return both the minimum and maximum numbers, in that order.

Examples
FindMinMax([1, 2, 3, 4, 5]) ➞ [1, 5]

FindMinMax([2334454, 5]) ➞ [5, 2334454]

FindMinMax([1]) ➞ [1, 1]
Notes
All test arrays will have at least one element and are valid.

---------------------------


Code

using System;
using System.Linq;
using System.Collections.Generic;
public class Program 
{
    public static double[] FindMinMax(double[] values)
        {
            double[] orderValues = values.OrderBy(x => x).ToArray();
            return new double[] { orderValues.First(), orderValues.Last() };
    }
}

-------------
test

using NUnit.Framework;
using System;
[TestFixture]
public class Tests
{
    [Test]
  public static void MaxText()
    {    
      Assert.AreEqual(new double[]{1,54},Program.FindMinMax(new double[]{14,35,6,1,34,54}));
    Assert.AreEqual(new double[]{1.346, 1.8734},Program.FindMinMax(new double[]{1.346, 1.6532, 1.8734, 1.8723}));
    Assert.AreEqual(new double[]{0.2345, 0.984},Program.FindMinMax(new double[]{0.432, 0.874, 0.523, 0.984, 0.327, 0.2345}));
    Assert.AreEqual(new double[]{13, 98},Program.FindMinMax(new double[]{13, 72, 98, 43, 24, 65, 31}));
    Assert.AreEqual(new double[]{-54, -21},Program.FindMinMax(new double[]{-54, -23, -54, -21}));
    Assert.AreEqual(new double[]{-0.6834, 0.5632},Program.FindMinMax(new double[]{-0.473, -0.6834, -0.1287, 0.5632}));
    Assert.AreEqual(new double[]{0, 0},Program.FindMinMax(new double[]{0, 0, 0, 0}));
    
    }
}

-----
estimacion: 10 minutos
tiempo real: 5 minutos



#################################

*****Convert Number to Corresponding Month Name*****
Create a function that takes a number (from 1 to 12) and returns its corresponding month name as a string. For example, if you're given 3 as input, your function should return "March", because March is the 3rd month.

Number	Month Name
1	January
2	February
3	March
4	April
5	May
6	June
7	July
8	August
9	September
10	October
11	November
12	December
Examples
MonthName(3) ➞ "March"

MonthName(12) ➞ "December"

MonthName(6) ➞ "June"
Notes
You can expect only integers ranging from 1 to 12 as test input.
If you get stuck on a challenge, find help in the Resources tab.
If you're really stuck, unlock solutions in the Solutions tab.

--------
code
public class Program 
{
    public static string MonthName(int num) 
    {
			switch(num) {
				case 1: 
					return "January";
				case 2:
					return "February";
					case 3:
					return "March";
					case 4:
					return "April";
					case 5:
					return "May";
					case 6:
					return "June";
					case 7:
					return "July";
					case 8:
					return "August";
					case 9:
					return "September";
					case 10:
					return "October";
					case 11:
					return "November";
					case 12:
					return "December";
				default:
					return "Don't";
			}
    }
}
---------
test

using NUnit.Framework;
using System;

[TestFixture]
public class Tests
{
		[Test]
		[TestCase(1, Result="January")]
		[TestCase(2, Result="February")]
		[TestCase(3, Result="March")]
		[TestCase(4, Result="April")]
		[TestCase(5, Result="May")]
		[TestCase(6, Result="June")]
		[TestCase(7, Result="July")]
		[TestCase(8, Result="August")]
		[TestCase(9, Result="September")]
		[TestCase(10, Result="October")]
		[TestCase(11, Result="November")]
		[TestCase(12, Result="December")]
    public static string MonthName(int num) 
    {
				Console.WriteLine($"Input: {num}");
        return Program.MonthName(num);
    }
}

----------------
estimacion: 7 minutos
tiempo real: 7 minutos
