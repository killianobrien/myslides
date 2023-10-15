---
title: "Symmetric ciphers and the Data Encryption Standard (DES)"
author:
- Killian O'Brien
- 6G6Z0024 Applied Cryptography 2023/24
date: Lecture Week 03 -- Mon 16 October 2023
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
    - <a href="https://mmu.on.worldcat.org/oclc/1334132058" target="_blank">Stallings, Chapter 3, Just Section 3.1: Symmetric Cipher Model</a>

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

## Symmetric Ciphers

* Something on security definition.

## Stream and Block ciphers

* **Stream cipher** <img src="./images/stream-cipher.png" alt="Smiley face" style="padding:10px;float:right;width:70%;"> 
* Considers plaintext $P$ as a stream of individual bits, $P=(p_0, p_1, p_2, \dots)$.
* Requires a key stream $K$ of individual bits, $K=(k_0, k_1, k_2, \dots)$, known only to sender and recipient. 
* Encryption is by $\pmod{2}$-addition-without-carry, also known as exclusive-or operation (XOR)
* Ciphertext $C=(c_0, c_1, c_2, \dots )$ computed as $c_i = p_i + k_i$
    - $0 + 0 = 0$, $1+1=0$
    - $0+1 = 1$, $1+0=1$
* Ideal $K$ is so-called **one-time pad**, a random stream of bits known only to sender and recipient. But this *impractical*.
* So some kind of keyed algorithm is used to produce the keystream $K$. 
* More on stream ciphers later in the unit. 

## Stream and Block ciphers

* **Block cipher** <img src="./images/block-cipher.png" alt="Smiley face" style="padding:10px;float:right;width:70%;"> 
* Plaintext $P$ divided into *blocks* of fixed bit-length $b$, typically 64 or 128 bits used.
* Encryption and decryption algortihms depend on same key $K$, known only to sender and recipient. 

## next 

**General intro**

* Stream ciphers
    - mention on-time-pad
    - but in reality use keyed algorithms to generate key streams

* Block ciphers
    - blocks of text
    - widely used

## Feistel ciphers

* Substitution and permutation

**Shannon's**

* diffusion and confusion

## Feistel ciphers

**Feistel cipher structure**

## Data Encryption Standard (DES)


