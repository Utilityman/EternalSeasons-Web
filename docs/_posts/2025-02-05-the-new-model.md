---
layout: post
title:  "The New Model"
date:   2025-02-05 14:00:00 -0500
categories: dev update
---

(This month we're trying MP4s to share the media, hopefully it works otherwise I'll do a second pass on the assets on this page)

Last month was ironing out the (most likely) 3D environment workflow that I'll be using in the future. And the end of the month being work on the character models and using the Synty characters.

This month was a test of that previous work to see how extendable it really was, and I think it ended up being a good success.

<video width="100%" muted autoplay controls loop>
    <source src="{{ site.baseurl }}/assets/2025/02/entity_playground_test.mp4" type="video/mp4">
</video>

Everything just worked perfectly. Everything basic to the humanoid model handles are put into the `HumanoidModel` and I've got separate `SyntyModel` and `PolytopeModel` extensions of this. 

Whereas the `SyntyModel` is _mostly_ dumb and provides a way to override its materials - the `PolytopeModel` needed a way to handle different equipment, weapons, and male/female body types. All of which, in the end, came together quite nicely.

<video width="100%" muted autoplay controls loop>
    <source src="{{ site.baseurl }}/assets/2025/02/polytope_model_playground.mp4" type="video/mp4">
</video>

One of the main drivers is that I have a `MeshProvider` resource which can be given a mesh and some other properties (for the time being just position/rotational offsets) which then will render its dynamic contents where it needs to. By default the asset pack for the models need no offsets, but weapons and equipment do. 

<video width="100%" muted autoplay controls loop>
    <source src="{{ site.baseurl }}/assets/2025/02/equipment_test.mp4" type="video/mp4">
</video>

For the time being these providers have the power to walk, and given that they're separate resources we can add the power to run later. 

### In Game

This month also came with wiring the model into the game. Previously we just had the model but it had no sense of direction, falling, or acting. But at this point we've reconnected all the normal logic back to the model so that it feels like playing the game again.

<video width="100%" muted autoplay controls loop>
    <source src="{{ site.baseurl }}/assets/2025/02/action_demo.mp4" type="video/mp4">
</video>

I also fixed the problem of "falling" off carpets! (and a few other weird cases)

<video width="100%" muted autoplay controls loop>
    <source src="{{ site.baseurl }}/assets/2025/02/no_carpet_falling.mp4" type="video/mp4">
</video>

I have these armors actually tied to different items in game.

<video width="100%" muted autoplay controls loop>
    <source src="{{ site.baseurl }}/assets/2025/02/equipment_demo.mp4" type="video/mp4">
</video>

I have a way to build NPCs _in the Godot Editor_ quickly - which should be incredibly useful when building out towns/villages.

<video width="100%" muted autoplay controls loop>
    <source src="{{ site.baseurl }}/assets/2025/02/entity_building.mp4" type="video/mp4">
</video>

Lastly, the last-est work of the month was to ensure all of this worked in multiplayer so I haven't left any feature behind.

<video width="100%" muted autoplay controls loop>
    <source src="{{ site.baseurl }}/assets/2025/02/networked_equipment.mp4" type="video/mp4">
</video>

There's still a lot more work to do. Nothing is quite exactly perfect here but I think for the time being I am quite happy with where we've landed. At this point I have the model fairly responsive to the world controls and able to represent what it needs to for now. 

![Far too much to do right now.]({{ site.baseurl }}/assets/2025/02/model_todos.PNG)

If I were to work all of these issues now, I would be perfecting the model for the next few months. And I think most of this will be battles for another day. A good start, with much more to come - eventually.

## What Else?

Besides that, in this month I went about reworking the main menu _again_. But this time I think I've landed on something that is going to be a bit more future proof than the previous implementations. 

<video width="100%" muted autoplay controls loop>
    <source src="{{ site.baseurl }}/assets/2025/02/new_main_menu.mp4" type="video/mp4">
</video>

This is built out using some of the work from the previous month - terrain 3D, Asset Placer, and dynamic scenes in these environments and such. More tooling work proving its worth!

Currently the game simply loads you into the default starter warrior definition as your player that I have hard coded, which is where "continue" is the only option (a light reference to Inscryption's main menu too). 

With the work done this month I think we're going to start working towards actually building out character building as a feature. In any order (but likely this order):

1. Build your own character
2. Save it!
3. Load it!

The dream main menu will have the camera transition between a few different states. 

- The current initial view will be the starting view, still.
- On character creation, shift to a character at a crossroads which will be the location for character creation.
- On character loading, shift to a campsite where all of the saved characters will reside.

Not sure how much of the dream will be built in this next month -- but I'm going to be working towards _part_ of this work in. 

In addition to some of the other recent work, having save data that can persist your character between runtimes, I _personally_ feel like the game is starting to really feel like a game. 

Next month perhaps I will share more of my plans for this first quarter of 2025, but if you've been following the articles in order you may be aware. This month marks the 1 year anniversary of this project! (at least since it's inception in Godot)

## A View of the Past

About a year ago I was working the game development dream of "It'll be done when it's done and that's ok.". I was coding in Java supported by the LibGDX framework - which by all means were super great tools to do plenty of things. But the problem became I don't want to be working on this game "til he's 90". I do want to complete this and working with LibGDX was requiring far too much to be handled by myself. 

<video width="100%" muted autoplay controls loop>
    <source src="{{ site.baseurl }}/assets/2025/02/javaland_demo.mp4" type="video/mp4">
</video>

Looking at this really has me thinking how good Godot has been for this project.

A good framework, but it's not an engine. The thing that finally broke the camel's back was handling networking. Ironically I had to go months prior in the project's commit history to get this video as I had otherwise only a visible plane I was about to START to think about replicating entities onto. 

I began writing an implementation for it but the whole thing -- everything about it -- just really started spiraling in complexity, requirements, and unknowns. Far too much to think about when I'm really just trying to make a game here.

So I looked into how to make a multiplayer Godot game. Oh, and it could be that easy? So I took most of a Godot course on Udemy and went off to the races on my game. 

The first handful of months was trying to recreate the game (with networking!) back to the sort of proof of concept - an ability-based combat system. _A lot_ of the code at this point was actually based on the old Java combat system. _A lot_ also had to change to make the translation for Godot + networking compatability. 

Realistically one thing I wonder if I should have done at this point is try to reimplement this code in C# in Godot. But since I was so fresh, I didn't. This may be an item to work back eventually but for now GDScript does everything I need fairly well.

<video width="100%" muted autoplay controls loop>
    <source src="{{ site.baseurl }}/assets/2025/02/EternallyWorkingOnThis.mp4" type="video/mp4">
</video>

But it worked. And I got _to_ and _past_ where I was in Godot in 6 months or so what I had been working in Java + LibGDX for _years_. 

I certainly wish I could have gotten started in Godot sooner. But at the same time, I feel like as I grew as a developer, I started writing more and more maintainable code. Over the years working on the Java project, I found myself throwing our less and less of old and terrible code. 

I learned, and it helped in ways.

I think at this point, at least from my own perspective, I've come to write better code. Code which will help create a better game in the end. I'm looking forward to comparing what we have right here in this article _today_ to what I'll have in a year from now again.

<video width="100%" muted autoplay controls loop>
    <source src="{{ site.baseurl }}/assets/2025/02/basically_everything_year_one.mp4" type="video/mp4">
</video>