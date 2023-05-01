---
layout: post
title: "Yet Another Boids Post"
date: 2022-08-06 21:00
description: A quick post about what I learned implementing boids after many years
categories: Game-Development
---

# Yet Another Boids Post

It's been a long time since I've implemented [boids](https://en.wikipedia.org/wiki/Boids) and I wouldn't be writing this post if it wasn't for a work prompt from work slack a few weeks ago. 

> Implement flocking behavior in the engine of your choice, and post your source code and/or a video of your results under this thread.
> If you're not sure what flocking is, [https://www.youtube.com/watch?v=mjKINQigAE4](https://www.youtube.com/watch?v=mjKINQigAE4) is pretty good basic tutorial.

Having not written code in awhile this seemed like a nice small and directed thing to do over a weekend. On top of that it would give me a topic to write about and I could use it to learn a bit more Unreal. Side comment about writing. Writing is a great way to help you clarify your thinking and understanding of problems. Even if you don't have a blog or feel like posting anything online, write. In my post about [intersection testing]({% link _posts/2022-07-31-intersection-testing-demo.md %}) there were a few times that I had to stop and rederive something, or check my math. For me these types of post help me verify my understanding of the material. So if you find this topic interesting, go and implement it, then write about it.

If you want to see boids in action and love interactive sites, go check out [Ben Eater's](https://eater.net/boids)[^1], I'm going to reference this page a few times during this post. Play around with the sliders on the page to get a sense of what each parameter does. Afterward, before reading the rest of his article or the rest of this one, think about how you might implement the behavior. 

Boids steer by following three simple rules:

Separation: Steer to avoid local crowding

[![Example of separation with an arrow indicating direction away from neighbor boids](/assets/images/yet-another-boids-post/separation-256.jpg)](/assets/images/yet-another-boids-post/separation.jpg)

Cohesion: Steer towards local average position

[![Example of cohesion with an arrow indicating direction towards average position of neighbor boids](/assets/images/yet-another-boids-post/cohesion-256.jpg)](/assets/images/yet-another-boids-post/cohesion.jpg)

Alignment: Steer towards local facing direction

[![Example of alignment with facing vector of boid aligning towards neighbor boids](/assets/images/yet-another-boids-post/alignment-256.jpg)](/assets/images/yet-another-boids-post/alignment.jpg)

Local here just means an individual boids perception of its flockmates (neighbors), black circle in the images above. Each boid has a radius and angle of perception. In Ben Eater's post, you can see the effect of the radius of perception by changing the visual range. Shrinking the field of view (angle of perception) will also reduce the neighborhood of flockmates. 

For each boid to know who its neighbors are it either needs access to the flock to filter from or is given a list of neighbors that are within some distance metrics and in its field of view, so pre-filtered. 

[![Example of reducing the field of view and the filtering out of neighbors](/assets/images/yet-another-boids-post/field-of-view-256.jpg)](/assets/images/yet-another-boids-post/field-of-view.jpg)

[![Example of increasing the radius of perception to increase the number of neighbors](/assets/images/yet-another-boids-post/radius-of-view-256.jpg)](/assets/images/yet-another-boids-post/radius-of-view.jpg)

Putting this all together,

```
w1 = weight of separation
w2 = weight of cohesion 
w3 = weight of alignment

for each boid in our list of neighbors
    v1 = compute the sum of difference vectors between the boid and each neighbor (separation)
	v2 = find the center of mass of neighbors, compute the vector from boid to that position (cohesion)
	v3 = compute the average facing angle of all neighbors (alignment)
	boid velocity = boid velocity + w1*v1 + w2*v2 + w3*v3
	boid position = boid position + boid velocity
```

Few things that tripped me up when reimplementing this system. First, limiting the amount of force applied each frame can be helpful not only for debugging, but for keeping the system from spinning out of control. Second, which seems obvious in hindsight is how important alignment is. On Ben's page, set coherence to its max value, but set separation and alignment to zero. After the simulation settles set alignment to max too. All the boids should rapidly coalesce into what will look like a single boid. Ok, last thing. Set alignment back to zero. Pretty quickly they'll start to diverge. They won't completely diverge, but there will be a bit more divergence of the flock. All this is without separation being considered. I like to think of alignment as how "chaotic" do I want the system to appear. 

When I was implementing this I had the coefficient of cohesion being used for alignment. On Ben's page put separation at the mid point and cohesion at 0. Then mess around with alignment. When it's at the max you get this really nice follow the leader school of fish. They act a bit odd, trying to keep in perfect alignment, but it's nice. When alignment is at zero it's just chaos. In my system with this bug, I was so focused that there was a problem with the separation code as they seemed to constantly trying to get away from each other. After I verified separation was fine, or at least should be, I then looked at the field of view filtering. This lead me to implementing more debug visualization that ended up being rather helpful throughout the implementation. Though it was nice to have the debug helpers, what I really needed to do was to stop. If I would have paused for a few minutes and thought about how the system was reacting to changes it would have been clear alignment was the culprit. 

Debugging starts with understanding the systems we're working in and how they respond to change. The code I write for work is thought through, mainly because I'm more aware about the time investment. But I have a blind spot for the code I write at home where the value of time is not on my mind. Typically it's the weekend and I'm exploring intellectual curiosities. My good programming practices at work sometimes don't make their way home; they're practices and not habits. 

Welp, that's it. Boids are beautiful. From these three simple steering rules you can get this wonderful and dynamic motion. They're are super approachable and very extendable. They also make a great introduction into steering behaviors and it's just really satisfying when you start to see them move in a perceived orderly fashion. The most complicated math in the whole things is filtering based on the the field of view. If you understand the basics of vector math there's and think this would be fun to implement, check out [kfish's](http://www.kfish.org/boids/pseudocode.html) pseudocode page. There's some fun ways to extend the system such as goal setting and object avoidance. Also, if you want to read the original paper, see [Craig Reynolds'](https://www.red3d.com/cwr/boids/) page. 

*Title comes from the fact that there are already a [number](https://www.google.com/search?q=boids) of pages on the topic*

[^1]: The site is great all around and strongly suggest checking it out
