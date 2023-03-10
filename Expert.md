## [Three Sum Problem](https://edabit.com/challenge/wrxoYop5uZKG4nNSb)
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

## [The Smallest Number](https://edabit.com/challenge/jgHNFWFGkiTJpueTK)
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

## [Palindrome Descendant](https://edabit.com/challenge/PvCD5nSYy3Dnvnfcq)
### A number may not be a palindrome, but its descendant can be. A number's direct child is created by summing each pair of adjacent digits to create the digits of the next number.

For instance, 123312 is not a palindrome, but its next child 363 is, where: 3 = 1 + 2; 6 = 3 + 3; 3 = 1 + 2.

Create a function that returns true if the number itself is a palindrome or any of its des

### Examples
- PalindromeDescendant(11211230) ➞ false
// 11211230 ➞ 2333 ➞ 56

- palindromeDescendant(13001120) ➞ true
// 13001120 ➞ 4022 ➞ 44

- PalindromeDescendant(23336014) ➞ true
// 23336014 ➞ 5665

- PalindromeDescendant(11) ➞ true
// Number itself is a palindrome.
### Notes
> Numbers will always have an even number of digits.

>(Our decision): If number is odd(higher than 1) or is equal to 2, and is not palindrome then return false.
### Solution
```cs
using System;
using System.Linq;
using System.IO;

public class Program 
{
    public static bool PalindromeDescendant(int num)
    {
        if (num < 0)
        {
            throw new InvalidDataException("Parameter number is negative");
        }
        string numAsSTring = num.ToString();

        if (numAsSTring.Length % 2 != 0 && numAsSTring.Length>=2)
        {
            throw new InvalidDataException("Parameter number doesn't have an even number of digits");
        }
        return CheckPalindromeDescendant(numAsSTring);
    }
    public static bool CheckPalindromeDescendant(string numAsSTring)
    {
        if (IsPalindrome(numAsSTring))
        {
            return true;
        }
        else if ((numAsSTring.Length % 2 == 1 && numAsSTring.Length > 2) || numAsSTring.Length == 2)
        {
            return false;
        }
        else
        {
            return CheckPalindromeDescendant(GetDescendant(numAsSTring));
        }
     }
    static bool IsPalindrome(string numberAsString)
    {
        return numberAsString.Equals(string.Concat(numberAsString.Reverse()));
    }
    static string GetDescendant(string numberAsString)
    {
        string finalNumberAsString = "";
        for (int i = 0; i < numberAsString.Length; i += 2)
        {
            finalNumberAsString += (int.Parse(numberAsString[i].ToString()) + int.Parse(numberAsString[i + 1].ToString())).ToString();
        }
        return finalNumberAsString;
    }
}
```
### Test
```cs
using NUnit.Framework;
using System;

public class TestPalindromeDescendantShould
    {
        [Test]
        public void ReturnNegativeParameterNumberException()
        {
            int number = -2121;

            var exception = Assert.Throws<InvalidDataException>(() => Program.PalindromeDescendant(number));

            Assert.AreEqual("Parameter number is negative", exception.Message);
        }
        [Test]
        public void ReturnNotEvenDigitsParameterNumberException()
        {
            int number = 13567;

            var exception = Assert.Throws<InvalidDataException>(() => Program.PalindromeDescendant(number));

            Assert.AreEqual("Parameter number doesn't have an even number of digits", exception.Message);
        }
      
        [Test]
        public void ReturnTrueWhenNumberIsPalindromeAndNumberLengthIsEqualOrHigherThanTwo()
        {
            int number = 22;
            int number2 = 214230;

            bool result = Program.PalindromeDescendant(number);
            bool result2 = Program.PalindromeDescendant(number2);

            Assert.IsTrue(result);
            Assert.IsTrue(result2);
        }
        [Test]
        public void ReturnFalseWhenNumberIsNotPalindromeAndNumberLengthIsTwo()
        {
            int number = 56;

            bool result = Program.PalindromeDescendant(number);


            Assert.IsFalse(result);
        }
        [Test]
        public void ReturnFalseWhenNumberAndAllDescendantsAreNotPalindrome()
        {
            int number = 11211230;
            int number2 = 97358817;

            bool result = Program.PalindromeDescendant(number);
            bool result2 = Program.PalindromeDescendant(number2);

            Assert.IsFalse(result);
            Assert.IsFalse(result2);
        }
        [Test]
        public void ReturnFalseWhenDescendantIsNotPalindromeAndLengthIsOddAndHigherThanOne()
        {
            int number = 112133;
            int number2 = 214422; 

            bool result = Program.PalindromeDescendant(number);
            bool result2 = Program.PalindromeDescendant(number2);

            Assert.IsFalse(result);
            Assert.IsFalse(result2);
        }
        [Test]
        public void ReturnTrueWhenDescendantIsPalindrome()
        {
            int number = 132231;
            int number2 = 13456322;

            bool result = Program.PalindromeDescendant(number);
            bool result2 = Program.PalindromeDescendant(number2);

            Assert.IsTrue(result);
            Assert.IsTrue(result2);
        }
	}
```
Estimation: 60 minutes
<br> Real time: 90 minutes (Test + Requeriments + solution)

