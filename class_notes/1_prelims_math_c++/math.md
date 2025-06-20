# Chapter 1. Mathematical Preliminaries

This is the math that you are required to know for the remainder of the course. It is extremely important that you commit these formulae to memory and know how to apply them in practice, because they do arise often in the study of algorithmic analysis, and in computer science in general.

## Series Summations

**Arithmetic Series**  
The formula for an arithmetic series is

$$
\sum_{k=0}^{n} k = \frac{n(n+1)}{2}
$$

From this formula, you can solve the more general arithmetic series sum of the form

$$
\sum_{k=0}^{n} (ak + b)
$$

by writing it out directly and redistributing:

$$
\sum_{k=0}^{n} (ak + b) = a\sum_{k=0}^{n} k + \sum_{k=0}^{n} b = a\frac{n(n+1)}{2} + (n+1)b
$$

If the series starts at some value ( c ) instead of 0:

$$
\sum_{k=c}^{n} (ak + b) = \sum_{k=0}^{n-c} (a(c + k) + b) = \sum_{k=0}^{m} (ak + d)
$$

where ( m = n - c ) and ( d = ac + b ).

Example: For the series 9, 13, 17, ..., 257 with ( a = 4 ), ( b = 9 ), solve ( 4n + 9 = 257 $\Rightarrow$ n = 62 ). Then,

$$
4 \cdot \frac{62 \cdot 63}{2} + 63 \cdot 9 = 8379
$$

**Quadratic Series**  
The sum of the sequence of squares:

$$
\sum_{k=1}^{n} k^2 = \frac{n(n+1)(2n+1)}{6}
$$

**Higher Order Series**  
For integer ( m $\neq$ -1 ):

$$
\sum_{k=1}^{n} k^m \approx \frac{n^{m+1}}{m+1}
$$

From calculus:

$$
\int_0^n x^m dx = \frac{n^{m+1}}{m+1}
$$

For ( m = -1 ):

$$
H_n = \sum_{k=1}^{n} \frac{1}{k} \approx \int_1^n \frac{1}{x} dx = \ln n
$$

**Geometric Series**  
For ( x $\neq$ 1 ):

$$
\sum_{k=0}^{n} x^k = \frac{x^{n+1} - 1}{x - 1}
$$

As ( $n \to \infty$ ), if ( 0 < x < 1 ), then:

$$
\sum_{k=0}^{\infty} x^k = \frac{1}{1 - x}
$$

Another common series:

$$
\sum_{k=0}^{n} k a^k
$$

Let’s derive the formula.

Multiply by ( a ):

$$
a \sum_{k=0}^{n} k a^k = \sum_{k=0}^{n} k a^{k+1} = a^2 + 2a^3 + ... + n a^{n+1}
$$

Original:

$$
\sum_{k=0}^{n} k a^k = a + 2a^2 + 3a^3 + ... + n a^n
$$

Subtracting:

$$
(1 - a) \sum_{k=0}^{n} k a^k = \sum_{k=0}^{n} a^k - n a^{n+1} - 1 = \frac{a^{n+1} - 1}{a - 1} - (1 + n a^{n+1})
$$

Thus:

$$
\sum_{k=0}^{n} k a^k = \frac{(1 - a^{n+1})}{(a - 1)^2} + \frac{1 + n a^{n+1}}{a - 1}
$$

Substituting ( $a = \frac{1}{2}$ ):

$$
\sum_{k=0}^{n} \frac{k}{2^k} = 2 - \frac{1}{2^{n-1}} - \frac{n}{2^n}
$$

As ( $n \to \infty$ ):

$$
\sum_{k=0}^{\infty} \frac{k}{2^k} = 2
$$

When ( a = 2 ):

$$
\sum_{k=0}^{n} k \cdot 2^k = 2 + (n - 1) 2^{n+1}
$$

## Modular Arithmetic (Congruences)

In mathematics, ( $a \equiv b \mod N$ ) means ( a - b ) is divisible by ( N ). This is equivalent to saying that ( a \% N = b \% N ).

Examples:

- ( $53 \equiv 29 \equiv 13 \mod 8$ )
- If ( $a \equiv b \mod N$ ), then:
  - ( $a + c \equiv b + c \mod N$ )
  - ( $ad \equiv bd \mod N$ )

