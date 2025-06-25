---
layout: post
title:  "Almost Playable"
date:   2025-06-23 16:30:00 -0500
categories: dev update
---

There's been a lot of great progress since May. I have been formalizing my processes and have actually started scheduling the tasks in hacknplan to my calendar. 

![Actual Project Planning]({{ site.baseurl }}/assets/2025/06/june-calendar.PNG)

More planning has ensured that I stay on task with the important items and that I'm considering all the pieces and the time they'll take to complete. My next big effort is going to be rehauling the UI and it's going to be a bit of an investigative process at first. But as soon as I move past that stage, I'm imagining I'll be repeating this.

Besides what appears in the June calendar - crossing out items from the last update:

- ~~Allegiances and Reputations (how is another entity good, bad, aggressive or otherwise in-game?)~~
- ~~Vending items (and paying for spell training)~~
- ~~Give experience when slaying enemies + Leveling Up~~
- Weapon proficiencies
- Crafting / Gathering systems
- More?

Which is a great start. Although "Weapon proficiencies" and "Crafting / Gathering" are hugely important, they aren't _essential_ (like how earning XP is) and will be returned to later.

## First Off

These two months have had a lot of important work in them - but I think one of the most important was to move to a good animation library. Which because they're good and consistent - the Synty Locomotion Pack was my pick.

<video width="100%" controls preload="none" loop poster="{{ site.baseurl }}/assets/2025/06/movement_demo.jpg">
    <source src="{{ site.baseurl }}/assets/2025/06/movement_demo.webm" type="video/webm">
</video>

The old animations had so much ground sliding, and inconsistencies (diagonal movement, repeat jumps, or jumping up ramps) and some of the new animations in the pack have helped smooth _all_ of this out. Which has just left the models feeling much more complete compared to their half-baked start. 

If you remember from a few devlogs back, I had a _huge_ laundry list of items to still address and I've nearly cut that list in half and addressed some of the most important and primary items that were dragging them down. 

The biggest wishlist items would be weapon clasping, facial movement, and IK leg support. All of which will be challenging and not entirely necessary at this point in time. 

Otherwise I have added transactions for items (and skill training) - 

<video width="100%" controls preload="none" loop poster="{{ site.baseurl }}/assets/2025/06/vending.jpg">
    <source src="{{ site.baseurl }}/assets/2025/06/vending.webm" type="video/webm">
</video>

Which is essential for the game and lays the framework for taking these systems even further. 

## Let There Be Sound!

At first I had light and graphics, and some minimal amount of VFX but now there is also sound. 

<video width="100%" controls preload="none" loop poster="{{ site.baseurl }}/assets/2025/06/warrior_demo.jpg">
    <source src="{{ site.baseurl }}/assets/2025/06/warrior_demo.webm" type="video/webm">
</video>

I've done a game jam and I remember when adding SFX to the game, it felt like it really came together. And I feel like it's nearly a repeat experience here. Once I started adding SFX to any ability _any other_ ability at that point felt so empty if it didn't have SFX.

<video width="100%" controls preload="none" loop poster="{{ site.baseurl }}/assets/2025/06/thief_demo.jpg">
    <source src="{{ site.baseurl }}/assets/2025/06/thief_demo.webm" type="video/webm">
</video>

## Let There Be VFX! (And Improvements to Ability Systems)

Before I had pretty barebones VFX (and honestly it still really is - I'd like to believe each next pass is getting better) and part of this stretch of goals was to "juice the abilities" which warranted improving the visual effects too. 

<video width="100%" controls preload="none" loop poster="{{ site.baseurl }}/assets/2025/06/cleric_demo.jpg">
    <source src="{{ site.baseurl }}/assets/2025/06/cleric_demo.webm" type="video/webm">
</video>

I've gone ahead and implemented the first ability (or more) for the 6 planned classes for the launch of the game. I have: 

- the Warrior: which was the original prototype
- the Cleric: which was also a part of the prototype
- the Cultist: brand new - and fairly designed in paper so far
- the Thief: brand new - and the idea for the design is there. I just need to implement it
- the Mage: brand new - and required a few bits and pieces of new system tech to allow for stacking auras and ability modifications which might be the system that talent trees eventually use too.
- the Scout: brand new - and very undesigned. I don't want to say it might hit the cutting floor, but the floor is right there. I think it'll depend on how the design for the class comes out.

One funny thing is that my damage values and ratios between the various classes are _not_ balanced at all right now. With the cultist dealing tons of additional damage compared to the mage which I feel really has to try to just do a little. But balancing will be for another day.

<video width="100%" controls preload="none" loop poster="{{ site.baseurl }}/assets/2025/06/mage_demo.jpg">
    <source src="{{ site.baseurl }}/assets/2025/06/mage_demo.webm" type="video/webm">
</video>

Also I'll definitely go more in depth with each class and its design later on, but for the time being I've got at least the "Level 1" kit implemented for each - and for some I have a small handful of abilities implemented (which accounts for what I expect to give the players up to level 9 at least).

While working on the abilities I've done a bit of work to generally improve the way that they work. The way that VFX are dispatched to clients has been overhauled (which ironically was some of the oldest work in the codebase for the original proof-of-concept). And separately a good bit of work concerning how casted abilities can have effects that occur as part of that cast.

<video width="100%" controls preload="none" loop poster="{{ site.baseurl }}/assets/2025/06/casting_hands.jpg">
    <source src="{{ site.baseurl }}/assets/2025/06/casting_hands.webm" type="video/webm">
</video>

## Anything Else?

One of the things I wanted to do through this time was re-import _all_ of my synty assets but without any materials applied to them. This way I can control all of my materials and their assignments completely within the Godot editor.

![TBD Texturing]({{ site.baseurl }}/assets/2025/06/untextured-gates.PNG)

This was a good bit of work to do but I think will make the Godot workflow even stronger. I think I've said this before but the more that happens in Godot the better.

I think one of the first things I'm going to do in the immediate future is build out a new `dev_island` which will actually be a properly textured location to test this workflow out. The existing `dev_island` may retire to serve moreso a playground environment - because otherwive I have gotten a lot of mileage out of creating `x_demo.tscn` scenes which serve as demos for individual tasks: Facilities, Combat, Behavior-AI, or Movement. 

With all the tools I've created, I'm getting closer to start building out a real game environment.

## What Next

Like previously mentioned I am going to be next working on revamping the entire UI to be 100% better. More juice, more functionality, more Godot-themey-ness. More. 

I think between the UI and the SFX (and perhaps a small demo environment) it's going to feel like playing a real game. 

Besides the UI, I plan on doing a good bit of improvements on the AI-Behaviors to make them smarter, more interesting, and better game pieces to fight against. Right now they really are the most basic they can be. The enemies will definitely have more to show off and share in the next update.

I've also put some work in making sure the devlogs are easier to load and higher quality than they previously had. I'm imagining this is likely the format I'll take going forward! Perhaps another thing to share eventually! 

<video width="100%" controls preload="none" loop poster="{{ site.baseurl }}/assets/2025/06/killed_by_chickens.jpg">
    <source src="{{ site.baseurl }}/assets/2025/06/killed_by_chickens.webm" type="video/webm">
</video>

This post is a bit early for the July devlog but if we keep up the 2 month cycle on these, I will see you at the end of August or early September!