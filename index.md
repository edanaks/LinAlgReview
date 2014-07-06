---
title       : Linear Algebra Review
subtitle    : Linear Optimization - Math 354, Summer 2014
author      : Shashank Kanade
job         : 
framework   : io2012     # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     : [mathjax]            # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
knit        : slidify::knit2slides
---

<style>em {  font-style: italic; text-decoration: underline}</style>
<style>strong {  font-weight: bold; }</style>


--- .class #id

## Matrices

1. Matrices are rectangular arrays of numbers.
2. Example of a matrix of dimension $2\times 3:$
$$
\mathbf{A}=\left[\begin{array}{rrr} 1 & 2 & 3 \\ 4 & 5 & 6 \end{array}\right]
$$
2. $\mathbf{A}_{ij}$ denotes the entry in $i^\text{th}$ row and $j^\text{th}$ column.
4. Column vectors of dimension $n$ are matrices of dimension $n \times 1$.
5. Row vectors of dimension $n$ are matrices of dimension $1\times n$.
6. Totality of row vectors of a fixed dimension $n$ is denoted as $\mathbb{R}^n$.
7. One can only add or subtract matrices of the **same size**.
8. The zero matrix $\mathbf{0}$ is a matrix each of whose entries is a zero.
7. Identity matrix $\mathbf{I}_n$ of size $n$ is a matrix with 1's on the diagonal and zeroes elsewhere.
1. In this class, matrices and vectors will be written with boldface letters, like $\mathbf{A, x, b}$ etc.
Unlike numeric variables, which will be written like $x,y,z$ etc.

--- .class #id 

## Matrix Multiplication

Multiplying $a\times b$ and $b\times c$ matrices produces a matrix of size $a\times c$.
Example:
$$\left[\begin{array}{rrr} 1 & 2 & 3 \\\\ 4 & 5 & 6 \end{array}\right]\times\left[\begin{array}{rr} 1 & -1  \\\\ 0 & -2 \\\\ 1 & -3 \end{array}\right]= \left[\begin{array}{rr} 4 & -14 \\\\ 10 & -32 \end{array}\right]$$
Here, $(2\times 3)\cdot (3\times 2) = (2\times 2).$ 

One can also multiply a matrix by a scalar as follows:
$$5\cdot\left[\begin{array}{rr} 4 & -14 \\\\ 10 & -32 \end{array}\right]=\left[\begin{array}{ll} 20 & -70 \\\\ 50 & -160 \end{array}\right].$$

--- .class #id 

## Properties of Matrix Multiplication

Matrix multiplication is quite different from multiplication of
numbers, and in general,

1. $A\cdot B\neq B\cdot A$.
2. $A\cdot C=B\cdot C$ does not always imply $A=B$.
2. $A\cdot B = 0$ without either being equal to 0.


--- .class #id

## Transpose of a Matrix

1. Flips rows and columns of a matrix.
2. From a $m\times n$ matrix, produces a $n\times m$ matrix.
3. Example: $$\left[\begin{array}{rrrr} 1 & 2 & 3 & 0 \\\\ 4 & 5 & 6 & 8\end{array}\right]^T= 
\left[\begin{array}{rr}1& 4\\2&5\\3&6\\0&8\end{array}\right]$$

Properties:

1. $(A^T)^T=A$
2. $(AB)^T=B^TA^T$. Note the change in the order.

Question: If $u,v\in\mathbf{R}^n$, what sort of an object is $u^Tv$?

--- .class #id

## Linear Systems

$$\begin{array}{lllllr}
3x & &+2z &+2w &= & -8\\
2x & +3y & +5z &-w &= & 4\\
x &  &  &+w &= & 6\\
\end{array}$$

This system can be written in a matrix form as $\mathbf{Ax} = \mathbf{b}$,
where 
$$\mathbf{A} = \left[\begin{array}{rrrr} 3 & 0 & 2 & 2 \\ 2 & 3 & 5 & -1 \\1& 0 & 1 & 1\end{array}\right],\quad\mathbf{x} = \left[\begin{array}{c}x\\y\\z\\w\end{array}\right],\quad\mathbf{b}=\left[\begin{array}{r}-8\\4\\6\end{array}\right].$$

The ***augmented matrix*** for this system is:
$$ \left[\begin{array}{rrrr|r} 3 & 0 & 2 & 2 & -8 \\ 2 & 3 & 5 & -1 & 4\\1& 0 & 1 & 1 & 6\end{array}\right].$$

--- .class #id

## RREF

Stands for Row Reduced Echelon Form.

