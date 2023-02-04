## Three Sum Problem
### Write a function that returns all sets of three elements that sum to 0.


### Examples
- ThreeSum(new int[] { 0, 1, -1, -1, 2 }) ➞ { { 0, 1, -1 }, { -1, -1, 2 } }

- ThreeSum(new int[] { 0, 0, 0, 5, -5 }) ➞ { { 0, 0, 0 }, { 0, 5, -5 } }

- ThreeSum(new int[] { 1, 2, 3 }) ➞ { }

- ThreeSum(new int[1]) ➞ { }
### Notes
> The original array may contain duplicate numbers.
Each three-element subarray in your output should be distinct.
Subarrays should be ordered by the first element of the subarray.
Subarrays themselves should be ordered the same as the original array.
Return an empty array if no three elements sum to zero.
Return an empty array if there are fewer than three elements.
### Solution
```cs
using System;
using System.Linq;
using System.Collections.Generic;

public class Program
{
	public static List<int[]> ThreeSum(int[] arr) 
	{
		List<int[]> listOfArrayThreeElementsThatSumZero = new List<int[]>();

            for (int i = 0; i < arr.Length -2; i++)
            {
                for (int j =i+1; j< arr.Length -1; j++)
                {
                    for(int k = j + 1; k<arr.Length; k++)
                    {
                        if(arr[i]+arr[j]+arr[k] == 0)
                        {
                            if (!listOfArrayThreeElementsThatSumZero.Any(numbers => numbers[0] == arr[i] && numbers[1] == arr[j] && numbers[2] == arr[k]))
                            {
                                listOfArrayThreeElementsThatSumZero.Add(new int[] { arr[i], arr[j], arr[k] });
                            }          
                        }                       
                    }
                }
            }
            return listOfArrayThreeElementsThatSumZero;
	}
}
```
### Test
```cs
using NUnit.Framework;
using System;
using System.Linq;

[TestFixture]
public class Tests
{
    [TestCase(new int[] { 0, 1, -1, -1, 2 }, Result = "{ { 0, 1, -1 }, { -1, -1, 2 } }")]
    [TestCase(new int[] { 0, 0, 0, 5, -5 }, Result = "{ { 0, 0, 0 }, { 0, 5, -5 } }")]
    [TestCase(new int[] { 0, -1, 1, 0, -1, 1 }, Result = "{ { 0, -1, 1 }, { 0, 1, -1 }, { -1, 1, 0 }, { -1, 0, 1 }, { 1, 0, -1 } }")]
    [TestCase(new int[] { 0, 5, 5, 0, 0 }, Result = "{ { 0, 0, 0 } }")]
    [TestCase(new int[] { 0, 5, -5, 0, 0 }, Result = "{ { 0, 5, -5 }, { 0, 0, 0 }, { 5, -5, 0 } }")]
    [TestCase(new int[] { 1, 2, 3, -5, 8, 9, -9, 0 }, Result = "{ { 1, 8, -9 }, { 2, 3, -5 }, { 9, -9, 0 } }")]
    [TestCase(new int[] { 0, 0, 0 }, Result = "{ { 0, 0, 0 } }")]
    [TestCase(new int[] { 1, 5, 5, 2 }, Result = "{  }")]
    [TestCase(new int[] { 1, 1 }, Result = "{  }")]
    [TestCase(new int[] { }, Result = "{  }")]
    public static string TestThreeSum(int[] arr)
    {
        var res = Program.ThreeSum(arr);
        var result = string.Join(", ", res.Select(itm => $"{{ {itm[0]}, {itm[1]}, {itm[2]} }}"));
        return "{ " + result + " }";
    }
}
```
Estimation: 30 minutes
<br> Real time: 25  minutes

---------------------------------------

## The Smallest Number
### Given a positive integer n, implement a function that finds the smallest number that is evenly divisible by the integers 1 through n inclusive. Return value as a string.

### Examples
- Smallest(1) ➞ "1"

- Smallest(5) ➞ "60"

- Smallest(10) ➞ "2520"

- Smallest(20) ➞ "232792560"
### Notes
> You will need to cope with numbers larger than Int64.MaxValue (see Resources).
### Solution
```cs
using System;
using System.Text;
using System.Text.RegularExpressions;
using System.Collections;
using System.Collections.Generic;
using System.Linq;
using System.Numerics;

public class Program 
{
			public static string Smallest(int n)
    {
        BigInteger number = 1;
        int divisor;
        List<int> numbers = new List<int>();

        if (n <= 1) return 1.ToString();

        for (int i = 1; i <= n; i++)
        {
            numbers.Add(i);
        }
        
        divisor = 2;
        while (numbers.Count > 0)
        {
            if (numbers.Any(num => num % divisor == 0))
            {
                numbers = numbers.Select(num => num % divisor == 0 ? num / divisor : num).Where(num => num > 1).ToList();
                number *= divisor;
                divisor = 2;
            }
            else
            {
                divisor++;
            }
        }
        return number.ToString();    
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
		[TestCase(1, Result="1")]
		[TestCase(10, Result="2520")]
		[TestCase(17, Result="12252240")]
		[TestCase(31, Result="72201776446800")]
		[TestCase(99, Result="69720375229712477164533808935312303556800")]
		[TestCase(100, Result="69720375229712477164533808935312303556800")]
		[TestCase(101, Result="7041757898200960193617914702466542659236800")]	  
		public static string TestSmallest(int n) 
    {
				Console.WriteLine($"Input: {n}");
        return Program.Smallest(n);
    }
}
```
Estimation: 30 minutes
<br> Real time: 27 minutes

---------------------------------------
##
### 

### Examples
- 
### Notes
> 
### Solution
```cs

```
### Test
```cs

```
Estimation: 20 minutes
<br> Real time: 13 minutes

---------------------------------------

