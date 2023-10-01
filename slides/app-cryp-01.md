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
and if no such integer $c$ exists then we say $b$ does *not divide* $a$.

* So $b | a$ is a binary relation on $a,b$, i.e. a statement that is true or false, depending on the values of $a,b$.

* If $b|a$ then we say $b$ is a *factor* or *divisor* of $a$. 

Examples

* $3|15$, $5|15$, $1|15$, $15|15$.

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

The *integer division algorithm* is simply a formalization of this

* 

## Greatest Common Divisors (gcd)

## The Euclidean Algorithm

## The mod operator and the congruence relation

## Modular arithmetic

A few slides here

## Prime numbers

## Fermat's Little Theorem

## Euler's totient function

## Euler's theorem

## Primality testing

## The Chinese Remainder Theorem

## Exponentiation and discrete logarithms