---
layout: post
title:  "The Beginning"
date:   2024-11-07 17:06:28 -0500
categories: dev update
---

Although this is our first post, realistically this game is coming around to the end of the first year of development. Which is a bit of a lie as it is still actively 3 months (nearly a quarter of the year!) until February 17th which officially marks this game's first loop around the sun. 

Although again, this is a bit of a lie as really this game has been at least an idea and occasionally developed throughout the years since _at least_ 2015. It was a bit different than it is now - originally planned to be a top down 2D RPG (still with multiplayer) and was developed in Java supported by the LibGDX framework. Moving to Godot was the best decision for the game I could have possibly made to make this dream come true. 

I will definitely share more of what was originally planned for this game including some of the original game design doc, class designs (which some elements have been able to be carried forward!), and the ideas from those 8 sporadic years developing on the Java application. But for now...


## Where are we right now?

A year in. I must have a starter area, a handful of classes, perhaps a few enemies, and a pretty good start - right? I'd agree with "a pretty good start" but as for the rest - not too much yet.

#### The Entity

So far these past 9 months I have been working diligently on making the very best Entity scene that I can possibly make. I figure that the entity is really the core of the entire gameplay. If it isn't fun to move this character around and use abilities it will not matter how good of a story I can give you, or how expansive the world is to explore. So this needs to be good. 

So far my entity includes:
- a robust ability system with various chaining effects
- some amount of visuals including spell effects and an _amount_ of animation for the character model
(which required taking a animation Blender course earlier this year. Despite now leveraging mixamo for quite a bit!)
- stats, state, inventory, equipment systems

And the best part of this (and which slowed me down the most) is that all of this is networked and can be played on two different instances (a host and client) together! I swear though that the networking has been a huge pain and Godot has done a brilliant job of making it easy but like most software development there are so many different ways to solve a problem and trying to pick a solution that is durable enough to persist and not have to be ripped out and replaced is incredibly difficult. 

Currently to test stuff out I have implemented (partially) the kit of the Warrior, and the Cleric which have some simple kits to start but have been (in my opinion) fun to whack the training dummies with. I will talk more about the classes in another post but to begin, I plan on launching with 6 different classes each with their own identity, abilities, and skill trees. 

Notably missing from the entity right now are the skill trees, and other sort of skills (weapon skills, trade skills), and allegiances. These will come but in terms of data are more complicated to put together. 

#### The User Interface

Along with the entity I've needed a UI for two reasons:

1. It also makes the game fun (or not fun)
2. I need it to be able to have my entity interact with the world (which should be fun)

Learning Godot's control nodes has had a curve but honestly it provides so much that anything that I have needed has been fairly simple to get done. Although unlike the Entity, I do plan on changing the UI _significantly_ once I get more real assets for it so the code has been quicker and dirtier - which by all means is fine. 

I've got my eyes on a particular asset pack that I'm waiting to pick up for when I have more time to pour into the UI. 

### What's Next?

Well _this_ for one - making a site to be able to post to was one of the things I wanted to do next after getting the entity into a decent spot. 

The immediate next two things I plan on working on is:

1. Add "Facilities" to Entities. These would be any sort of entity interaction. It would be the "SpellTrainerFacility" which would allow me to add NPCs that can train you new abilities (useful for testing stuff too). This would be a "ShopKeepFacility" which would be similarly useful to have. I plan on doing these up in a generic way where additional sorts of facilities (LootFacility, PlayerTradeFacility, etc.) could be added easily so that more tools can be added as needed. 

2. Grayboxing an environment. I originally got an the environment that I still use to this day from the same resource that I used to help build my 3D camera which includes some slopes and steps. It has served me absolutely well. But it is about time to add something new to look at. I'm half thinking about Grayboxing an environment and half thinking about actually designing an environment with the asset packs that I have available to use. One reason I'd like to implement perhaps more is so that I would have more complex shapes to bounce lights off of and such to ensure I can achieve an environment style that I want. 

Once these are done, I feel like I'm going to want to start adding more dynamics to the game world (non-entity stuff) and _that_ is going to be another can of worms to handle especially with networking. Just thinking of something like an elevator platform, or a door that could swing open is definitely more challenging once you have to start tracking these items' states. Especially since it really _must_ be generic so that I'm not reimplementing brand new networking for each doodad I place in my world. 

Following these items, I'm looking to start implementing more abilities for each of my 6 classes as I've designed all of my original 6 classes level 1 abilities if not the first few abilities you will get on your way towards level 10. 

### In Closing

There will be more to share soon. And I think you so much for your support and I cannot wait to show you what is brewing next time. 

