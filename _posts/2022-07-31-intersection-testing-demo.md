---
layout: post
title: "Intersection Testing Demo"
date: 2022-07-31 21:00
description: Let's make some game elements to illustration how interection testing works
categories: Game-Development
---

# Intersection Testing

Let's make a game! Well, parts of a game that we can use to illustrate intersection testing in 2 and 3-space. We have an action RPG that has the following elements:

1. A UI element that points to an area of interest on a map
2. A spell pierces a target causing an effect to spawn at point of contact and point of exit
3. A summon that causes a meteor to hit the planet, like you'd see in an RPG maybe

Now that we have our three hypothetical situations, let's break down each one to show where we might use intersection testing to help us implement them. 

## UI Element

Imagine our UI element looks like this,

![UI element over map with arrow pointing to map item](/assets/images/intersection-testing-demo/map.jpg)

The goal here is to find a point `q` on the left edge that's nearest to our point on the map. In the image above we can see this point as the intersection of `st` with the line perpendicular or normal to `st` starting at `p`.

Another way to look at what we're trying to do is we'd like to project our map point onto the edge of the UI widget and see if it's on the line and to the left. We're not going to really cover the "to the left bit". Exercise for the reader? OK, time for math! There's lots of ways to approach this problem, but hopefully this approach will help you build some intuition for the rest of the post. 

