---
layout: post
title: Action coordinates as a limit of maps
---

Here is an animation I made to spice up seminar talks about my recent joint paper [on integrable systems](https://arxiv.org/abs/1804.01504). The code it was created with is at the end of the post.

![gif]({{ "/images/image_of_orbit_animation1.gif" | absolute_url }})

So what's going on in this picture? 

On the left side we have a picture of two concentric spheres (red and blue) in \\(\mathbb{R}^3\\) (really, they are coadjoint orbits in the dual of the Lie algebra of \\(SU(2)\\), \\(\mathfrak{su}(2)^\*\\)).  

There are two things happening on the right side.  Let me explain the vertical line segments and pink cone **first**.  These are a visualization of cylindrical coordinates on \\(\mathbb{R}^3\\), with the angle \\(\theta\\) thrown away. The horizontal axis corresponds to radius (\\(r = \sqrt{x^2+y^2+z^2}\\)) and the vertical axis corresponds to height (\\(h = z\\)), and we have scaled both by a factor of 1/2 (for reasons that are unimportant here). The image of \\(\mathbb{R}^3\\) under the map \\((x,y,z) \mapsto (r/2,h/2)\\) is the pink cone. The image of the red sphere is the red vertical line, and the image of the blue sphere is the blue vertical line. The image of any other concentric sphere will be a similar vertical line segment.

So why do we care about this?  From the perspective of Poisson geometry, concentric spheres in \\(\mathbb{R}^3\\) are "symplectic leaves" of a Poisson structure (I have only drawn two concentric spheres, but you should try to imagine that there is a sphere for every radius, like layers in an onion). To describe this structure more simply, each concentric sphere has a measure of area on it that scales linearly with radius and is rotationally invariant.  

Cylindrical coordinates on \\(\mathbb{R}^3\\) are particularly nice because, as Archimedes observed, the area of a region on a sphere bounded by two latitudes only depends on the difference in heights between the two latitudes. This is illustrated in the following picture [from wolfram mathworld](http://mathworld.wolfram.com/ArchimedesHat-BoxTheorem.html), where the two surface areas \\(S_1\\) and \\(S_2\\) are equal.

![archimedes]({{ "/images/archimedes.gif" | absolute_url }})

In differential geometry terms, in cylindircal coordinates, the area form on a sphere equals
\\[
 dh\wedge d\theta.
\\]

So cylindrical coordinates are perfectly tailored for describing the areas of concentric spheres in \\(\mathbb{R}^3\\).  The way to say this in the language of Poisson geometry is that cylindrical coordinates are *action coordinates* for the Poisson structure (action coordinates are a particularly well-behaved type of *integrable system*). 

The **second** thing happening on the right is an animation of the images of the two spheres under a family of maps that depend on a parameter \\(t\\). We see from the picture that as \\(t\to \infty\\), the images of the two spheres under these maps are converging to the images of the two spheres under cylindrical coordinates. Near the equator, this convergence is very fast, but as you go towards the two poles, the convergence rate slows down exponentially (the image of every point except the poles does converge eventually).

Ok, so we are convinced that cylindrical coordinates are nice, and we have recovered cylindrical coordinates as a limit of some family of maps. Why should we care about this? 

Well, the Poisson structure on \\(\mathbb{R}^3\\) is the simplest example of a linear Poisson structure on a vector space (we call these *Poisson vector spaces*). Poisson vector spaces are simultaneously one of the simplest families of Poisson structures (they are linear), but they are also quite beautiful and complicated. Linear Poisson structures correspond to  Lie algebras, their symplectic leaves are interesting topologically, and their geometry is related to representation theory through Kirillov's orbit method. Our motivation is the following problem:

**Problem:** Find coordinates analogous to cylindrical coordinates (i.e. action coordinates) on all Poisson vector spaces.

It turns out this problem is quite difficult and is unsolved for all Poisson vector spaces except a small family (those corresponding to compact Lie groups of type A,B, or D). On this family, a set of action coordinates called *Gelfand-Zeitlin systems* were discovered by [Guillemin and Sternberg in the early 1980's](https://www.sciencedirect.com/science/article/pii/0022123683900927).  Since then, no one has found a way to generalize Gelfand-Zeitlin systems to Poisson vector spaces corresponding to other Lie algebras\*.

The main result of our paper is that a family of maps \\({\rm gw}\_t\\) coming from Poisson geometry (called *Ginzburg-Weinstein* maps) have the following property:

**Theorem:** As \\(t\to\infty\\), the maps \\({\rm gw}\_t\\) converge to Gelfand-Zeitlin systems (on the family of Poisson vector spaces corresponding to type A). 

The family of maps \\({\rm gw}\_t\\) is defined more generally (for all compact simple Lie algebras). We hope we can prove a more general version of this convergence result and thus generalize Gelfand-Zeitlin systems.

\* It should be mentioned that Megumi Harada did find a system that extends Gelfand-Zeitlin to type C. 

## Code

For people more interested in the animation than the math, here is the python code to create it yourself (you will need to install imagemagick).

```
import math
import numpy as np
import matplotlib
import matplotlib.pyplot as plt
import matplotlib.animation as animation
from matplotlib import patches


fig, ax = plt.subplots(1,2,figsize = (12,6))

fig.suptitle("Action coordinates as a tropical limit of Ginzburg-Weinstein diffeomorphisms",fontsize=20)

# ax[0]

ax[0].axis('off')

ax[0].set_xlim(-2,2)
ax[0].set_ylim(-2,2)

su2 = ax[0].text(0.05, 0.05, r'$\mathfrak{su}(2)^* $' ,  
                 transform=ax[0].transAxes, fontsize=15)

# outer orbit
circle1 = plt.Circle((0, 0), 1.5, color='b', fill=False, linewidth=1.5)
ax[0].add_artist(circle1)

ellipse1 = patches.Ellipse((0, 0), 3, 0.4,
                           angle=0, linewidth=1, fill=False, 
                           zorder=2, color = 'b',linestyle='--')
ax[0].add_patch(ellipse1)

# inner orbit
circle2 = plt.Circle((0, 0), 1, color='r', fill=False, linewidth=1.5)
ax[0].add_artist(circle2)

ellipse2 = patches.Ellipse((0, 0), 2, 0.2,
                           angle=0, linewidth=1, fill=False, 
                           zorder=2, color = 'r',linestyle='--')
ax[0].add_patch(ellipse2)

# ax[1]

# labels, ticks, arrows
ax[1].set_xlim(-0.5,1.5)
ax[1].set_ylim(-2,2)

ax[1].spines['top'].set_visible(False)
ax[1].spines['right'].set_visible(False)

ax[1].set_xlabel(r'$\zeta_1^2$',fontsize=15)
ax[1].set_ylabel(r'$\zeta_1^1$',fontsize=15,rotation=0)

ax[1].xaxis.set_label_coords(.95, -0.05)
ax[1].yaxis.set_label_coords(-0.06, .95)

plt.sca(ax[1])
plt.xticks([1],[r'$r/2$'],fontsize=15)
plt.yticks([-1,1],[r'$-r/2$',r'$r/2$'],fontsize=15)

ax[1].arrow(1.4,-2,.1,0,fc='k', ec='k', lw = .15, 
             head_width=.08, head_length=.12, overhang = .1, 
             length_includes_head= True, clip_on = False)
ax[1].arrow(-.5,1.9,0,.1,fc='k', ec='k', lw = .15, 
             head_width=.08*.5, head_length=2*.12, overhang = .1, 
             length_includes_head= True, clip_on = False)

# equations
time_text = ax[1].text(0.06, 0.95, 't = 1', 
                       transform=ax[1].transAxes, fontsize=15)
eq1 = ax[1].text(0.06, 
                 0.85, 
                 r'$\zeta_1^2\geq \zeta_1^1\geq -\zeta_1^2 $' , 
                 transform=ax[1].transAxes, 
                 fontsize=15)

eq2 = ax[1].text(0.06, 
                 0.15, 
                 r'$\zeta_1^1 = \frac{h}{2}$', 
                 transform=ax[1].transAxes, 
                 fontsize=15)
eq3 = ax[1].text(0.06, 
                 0.05, 
                 r'$\zeta_1^2 = \frac{1}{2t}\ln(2\cosh(tr)-2\cosh(th))$' , 
                 transform=ax[1].transAxes, fontsize=15)

# draw the cone
t = np.linspace(0,1.5,100)
lower_bound = -t
upper_bound = t
ax[1].fill_between(t, lower_bound, upper_bound, 
                   facecolor='pink', alpha=0.5)

# draw the fiber of hw
ax[1].plot([1, 1], [1, -1], 'k-', lw=1.5,color = 'b')
ax[1].plot([.75, .75], [.75, -.75], 'k-', lw=1.5,color = 'r')

# the curve to be animated
line1, = ax[1].plot([], [], lw=1.5,color = 'b')
line2, = ax[1].plot([], [], lw=1.5,color = 'r')
lines = [line1,line2]

# add the blue arrow from left to right 
ax0tr = ax[0].transData # Axis 0 -> Display
ax1tr = ax[1].transData # Axis 1 -> Display
figtr = fig.transFigure.inverted() # Display -> Figure
# 2. Transform arrow start point from axis 0
ptB = figtr.transform(ax0tr.transform((1.7, 0)))
# 3. Transform arrow end point from axis 1 
ptE = figtr.transform(ax1tr.transform((-.6, 0)))
# 4. Create the patch
arrow = matplotlib.patches.FancyArrowPatch(
    ptB, ptE, transform=fig.transFigure,  
    fc = "b", connectionstyle="arc3,rad=0.", 
    arrowstyle='simple', alpha = 0.5,
    mutation_scale = 20.
)
# 5. Add patch to list of objects to draw onto the figure
fig.patches.append(arrow)

def init():
    y1 = np.linspace(-1, 1, 10000)
    x1 = np.log(2*np.cosh(1*2) - 2*np.cosh(1*2*y1))/(2*1)
    y2 = np.linspace(-.75, .75, 10000)
    x2 = np.log(2*np.cosh(1*1.5) - 2*np.cosh(1*2*y2))/(2*1)
    lines[0].set_data(x1, y1)
    lines[1].set_data(x2, y2)
    return tuple(lines)

def animate(i):
    s = 1+i/100
    y1 = np.linspace(-1, 1, 100000)
    x1 = np.log(2*np.cosh(s*2) - 2*np.cosh(s*2*y1))/(2*s)
    y2 = np.linspace(-.75, .75, 50000)
    x2 = np.log(2*np.cosh(s*1.5) - 2*np.cosh(s*2*y2))/(2*s)
    lines[0].set_data(x1, y1)
    lines[1].set_data(x2, y2)
    time_text.set_text('t = %.1f' % s)
    return tuple(lines)

anim = animation.FuncAnimation(fig, animate, init_func=init, 
                               frames=200, interval=20, 
                               blit=True,repeat=True)

anim.save('image_of_orbit_animation.gif', 
          dpi=80, writer='imagemagick')

plt.show()
```