Example:
$$\left[\begin{array}{rrrrr}\fbox{1} & 0 & 3 & 0 & 4\\0 & \fbox{1} & 2 & 0 & 1\\0 & 0 & 0 & \fbox{1} & 2\\0 & 0 & 0 & 0 & 0\\0 & 0 & 0 & 0 & 0\\\end{array}\right].$$

+ A boxed number indicates a ***leading entry*** of a row.
+ Columns containing a leading entry are called ***pivot columns***.
+ Column 1, 2, 4 are pivot columns.
+ ***Rank*** = No. of pivot columns = No. of leading entries


--- .class #id

### What is RREF?

+ All "0 rows" are at the bottom of the matrix.
+ Leading entries of the successive rows keep "moving right".
+ All pivot columns have exactly one 1, and rest of their entries are 0s.


**It is easy to solve linear systems once their
augmeted matrix is put in an RREF.** Example on the board.

**Therefore, the first (and the biggest) step in solving a linear system is transforming its augmented matrix
in the RREF!**

--- .class #id

### Elementary row operations

+ Interchange rows $i$ and $j.$ Denoted as $\mathbf{R}_i\leftrightarrow \mathbf{R}_j.$
+ Multiply row $i$ by a non-zero scalar $c:$ Denoted as $\mathbf{R}_i \leftarrow c\mathbf{R}_i.$
+ Add a non-zero multiple of a row $i$ to row $j$ and store the result in row $j:$ 
Denoted as $\mathbf{R}_j \leftarrow \mathbf{R}_j + c\mathbf{R}_i.$

### More about RREF
+ Any matrix can be brought into a (unique) RREF using a sequence of elementary row  operations.
 --> ***Gauss-Jordan Elimination***
+ Each elementary row operation corresponds to multiplying the given matrix by an ***Elementary Matrix***
on the left.
+ Elementary matrices are square matrices, whose inverse is the elementary matrix corresponding to the "opposite" row operation.
+ Gauss-Jordan Elimination is perhaps *the* *most important* topic from math 250.
+ Example of Gauss-Jordan Elimination on the board (if there is time).

--- .class #id

## Inverse of a matrix

1. We talk of inverses only for square matrices.
2. ***Inverse*** of an $n\times n$ matrix $\mathbf{A}$ (if it exists) is another $n\times n$ matrix $\mathbf{B}$
such that $$\mathbf{A}\cdot\mathbf{B} = \mathbf{I}_n = \mathbf{B}\cdot\mathbf{A}.$$
3. Inverse, if it exists is unique. 
4. Matrices without inverses are called **singular**, else are called **invertible** or **non-singular**. 
5. If $\mathbf{A}$ is invertible, then $\mathbf{A}\mathbf{x}=\mathbf{b}$ has a *unique* solution for
any vector $\mathbf{b}$ of appropriate size, and that solution is given by $\mathbf{x}=\mathbf{A}^{-1}\mathbf{b}.$
6. A matrix is invertible if and only if its determinant is non-zero.

Questions:  What is the RREF of an invertible matrix? What is the rank of an invertible matrix of size $n\times n$?

--- .class #id

### Finding inverse

1. Make an augmented matrix $[\mathbf{A}|\mathbf{I}_n]$. 
2. Now perform row operations on this augmented matrix 
so that the "left block" gets transformed
into an identity matrix. 
3. Say you arrive at $[\mathbf{I}_n|\mathbf{B}]$, then $\mathbf{B}$ is the inverse of $\mathbf{A}$.
4. If you arrive at a "zero row" in the left block, then the matrix is singular.

--- .class #id

### Examples:

(1) Invertible example:

$$ \mathbf{A} = \left[\begin{array}{rr}2 & 0\\-2 & 2\end{array}\right] \xrightarrow{\text{Augment}}
 \left[\begin{array}{rr|rr}2 & 0&1&0\\-2 & 2&0&1\end{array}\right]
 \xrightarrow{\text{Row Ops}} \left[\begin{array}{rr|rr}1 & 0&1/2&0\\0 & 1&1/2&1/2\end{array}\right]$$

So $\mathbf{A}$ is invertible and

$$\mathbf{A}^{-1}=\left[\begin{array}{rr}1/2&0\\1/2&1/2\end{array}\right].$$

(2) A singular example:

$$\mathbf{A}=
\left[\begin{array}{rrr}
1&2&1 \\2&3&-4\\2&3&7
\end{array}\right] \xrightarrow{\text{Augmentation, Row ops}}
\left[\begin{array}{rrr|rrr}
1&2&1&1&0&0\\
0&-1&-6&-2&1&0\\
0&0&0&-3&1&1
\end{array}\right].
$$

--- .class #id

## Subspaces

