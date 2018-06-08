---
layout: post
title: Quick and dirty tropical matrix multiplication in NumPy
---

The semifield of tropical numbers (or the min-plus algebra) is the set of real numbers 
with the "addition" and "multiplication" operations

\\[
x\oplus y = \min\\{x,y\\},\, x\otimes y = x + y.
\\]
So that we have an additive identity, we adjoin negative infinity to our set of numbers. Thus the set of tropical real numbers is \\( \mathbb{T} = \mathbb{R}\cup\\{-\infty\\} \\).

Matrix multiplication over \\( \mathbb{T} \\) works the same way as ordinary matrix multiplication (replacing the +,\* operations), 
\\[
\[A\cdotB\]\_{i,j} = \oplus_{k} (a_{i,k}\otimes b_{k,j}) = \min_k \left\\{ a_{i,k} + b_{k,j} \right\\}.
\\]
Tropical matrix multiplication is interesting for many reasons, one being that the entries of the resulting matrix can be interpreted as [shortest paths in a weighted directed graph](https://en.wikipedia.org/wiki/Min-plus_matrix_multiplication). Tropical algebra also has applications in [scheduling problems](https://golem.ph.utexas.edu/category/2013/03/project_planning_parallel_proc.html).  For more background, I recommend reading the first chapter of "Introduction to Tropical Geometry" by Maclagan and Sturmfels.

Tropical matrix multiplication isn't built into NumPy, but we can implement it in one line:

```>>> np.min(X.reshape((n,1,p)) + Y.T.reshape((1,m,p)),axis=2)```
  
Here is a picture of what the code does (dashes represent broadcasting)

![Tropical multiplication]({{ "/images/tropical_multiplication.png" | absolute_url }})

Of course, the algorithm behind this code is not optimal: what it does is the exact same as the naive algorithm for 
matrix multiplication with the operations changed. Taking the sum of two \\( n\times m \times p\\) 
arrays is \\( O(nmp)\\) and taking the minimum entry of \\(nm\\) length \\(p\\) vectors is also \\( O(nmp)\\), 
so the whole line of code is \\( O(nmp)\\). This performs badly for large matrices.

That being said, this code is more efficient for tropical matrix multiplication 
than writing your own naive implementation in python using for-loops, since it replaces two for-loops 
with numpy broadcasting.
