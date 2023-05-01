---
layout: post
title: "Intersection Testing UI Demo"
date: 2022-10-11 21:00
description: Implementing a small UI widget from a previous post 
categories: Game-Development
---

# Intersection Testing UI Demo

In a [previous post]({% link _posts/2022-07-31-intersection-testing-demo.md %}) on intersection testing I describe a UI widget that would always point to an element on a map. It was a long weekend for Pipeworks (Indigenous People's day here in the U.S.) so I decided to spend some time in Unreal and implement a rough version. Source is available on [Github](https://github.com/coderchrismills/CommonUIPlayground).

![Imaging showing map marker with points marked for intersection](/assets/images/intersection-testing-ui-demo/unreal-map-ui-marker.png)

In the screenshot above we take the mid point of the "map marker" (green box) and project it onto the right side of our "info box", intersecting at point PP (projected point). The way dragging and dropping is implemented in Unreal I found it best to work was with the absolute coordinate values of the "info" view and the "map marker" view. The marker is a a part of the map hierarchy, where as the info box is a completely separate entity in the viewport. 
 