---------------------------------------






Notes
N/A
## [Poker Hand Ranking](https://edabit.com/challenge/MnPogX5KgggaRpaJo)
### In this challenge, you have to establish which kind of Poker combination is present in a deck of five cards. Every card is a string containing the card value (with the upper-case initial for face-cards) and the lower-case initial for suits, as in the examples below:

###  Name	Description
Royal Flush	A, K, Q, J, 10, all with the same suit.
Straight Flush	Five cards in sequence, all with the same suit.
Four of a Kind	Four cards of the same rank.
Full House	Three of a Kind with a Pair.
Flush	Any five cards of the same suit, not in sequence.
Straight	Five cards in a sequence, but not of the same suit.
Three of a Kind	Three cards of the same rank.
Two Pair	Two different Pair.
Pair	Two cards of the same rank.
High Card	No other valid combination.
Given an array hand containing five strings being the cards, implement a function that returns a string with the name of the highest combination obtained, accordingly to the table above.
- "Ah" ➞ Ace of hearts
- "Ks" ➞ King of spades
- "3d" ➞ Three of diamonds
- "Qc" ➞ Queen of clubs
- "10c" ➞ Ten of clubs
- There are 10 different combinations. Here's the list, in decreasing order of importance:


### Examples
-PokerHandRanking({ "10h", "Jh", "Qh", "Ah", "Kh" }) ➞ "Royal Flush"

-PokerHandRanking({ "3h", "5h", "Qs", "9h", "Ad" }) ➞ "High Card"

-PokerHandRanking({ "10s", "10c", "8d", "10d", "10h" }) ➞ "Four of a Kind"


### Notes


