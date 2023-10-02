---
title: "Introduction to Number Theory"
author:
- Killian O'Brien
- 6G6Z0024 Applied Cryptography
date: Lecture Week 01 -- Mon 02 October 2023
transition: fade
theme: killian
width: 1920
height: 1080
margin: 0.07
center: false
revealjs-url: ../reveal.js
title-slide-attributes:
    data-background-color: rgb(0,47,108)	
    data-background-image: logowhite.png
    data-background-size: 18%
    data-background-repeat: no-repeat
    data-background-position: 95% 5%	
---

## Introduction to the unit

* <img src="./images/mee.jpg" alt="Smiley face" style="padding:3px;float:right;width:150px;"> My name is Dr Killian O'Brien
* Contacts: [k.m.obrien@mmu.ac.uk](mailto:k.m.obrien@mmu.ac.uk), [Teams chat](https://teams.microsoft.com/l/chat/0/0?users=k.m.obrien@mmu.ac.uk){target="_blank"}, Office JDE 114a (first floor of John Dalton East, Chester St end)

* 6G6Z0024 Applied Cryptography (15 credits)

* Timetable

* Let's look at the [Moodle](https://moodle.mmu.ac.uk/course/view.php?id=172138){target="_blank"} page for the unit.

## Introduction to Number Theory

We deal with the positive and negative *counting* numbers, more properly named the *integers*, and denoted by the symbol $\mathbb{Z}$, (coming from the German *Zahl*, for number)

* $\mathbb{Z} = \{ \dots, -3, -2, -1, 0, 1, 2, 3, \dots \}$
* $\mathbb{Z}$ is an *infinite* set.

* $\mathbb{Z}$ obviously carries the operations of addition, $+$, and multiplication, $\cdot$, that you've known from primary school.

Modern cryptography relies heavily on techniques and facts from *number theory*, which is the mathematical study of the integers and their properties under $+$ and $\cdot$. 

## Topics we need to know

* The **divisibility relation** on $\mathbb{Z}$.
* **Greatest Common Divisors** (gcd) and the **Euclidean Algorithm**.
* The **congruence relation** and **modular arithmetic**.
* **Prime** numbers and 
	- The **Fundamental Theorem of Arithmetic** and **prime factorizations**
	- **Fermat's Little Theorem**
	- **Euler's totient** function
	- **Euler's theorem**
	- **Primality** testing, the **Miller-Rabin** test
* **The Chinese Remainder Theorem**
* **Discrete logarithms**

All these covered in <a href="https://mmu.on.worldcat.org/oclc/1064983791" target="_blank">Stallings, Chapter 2: Introduction to Number Theory</a>.

## The divisibility relation

* Recall, a *relation* in computer science / mathematics is a formula $A(x_1, \dots , x_n)$, so that when values are supplied for the variables $x_1, \dots , x_n$, results in a *statement* $A(x_1, \dots , x_n)$, i.e. something which is true or false.

* For a pair of integers $a,b$, with $b \neq 0$, we say $b$ *divides* $a$, and write $b|a$ if there exists an integer $c$ such that 
$$a = b \cdot c,$$
and if no such integer $c$ exists then we say $b$ does *not divide* $a$, and can write $b \centernot | a$.

* So $b | a$ is a binary relation on $a,b$, i.e. a statement that is true or false, depending on the values of $a,b$.

* If $b|a$ then we say $b$ is a *factor* or *divisor* of $a$. 

Examples

* $3|15$, $5|15$, $1|15$, $15|15$.
* $3 \centernot | 10$, $17 \centernot | 20$.

## Properties of divisibility

The divisibility relation enjoys the following properties, which can all be demonstrated (and proved) using its definition and basic properties of the integers.

* If $a|1$ then $a=\pm 1$, i.e. $a=-1$ or $a=+1$.
* If $a|b$ and $b|a$ then $a = \pm b$.
* For all non-zero integers $b$, we have $b|0$, i.e. *everything divides 0*.
* If $a|b$ and $b|c$ then $a|c$, i.e. the divisibility relation is *transitive*, it travels through intermediaries. 
* If $x|y$ and $x|z$ then for all pairs of integer coefficients $\alpha, \beta$, we have 
$$ x | (\alpha \cdot y + \beta \cdot z),$$
i.e. $x$ divides all *linear combinations* of $y$ and $z$.

To familiarise yourself with these, work through some examples of the transitivity of divisibility and the divisibility of linear combinations. 

## The integer division algorithm

Do you remember this kind of thing from primary school?

* $20$ divided by $3$, goes in $6$ times, with remainder $2$.
* $20 = 6 \cdot 3 + 2$

The *integer division algorithm* is simply a formalization of this. It is:

* Given any postitive integer $n$ and any non-negative integer $a$, we can divide $a$ by $n$ to get an integer quotient $q$ and remainder $r$ that satisfy

* $a = qn + r$, \quad and $0 \leq r \lt n$, and $q = \left \lfloor a/n \right \rfloor$
* $\left \lfloor x \right \rfloor$ is defined as the largest integer less than $x$, the so-called <em>floor</em> function.

## Greatest Common Divisors (gcd)

We write $\gcd(a,b)$ for the <em>greatest common divisor of $a$ and $b$</em>. So $\gcd$ is defined by 

* $\gcd(a,b) = d$, where $d$ is the alrgest integer that divides both $a$ and $b$.
* For neatness, we also define $\gcd(0,0) = 0$.

For example

* $\gcd(60,24) = 12$, $\gcd(100,75) = 25$, $\gcd(15,32) = 1$. 
* Note that, by its definition, $\gcd$ will always be non-negative, i.e. $\gcd(-60,24) = 12$. 

For small arguments $a,b$, we can calculate $\gcd(a,b)$ <em>in our heads</em>, so to speak.

* $\gcd(25,3) = ?,$ $\gcd(99, 27) = ?, \dots$.
* But what about $\gcd(12349878973245, 324765)$?

## The Euclidean Algorithm

In fact there is a classic algorithm that can quickly determine $\gcd$, and establishes the following, non-obvious fact,

* $\gcd(a,b)$ is the smallest postitive integer $d$ that can be written in the form 

$$ d = x \cdot a + y \cdot b,$$

for integer coefficients $x,y$.

The Euclidean algortihm was known to ancient mathematicians and has severl important uses and generalisations in mathematics and cryptography.


## The Euclidean Algorithm

A detailed treatment is given in Stallings. The algorithm depends on the following property of $\gcd$. 

* If $a = qn + r$ then $\gcd(a,n) = \gcd(n,r)$.

This is true because 

* if $d$ is a common divisor of $a$ and $n$, then since $r = a - qn$, i.e. $r$ is a linear combination of $a$ and $n$, then $d$ divides $r$ also. And so $d$ is a common divisor of $n$ and $r$. 

* Similarly we can show that if $e$ is a common divisor of $n$ and $r$, then $e$ divides $a$ also. And so $e$ will be a common divisor of $a$ and $n$.

* So the pairs $(a,n)$ and $(n,r)$ have the exact same set of common divisors.

* Therefore,
$$\gcd(a,n) = \gcd(n,r).$$

## The Euclidean Algorithm

The algorithm works by repeatedly applying the property from the last slide, to a sequence of integer divisions, until the $\gcd$ is clear. Best seen with a worked example

* What is $\gcd(710,310)$?
* $710 = 2 \cdot 310 + 90$ so $\gcd(710,310) = \gcd(310,90)$,
* $310 = 3 \cdot 90 + 40$ so $\gcd(310,90) = \gcd(90,40)$,
* $90 = 2 \cdot 40 + 10$ so $\gcd(90,40) = \gcd(40,10)$,
* $40 = 4 \cdot 10 + 0$ so $\gcd(40,10) = \gcd(10,0)=10$.

Note that 

* The algorithm will terminate, since the remainders are a strictly decreasing sequence of non-negative integers.
* By definition of divisibility, $\gcd(x,0) = x$, for all integers $x$. 
* The $\gcd$ equations associated to the integer divisions all link together.
* So we can conclude that 
$$\gcd(710,310) = 10.$$

See Stallings for the full detail, a flowchart specification of the algorithm, and more examples.

## The mod operator and the congruence relation

For an integer $a$ and a positive integer $n$ we say that <em>$a$ modulo $n$</em> is the remainder $r$ in the integer division of $a$ by $n$. 

* $a = qn + r$, \quad $0 \leq r \lt n$
* We write $(a \mod n) = r$.
* $n$ is called the <em>modulus</em> in this expression.

For example

* $(11 \mod 7) = 4$ and $(-11 \mod 4) = 1$.

There is an associated binary relation here. We say that two integers $a$ and $b$ are <em>congruent modulo $n$</em>, written as 

$$ a \equiv b \pmod{n},$$

if 

* $(a \mod n) = (b \mod n)$
* That is, if $a$ and $b$ <em>leave the same remainder</em>, after division by $n$. 

## The mod operator and the congruence relation

Examples

* $23 \equiv 8 \pmod{5}$
* $-11 \equiv 5 \pmod{8}$
* $81 \equiv 0 \pmod{27}$

The congruence relation has the following properties

* $a \equiv b \pmod{n}$ if and only if $n | (a-b)$
* $a \equiv a \pmod{n}$, $\quad$ called <em>reflexivity</em>
* $a \equiv b \pmod{n}$ implies that $b \equiv a \pmod{n}$, $\quad$ called <em>symmetry</em>
* If $a \equiv b \pmod{n}$ and $b \equiv c \pmod{n}$, then $a \equiv c \pmod{n}$, $\quad$ called <em>transitivity</em>
* These last three properties mean congruence modulo $n$ is an <em>equivalence relation</em> on $\mathbb{Z}$. 

## Modular arithmetic

* The mod operator $(a \mod n)$ maps all integers $a$ into the set
$$\mathbb{Z}_n = \left \{ 0, 1, 2, 3, \dots , n-1 \right \}.$$
* This is the set of <em>residues</em>, or <em>remainders</em>, modulo $n$.
* The familiar operations of $+$ and $\cdot$ on $\mathbb{Z}$ extend to $\mathbb{Z}_n$ in a natural way. 
$$ (a \mod n) + (b \mod n) := ((a+b) \mod n)$$
$$ (a \mod n) \cdot (b \mod n) := ((a\cdot b) \mod n)$$

This means that $\mathbb{Z}_n$, with the operations of $+$ and $\cdot$ will form a <em>closed system</em> with respect to these operations, i.e. for any pair $x,y$ from $\mathbb{Z}_n$, $x+y$ and $x \cdot y$ will again be elements of $\mathbb{Z}_n$. 

See Stallings for worked examples of $\mathbb{Z}_8$ under $+$ and $\cdot$. 

## Modular arithmetic

* So given $x$ from $\mathbb{Z}_n$, $x$ will have an <em>additive inverse</em>, $n-x$, which satisfies
$$x + (n-x) \equiv 0 \pmod{n}.$$
* Given $x$ from $\mathbb{Z}_n$, if there exists a $y$ in $\mathbb{Z}_n$ which satisfies
$$ x \cdot y \equiv 1 \pmod{n},$$
then we say $y$ is the <em>multiplicative inverse of $x$ modulo $n$</em>, and vice versa. We can write $y \equiv x^{-1} \pmod{n}$.
* But multiplicative inverses do not necessarily exist for every element of $\mathbb{Z}_n$.

## Modular arithmetic

This is connected to the issue of cancellation in $\mathbb{Z}_n$.

* If $(a+b) \equiv (a+c) \pmod{n} then b \equiv c \pmod{n}$.
* If $(a\cdot b) \equiv (a \cdot c) \pmod{n}$ then it's not neccessarily true that $b \equiv c \pmod{n}$.
* However if $a^{-1} \pmod{n}$ exists then we can cancel from products as
$$a^{-1} (a\cdot b) \equiv a^{-1} (a \cdot c) \pmod{n}$$
and so 
$$(a^{-1}a)\cdot b \equiv (a^{-1} a) \cdot c \pmod{n}$$
and so 
$$b \equiv c \pmod{n}.$$

## Extended Euclidean algorithm and multiplicative inverses

Using linear combinations and the Euclidean algorithm we can show that 

* for $a$ in $\mathbb{Z}_n$, a multiplicative inverse of $a$ modulo $n$ will exists if and only if $\gcd(a,n)=1$. 

Terminology

* If $\gcd(x,y)=1$ then $x,y$ are said to be <em>relatively prime</em>, or <em>coprime</em>.

See Stallings chapter 2 for details. 

<!-- ## Prime numbers

## Fermat's Little Theorem

## Euler's totient function

## Euler's theorem

## Primality testing

## The Chinese Remainder Theorem

## Exponentiation and discrete logarithms -->