But note: ( $ab \equiv 0 \mod N$ ) does not imply ( a = 0 ) or ( b = 0 ). For instance, ( $3 \cdot 4 \equiv 0 \mod 12$ ).

Only when ( N ) is a prime number ( p ), does the set ( \{0, 1, ..., p - 1\} ) form a field:

- If ( $ab \equiv 0 \mod p$ ), then ( a ) or ( b ) is divisible by ( p )
- If ( $ax \equiv 1 \mod p$ ), then ( x ) is the unique inverse of ( $a \mod p$ )
- The equation ( $x^2 \equiv a \mod p$ ) has 0 or 2 solutions for ( 0 < a < p )


### Modular Arithmetic as Partitioning the Integers

### Core Idea

Modulo m partitions the integers ℤ into m equivalence classes, where each class contains all numbers that leave the same remainder when divided by m.

This is the set ℤ/mℤ (integers modulo m).

### What is a Partition?

A partition of a set divides it into non-overlapping subsets (called equivalence classes) such that:
- Every element belongs to exactly one class.
- No elements are left out.

In modular arithmetic:
> Two integers a and b belong to the same class if a ≡ b (mod m)

This is an equivalence relation (reflexive, symmetric, transitive).

### Example: Modulo 4

Let’s look at ℤ mod 4. The set ℤ is partitioned into 4 classes:

[0] = {..., -8, -4, 0, 4, 8, ...}  
[1] = {..., -7, -3, 1, 5, 9, ...}  
[2] = {..., -6, -2, 2, 6, 10, ...}  
[3] = {..., -5, -1, 3, 7, 11, ...}  

Each class contains all integers that give the same remainder when divided by 4.

### These Are the Equivalence Classes

We write:

ℤ/4ℤ = { [0], [1], [2], [3] }

Where:

- [a] is the equivalence class of all integers congruent to a mod 4
- So [5] = [1] because 5 ≡ 1 mod 4

### Why It Matters

- This structure is used in modular rings in abstract algebra.
- Helps define arithmetic operations on equivalence classes (not just numbers).
- You can think of [a] + [b] = [a + b], etc.


### Multiplicative Inverse Modulo m

The multiplicative inverse of a number `a` modulo `m` is a number `x` such that:

a × x ≡ 1 (mod m)

We write this as:

x ≡ a⁻¹ (mod m)

### Condition for Existence

`a` has a multiplicative inverse modulo `m` **if and only if**:

gcd(a, m) = 1

That is, `a` and `m` must be coprime.

### Example

Find the inverse of 3 modulo 7:

Try values of x:
- 3 × 1 = 3 mod 7 → 3
- 3 × 2 = 6 mod 7 → 6
- 3 × 3 = 9 mod 7 → 2
- 3 × 4 = 12 mod 7 → 5
- 3 × 5 = 15 mod 7 → 1 ✅

So:

3⁻¹ ≡ 5 (mod 7)

### Non-Zero Products Being Congruent to Zero (Zero Divisors)

In modular arithmetic, it’s possible for:

a $\neq$ 0,  b $\neq$ 0, but a × b ≡ 0 (mod m)

This can happen **if m is not a prime number**. These numbers are called **zero divisors modulo m**.

### Why?

If `m` is composite, then it has nontrivial divisors. So two non-zero elements could multiply to a multiple of `m`.

### Example (mod 8):

a = 2, b = 4  
2 × 4 = 8 ≡ 0 mod 8

But:
- 2 $\neq$ 0 mod 8
- 4 $\neq$ 0 mod 8

So:

2 × 4 ≡ 0 mod 8

2 and 4 are zero divisors mod 8.

### Prime Modulus Prevents Zero Divisors

If `m` is prime, then there are no zero divisors modulo `m`.

In ℤ/pℤ (integers mod p), if:

a × b ≡ 0 mod p

Then either:

a ≡ 0 mod p OR b ≡ 0 mod p

This property makes fields: structures where every non-zero element has a multiplicative inverse and no zero divisors exist.


### What is GCD?

The GCD of two integers a and b is the largest positive integer that divides both a and b without leaving a remainder.

We write it as:

gcd(a, b)

### Example

Find gcd(18, 24):

- Factors of 18: 1, 2, 3, 6, 9, 18  
- Factors of 24: 1, 2, 3, 4, 6, 8, 12, 24  
- Common factors: 1, 2, 3, 6  
- Greatest common divisor: 6

