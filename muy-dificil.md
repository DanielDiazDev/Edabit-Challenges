## Cup Swapping
### There are three cups on a table, at positions A, B, and C. At the start, there is a ball hidden under the cup at position B.
However, I perform several swaps on the cups, which is notated as two letters. For example, if I swap the cups at positions A and B, I could notate this as AB or BA.

Create a function that returns the letter position that the ball is at, once I finish swapping the cups. The swaps will be given to you as an array.
### Worked Example
- cupSwapping(["AB", "CA", "AB"]) ➞ "C"

// Ball begins at position B.
// Cups A and B swap, so the ball is at position A.
// Cups C and A swap, so the ball is at position C.
// Cups A and B swap, but the ball is at position C, so it doesn't move.
### Examples
- cupSwapping(["AB", "CA"]) ➞ "C"

- cupSwapping(["AC", "CA", "CA", "AC"]) ➞ "B"

- cupSwapping(["BA", "AC", "CA", "BC"]) ➞ "A"
### Notes
> A swap could be notated in two different ways, since both ways end up with the same outcome.
All swaps will be notated as capital letters and will be valid.
You cannot swap a cup with itself.
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
  	[Test]
	public void TestCupSwapping()
    {
	  	var i = 1;
		Assert.AreEqual(Program.CupSwapping(new String[] { "AB", "CA" }), "C", $"Test {i++}");
		Assert.AreEqual(Program.CupSwapping(new String[] { "AB", "CA", "AB" }), "C", $"Test {i++}");
		Assert.AreEqual(Program.CupSwapping(new String[] { "AC", "CA", "CA", "AC" }), "B", $"Test {i++}");
		Assert.AreEqual(Program.CupSwapping(new String[] { "BA", "AC", "CA", "BC" }), "A", $"Test {i++}");
		Assert.AreEqual(Program.CupSwapping(new String[] { "BC", "CB", "CA", "BA" }), "A", $"Test {i++}");
		Assert.AreEqual(Program.CupSwapping(new String[] { "BC" }), "C", $"Test {i++}");
		Assert.AreEqual(Program.CupSwapping(new String[] { "BA", "CA", "CB", "CA" }), "B", $"Test {i++}");
		Assert.AreEqual(Program.CupSwapping(new String[] {  }), "B", $"Test {i++}");
	}
}
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
