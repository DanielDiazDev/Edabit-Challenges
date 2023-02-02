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
--------------------------


## Consecutive Numbers
### Given a string, create a function to reverse the case. All lower-cased letters should be upper-cased, and vice versa.

### Examples
- Cons([5, 1, 4, 3, 2]) ➞ true
// Can be re-arranged to form [1, 2, 3, 4, 5]

- Cons([5, 1, 4, 3, 2, 8]) ➞ false

- Cons([5, 6, 7, 8, 9, 9]) ➞ false
// 9 appears twice
### Notes
> N/A
### Solution
```cs

using System.Linq;

public class Program
{
	public static bool Cons(int[] arr)
	{
		 int[] orderedArr = arr.OrderBy(x=>x).ToArray();
           
            for (int i = 0; i < orderedArr.Length -1; i++)
            {
                if (orderedArr[i]+1 != orderedArr[i+1] ) return false;
            }

            return true;
       
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
	[TestCase(new int[]{5, 1, 4, 3, 2}, Result=true)]
	[TestCase(new int[]{55, 59, 58, 56, 57}, Result=true)]
	[TestCase(new int[]{-3, -2, -1, 1, 0}, Result=true)]
	[TestCase(new int[]{5, 1, 4, 3, 2, 8}, Result=false)]
	[TestCase(new int[]{5, 6, 7, 8, 9, 9}, Result=false)]
	[TestCase(new int[]{5, 3}, Result=false)]
	public static bool FixedTest(int[] arr) =>
		Program.Cons(arr);

}
```
Estimation: 20 minutes
<br> Real time: 13 minutes
--------------------------





## A Week Later
### Create a function which takes in a date as a string, and returns the date a week after.

### Examples
- WeekAfter("12/03/2020") ➞ "19/03/2020"

- WeekAfter("21/12/1989") ➞ "28/12/1989"

- WeekAfter("01/01/2000") ➞ "08/01/2000"
### Notes
> - Note that dates will be given in day/month/year format.
- Single digit numbers should be zero padded.
### Solution
```cs

```
### Test
```cs
using NUnit.Framework;
using System;

[TestFixture]
public class Tests
{
	[TestCase("12/03/2020", Result="19/03/2020")]
	[TestCase("21/12/1989", Result="28/12/1989")]
	[TestCase("01/01/2000", Result="08/01/2000")]
	[TestCase("24/09/1924", Result="01/10/1924")]
	[TestCase("21/07/1964", Result="28/07/1964")]
	[TestCase("14/07/2085", Result="21/07/2085")]
	[TestCase("25/04/1953", Result="02/05/1953")]
	[TestCase("02/01/2200", Result="09/01/2200")]
	[TestCase("06/01/2007", Result="13/01/2007")]
	[TestCase("07/04/2195", Result="14/04/2195")]
	[TestCase("04/09/2094", Result="11/09/2094")]
	[TestCase("20/08/1910", Result="27/08/1910")]
	[TestCase("12/12/1894", Result="19/12/1894")]
	[TestCase("02/11/2094", Result="09/11/2094")]
	[TestCase("22/12/1955", Result="29/12/1955")]
	[TestCase("18/04/1859", Result="25/04/1859")]
	[TestCase("17/03/1847", Result="24/03/1847")]
	[TestCase("17/03/2142", Result="24/03/2142")]
	[TestCase("26/01/2145", Result="02/02/2145")]
	[TestCase("03/12/1959", Result="10/12/1959")]
	[TestCase("01/06/1947", Result="08/06/1947")]
	[TestCase("26/12/1853", Result="02/01/1854")]
	[TestCase("27/10/2068", Result="03/11/2068")]
	[TestCase("05/05/2080", Result="12/05/2080")]
	[TestCase("22/12/2144", Result="29/12/2144")]
	[TestCase("12/05/1870", Result="19/05/1870")]
	[TestCase("07/01/1882", Result="14/01/1882")]
	[TestCase("16/06/2032", Result="23/06/2032")]
	[TestCase("02/10/2007", Result="09/10/2007")]
	[TestCase("24/03/1871", Result="31/03/1871")]
	[TestCase("19/08/1847", Result="26/08/1847")]
	[TestCase("24/07/2157", Result="31/07/2157")]
	[TestCase("28/12/1848", Result="04/01/1849")]
	[TestCase("20/07/1951", Result="27/07/1951")]
	[TestCase("14/11/2071", Result="21/11/2071")]
	[TestCase("07/12/2170", Result="14/12/2170")]
	[TestCase("01/03/2080", Result="08/03/2080")]
	[TestCase("28/04/1906", Result="05/05/1906")]
	[TestCase("15/06/2023", Result="22/06/2023")]
	[TestCase("11/08/1950", Result="18/08/1950")]
	[TestCase("15/11/2103", Result="22/11/2103")]
	[TestCase("23/11/1852", Result="30/11/1852")]
	[TestCase("08/01/1928", Result="15/01/1928")]
	[TestCase("14/11/2118", Result="21/11/2118")]
	[TestCase("11/10/2096", Result="18/10/2096")]
	[TestCase("02/12/1816", Result="09/12/1816")]
	[TestCase("10/10/1937", Result="17/10/1937")]
	[TestCase("28/11/1959", Result="05/12/1959")]
	[TestCase("27/05/2133", Result="03/06/2133")]
	[TestCase("28/04/1932", Result="05/05/1932")]
	[TestCase("23/02/2050", Result="02/03/2050")]
	[TestCase("23/05/2146", Result="30/05/2146")]
	[TestCase("24/07/2167", Result="31/07/2167")]
  	public static string TestSolution(string date)
    {
        return Program.WeekAfter(date);
    }
}
```
Estimation: 15 minutes
<br> Real time: nnn minutes
--------------------------



