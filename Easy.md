## [Find the Smallest and Biggest Numbers](https://edabit.com/challenge/kMWmiNJM4szSv7dLd)
### Create a function that takes an array of numbers and return both the minimum and maximum numbers, in that order.

### Examples
- FindMinMax([1, 2, 3, 4, 5]) ➞ [1, 5]

- FindMinMax([2334454, 5]) ➞ [5, 2334454]

- FindMinMax([1]) ➞ [1, 1]

### Notes
> All test arrays will have at least one element and are valid.



### Solution
```cs
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
```

### Test

```cs
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
```

Estimation: 10 minutes
<br> Real time: 5 minutes



------------------------------------
## [Convert Number to Corresponding Month Name](https://edabit.com/challenge/uevxL5FNM77otyo9Z)
### Create a function that takes a number (from 1 to 12) and returns its corresponding month name as a string. For example, if you're given 3 as input, your function should return "March", because March is the 3rd month.

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

### Examples
- MonthName(3) ➞ "March"

- MonthName(12) ➞ "December"

- MonthName(6) ➞ "June"

### Notes

> - You can expect only integers ranging from 1 to 12 as test input.
> - If you get stuck on a challenge, find help in the Resources tab.
> - If you're really stuck, unlock solutions in the Solutions tab.

### Solution
```cs
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
```

### Test
```cs
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
```

Estimation: 7 minutes
<br> Real time: 7 minutes


------------------------------------
## [How Many Vowels?](https://edabit.com/challenge/5ytLyHsZHfyDhBgXr)
### Create a function that takes a string and returns the number (count) of vowels contained within it.

### Examples
- CountVowels("Celebration") ➞ 5

- CountVowels("Palm") ➞ 1

- CountVowels("Prediction") ➞ 4

### Notes
> a, e, i, o, u are considered vowels (not y).
All test cases are one word and only contain letters.

### Solution
```cs
using System;
using System.Collections.Generic;
using System.Linq;

public class Program 
{
    public static int CountVowels(string str)
        {
            string vocals = "aeiou";
             return str.Where(x=> vocals.Contains(x)).Count();
        }
}
```
### Test
```cs
using NUnit.Framework;

[TestFixture]
public class Tests
{
  [Test]
  [TestCase("Celebration", Result=5)]
  [TestCase("Palm", Result=1)]
  [TestCase("Prediction", Result=4)]
  [TestCase("Suite", Result=3)]
  [TestCase("Quote", Result=3)]
  [TestCase("Portrait", Result=3)]
  [TestCase("Steam", Result=2)]
  [TestCase("Tape", Result=2)]
  [TestCase("Nightmare", Result=3)]
  [TestCase("Convention", Result=4)]
    public static int FixedTest(string str)
    {
        return Program.CountVowels(str);
    }
}
```
Estimation: 7 minutes
<br> Real time: 8 minutes
------------
## [Smaller String Number]([https://edabit.com/challenge/5ytLyHsZHfyDhBgXr](https://edabit.com/challenge/uBqpafqjoYNPuQ7Pr))
### Create a function that returns the smaller number.

### Examples
- smallerNum("21", "44") ➞ "21"

- smallerNum("1500", "1") ➞ "1"

- smallerNum("5", "5") ➞ "5"

### Notes
> Numbers will be represented as strings, and your output should also be a string.
If both numbers tie, return either number.
Numbers will be positive.
Bonus: See if you can do this without converting to integers.

### Solution
```cs
public class Program
{
	public static string smallerNum(string n1, string n2)
	{
		if(n1.CompareTo(n2) < 0 && n1.Length <= n2.Length) 
        {
            return n1;
        }
        else
        {
            return n2;
        }
	}
}
```
### Test
```cs
using NUnit.Framework;

[TestFixture]
public class TestSmallerNumShould
    {
        ////Requirements:
        //Recibe 2 numbers as string
        //Should return smallest 
        //if both are equals, return any
        //  BONUS: don't convert to integer
        [SetUp]
        public void Setup()
        {

        }

        [Test]
        public void ReturnFirstNumberWhenFirstNumberIsSmaller()
        {
            string firstNumber = "1";
            string secondNumber = "2";

            string result = Program.smallerNum(firstNumber, secondNumber);

            Assert.AreEqual(firstNumber, result);


        }
        [Test]
        public void ReturnSecondNumberWhenSecondNumberIsSmaller()
        {
            string firstNumber = "3";
            string secondNumber = "2";

            string result = Program.smallerNum(firstNumber, secondNumber);

            Assert.AreEqual(secondNumber, result);


        }
        [Test]
        public void ReturnAnyNumberWhenBothAreEquals()
        {
            string firstNumber = "2";
            string secondNumber = "2";


            string result = Program.smallerNum(firstNumber, secondNumber);

            Assert.AreEqual("2", result);


        }
        [Test]
        [TestCase("21", "44",  ExpectedResult = "21")]
        [TestCase("153", "367", ExpectedResult = "153")]
        [TestCase("1500", "16", ExpectedResult = "16")]
        [TestCase("100", "23", ExpectedResult = "23")]
        [TestCase("1500", "1", ExpectedResult = "1")]
        [TestCase("5", "5", ExpectedResult = "5")]
        public static string smallerNum(string n1, string n2)
        {
            return Program.smallerNum(n1, n2);
        }

    }
```
Estimation: 7 minutes
<br> Real time: 8 minutes
