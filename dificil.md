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
Estimation: 
<br> Real time: 
--------------------------
