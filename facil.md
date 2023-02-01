*****Find the Smallest and Biggest Numbers********
Create a function that takes an array of numbers and return both the minimum and maximum numbers, in that order.

Examples
FindMinMax([1, 2, 3, 4, 5]) ➞ [1, 5]

FindMinMax([2334454, 5]) ➞ [5, 2334454]

FindMinMax([1]) ➞ [1, 1]
Notes
All test arrays will have at least one element and are valid.

---------------------------


Code

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

-------------
test

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

-----
estimacion: 10 minutos
tiempo real: 5 minutos

