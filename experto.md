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