Fix a value of $n$, we will talk of subspaces of $\mathbb{R}^n$.

$S$ is called a ***subspace*** of $\mathbb{R}^n$ if:

1. $S$ is a collection of vectors from $\mathbb{R}^n.$
2. Zero vector is a member of $S$.
3. If $\mathbf{u}\in S$ and $c$ is any scalar, then $c\mathbf{u} \in S$.
3. If $\mathbf{u},\mathbf{v}\in S$, then $\mathbf{u}+\mathbf{v}\in S$.


--- .class #id

### Basic Examples

1. $S=\{\mathbf{0}\}.$
2. $S=\mathbb{R}^n.$



### Geometric examples:

1. Any line passing through the origin
2. Any plane passing through the origin
3. Any "hyper-plane" passing through the origin

(Examples on the board)

--- .class #id

### Examples Continued

"Spock, take me through that subspace fracture" --- Kirk.

"Ever took linear algebra, Sir?" --- Spock.

--- .class #id

### Examples continued

Given a set of vectors $\mathbf{u}_1,\mathbf{u}_2,\mathbf{u}_3,\dots,\mathbf{u}_k$,
the **span** of these vectors is the collection of all possible vectors $\mathbf{v}$
which can be written as 
$\mathbf{v} = c_1\mathbf{u}_1+c_2\mathbf{u}_2+\dots+c_k\mathbf{u}_k.$

Spans are always subspaces!

Collection of vectors of the form $\begin{bmatrix}2a+b\\b-c\\a\end{bmatrix}$  is the
span of $\begin{bmatrix}2\\0\\1\end{bmatrix}, \begin{bmatrix}1\\1\\0\end{bmatrix},\begin{bmatrix}0\\-1\\0\end{bmatrix}$,
since
$$\begin{bmatrix}2a+b\\b-c\\a\end{bmatrix}= 
a\begin{bmatrix}2\\0\\1\end{bmatrix}+b \begin{bmatrix}1\\1\\0\end{bmatrix}+c\begin{bmatrix}0\\-1\\0\end{bmatrix}.$$

Question: What about collection of vectors of the form $\begin{bmatrix}a\\b+a\\a-3\end{bmatrix}?$

--- .class #id

## Linear Independence

Caution: An extremely important concept.

- A set $V=\{\mathbf{v}_1,\mathbf{v}_2,\dots,\mathbf{v}_k\}$ of vectors in $\mathbb{R}^n$ is called ***Linearly Dependent*** if there exist scalars $c_1,c_2,\dots,c_k$, **not all zero** such that $$c_1\mathbf{v}_1+c_2\mathbf{v}_2+\dots+c_k\mathbf{v}_k=\mathbf{0}.$$
Otherwise, the set is called ***Linearly Independent***

- In other words, if the only scalars which satisfy $c_1\mathbf{v}_1+c_2\mathbf{v}_2+\dots+c_k\mathbf{v}_k=\mathbf{0}$ are $c_1=0,c_2=0,\cdots,c_k=0$, then $V$ is linearly independent.

- Any set $V$ which contains the $\mathbf{0}$ vector is linearly dependent.

- Btw, a vector of the form $c_1\mathbf{v}_1+c_2\mathbf{v}_2+\dots+c_k\mathbf{v}_k$ is called a ***Linear Combination*** of the vectors $\mathbf{v}_1,\mathbf{v}_2,\dots,\mathbf{v}_k.$

--- .class #id

### Example

$$V = \left\lbrace\mathbf{v}_1= \begin{bmatrix}1\\2\\0\\1\end{bmatrix},
\mathbf{v}_2= \begin{bmatrix}0\\1\\1\\2\end{bmatrix},\mathbf{v_3}= \begin{bmatrix}1\\1\\-1\\-1\end{bmatrix}    \right\rbrace.$$

Of course, $\mathbf{v}_1+\mathbf{v}_2+\mathbf{v}_3=\mathbf{0}.$ So $c_1=c_2=c_3=1$ in the definition of linear dependence => $V$ is L.D.

How do we see it in a non-ad-hoc way? RREFs!

Essentially, we are trying to solve the system 
$$\begin{bmatrix}\vdots & \vdots &  \cdots & \vdots \\ \mathbf{v}_1 & \mathbf{v}_2 & \cdots & \mathbf{v}_k \\\vdots & \vdots &  \cdots & \vdots \end{bmatrix}
\begin{bmatrix}c_1\\c_2\\ \vdots\\c_k\end{bmatrix}=\mathbf{0}.$$

--- .class #id