So:

gcd(18, 24) = 6

### Euclidean Algorithm (Fast Method)

Instead of listing factors, use:

gcd(a, b) = gcd(b, a mod b)

Repeat until b = 0

### Example: gcd(48, 18)

1. 48 mod 18 = 12 ⇒ gcd(48, 18) = gcd(18, 12)  
2. 18 mod 12 = 6  ⇒ gcd(18, 12) = gcd(12, 6)  
3. 12 mod 6 = 0   ⇒ gcd(12, 6) = 6

Answer: gcd(48, 18) = 6

### Why GCD Matters

- Simplifies fractions (reduce a/b using gcd)
- Needed for modular inverse: a⁻¹ mod m exists iff gcd(a, m) = 1
- Used to check if two numbers are coprime (gcd = 1)
- Core in number theory and cryptography (e.g., RSA)

### Properties of GCD

- gcd(a, 0) = |a|
- gcd(0, 0) is undefined
- gcd(a, b) = gcd(b, a) (commutative)
- gcd(a, b) = gcd(b, a mod b)
- If gcd(a, b) = 1, then a and b are coprime


### Brute Force Method
1. Start from min(a, b)
2. Check each integer downward to see if it divides both a and b
3. First match is the GCD

### Steps Required (Worst Case)

- In the worst case, we start from min(a, b) and count down to 1
- So the number of steps is up to:

O(min(a, b))

### Example

Find gcd(1000000, 3):

- Brute-force would check:
  - Is 3 a divisor of 1000000? No  
  - 2? No  
  - 1? Yes  
- Took 3 steps here, but could take up to 999,999 steps in general

### Euclidean Algorithm

Repeatedly apply:

gcd(a, b) = gcd(b, a mod b)

until remainder = 0

### Steps Required (Worst Case)

- Each step reduces the size of the smaller number
- Worst-case number of steps is:

O(log min(a, b))

### Example

Find gcd(1000000, 3):

1. 1000000 mod 3 = 1 → gcd(3, 1)
2. 3 mod 1 = 0 → done

Only 2 steps

### Summary Table

| Method          | Worst-Case Steps            | Efficiency       |
|-----------------|-----------------------------|------------------|
| Brute Force     | O(min(a, b))                | Slow (linear)    |
| Euclidean Algo  | O(log min(a, b))            | Fast (logarithmic) |


### Why the Euclidean Algorithm Is Logarithmic (O(log n))

Show that the number of steps in the Euclidean algorithm for gcd(a, b) is at most:

O(log min(a, b))

### Key Idea: Fast Decrease in Remainders

Each step of the Euclidean algorithm does:

gcd(a, b) → gcd(b, a mod b)

This means you're replacing (a, b) with (b, a mod b) where:

a mod b < b

So the second number strictly decreases, and fairly quickly.

### Real-World Intuition

- Suppose b is a number with d digits.
- Then Euclidean algorithm will take at most about 2d steps — i.e., grows with the number of digits, not the number itself.

That’s what we mean when we say:

Time complexity = O(log b)


## Selection Sort Analysis using Arithmetic Series
```c
void selection_sort(int* arr, int size)
{
  for(int i=size-1;i>0;i++)
  {
    int max_index=0;
    for(intj=1;j<=i;j++)
      if(arr[j]>arr[max_index]) max_index=j;
    std::swap(arr[i],arr[max_index]);
  }
}
```
#### Breakdown
* The coefficient for j is the number of steps it takes the inner for loop to run. The for loop on its own has a cost of 2 steps for each iteration(update j, check condition). The check to find the max in each iteration ```if(arr[j]>arr[max_index]) max_index=j;``` which is 1 step for the check and 1 step for the assignment. In total we get a coefficient of 4. 
* Now we must compute the cost for each iteration of the outer for loop(variable i). Here we get 2 steps for each iteration of the outer for loop and 1 step for ```int max_index=0``` and 1 step for ```std::swap(arr[i],arr[max_index]);```. SInce the inner for loop runs inside the outer for loop we must add 4j. So, for each iteration of the outer for loop it will cost us $4j+4$
* Lastly, we just need to sum up the number of steps each iteration of the outer for loop cost. Note that j runs from 1 to i on the first iteration, 1 to i-1 on the second, and so on until i is equal to 1 and j is equal to 1. Thus, we can use a summation to compute the steps as shown below.


