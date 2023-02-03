## Working 9 to 5
### Write a function that calculates overtime and pay associated with overtime.
### Working 9 to 5: regular hours
### After 5pm is overtime
### Your function gets an array with 4 values:

### Start of working day, in decimal format, (24-hour day notation)
### End of working day. (Same format)
### Hourly rate
### Overtime multiplier
### Your function should spit out:

### $ + earned that day (rounded to the nearest hundreth)



### Examples


- OverTime([9, 17, 30, 1.5]) ➞ "$240.00"

- OverTime([16, 18, 30, 1.8]) ➞ "$84.00"

- OverTime([13.25, 15, 30, 1.5]) ➞ "$52.50"

-2nd example explained:
From 16 to 17 is regular, so 1 * 30 = 30
From 17 to 18 is overtime, so 1 * 30 * 1.8 = 54
30 + 54 = $84.00

### Notes
> N/A
### Solution
```cs
public class Challenge
    {
        public static string OverTime(double[] arr)
        {
            double startDay = arr[0];
            double endDay = arr[1];
            double hourlyRate = arr[2]; 
            double overtimeMultiplier = arr[3];
            double hours = 0;
            double overHours = 0;

            if(endDay <= 17)
            {
                hours = endDay - startDay;
            }
            else if(startDay <= 17)
            {
                hours = 17 - startDay;
                overHours = endDay - 17;
            }
            else
            {
                overHours = endDay- startDay;
            }
            double total = (hours * hourlyRate) + (overHours * overtimeMultiplier * hourlyRate);
            return "$" + string.Format("{0:0.00}", total);
        }
```
### Test
```cs
using NUnit.Framework;

namespace Tests
{
	[TestFixture]
	public class ChallengeTests
	{
		[Test]
		public void Test1()
			=> Assert.AreEqual("$240.00", Challenge.OverTime(new [] { 9, 17, 30, 1.5 }));
        
		[Test]
		public void Test2() 
			=> Assert.AreEqual("$400.00", Challenge.OverTime(new double[] { 9, 18, 40, 2 }));
        
		[Test]
		public void Test3() 
			=> Assert.AreEqual("$325.00", Challenge.OverTime(new [] { 13, 20, 32.5, 2 }));
        
		[Test]
		public void Test4() 
			=> Assert.AreEqual("$100.00", Challenge.OverTime(new [] { 9, 13, 25, 1.5 }));
        
		[Test]
		public void Test5() 
			=> Assert.AreEqual("$364.00", Challenge.OverTime(new [] { 11.5, 19, 40, 1.8 }));
        
		[Test]
		public void Test6() 
			=> Assert.AreEqual("$210.00", Challenge.OverTime(new[] { 10, 17, 30, 1.5 }));
        
		[Test]
		public void Test7() 
			=> Assert.AreEqual("$209.63", Challenge.OverTime(new [] { 10.5, 17, 32.25, 1.5 }));
        
		[Test]
		public void Test8() 
			=> Assert.AreEqual("$84.00", Challenge.OverTime(new [] { 16, 18, 30, 1.8 }));
        
		[Test]
		public void Test9() 
			=> Assert.AreEqual("$130.00", Challenge.OverTime(new [] { 18, 20, 32.5, 2 }));
        
		[Test]
		public void test10() 
			=> Assert.AreEqual("$52.50", Challenge.OverTime(new [] { 13.25, 15, 30, 1.5 }));
        
		[Test]
		public void Test11() 
			=> Assert.AreEqual("$432.32", Challenge.OverTime(new [] { 13, 21, 38.6, 1.8 }));
	}
}
```
Estimation: 25 minutes
<br> Real time: 20  minutes

---------------------------------------

## Amount of Unique Fractions
### Create a function double UniqueFract(), which should sum all irreducible regular fractions between 0 and 1, in the numerator and denominator of which there are only single-digit numbers: 1/2, 1/3, 1/4, ... 2/3, 2/4, ... 8/9.

### Task
- UniqueFract() ➞ sum
### Notes
> Of the fractions 1/2 2/4 3/6 4/8, only 1/2 is included in the sum.
Don't include any values >= 1.
Both the numerator and denominator are single digit.
### Solution
```cs
using System;
using System.Collections.Generic;
using System.Linq;
public class Program
{
    public static double UniqueFract()
    {
			double sum = 0;
            List<double> fractionsInNumber = new List<double>();
            for (double denominator = 2; denominator <= 9; denominator ++)
            {
                for(double numerator = 1; numerator < denominator; numerator++)
                {

                    if (!fractionsInNumber.Contains(numerator / denominator)) fractionsInNumber.Add(numerator / denominator);


                }
            }
            sum = fractionsInNumber.Sum();
            return sum;
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
	[TestCase(Result=13.5)]
  public static double FixedTest()
    {
        return Program.UniqueFract();
    }
}
```
Estimation: 25 minutes
<br> Real time: 12 minutes

---------------------------------------


## True Alphabetical Order
### Create a function which takes every letter in every word, and puts it in alphabetical order. Note how the original word lengths must stay the same.

### Examples
- TrueAlphabetic("hello world") ➞ "dehll loorw"

- TrueAlphabetic("edabit is awesome") ➞ "aabdee ei imosstw"

- TrueAlphabetic("have a nice day") ➞ "aaac d eehi nvy"
- 
### Notes
> All sentences will be in lowercase.
> No punctuation or numbers will be included in the Tests.
### Solution
```cs
using System;
using System.Collections.Generic;
using System.Linq;

public class Program
{
    public static string TrueAlphabetic(string str)
        {
            List<char> lista = str.Replace(" ", "").OrderBy(x => x).ToList();
            for(int i = 0; i < str.Length; i++)
            {
                if (str[i] == ' ')
                {
                    lista.Insert(i, ' ');
                }
            }
            return new string(lista.ToArray());
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
	[TestCase("hello world", Result="dehll loorw")]
	[TestCase("edabit is awesome", Result="aabdee ei imosstw")]
	[TestCase("have a nice day", Result="aaac d eehi nvy")]
	[TestCase("i love to code", Result="c deei lo ootv")]
	[TestCase("joshua senoron", Result="aehjnn ooorssu")]
    public static string TestSolution(string str)
    {
        return Program.TrueAlphabetic(str);
    }
}
```
Estimation: 25 minutes
<br> Real time: 15 minutes

---------------------------------------
