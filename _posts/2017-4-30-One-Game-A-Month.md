---
layout: post
title: 1 Game a month! - April - Tank shooter
---

The objective of this month was to add texture support to the engine and improve user input.

I was able to achieve these, but unfortunately I wasn't able to add a UI to the game and create a deformable terrain in the same style of worms, as I wanted, so I guess these will be my objectives for May's project.

One of the biggest challenge of this month was to find a good way to manage my graphical resources, and make sure that I could adapt the solution for other resources to make resource release easier in the long run. The solution I adopted was to create a manager singleton for the graphical resources and everytime that I need to a resource the manager will know how to load it and make sure only a single instance of each resource is loaded, avoiding duplication of textures, shaders, meshes and so on.

To aid my previous solution I created a generic ManagedResource class that works in the same style as a SharedPtr, it contains a reference counter provided by the manager that creates the resource and when the reference counter reaches 0 the resource is deleted, this helps me to avoid resource duplication and memory leaks, it's still experimental, but in this month's game I didn't run into any trouble for now.

I also improved the rendering layer and added new utilitary functions for math and camera.

Here is the tag for the project [Tag](https://gitlab.com/TiagoJSM/SimpleEngine/tags/Tank-Shooter-April%2F2017)
