---
layout: post
title: Animation - action coordinates as a tropical limit of Ginzburg-Weinstein diffeomorphisms
---

Here is an animation I made to spice up seminar talks about my recent joint paper [on integrable systems](https://arxiv.org/abs/1804.01504).

![gif]({{ "/images/image_of_orbit_animation.gif" | absolute_url }})

So what's going on in this picture? On the left side we have a picture of two concentric spheres (red and blue) in \\(\mathbb{R}^3\\) (really, they are coadjoint orbits in the dual of the Lie algebra of \\(SU(2)\\)).

There are two things happening on the right side.  Let me explain the black vertical lines and pink cone first.  These are a visualization of cylindrical coordinates on \\(\mathbb{R}^3\\), with the angle thrown away. The horizontal axis corresponds to radius (\\(\sqrt{x^2+y^2+z^2}\\)) and the vertical axis corresponds to height (\\(z\\)), and we have scaled both by a factor of 1/2. The image of \\(\mathbb{R}^3\\) under the map \\((x,y,z) \mapsto (r/2,h/2)\\) is the pink cone. The image of the red sphere is the first black vertical line, and the image of the blue sphere is the second black vertical line.

The second thing happening on the right is an animation of the images of the two spheres under a family of maps that depend on a parameter \\(t\\). We see from the picture that as \\(t\to \infty\\), the images of the two spheres under these maps are converging to the images of the two spheres under cylindrical coordinates.

So why do we care about this?  From the perspective of Poisson geometry, the concentric spheres in \\(\mathbb{R}^3\\) are "symplectic leaves" of a Poisson structure. To put it more simply, each concentric sphere has an area form on it that scales linearly with radius.  Cylindrical coordinates on \\(\mathbb{R}^3\\) are particularly nice because, as Archimedes observed, the area of a region on a sphere bounded by two latitudes only depends on the difference in heights between the two latitudes. In differential geometry terms, in cylindircal coordinates, the area form on a sphere equals
\\[
 dh\wedge dr.
\\]

So cylindrical coordinates are perfectly tailored for describing the areas of concentric spheres in \\(\mathbb{R}^3\\).  Another way to say this, in the language of Poisson geometry, is that cylindrical coordinates on \\(\mathbb{R}^3\\) are action coordinates for the standard Poisson structure (we might also say they are an "integrable system"). 

The animation shows us that 
