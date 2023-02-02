
### Examples

### Notes

### Solution

### Test

Estimation: 
<br> Real time: 

-----------------------
## Reverse the Case
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
