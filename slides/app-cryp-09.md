---
title: "Cryptographic hash functions"
author:
- Killian O'Brien
- 6G6Z0024 Applied Cryptography 2023/24
date: Lecture Week 09 -- Mon 27 November 2023
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

* Reading: <a href="https://mmu.on.worldcat.org/oclc/1334132058" target="_blank">Stallings, Chapter 11,<em>Cryptographic Hash Functions</em></a>

**Basic idea of a (cryptographic) hash function $H$**

* <img src="./images/hash-idea.png" alt="Stallings" style="padding:5px;height=100%;float:right"> $H$ takes a variable-length block of data $M$ and computes a fixed sized output $h=H(M)$.
* $h$ called the *hash value*, or *hash code* or *message digest*. 
* Typically the input message $M$ is split into standard sized blocks, with padding $P$ if necessary, often including data on the length $L$ of $M$.
* Typically $h$ will come from a very large domain of possible values, and different inputs $M$ will produce outputs $h$ that are evenly distributed and apparently random selections from this domain. 
* The inner workings of $H$ will be somewhat complex, but still have fast implenetations in software and/or hardware. 
* For cryptographic hash functions, the inner workings of $H$ will ensure security, in that it should be computationally infeasible to compute
    - a message $M$ that will hash to a given hash value $h$ (pre-image resistance)
    - two messages $M_1$ and $M_2$ that hash to the same hash value (collision resitance)


## Applications of cryptographic hash functions

* Message authentication
* Digital signatures
* Password authentication
* ...

## Applications of cryptographic hash functions

**Message authentication**

* $H$ can be used to verify the integrity of data in storage or communication. To ensure that it has not been changed. 
* In very simple terms, the hash value can be appended to the data as shown on below on left.
* This is too simple though, and susceptible to *man-in-the-middle attacks*, as shown on right.
* <img src="./images/simple-hash.png" alt="Stallings" style="padding:5px;height=100%;float:left"> <img src="./images/maninthemiddlehash.png" alt="Stallings" style="padding:5px;height=100%;float:right">

## Applications of cryptographic hash functions

**Message authentication possibilities**

* <img src="./images/MACmodes.png" alt="Stallings" style="padding:5px;height=100%;float:right"> The diagram on the right shows some ways in whcih $H$ can be used to implement message authentication.
* Diagram key
    - a cryptographic hash function $H$
    - message $M$ to be communicated
    - concatenation operator $||$
    - a secret symmetric key $K$
    - symmetric key encryption $E$
    - a shared secret value $S$

## Applications of cryptographic hash functions

**Digital signatures**

* <img src="./images/hash-signatures.png" alt="Stallings" style="padding:5px;height=100%;float:right"> Here the emphasis is on authentication and proof of the identity of the sender of the message $M$
* The hash function $H$ can be used in combination with asymmetric public key encryption $E$, with public $PU_a$, and private $PR_a$, keys of the sender $A$. 
* Diagram key
    - a cryptographic hash function $H$
    - message $M$ to be communicated
    - concatenation operator $||$
    - sender $A$'s (public,private) key pair $(PU_a,PR_a)$
    - symmetric/asymmetric (depending on keys used) encryption $E$
  
## Requirements and security


## Merkle-Damgard iterated hashs function design 

* <img src="./images/merkle-hash.png" alt="Stallings" style="padding:5px;height=100%;float:right"> Merkle and Damgard proposed this iterated design based on a *compression function* $f$ that produces an $n$-bit hash value. 
* The input message is split into $L$ fixed-size blocks $Y_i$ of $b$ bits each. 
* The final block $Y_{L-1}$ also contains the length information of the original message and any necessary padding to make it up to $b$ bits. 
* The compression function $f$ takes two inputs, the message block $Y$ and an $n$ bit *chaining variable* $CV$, and produces an $n$-bit output chaining variable $CV'$.
* $CV_0 = IV = \text{ standard initial $n$-bit value}$
* $CV_{i} = f(CV_{i-1}, Y_{i-1}), \quad 1 \leq i \leq L$
* $H(M) = CV_L$

## The SHA family and SHA-512

* Secure Hash Algorithm (SHA) family produced by NIST have been the most widely used crpytographic hash functions. 
* <img src="./images/SHAfamily.png" alt="Stallings" style="padding:5px;height=100%;float:right"> Offers hash functions of increasing complexity and security. 
* As earlier versions become vulnerable to weaknesses incombination with brute-force attack, then later versions adopted.
* Currently SHA-256 and SHA-512 seen as sensible.

## SHA-512
