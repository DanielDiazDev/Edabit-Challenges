## [Reverse the Case](https://edabit.com/challenge/99oN5igrbXddAjHEL)
### Given a string, create a function to reverse the case. All lower-cased letters should be upper-cased, and vice versa.




### Examples
- ReverseCase("Happy Birthday") ➞ "hAPPY bIRTHDAY"

- ReverseCase("MANY THANKS") ➞ "many thanks"

- ReverseCase("sPoNtAnEoUs") ➞ "SpOnTaNeOuS"

### Notes
> N/A


### Solution
```cs
using System.Linq;
public class Program 
{
    public static string ReverseCase(string str) 
    {
			return string.Concat(str.Select(x=>char.IsUpper(x)?char.ToLower(x):char.ToUpper(x)));
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
		[TestCase("Happy Birthday", Result="hAPPY bIRTHDAY")]
		[TestCase("MANY THANKS", Result="many thanks")]
		[TestCase("sPoNtAnEoUs", Result="SpOnTaNeOuS")]
		[TestCase("eXCELLENT, yOuR mAJESTY", Result="Excellent, YoUr Majesty")]
    public static string ReverseCase(string str) 
    {
				Console.WriteLine($"Input: {str}");
        return Program.ReverseCase(str);
    }
}
```

Estimation: 14 minutes
<br> Real time: 10 minutes

-----------------------

## [Find the Largest Numbers in a Group of Arrays](https://edabit.com/challenge/nermqxzovZbfFBC9X)
### Create a function that takes an array of arrays with numbers. Return a new (single) array with the largest numbers of each.



### Examples
- FindLargest([[4, 2, 7, 1], [20, 70, 40, 90], [1, 2, 0]]) ➞ [7, 90, 2]

- FindLargest([[-34, -54, -74], [-32, -2, -65], [-54, 7, -43]]) ➞ [-34, -2, 7]

- FindLargest([[0.4321, 0.7634, 0.652], [1.324, 9.32, 2.5423, 6.4314], [9, 3, 6, 3]]) ➞ [0.7634, 9.32, 9]

### Notes
> Watch out for negative numbers.


### Solution
```cs
using System;
using System.Linq;
using System.Collections.Generic;

public class Program 
{
    public static double[] FindLargest(double[][] values) 
    {
	return values.Select(x=> x.Max()).ToArray();
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
      Assert.AreEqual(new double[]{7,90,2},Program.FindLargest(new double[][]{new double[]{4,2,7,1},new double[]{20,70,40,90},new double[]{1,2,0}}));
    Assert.AreEqual(new double[]{0.7634, 9.32, 9},Program.FindLargest(new double[][]{new double[]{0.4321, 0.7634, 0.652},new double[]{1.324, 9.32, 2.5423},new double[]{9, 3, 6, 3}}));
    Assert.AreEqual(new double[]{-34, -2, 7},Program.FindLargest(new double[][]{new double[]{-34, -54, -74},new double[]{-32, -2, -65},new double[]{-54, 7, -43}}));
    Assert.AreEqual(new double[]{1.34, -1.762, 65},Program.FindLargest(new double[][]{new double[]{0.34, -5, 1.34},new double[]{-6.432, -1.762, -1.99},new double[]{32, 65, -6}}));
    Assert.AreEqual(new double[]{ 0, 3, -2 },Program.FindLargest(new double[][]{new double[]{0, 0, 0, 0},new double[]{3, 3, 3, 3},new double[]{-2, -2}}));
    }
}
```

Estimation: 15 minutes
<br> Real time: 4 minutes



## [Find the Bomb](https://edabit.com/challenge/JYEufqRvkusjr5R58)
### Create a function that finds the word "bomb" in the given string (not case sensitive). If found, return "Duck!!!", otherwise, return "There is no bomb, relax.".



### Examples
- Bomb("There is a bomb.") ➞ "Duck!!!"

- Bomb("Hey, did you think there is a bomb?") ➞ "Duck!!!"

- Bomb("This goes boom!!!") ➞ "There is no bomb, relax."

### Notes
> "bomb" may appear in different cases (i.e. uppercase, lowercase, mixed).

### Solution
```cs
using System;
public class Program
{
	public static string Bomb(string txt)
        {
            if (txt.ToLower().Contains("bomb")) return "Duck!!!";
            return "There is no bomb, relax.";
        }
}
```
### Test
```cs
using System;
using NUnit.Framework;

[TestFixture]
public class Tests
{
    [Test]
[TestCase("There is a bomb.", Result =  "Duck!!!")]
[TestCase("Hey, did you find it?", Result =  "There is no bomb, relax.")]
[TestCase("Hey, did you think there is a bomb?", Result =  "Duck!!!")]
[TestCase("This goes boom!!!", Result =  "There is no bomb, relax.")]
[TestCase("Hey, did you find the BoMb?", Result =  "Duck!!!")]
[TestCase("Commotion in the third, a bomb is found!", Result =  "Duck!!!")]
    public static string FixedTest(string a)
    {
        return Program.Bomb(a);
    }
}
```
Estimation: 15 minutes
<br> Real time: 11 minutes


## [Count Ones in Binary Representation of Integer]([https://edabit.com/challenge/JYEufqRvkusjr5R58](https://edabit.com/challenge/zn3A3AAzoE7vezw7Q))
### Count the amount of ones in the binary representation of an integer. For example, since 12 is 1100 in binary, the return value should be 2.


### Examples
- CountOnes(0) ➞ 0

- CountOnes(100) ➞ 3

- CountOnes(999) ➞ 8

### Notes
> The input will always be a valid integer (number).

### Solution
```cs
public class Program
{
    public static int CountOnes(int i)
    {
			int count = 0;
        while (i > 0)
        {
            count += i % 2;
            i /= 2;
        }
        return count;
    }
}
```
### Test
```cs
using System;
using NUnit.Framework;

[TestFixture]
public class TestCountOnesShould
    {
        //count number of 1s 
        [Test]
        public void ReturnZeroWhenNumberZero()
        {
            int number = 0;

            int result = Program.CountOnes(number);

            Assert.Zero(result); 
        }
        [Test]
        public void ReturnOneWhenNumberIsOne()
        {
            int number = 1;

            int result = Program.CountOnes(number);

            Assert.AreEqual(1, result);
        }
        [Test]
        public void ReturnOneWhenNumberIsTwo()
        {
            int number = 2;

            int result = Program.CountOnes(number);

            Assert.AreEqual(1, result);
        }
        [Test]
        public void ReturnTwoWhenNumberIsThree()
        {
            int number = 3;

            int result = Program.CountOnes(number);

            Assert.AreEqual(2, result);
        }

        [Test]
        [TestCase(12, ExpectedResult = 2)]
        [TestCase(100, ExpectedResult = 3)]
        [TestCase(101, ExpectedResult = 4)]
        [TestCase(999, ExpectedResult = 8)]
        [TestCase(123456789, ExpectedResult = 16)]
        [TestCase(1234567890, ExpectedResult = 12)]
        public static int CountOnes(int i)
        {
            return Program.CountOnes(i);
        }


    }
```
Estimation: 15 minutes
<br> Real time: 20 minutes
