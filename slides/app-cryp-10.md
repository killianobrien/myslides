---
title: "Coursework support"
author:
- Killian O'Brien
- 6G6Z0024 Applied Cryptography 2023/24
date: Lecture Week 10 -- Mon 04 December 2023
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

## Plan

* Some polynomial problems
  * One of the poly product examples from <a href="https://killianobrien.github.io/app-cryp2324/schedule/notebooks/lab04.html" target="_blank">Lab 08</a>.
  * A polynomial $\gcd$ problem. Let $m(x) = x^8 + x^4 + x^3 + x + 1$, i.e. the modulus polynomial of $\text{GF}(2^8)$. Let $p(x) = x^5 + x^3 + x^2 + 1$. Confirm that $\gcd(m(x), p(x)) = 1$ and find $p^{-1}(x)$ in $\text{GF}(2^8)$.
* A Diffie-Helman key exchange problem. 
  * problem 10.1 from <a href="https://mmu.on.worldcat.org/oclc/1334132058" target="_blank">Stallings</a>.
