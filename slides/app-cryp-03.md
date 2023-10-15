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
* Figure from Stallings, Ch 4, pg 114

## Stream and Block ciphers

* **Block cipher** <img src="./images/block-cipher.png" alt="Smiley face" style="padding:10px;float:right;width:70%;"> 
* Plaintext $P$ divided into *blocks* of fixed bit-length $b$, typically 64 or 128 bits used.
* Encryption and decryption algortihms depend on same key $K$, known only to sender and recipient. 
* More widely used design than stream ciphers. 
* Provides a basic encryption/decryption component that can be used to build further ciphers, through so-called *modes of operation*. More on this later.
* Figure from Stallings, Ch 4, pg 114

## Possibilities for block ciphers
* **Outlining the possiblities** <img src="./images/4-bit-block-cipher.png" alt="Smiley face" style="padding:5spx;float:right;width:55%;"> 
* The encryption algorithm needs to map blocks of bit-length $n$ to blocks of bit-length $n$. 
* There are $2^n$ possible blocks of length $n$.
* The mapping needs to be *reversible*, i.e. a so-called *permutation* or *non-singular transformation*. 
* There are $(2^n)!$ such transformations to choose from.
* The factorial operator $!$ is defined as $$N! = N \cdot (N-1) \cdot (N-2) \cdot \dots \cdot 3 \cdot 2 \cdot 1.$$
* An example for $n=4$ shown on the right. 
* The key $K$ is, in effect, the whole mapping table. 
* However, short block lengths, known statistical properties of the plaintexts would leak through to the ciphertexts and allow attacks, such as *fequency analyis*.
* So in practice the block bit-length needs to be large, eg. $n=64$ or $128$. 
* But then the size of the mapping table is **very big** e.g. $2^{64}$ or $2^{128}$, which makes it hard to manage $K$ and keep it secure.
* So instead, require some way to base block ciphers on *smaller keys*.

## Feistel ciphers

* A Feistel cipher uses a block length of $n$ bits and a key of length $k$ bits. So there are $2^k$ possible keys. 
* It employs combinations of the two principles of **substitution** and **permutation** to achieve security.
    - <span class="definition" name="substitution">Each plaintext element is uniquely replaced by a corresponding ciphertext element.</span>
    - <span class="definition" name="permutation">A sequence of plaintext elements is replaced by a permutation of that sequence. So no new elements are added or deleted, rather the order the elements appear in the sequence is changed.</span>
* These correspond to the theoretical principles of **diffusion** and **confusion** developed by Claude Shannon. See Stallings chapter 4 for discussion.

## Feistel cipher structure

**Feistel cipher structure**

## Data Encryption Standard (DES)