$$
\sum_{j=1}^{i} (4j + 4) = \sum_{j=0}^{i-1} (4(j+1) + 4)=\sum_{j=0}^{i-1} (4j + 8)= 4\frac{i-1(i)}{2} + 8i
$$
The analysis above counts the number of steps it takes in the worst case to run the selection sort algorithm. It is assumed that ```std::swap()``` has a cost of 1 step.

It is good practice to write our formula in terms of the input size n, instead of i. In the case for the seelction sort the input size will be the size of the array. According to our outer for loop in the code, you can observe that i=n-1. So we can just replace i with n-1 in the formula above to get:
$$
4\frac{i-1(i)}{2} + 8i=4\frac{n-2(n-1)}{2} + 8(n-1)
$$

Let c(n) be the number of steps it takes for the algorithm selection sort to complete in the worst case for an array of size n.
$$
c(n)=4\frac{n-2(n-1)}{2} + 8(n-1)
$$

* n=1, c(n)=0
* n=2, c(n)=8
* n=3, c(n)=20
* n=4, c(n)=36
* and so on


We will cover this in further detail later, but we can describe c(n) in terms of big notation:
$$
c(n)=4\frac{n-2(n-1)}{2} + 8(n-1) \in O(n^2)
$$


## Proofs
Proofs are important. When we make a claim that something is true, we have to prove that it is true. Although there are philosophical arguments about what constitutes a proof, we will restrict this discussion to methods of proof that no one disputes are valid. Three such methods of proof can be used to solve most problems:

1. direct proof, 
2. proof by mathematical induction,  
3. proof by contradiction, and  
4. proof by counterexample.

We describe and give examples of each. 
### Proof that gcd(a, b) = gcd(b, a mod b) (direct)

#### Let a and b be integers with b $\neq$ 0

We want to prove:

gcd(a, b) = gcd(b, a mod b)

Let r = a mod b

By the Division Algorithm, there exist integers q and r such that:

a = bq + r   with  0 ≤ r < |b|

Therefore:

r = a - bq

### Step 1: Show that any common divisor of a and b is also a divisor of b and r

Suppose d divides both a and b:
- d | a
- d | b

Then:

d | (a - bq) ⇒ d | r

So d divides both b and r

Therefore:

Every common divisor of a and b is a common divisor of b and r

### Step 2: Show that any common divisor of b and r is also a divisor of a and b

Suppose d divides both b and r:
- d | b
- d | r

Recall:

a = bq + r

Then:

d | (bq + r) ⇒ d | a

So d divides both a and b

Therefore:

Every common divisor of b and r is a common divisor of a and b

### Step 3: Conclusion

The set of common divisors of (a, b) is the same as the set of common divisors of (b, r)

Hence, the greatest common divisor is the same:

gcd(a, b) = gcd(b, a mod b)


### Why Repeatedly Applying gcd(a, b) = gcd(b, a mod b) Yields the GREATEST Common Divisor

Each step:

gcd(a, b) = gcd(b, a mod b)

**preserves the set of common divisors**.  
So you’re not losing or gaining any divisors — just rewriting the problem with **smaller numbers**.

### What the algorithm does

You apply:

gcd(a₀, b₀) = gcd(b₀, r₁)
            = gcd(r₁, r₂)
            = ...
            = gcd(rₙ₋₁, rₙ)

until eventually:

rₙ = 0

At that point:

gcd(rₙ₋₁, 0) = rₙ₋₁

That last nonzero number is your answer.

### Why is the last nonzero remainder the GREATEST common divisor?

Let’s say the steps ended with:

gcd(a, b) = gcd(b, r) = ... = gcd(d, 0)

Then:

- d | 0 (by definition)
- We already know (by previous steps) that d divides all earlier remainders
- And we know from the identity that the set of common divisors hasn't changed at each step

So:
- d divides both a and b
- And no number larger than d can divide both a and b, because d is the **last nonzero remainder**, and all previous remainders were reduced versions of the same GCD

Hence:
d = GREATEST common divisor of a and b

### Quick Example

Let’s find gcd(30, 12):

30 mod 12 = 6 → gcd(30, 12) = gcd(12, 6)  
12 mod 6 = 0 → gcd(12, 6) = gcd(6, 0)