To start, we will be using the [dot product](https://en.wikipedia.org/wiki/Dot_product) for this.  

![Equations that define the dot product](/assets/images/intersection-testing-demo/dot-product.jpg)

With the dot product defined, let's look again at the diagram above and see how we can use it to solve our problem. 

Since we don't know theta let's use the algebraic definition of the dot product, and as an aside if you're using a math library of some sort it's more than likely built in. Ok, so our target point `q` is a point from `s` in the direction of `st` of length `l`. So what is the length `l`?

Looking at our first case where `p` is between `s` and `t`, `l` is one of the sides of the right triangle formed by the three points `s`, `p`, and `q`. So if we can find the proportion along the line where the line normal to `st` and `p` intersect we'll have q. This leads us to the dot product as projection. 

![Dot product as projection equations](/assets/images/intersection-testing-demo/projection.jpg)

The above defines the projection equations, but take a moment to think through some things. When is the dot product less than zero? When is the dot product zero? In each case, what would that projection look like? How might we tell when the map point is below `t`? From these equations we can see here that the resultant vector formed from `s` to `q` is a vector that a proportional length of `sp` and `st` in the direction of `st`. So our point `q` is:

![Point q solution](/assets/images/intersection-testing-demo/q-solution.jpg)

The end result of all of this is an UI element that we can make "taller" using a proportional distance from `p` to `q` and will slide up and down the left edge of our widget as we move around our map. Neat! Even better, we've defined the projection equation and have started to build some sense of how it works. 

## Spell Effect

Next up. We have our cool spell that when it impacts with another player we're going to see an effect on the entry and exit points of the collision. Here's the setup to our problem.

![Sphere-ray intersection of player casting line through another player](/assets/images/intersection-testing-demo/sphere-ray-problem.jpg)

We can simplify this problem a bit, by focusing on the 2-D representation of the problem. When in doubt simplify and draw the problem. This helps in modeling scenarios and edge cases. In the UI problem above we had a ray and a map point. We were curious about the point `p` on our UI widget, the intersection point to the line that was normal to `st` and `p`. This is essentially the same problem. All we've done is replaced `p` in our map problem with `c`, the center of the sphere. When we project `c` onto the ray defined by `st` we get an intersection point `p` in this example. If `p` is within the radius of the sphere, we know we have two possible points of intersection (in the pathological case there may only be one point). Looking at the image above, do you see how we might find these points? 

Let's start by using the projection equation to get our point `p`. Once we have `p` we have we need to wrap this up. Imagine a line from the center of the sphere `c` to our first intersection point `s_i`. We can form a right triangle with `p`, `c`, and `s_i`. We know the length of the vector between `s_i` and `c`, it must be `r` as `s_i` lies on the sphere. We know the length of another side of our triangle, `||n||`. Using the Pythagorean Theorem, we can solve for the length of `l`, the length of the vector between `p` and `s_i`. With that length we can start at `p` and move along `st` in the direction of `s` and in the direction of `t` to find our points of intersection. 

![Breakdown of sphere ray intersection and Pythagorean Theorem](/assets/images/intersection-testing-demo/sphere-ray-solution.jpg)

## Meteor!

Alright! We have some nice UI and a cool spell effect, time to summon our meteor. Our last type of intersection testing is sphere-sphere. Checking to see if two spheres intersect is as easy as seeing if the sum of their radii is larger than the length of the vector between their centers. What is slightly more difficult, and the problem we're trying to solve, is what's the circle (all points of intersection) between the two spheres? Do you see why we end up with a circle? 

![Sphere-sphere intersection of two orbital bodies impacting](/assets/images/intersection-testing-demo/sphere-sphere-problem.jpg)

First, what does it mean for two spheres to intersect. If we had the equations of these two sphere's we would be looking for all points where the two equations were equal. Surprisingly, we can solve sphere-sphere intersection with algebra and a bit of geometry. 

Let's start by defining our sphere's geometrically. First, let's assume our sphere's are aligned along the x-axis. This won't change the solution, but it does simplify the problem. 

![Alegabraic walkthough solving of two sphere equations](/assets/images/intersection-testing-demo/sphere-sphere-finding-p.jpg)

So what did we just find? Well, `x` is how from from `c1` we need to go along `c1c2` to find `p`. Awesome! We have `p`, but what's the radius; what's `a`? The radius of the circle is in the yz-plane centered around `x` in our setup of the two spheres being aligned on the x-axis. So, plugging in `x` to our original equation and solving for y<sup>2</sup> + z<sup>2</sup> gives us,

![Alegabraic walkthough finding the radius to the intersection](/assets/images/intersection-testing-demo/sphere-sphere-finding-a.jpg)

So we now have our point `p` and our radius `a`. Finally everything we need to construct our circle. But which way is it oriented? Well, it's "facing" along the vector formed by `c1c2`. If you want to draw this circle. you'll need some vectors orthogonal to `c1c2`. So if this is something you want to do, check out [Gram-Schmidt Orthogonoaliztion](https://en.wikipedia.org/wiki/Gram–Schmidt_process).

## Summary

I hope this was useful for you to see another application of these intersection testing equations. Rather than testing for intersections another way to look at the three example is to view them all as forms of projections. In the first we project a point onto a line. The ray-sphere test is we project our sphere's center onto our ray. If the length of that project is less than the radius of our sphere we got a hit. The points of intersection can be found via the Pythagorean Theorem. In the sphere-sphere intersection we're projecting one sphere onto another and looking the circle of intersection. For me a deeper appreciation for projecting a point onto a line, and projections in general, came from Linear Algebra by Gilbert Strang, specifically chapter 4, [lectures 14-17](https://ocw.mit.edu/courses/18-06-linear-algebra-spring-2010/video_galleries/video-lectures/). Strongly suggested if you've never seen the linear algebra approach to this topic. [3Blue1Brown](https://www.youtube.com/watch?v=LyGKycYT2v0) has a great video on the dot product (suggest the whole linear algebra series) and there's a good [Khan Academy](https://www.youtube.com/watch?v=27vT-NWuw0M) if you're interesting in going deeper into the projection equation. 

If you want to see this in a simple Unreal demo, check out my [GitHub](https://github.com/coderchrismills/UnrealPlayground) repro. There's an Unreal Map "MathDemos", that shows this in action. 

![Screenshot of Unreal intersection tests](/assets/images/intersection-testing-demo/intersections.jpg)