$$
\mathbf{A}=\begin{bmatrix}\vdots & \vdots &  \cdots & \vdots \\ \mathbf{v}_1 & \mathbf{v}_2 & \cdots & \mathbf{v}_k \\\vdots & \vdots &  \cdots & \vdots \end{bmatrix}
=\begin{bmatrix}1&0&1\\2&1&1\\0&1&-1\\1&2&-1\end{bmatrix}\xrightarrow{\text{RREF}}
\begin{bmatrix}1&0&1\\0&1&-1\\0&0&0\\0&0&0\end{bmatrix}$$

- If $\mathbf{A}$ has any non-pivot columns, (the $3^\text{rd}$ column above), then the columns of $\mathbf{A}$ form a set of linearly dependent vectors.

- In fact, the pivot columns of $\mathbf{A}$, (the $1^\text{st}$ and $2^\text{nd}$ columns) form a set of linearly independent vectors. So, $L=\{ \mathbf{v}_1,\mathbf{v_2}\}$ is a linearly independent subset of $V=\{\mathbf{v}_1,\mathbf{v}_2,\mathbf{v}_3 \}.$

- In other words, if Rank of $\mathbf{A}$ (= the number of pivot columns) equals the number of columns of $\mathbf{A}$, then the columns
of $\mathbf{A}$ form a linearly independent set.

--- .class #id

## Bases

Let us talk of bases of $\mathbb{R}^n.$ In general, one can talk of bases for any subspace for $\mathbb{R}^n$. 

Caution: An extremely important concept.

A set of vectors $V$ in $\mathbb{R}^n$ is called a ***Basis*** for $\mathbb{R}^n$ if:

1. $V$ spans $\mathbb{R}^n$, i.e., any $n$-dimensional vector can be expressed as a linear combination of vectors in $V.$
2. $V$ forms a linearly independent set.

Notes:

1. A basis for $\mathbb{R}^n$ will have exactly $n$ vectors. 
2. If $V$ has size less than $n$, then $V$ won't span $\mathbb{R}^n.$
3. If $V$ has size greater than $n$, then $V$ will necessarily be linearly dependent, as the matrix $\mathbf{A}=[\mathbf{v}_1,\dots,\mathbf{v}_k]$ will
have a non-pivot column.

--- .class #id

### Analysis

First form the matrix $\mathbf{A}=\begin{bmatrix}\vdots & \vdots &  \cdots & \vdots \\ \mathbf{v}_1 & \mathbf{v}_2 & \cdots & \mathbf{v}_k \\\vdots & \vdots &  \cdots & \vdots \end{bmatrix}.$


- If RREF of $\mathbf{A}$ has no non-zero rows, then the columns of $\mathbf{A}$ span $\mathbb{R}^n$.
- If each column of $\mathbf{A}$ is a pivot column, then the columns of $\mathbf{A}$ are linearly independent.

Therefore,
- If the RREF of $\mathbf{A}$ satisfies both the conditions, then the columns of $\mathbf{A}$ form a basis of $\mathbb{R}^n.$
- If the RREF of $\mathbf{A}$ satisfies both the conditions, then the RREF equals the identity matrix $\mathbf{I}_n!$

--- .class #id

### Examples

In each of the following cases, answer:

1. If the columns of $\mathbf{A}$ span $\mathbb{R}^n$, for some appropriate value of $n$.
1. What is this appropriate value of $n$?
1. Are columns of $\mathbf{A}$ linearly independent?
1. Which columns of $\mathbf{A}$ form a linearly independent set?
1. Do columns of $\mathbf{A}$ form a basis of $\mathbb{R}^n$ for some appropriate value of $n$?

--- .class #id

$$
\begin{align}
(1) \quad \mathbf{A}= \begin{bmatrix} 1 & 0 & 1 & 1\\1 & 1 & 2 & 0 \end{bmatrix}&\xrightarrow{\text{RREF}}
\begin{bmatrix} 1 & 0 & 1 & 1\\0 & 1 & 1 & -1 \end{bmatrix}\\ & \\
(2) \quad \mathbf{B}= \begin{bmatrix} 1 & 0 & 2\\2 & 1 & 5  \\ 3 & -1 & 5\end{bmatrix}&\xrightarrow{\text{RREF}}
\begin{bmatrix} 1 & 0 & 2 \\0 & 1 & -1 \\ 0 & 0 & 0 \end{bmatrix}\\ & \\
(3) \quad \mathbf{C} = \begin{bmatrix} 1 & 0 & 2\\2 & 1 & 5  \\ 3 & -1 & 0\end{bmatrix}&\xrightarrow{\text{RREF}}
\begin{bmatrix} 1 & 0 & 0 \\0 & 1 & 0 \\ 0 & 0 & 1 \end{bmatrix}\end{align}
$$