---
layout: post
title: Action coordinates as a limit of maps
---

Here is an animation I made to spice up seminar talks about my recent joint paper [on integrable systems](https://arxiv.org/abs/1804.01504).

![gif]({{ "/images/image_of_orbit_animation1.gif" | absolute_url }})

So what's going on in this picture? On the left side we have a picture of two concentric spheres (red and blue) in \\(\mathbb{R}^3\\) (really, they are coadjoint orbits in the dual of the Lie algebra of \\(SU(2)\\), \\(\mathfrak{su}(2)^\*\\)).

There are two things happening on the right side.  Let me explain the black vertical lines and pink cone **first**.  These are a visualization of cylindrical coordinates on \\(\mathbb{R}^3\\), with the angle thrown away. The horizontal axis corresponds to radius (\\(\sqrt{x^2+y^2+z^2}\\)) and the vertical axis corresponds to height (\\(z\\)), and we have scaled both by a factor of 1/2. The image of \\(\mathbb{R}^3\\) under the map \\((x,y,z) \mapsto (r/2,h/2)\\) is the pink cone. The image of the red sphere is the red vertical line, and the image of the blue sphere is the blue vertical line.

So why do we care about this?  From the perspective of Poisson geometry, concentric spheres in \\(\mathbb{R}^3\\) are "symplectic leaves" of a Poisson structure. To describe this structure more simply, each concentric sphere has a measure of area on it that scales linearly with radius and is rotationally invariant.  Cylindrical coordinates on \\(\mathbb{R}^3\\) are particularly nice because, as Archimedes observed, the area of a region on a sphere bounded by two latitudes only depends on the difference in heights between the two latitudes. In differential geometry terms, in cylindircal coordinates, the area form on a sphere equals
\\[
 dh\wedge dr.
\\]

So cylindrical coordinates are perfectly tailored for describing the areas of concentric spheres in \\(\mathbb{R}^3\\).  The way to say this in the language of Poisson geometry, is that cylindrical coordinates on \\(\mathbb{R}^3\\) are *action coordinates* for the Poisson structure (action coordinates are a particularly well-behaved type of *integrable system*). 

The **second** thing happening on the right is an animation of the images of the two spheres under a family of maps that depend on a parameter \\(t\\). We see from the picture that as \\(t\to \infty\\), the images of the two spheres under these maps are converging to the images of the two spheres under cylindrical coordinates. Near the equator, this convergence is very fast, but as you go towards the two poles, the convergence rate slows down exponentially (but the image of every point does eventually converge).

Ok, so we are convinced that cylindrical coordinates are nice, and we have recovered cylindrical coordinates as a limit of some family of maps, who cares? The Poisson structure on \\(\mathbb{R}^3\\) is the simplest example of a linear Poisson structure on a vector space (we call these *Poisson vector spaces*). Poisson vector spaces are simultaneously one of the simplest families of Poisson structures (they are linear), but they are also quite beautiful and complicated. There are linear Poisson structures corresponding to every Lie algebra, and their symplectic leaves are interesting topologically. Our motivation is the following problem:

**Problem:** Find coordinates analogous to cylindrical coordinates (i.e. action coordinates) on all Poisson vector spaces.

It turns out this problem is quite difficult and is unsolved for all Poisson vector spaces except for a small family (those corresponding to compact Lie groups of type A,B, or D). On this family, a set of action coordinates called *Gelfand-Zeitlin systems* were discovered by [Guillemin and Sternberg in the early 1980's](https://www.sciencedirect.com/science/article/pii/0022123683900927).  Since then, no one has found a way to generalize Gelfand-Zeitlin systems to Poisson vector spaces corresponding to other Lie algebras\*.

The main result of our paper is that there is a family of maps (called *Ginzburg-Weinstein* maps) coming from Poisson geometry such that in the limit as \\(t\to\infty\\), they converge to Gelfand-Zeitlin systems (on the family of Poisson vector spaces corresponding to type A). Since the family of maps is defined more generally (for all compact simple Lie algebras), we hope that we can eventually prove a more general version of this convergence result, and thus generalize Gelfand-Zeitlin systems.

\* It should be mentioned that Megumi Harada did find a system that extends Gelfand-Zeitlin to type C.
