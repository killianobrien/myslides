---
title: "Introduction to Number Theory"
author:
- Killian O'Brien
- 6G6Z0024 Applied Cryptography 2023/24
date: Lecture Week 02 -- Mon 09 October 2023
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

* <img src="./images/mee.jpg" alt="Smiley face" style="padding:3px;float:right;width:150px;"> My name is Dr Killian O'Brien
* Contacts: [k.m.obrien@mmu.ac.uk](mailto:k.m.obrien@mmu.ac.uk), [Teams chat](https://teams.microsoft.com/l/chat/0/0?users=k.m.obrien@mmu.ac.uk){target="_blank"}, Office JDE 114a (first floor of John Dalton East, Chester St end)

* Office hours are Thurs 2-3pm &amp; Thur 4-5pm - before/after your Thurs lecture.
    - Normally in my office JD E114a
    - Though I might be based in the Learning Studio for these office hours. I'll send a Moodle announcement/email if I am there. 

* 6G6Z0024 Applied Cryptography (15 credits)

* The [Moodle](https://moodle.mmu.ac.uk/course/view.php?id=172138){target="_blank"} page for the unit.

* Reading for this topic
    - <a href="https://mmu.on.worldcat.org/oclc/1334132058" target="_blank">Stallings, Chapter 4: Block Ciphers and the Data Encryption Standard (DES)</a>

## Symmetric Ciphers

Some definitions, (Stallings, *Cryptography and Network Security*, Ch. 3)

* <span class="definition" name="Plaintext">The original intelligible message or data.</span>
* <span class="definition" name="Encryption algorithm">The encryption algorithm performs various substitutions and transformations of the plaintext.</span>
* <span class="definition" name="Secret key">The secret key $K$ is input into the encryption algorithm along with the plaintext. The algorithm will produce different outputs depending on the specific value of $K$ used for the same plaintext. The exact substitutions and transformations carried out by the algorithm depend on $K$.</span>
* <span class="definition" name="Ciphertext">The scrambled message output by the encryption algorithm. It depends on the agorithm, plaintext and key $K$. The ciphertext should be an apparently unintelligible random stream of data. </span>

## Symmetric Ciphers

![Stallings *Cryptography and Network Security*, Sec. 3.1, pg 85](./images/symmetric-cipher.png){style="width:60%"}

## Symmetric Ciphers

* Bob (message source) sends an encrypted message to Alice (destination)
* The cryptanalyst Eve, intercepts $Y$, has knowledge of the encryption and decryption algorithms, and seeks to develop estimates $\hat X$ and/or $\hat K$ of the plaintext $X$ and key $K$. 

![Stallings *Cryptography and Network Security*, Sec. 3.1, pg 86](./images/symmetric-cipher2.png){style="width:60%"}

## Symmetric Ciphers

* The types of attacks carried out by Eve can be classified in various ways,

![Stallings *Cryptography and Network Security*, Sec. 3.1, pg 88](./images/types-of-attack.png){style="width:70%"}

## g