### Solution
```cs
using System;
using System.Linq;
using System.IO;

public class Program
{
	public static string PokerHandRanking(string[] hand)
    {
        string[] ranksOrder = new string[] { "2", "3", "4", "5", "6", "7", "8", "9", "10", "J", "Q", "K", "A" };
        string[] suits = new string[] { "s", "h", "c", "d" };
        


        


        if (hand == null) throw new InvalidDataException("Hand Parameter is null");
        if (hand.Length != 5) throw new InvalidDataException("Hand has not five Cards");

        if (hand.Any(c => c == null)) throw new InvalidDataException("There are cards with null value");

        if (hand.Any(c => !ranksOrder.Contains(CardRank(c)) || !suits.Contains(CardSuit(c)))) throw new InvalidDataException("There are invalid cards");

        if (hand.GroupBy(c => c).Count() != 5) throw new InvalidDataException("There are repeated cards");

       

        if (HandHasAllCardsWithSameSuit(hand) && HandHasCardsInSequence(hand, ranksOrder) && hand.Any(c => CardRank(c) == "A")) return "Royal Flush";
        if (HandHasAllCardsWithSameSuit(hand) && HandHasCardsInSequence(hand, ranksOrder)) return "Straight Flush";
        if (HandHasSameRanks(hand, new int[] { 4 })) return "Four of a Kind";
        if (HandHasSameRanks(hand, new int[] { 3, 2 })) return "Full House";
        if (HandHasAllCardsWithSameSuit(hand)) return "Flush";
        if (HandHasCardsInSequence(hand, ranksOrder)) return "Straight";
        if (HandHasSameRanks(hand, new int[] { 3 })) return "Three of a Kind";
        if (HandHasSameRanks(hand, new int[] { 2, 2 })) return "Two Pair";
        if (HandHasSameRanks(hand, new int[] { 2 })) return "Pair";
        return "High Card";




    }

    static bool HandHasCardsInSequence(string[] hand, string[] ranksOrder)
    {

        int[] rankIndexOrdered = hand.Select(c => Array.IndexOf(ranksOrder, CardRank(c))).OrderBy(i => i).ToArray();

        int actualIndex = rankIndexOrdered.First();

        for (int i = 0; i < rankIndexOrdered.Length; i++)
        {
            if (rankIndexOrdered[i] != actualIndex) return false;

            actualIndex++;
        }
        return true;
    }


    static bool HandHasAllCardsWithSameSuit(string[] hand)
    {
        return hand.GroupBy(card => CardSuit(card)).Count() == 1;
    }


    static bool HandHasSameRanks(string[] hand, int[] ranksCounts)
    {
        return hand.GroupBy(c => CardRank(c))
            .Select(r => r.Count())
            .Where(rc => rc > 1)
            .OrderBy(rc => rc)
            .SequenceEqual(ranksCounts.OrderBy(rc => rc));
    }

    static string CardRank(string card)
    {
        return string.Concat(card
            .Where(character => char.IsNumber(character) || char.IsUpper(character)));
    }

    static string CardSuit(string card)
    {
        return string.Concat(card.Where(character => char.IsLower(character)));
    }
}
```
### Test
```cs
using NUnit.Framework;
using System;

[TestFixture]
public class TestPokerHandRankingShould
        {
            /*
                 * recibir array de string de 5 elementos, donde cada elemento es una carta
                 * separar cada carta por valor(letras may o numeros) y palo(letra min)
                 * retorna un string en base a la condicion de mayor valor que cumpla
                 *funciones a realizar para cumplir con las condiciones:   
                    * contar cantidad de cartas iguales 
                    * determinar si los valores de las cartas estan en secuencia
                    * determinar si todas las cartas son del mismo palo
                    * Royal Flush, la mano debe contener A 
             */
            [Test]
            public void ReturnNullException()
            {
                string[] handNull = null;

                var exception = Assert.Throws<InvalidDataException>(() => Program.PokerHandRanking(handNull));

                Assert.AreEqual("Hand Parameter is null", exception.Message);
            }

            [Test]
            public void ReturnInvalidsCardsException()
            {
                string[] hand = { "3h", "5h", "Qs", "13h", "10h" };

                var exception = Assert.Throws<InvalidDataException>(() => Program.PokerHandRanking(hand));

                Assert.AreEqual("There are invalid cards", exception.Message);
            }
            [Test]
            public void ReturnInvalidsCardsExceptionWithNullValue()
            {
                string[] hand = { "3h", "5h", "Qs", "9y", null };

                var exception = Assert.Throws<InvalidDataException>(() => Program.PokerHandRanking(hand));

                Assert.AreEqual("There are cards with null value", exception.Message);
            }

            [Test]
            public void ReturnRepeatedCardsException()
            {
                string[] hand = { "3h", "5h", "Qs", "9h", "9h" };

                var exception = Assert.Throws<InvalidDataException>(() => Program.PokerHandRanking(hand));

                Assert.AreEqual("There are repeated cards", exception.Message);
            }


            [Test]
            public void ReturnInvalidNumberOfCardsException()
            {
                string[] hand1 = new string[] { "3h", "5h", "Qs", "9h"};
                string[] hand2 = new string[] { "3h", "5h", "Qs", "9h", "Ad","2s" };
                

                var exception1 = Assert.Throws <InvalidDataException>(()=> Program.PokerHandRanking(hand1));
                var exception2 = Assert.Throws<InvalidDataException>(() => Program.PokerHandRanking(hand2));
                

                Assert.AreEqual("Hand has not five Cards", exception1.Message);
                Assert.AreEqual("Hand has not five Cards", exception2.Message);
               

            }

            [Test]
            public void ReturnHighCard()
            {
                string[] cards = new string[] { "3h", "5h", "Qs", "9h", "Ad" };

                string result = Program.PokerHandRanking(cards);

                Assert.AreEqual("High Card", result);
            }
            [Test]
            public void ReturnSameRanksCollections()
            {
                string[] cardsRanks_4 = new string[] { "10s", "10c", "8d", "10d", "10h" };
                string[] cardsRanks_3_2 = new string[] { "10c", "9c", "9s", "10s", "9h" };
                string[] cardsRanks_3 = new string[] { "10c", "9c", "9s", "3s", "9h" };
                string[] cards_2_2 = new string[] { "3h", "8h", "2s", "3s", "2d" };
                string[] cards_2 = new string[] { "8h", "8s", "As", "Qh", "Kh" };

                string result_4 = Program.PokerHandRanking(cardsRanks_4);
                string result_3_2 = Program.PokerHandRanking(cardsRanks_3_2);
                string result_3 = Program.PokerHandRanking(cardsRanks_3);
                string result_2_2 = Program.PokerHandRanking(cards_2_2);
                string result_2 = Program.PokerHandRanking(cards_2);

                Assert.AreEqual("Four of a Kind", result_4);
                Assert.AreEqual("Full House", result_3_2);
                Assert.AreEqual("Three of a Kind", result_3);
                Assert.AreEqual("Two Pair", result_2_2);
                Assert.AreEqual("Pair", result_2);
            }

            [Test]
            public void ReturnFlush()
            {
                string[] cards = new string[] { "Ad", "Kd", "Qd", "Jd", "9d" };

                string result = Program.PokerHandRanking(cards);

                Assert.AreEqual("Flush", result);
            }
            [Test]
            public void ReturnStraight()
            {
                string[] cards = new string[] { "10h", "Jh", "Qs" ,"Ks", "Ac" };

                string result = Program.PokerHandRanking(cards);

                Assert.AreEqual("Straight", result);
            }
            [Test]
            public void ReturnStraightFlush()
            {
                string[] cards = new string[] { "10h", "Jh", "Qh" ,"Kh", "9h" };

                string result = Program.PokerHandRanking(cards);

                Assert.AreEqual("Straight Flush", result);
            }
            [Test]
            public void ReturnRoyalFlush()
            {
                string[] cards = new string[] { "10h", "Jh", "Qh", "Ah", "Kh" };

                string result = Program.PokerHandRanking(cards);

                Assert.AreEqual("Royal Flush", result);
            }


            
    }
```
Estimation: 2h
<br> Real time: 1h 30m

---------------------------------------

