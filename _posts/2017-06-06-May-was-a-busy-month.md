---
layout: post
title: May was a busy month
---

Unfortunatelly I failed to produce any significant work for May's 1 game a month, but that doesn't mean that I was completely lazy, just busy!

There was a good amount of things that I and some friends have been working on, so here goes a list:

- Developed a city generator alghorithm in Unity3D to generate roads of a city, we followed the pseudo code from [this link](http://www.tmwhere.com/city_generation.html) and applied some modifications, instead of using segments to produce the city we opted to use points, that later will be grouped to generate the roads, we prefered this way because it reduced the mathematical complexity that we were getting in an initial phase when using segments, allowing us to generate the city roads in less than a second, while before we were getting similar results but was taking much longer, unfortunatelly I don't have any benchmarks and the repository is private, but that's not the purpose of this post.

- I continued to work on my C++ engine, polishing the component model and today I added a Box2D physics engine to it, really easy to set up, just took me about 1 hour, after using the physics in Unity3D everything became quite clear and easy to understand how the different components of a physics engine get together in a component based game engine. Box2D documentation is top notch by the way, [here](http://box2d.org/) is the link for the library

- But my biggest achievement during this month was definitely to integrate an online game I'm working on with another team with [Playfab](https://playfab.com/), after experimenting with Unity's matchmaking service we realised that was not going to do it for us, the reason for that is due to the client host model, which could easily lead to cheating and security issues since we would need to leave sensible information on the client about our game. In the beggining we were trying to use [Amazon's gamelift](https://aws.amazon.com/gamelift/), from all the documentation seems like a great service, but what killed it was the lack of SDK for Unity3D in client side, which made Playfab a decisive choice. There's still work in there to be done, but at the moment we can already host a game on Playfab close the server if new players come in and search for matches, the next steps will be to correct the bugs brough by using Unity3D's StartServer instead of StartHost, required by unity's matchmaking service.