So:
gcd(30, 12) = 6

And 6 is:
- The largest number that divides both 30 and 12
- The last nonzero remainder

#### Summary

- The identity gcd(a, b) = gcd(b, a mod b) keeps the set of common divisors unchanged
- Each step makes the numbers smaller
- When one becomes 0, the other is the greatest common divisor — because it still divides both, and no larger number could


---

### Induction

Suppose a statement S can be formulated as depending on a single non-negative integer n. A proof of S by mathematical induction has two parts: a base case that establishes that S(n) is true for a finite number of values of n, typically that it is true for $n = 0$, and an inductive argument that shows that if S is true for arbitrary $k$, then it is also true for $k + 1$. I.e., $S(k) \Rightarrow S(k + 1)$.

We demonstrate this method by proving the equation:

$$\sum_{k=1}^{n} k^2 = \frac{n(n + 1)(2n + 1)}{6}$$

**Base Case:** $n = 0$  
LHS: 0  
RHS: 0  
So, base case is true.

**Inductive Hypothesis:** Assume the formula holds for $n = N$:  
$$\sum_{k=0}^{N} k^2 = \frac{N(N + 1)(2N + 1)}{6}$$

**Inductive Step:** Prove for $n = N + 1$:  
$$\sum_{k=0}^{N+1} k^2 = \sum_{k=0}^{N} k^2 + (N + 1)^2$$  
$$= \frac{N(N + 1)(2N + 1)}{6} + (N + 1)^2$$  
$$= (N + 1)\left[\frac{N(2N + 1)}{6} + (N + 1)\right]$$  
$$= (N + 1)\left(\frac{2N^2 + 7N + 6}{6}\right)$$  
$$= \frac{(N + 1)(N + 2)(2N + 3)}{6}$$  
$$= \frac{(N + 1)((N + 1) + 1)(2(N + 1) + 1)}{6}$$

Which matches the original formula with $n = N + 1$. Therefore, by induction, the formula holds for all non-negative integers $n$.

---

### Contradiction

In a proof by contradiction, we assume the statement to be proved true is false, then show this assumption leads to a contradiction.

Let S be the statement. Assume $\neg S$ is true.  
If $\neg S$ leads to a contradiction (like $R \land \neg R$), then $\neg S$ is false, so S must be true.

**Example:** Prove $\sqrt{2}$ is irrational.

Assume $\sqrt{2}$ is rational.  
Then there exist integers p and q (gcd(p, q) = 1), such that $(p/q)^2 = 2$ <br>
$\Rightarrow p^2 = 2q^2 \Rightarrow p^2$ is even <br>
$\Rightarrow p$ is even $\Rightarrow p = 2m$ <br>
$\Rightarrow p^2 = 4m^2$ <br>
Then $4m^2 = 2q^2 \Rightarrow q^2 = 2m^2 \Rightarrow q$ is even <br> 
So both p and q are even $\Rightarrow$ contradiction with $\gcd(p, q) = 1$ <br>
Thus, $\sqrt{2}$ is irrational.

---

### Counterexample

Universal statements are of the form: "For every $x$, $P(x)$ is true."  
To disprove such a statement, find a single counterexample.

**Example:** "Every month has 31 days"  
Counterexample: April has only 30 days

**Another example:**  
Fibonacci sequence:  
$F_0 = 1, F_1 = 1, F_{n+2} = F_{n+1} + F_n$ <br>
Claim: $\forall k, F_k \leq k^2$  
Disproof: <br> 
$F_{11} = 144, 11^2 = 121$ <br>  
$144 > 121 \Rightarrow$ counterexample

Therefore, the statement is false.


## Attribution
This repository contains derivative work based on course materials by Professor Stewart Weiss for CSCI 335 at Hunter College, CUNY, Spring 2019.

Original materials are available at: [https://www.cs.hunter.cuny.edu/~sweiss/course_materials/csci335/csci335_s19.php](https://www.cs.hunter.cuny.edu/~sweiss/course_materials/csci335/csci335_s19.php)

The original work is licensed under the [Creative Commons Attribution-ShareAlike 4.0 International License (CC BY-SA 4.0)](https://creativecommons.org/licenses/by-sa/4.0/).  
This repository is licensed under the same license. Changes include summarization, reorganization, and additional commentary.
