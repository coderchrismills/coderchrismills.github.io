---
layout: post
title: "Types of UI in Games"
date: 2022-10-16 21:00
description: Continuing to learn Common UI I go over the four UI types often seen in games
categories: Game-Development
---

While continuing to learn the Unreal UI System I built a small demo illustrating the four main types of UI's found in games. 

![From left to right and example of non-diegetic, spatial, diegetic, and meta UI elements](/assets/images/types-of-ui-in-games/types-of-ui-demo.png)

1. Non-Diegetic
2. Spatial
3. Diegetic
4. Meta

If you're looking for a more in depth description of each, check out [Code Changers](https://codechangers.com/blog/video-game-ui-made-simple-with-case-studies/).

## Non-Diegetic

For an example of non-diegetic UI I chose to implement a classic "health bar" and "energy bar", these specifically were inspired by [Forbidden West](https://www.guerrilla-games.com/games) which I happened to be playing at the time. The goal of this exercise was to learn how to use size boxes and horizontal / vertical boxes. I did't build this in modular way. I wanted to go the quick route, focused more on building it versus building it right. Regardless, there were a few lessons learned.

![Non-diegetic hierarchy in Unreal](/assets/images/types-of-ui-in-games/non-diegetic-hierarchy.png)

**Lesson 1**: Size boxes are great. Not just for overriding the width and height, but specifying desired size combined with aspect ratio makes them, pardon the pun, rather flexible. The majority of UI's I've built over my career have all be based on specific pixel dimensions. The main utility of size boxes so far for me as been blocking out UI elements. Rather than using images. Size box + a Common Border set to Draw As box is a quick way to prototype layout. 

**Lesson 2**: Horizontal box and percentage based fills. Coming from iOS with horizontal and vertical stacks these behaved in a similar manner. If the box is set to fill, then each element will initially be greedy and attempt to fill the space. In each element you can specify a fill value (0-1) that specifies it's preferred area to fill. For example, if you have 3 widgets all set to  1.0 for their fill, each will take 1/3 of the total area. If you set one of them to 0.25, you're saying 0.25 of 0.33. While at first it's not intuitive, once you're used to it's easy to work with. 

**Lesson 3**: My background in laying out UI elements has primarily come from iOS app development and web development. UMG's layout system is rather intuitive if you share a similar background. I found [joyrok's](https://joyrok.com/UMG-Layouts-Tips-and-Tricks) site incredibly useful in the way they break down different widgets and their various tips. 100% worth a read. 

## Spatial 

Spatial and diegetic only differ by the avatar's perceptiveness of the widget. That is, if the avatar would be aware of it in the world. Unreal makes building these kind of UI element trivial. 

![Unreal hierarchy of the spatial UI widget](/assets/images/types-of-ui-in-games/spatial-hierarchy.png)

Since implementing this UI was easy, and there wasn't much to learn from it, I wanted to get it to [billboard](https://www.youtube.com/watch?v=91-89b3wlSo) (see the first minute of this video for an explanation). Implementing this was actually easy and as straightforward as you'd expect. Get the position of the player, get the position of the UI widget, find the look at, set the rotation. 

![Spatial UI billboarding blueprint](/assets/images/types-of-ui-in-games/spatial-billboarding.png)

## Diegetic

I always find diegetic UI interesting. The purpose of UI in games is to convey information in a readily available way. The health bar in a fighting game is prominent to the point you can see it in your periphery while focused on the fight. Diegetic UI however lives in world as is just as much a part of it as the player. So it needs to be clear that it's a "UI" element, but still feel like it belongs in the world. The most recent game I've played that I think did this really well was [Stray](https://stray.game/). The use of wall art and neon signs to guild the player through the world was so well done that after you see the first couple you start to be on the look out for them.

![Unreal hierarchy of the diegetic UI widget](/assets/images/types-of-ui-in-games/diegetic-hierarchy.png)

## Meta

Meta UI's are what you would see in an an old school JRPG when a character is talking to you. While setting up this UI is no different than setting up a non-diegetic UI, it's context is what separates it from non-diegetic. Rather than simply implement another widget in screen space, I thought this would be a good time to learn how to create a render-to-texture in Unreal. 

![Unreal hierarchy of the meta UI widget](/assets/images/types-of-ui-in-games/meta-hierarchy.png)

A render-to-texture needs two things: a camera to do the capture and a target to render the capture to. In Unreal you can set this up by doing the following:

1. A camera that will be used for the capture, in Unreal this would be a SceneCaptureComponent
2. Create a RenderTarget asset
3. Set your SceneCaptureComponent render target to the RenderTarget asset in step 2. 
4. Right click on the RenderTarget and choose "Create Material"

After that you'll have a material that you can use in your UI or anywhere else. 

## Wrapping Up

I hope you found some of this useful and informative. Building  small examples / demos helps reinforce what you know and what you don't know. They're a good way to slow build competency in a given area. Next time you're playing a game see if you can identify these types of UIs.  
