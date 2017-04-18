---
layout: post
title: Unity Animator as a combat state machine
---

During the last year and a half I've been developing a game with a combat style that relies on combos, my main character contains a state machine, every Update cycle I feed the state machine with some input information and it's processed in one of the configured states.

Now and then I had a problem where the character got stuck in its attack, locking every player action, this is definitely unnaceptable, the flow here was something along the lines:

- Player presses attack button.
- Attack button triggers state machine to go to attack state.
- Entering attack state sets Animator's parameter to perform attack animation.
- Attack animation ends and triggers a callback to the character informing that it can proceed to another state.

This seems simple, but when we introduce a combo system with light and strong attack combinations, where multiple inputs may trigger different states that require synchronization with Unity's Animator the flow becomes a bit more complex and difficult to predict and debug.

The gameplay elements described previously are nothing new, they've been around in many fighting games like Tekken, to action games and action RPGs like Devil May Cry, The Witcher, etc, so for sure someone in Unity had already delt with something of this nature.

Fortunatelly for me I there was a recent game that contained mechanics dependent on animations, Firewatch, [and they did a talk](https://www.youtube.com/watch?v=8VgQ5PpTqjc) about how they solved the problem.

After understanding all the reasons behind their solution and rethinking how the state flow could be redone in my game I started to make some modifications, one of the problem of the previous flow was that the character's state machine was triggering a change in Unity's Animator state machine and waiting for a signal to notify that an attack was over.

One major problem here could be that the Animator's state machine couldn't transition to the attack animation, because it wasn't to be done like that by design, so the character's state machine would be stuck eternally, this was an easy problem to solve, the player input could change the Animator's parameters, and in the beggining of the attack a notification would be send to the character's state machine, from a State Machine Behaviour, to transition the character into attack state, and when the attack would end the State Machine Behaviour would trigger the character to transition to another state, that way I avoid getting stuck.

You can find the solution in [this project](https://github.com/TiagoJSM/Arx), since I changed the implementation I never had any bug like the one described before.
