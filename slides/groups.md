---
title: "6G6Z3024 Group Theory"
author: Killian O'Brien
date: April 2022
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

## The unit

* Optional unit in first semester
* 4 hours lecture + 2 hour tutorial per week
* Assessment: Coursework problems (40%), Examination (60%)
* A unit that allows you to continue your study of pure mathematics
* Excellent free open-source textbook, [Abstract Algebra](http://abstract.pugetsound.edu/), by Tom Judson
* We study a selection from chapters 1 - 15


## The unit

* A thorough introduction to a substantial area of pure mathematics that has strong connections to areas of geometry, combinatorics, graph theory, ... .
* Definitely suited to students who like problem solving and the unit will develop your skills in this area.
* We will use the Sage mathematics system to aid our investigations with the Python programming language.  ([SageMath](http://www.sagemath.org), [CoCalc](https://cocalc.com), [sagecell.sagemath.org](https://sagecell.sagemath.org))

## The unit gives

* An appreciation for the many aspects of group theory and its connections to other areas of mathematics.
* Development of your problem solving and abstract thinking skills.
* Exposure to SageMath mathematical software, aimed at pure mathematics teaching and research.
* SageMath uses the Python programming language which is widely used in many areas of computing.

## What is a group?

A set of mathematical objects with a mathematically meaningful operation applied amongst them that is *well behaved*, will be a group. It's a very broad concept and present in many areas of mathematics.

## More formally

A set $G$ with a binary operation $\star$ satisfying

* $G$ is a closed system under $\star$, i.e. $x \star y \in G$.
* $\star$ is associative on $G$, i.e. $x \star ( y \star z) = (x \star y) \star z$.
* $G$ contains an identity element, $e$, for $\star$, i.e.
$$x \star e = e \star x = x.$$
* $G$ contains inverse elements for $\star$, i.e. $x \star x^{-1} = e$.



## Syllabus topics

### Examples of groups:

* Symmetry groups of two and three-dimensional objects,
* the dihedral groups $D_n$,
* rotational symmetry groups of three-dimensional polyhedra.
* Permutation groups, the Symmetric groups $S_n$ and the Alternating groups $A_n$,
* Number based groups under arithmetic operations,
* the cyclic groups $\mathbb{Z}_n$,
* Groups of matrices
* ...

## Syllabus topics

$\Gamma^+(T)$ is the set of rotational symmetries of the tetrahedron.

<img  style="height:90%; object-fit:contain;display:block;margin:auto; " src=./tetrahedrons.png>

## Syllabus topics

The symmetric group, $S_4$, is the group of all rearrangments, or *permutations*, of four objects.

<img style=" height:100%; object-fit:contain;display:block;margin:auto; " src=./S4_Cayley.png>

## Syllabus topics

Group theory lends itself to visual thinking with beautiful mapping diagrams (from Nathan Carter's *Visual Group Theory*, MAA)

<img style="display:block;margin:auto; height:90%; object-fit:contain;display:block;margin:auto; "  src=./homomorphisms.png>


## Syllabus topics

### Classification problems:

* The grand enterprise of group theory is to discover and classify all the groups that there are.
* What classification problems can be posed?

### Lagrange's theorem:

* Restricts the possibilities for the sizes of subgroups.
* If $H$ is a subgroup of $G$ then $|H|$ divides $|G|$.

### The classification of finitely presented Abelian groups:

* All the possible structures of such groups are found and classified
* Can relate this to a type of matrix reduction algorithm on presentation matrices of such groups


### Classification of groups of low order:

* What about non-Abelian groups? 
* Why we can't solve using matrix reduction? Investigation of groups of low order and enumeration and classification of all groups up to some suitable order.

## Syllabus topics

### Sylow's theorems:

* Discussion of the converse to Lagrange's theorem:
* If $d$ divides $|G|$, does $G$ have a subgroup of size $d$?.
* Group actions, orbits, stabilizers. Self-action by conjugation.
* Sylow's theorems relating to powers of prime divisors of $|G|$.


## Wider interest material / applications

The unit allows us to access interesting general material on the following topics/applications.

### The classification of finite simple groups

The grand project. Status of the proof. Some history and biographical details of the completion of the project. The families in the classification. The sporadic groups. The Monster group and Monstrous Moonshine.

### The Monster group

* A group, $M$, with approx. $8 \times 10^{53}$ elements, that is *simple*, i.e. it has no *normal* subgroups.
* $M$ is (isomorphic to) a group of rotations of 196883-dimensional space.
* $M$ is (isomorphic to) a group of matrices generated by two particular binary $196882 \times 196882$ matrices.

### Algorithmic problems

* The word problem. Computability. Alan Turing.

<img style="height:20%;object-fit:contain;  display:block;margin:auto;" src=./turing.jpg>

## Wider interest material / applications

### Combinatorial enumeration and geometric classification problems

Counting number of distinguishable colourings of geometric objects. Classifying the symmetry types of two-dimensional wallpaper patterns. Classifying two and three-dimensional crystal structures (lattices).

<iframe width = "50%" height="50%" style="display:block; margin:auto;" src="file:///home/killian/Dropbox/Teaching2021/groups/sessions/dodecahedron-labelled.html" title="Dodecahedron"></iframe>

## Wider interest material / applications

### The are exactly 17 different types of wallpaper, when classified according to their symmetries.

<img style="width:60%; object-fit:contain;display:block;margin:auto; " src=./wallpapers.png>


## SageMath

~~~~~{.python}
G=DihedralGroup(12)

HH = [H for H in G.subgroups() if not H.order()==1]

for H in HH:
    P = plot(H.cayley_graph(), vertex_labels=False)
    show(P)
~~~~~

The above code displays the *Cayley Graph* of every subgroup of $D_{12}$. See the results from SageMath in a [SageCell](https://sagecell.sagemath.org/?z=eJw9kLFqxDAQRHuD_2HgGruIwVcGXCUgfcB1IQTFXluCPa2RZA7_fSSfc1sO82Z2Vw2fztIUDKsg29r017auLlBwEckSlqJCZgRJJjnxhmH8VDyBZqbx1OJ-v1MKjmIxZ_LpWDY2Af31LbqJJqzC-yK-rupKawz40pglQMN5qC5uv0ddbFq4GV4SdCdhotC0w9B_l8iMnZtFSqXKcC7_B4ugSvoFt2yZhVkezi9HC4usWIPz6RlQXB9mZ9rzlWa1BSYz2lfcmfbaUOv3ukKeaOXR6G484J8Dbtr8tz_mQmmX&lang=sage)






