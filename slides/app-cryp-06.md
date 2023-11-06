---
title: "Advanced Encryption Standard (AES)"
author:
- Killian O'Brien
- 6G6Z0024 Applied Cryptography 2023/24
date: Lecture Week 06 -- Mon 06 November 2023
transition: fade
theme: killian
width: 1920
height: 1080
margin: 0.05
center: false
revealjs-url: ../reveal.js
title-slide-attributes:
    data-background-color: rgb(0,47,108)	
    data-background-image: logowhite.png
    data-background-size: 18%
    data-background-repeat: no-repeat
    data-background-position: 95% 5%	
---

## Introduction

* The **Advanced Encryption Standard** (AES), published by NIST in 2001.
* To replace DES due to security concerns over small key size and other considerations. 
* AES designed to be more secure and fast.
* From 2008 on, chip manufacturers implement AES capabilities in low-level chip design. 
* Now the most widely used cipher. 

## Polynomial arithmetic and the fields $GF(2^n)$

* Consider all polynomials 
$$f(x) = a_{n-1} x^{n-1} + a_{n-2} x^{n-2} + \dots + a_1 x + a_0 = \sum_{i=0}^{n-1} a_i x^i, \quad a_i \in \mathbb{Z}_2.$$
of degree $n-1$ or less.
* Arithmetic follows the rules of $+$ and $\cdot$ for polynomials, with arithmetic of the coefficients $a_i$ carried out in $\mathbb{Z}_2$, i.e. addition of coefficients is the same as $\text{XOR}$.
* If multiplication results in a polynomial of degree greater than $n-1$ then the product is reduced modulo a specified irreducible polynomial $m(x)$ of degree $n$, the modulos polynomial. 

## AES and $\text{GF}(2^8)$. 

 * <img src="./images/GF8examp.png" alt="Stallings" style="padding:5spx;width=100px;float:right"> The Advanceed Encryption Standard (AES) uses such a field $\text{GF}(2^8)$, consisting of polynomials of degree less than or equal to 7, with binary coefficients and polynomial operations carried out modulo the irreducible polynomial 
 $$m(x) = x^8 + x^4 + x^3 + x +1.$$
 * The figure on the right shows the calculation of an example product in $\text{GF}(2^8)$.
 * AES uses this since it is designed to operate on 8-bit bytes.
    - addition of bytes is just bit-wise $\text{XOR}$.
    - *multiplication* of bytes is defined as multiplication in the finite field $\text{GF}(2^8)$, modulo the irreducible polynomial $m(x) = x^8 + x^4 + x^3 + x +1.$


