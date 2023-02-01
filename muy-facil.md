
Return the Sum of Two Numbers
Create a function that takes two numbers as arguments and returns their sum.

Examples
addition(3, 2) ➞ 5

addition(-3, -6) ➞ -9

addition(7, 3) ➞ 10
Notes
Don't forget to return the result.
If you get stuck on a challenge, find help in the Resources tab.
If you're really stuck, unlock solutions in the Solutions tab.

--------------------

public class Program
{
    public static int Sum(int a, int b)
    {
        int result = a + b;
        return result;
    }
}

-----------------------------

Test.assertEquals(addition(2, 3), 5)
Test.assertEquals(addition(-3, -6), -9)
Test.assertEquals(addition(7, 3), 10)
Test.assertEquals(addition(88, 2), 90)

---------------------
estimación: 4 minutos
Tiempo real: 2 minutos

##########################
Convert Age to Days
Create a function that takes the age in years and returns the age in days.

Examples
calcAge(65) ➞ 23725

calcAge(0) ➞ 0

calcAge(20) ➞ 7300

Notes
Use 365 days as the length of a year for this challenge.
Ignore leap years and days between last birthday and now.
Expect only positive integer inputs.

------------------------------

estimación: 4 minutos 
Tiempo real: 1 minutos

