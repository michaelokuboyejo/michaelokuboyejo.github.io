---
layout: post
title: Mathematics for Coders
---

While preparing for [IEEE Xtreme 9.0](http://ieee.org/xtreme) i listed some [topics](http://docs.google.com/) i knew every programming competition would contain. One of them is **Arithmetic**. Many programmers complain that coding test platforms like Codility, Hackerrank could be too academic. Challenges on Topcoder could seem too mathematical. I personally like Math but many developers do not have a Math background. So here is a list of  math one could encounter in a programming test.

### Fibonacci Numbers
Fibonacci Numbers form a sequence of integers defined recursively in the following way. The first two numbers in the Fibonacci sequence are 0 and 1, and each subsequent number is the sum of the previous two.
 The traditional method of generating 
 
 ```
 def fibonacci(n):
 	if ( n <= 1 ):
 		return n
 	return fibonacci(n - 1) + fibonacci(n-2)
 
 ```
 
 The above algorithm works but as the sequence grows exponentially we get an inefficient solution. A faster algorithm based on the formula: 
 
 ```
  #Fibonacci formula that returns immediately
 def fibonacci(n):
    fterm = (((1 + sqrt(5))/2)**n)/sqrt(5)
    sterm = (((1 - sqrt(5))/2)**n)/sqrt(5)
    return fterm - sterm
    
 ```
 
 This Algorithm delivers in O(logN) time :-) 
 
 
###Primality Testing
 
 A number is prime if it is only divisible by 1 and itself. So for example 2, 3, 5, 79, 311 and 1931 are all prime, while 21 is not prime because it is divisible by 3 and 7. To find if a number n is prime we could simply check if it divides any numbers below it. We can use the modulus (%) operator to check for divisibility:
 
 ```
 ￼def isPrime(n):
 	for i in range(2,n):
 		if n % i == 0:
 			return False
 		
```
Now suppose we wanted to find all the primes from 1 to 100000, then we would have to call the above method 100000 times. Here's something faster:
```
def isPrime(n):
    from math import sqrt
    if n <= 1:
         return False
    if n==2:
        return True
    if n%2==0:
        return False
    m= sqrt(n);

    for i in range(3,m , 2):
        if n % i == 0:
            return False
    return True```
So, there's an algorithm you can use too- Miller Rabin's Test. It's  part of the standard library (java.math.BigInteger):

```
import java.math.BigInteger;
 
public class MillerRabinPrimalityTest {
  public static void main(String[] args) {
    BigInteger n = new BigInteger(args[0]);
    int certainty = Integer.parseInt(args[1]);
    System.out.println(n.toString() + " is " + (n.isProbablePrime(certainty) ? "probably prime" : "composite"));
  }
}

```###GCD
The greatest common divisor (GCD) of two numbers a and b is the greatest number that divides evenly into both a and b. We could ( naively ) start from the smallest of the two numbers and work our way downwards until we find a number that divides into both of them: 

```
def gcd(a, b):
    i = min(a, b)
    while i >= 1:
        if a%i == 0 and b%i == 0:
            return i
        i -= 1

```
there is a faster method called Euclid’s algorithm. Euclid’s algorithm iterates over the two numbers until a remainder of 0 is found.

```
def euclidean(a, b):
    if b == 0:
        return a
    return euclidean(b, a % b)
	
```
The cool stuff is you can use this algorithm to compute the Lowest Common Multiple (L.C.M.) of two numbers.

```
def lcm(a, b):
    return b * a // gcd(a, b)
```

##Bases

A very common problem faced during contests involve conversion to and from a base.

```
public int toDecimal(int n, int b) {	int result=0; int multiplier=1;	while(n>0) {		result+=n%10*multiplier; multiplier*=b;		n/=10;	}
	return result;
}
```
##Combinatorics
##Fraction
##Coordinate geometry
--
Tests:--


```
1. Given two lines on a Cartesian plane, determine whether the two lines would inter- sect.
2. Write a method that revereses a number i.e. Takes a number 1234 and returns 4321
3. 
```###References
[1]: http://facebook.comGood luck :-)