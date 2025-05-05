---
layout: post
title:  "Systems and More"
date:   2025-02-05 14:00:00 -0500
categories: dev update
---

It's been a second since the last update but it has been _busy_ in real life for the past few months. But with that being said, I've also made a ton of good progress in the past recent weeks. 

Godot 4.4 and then 4.4.1 has been released since my last post. Which is exciting to finally _not_ be on a `.dev` version. It was certainly nice for a handful of the updates but being on a stable version has certainly felt... stable. 

Onto the new features!

### Main Menu + Character Creation

This feature has been done for a while at this point. To me it doesn't even necessarily feel that new anymore. But it certainly is vital for the game.

<video width="100%" muted autoplay controls loop>
    <source src="{{ site.baseurl }}/assets/2025/05/character_creation.mp4" type="video/mp4">
</video>

To start the game you must first create a character which can be any class (though most aren't implemented), with whichever weapon you want, and a specific background. Some of the specifics here are still a work in progress but I'm figuring that each weapon will have unique skills which allows the player to start in almost an entirely unique way for their play style. 

The background system is very barebones for the time being but I think the plan is to eventually have it so that the backgrounds are going to be part of your story in the world and that by picking "Noble" or "Merchant" you'll get different introductions in the world and perhaps even have unique background-based quests.

Characters can later be selected to be able to load into whichever character that you want to progress.

<video width="100%" muted autoplay controls loop>
    <source src="{{ site.baseurl }}/assets/2025/05/character_selection.mp4" type="video/mp4">
</video>

All critically essential features. Plus for my own development purposes this will likely be fun to have my own character(s) to develop and level up as I add even more into the game.

### Dialogue Systems

For a long while I wasn't quite sure exactly how I'd do dialogue in the game. There are a lot of different sorts of systems to draw inspiration from for this. But I think in order to tell the story that I want, something like Larian's choices system made the most sense.

<video width="100%" muted autoplay controls loop>
    <source src="{{ site.baseurl }}/assets/2025/05/doing_dialogue.mp4" type="video/mp4">
</video>

Which ultimately was incredibly easy to implement using the [DialogueManager](https://github.com/nathanhoad/godot_dialogue_manager) addon. At this point I have the ability to setup up basic conversations using my `DialogueFacility` which can make reference to the player and speaker and attributes about them on-the-fly. 

Here's that sample from above. 

```
~ start
{{speaker.info.entity_name}}: [[Hi|Hello|Howdy]] {{player.info.entity_name}}, this is some dialogue.
{{speaker.info.entity_name}}: Why are you talking to me?
- Looked like fun.
	{{player.info.entity_name}}: I thought you looked cool and might have a story to share.
	{{speaker.info.entity_name}}: I'm really not too sure about that. 
- Ability training.
	{{player.info.entity_name}}: I heard you know how to shoot a bow. Can you teach me?
	{{speaker.info.entity_name}}: Indeed I can!
	do facilities[0].interact_with(player, speaker)
	=> END
- Go back to introductions. => start
- End the conversation. => END
{{speaker.info.entity_name}}: Anyways, thanks for dropping by.
=> END
```

The system is implemented in a way that it should be fairly straight forward to add additional speakers, and eventually being able to do camera controls and such from the dialogue. For the time being, the only real extra bit is that you can access other entity facilities from the dialogue.

<video width="100%" muted autoplay controls loop>
    <source src="{{ site.baseurl }}/assets/2025/05/acccess_a_facility.mp4" type="video/mp4">
</video>

### NPC Behavior

Part of the work to bring the world alive is adding NPC behaviors. Which I'm doing using Godot's [beehave](https://github.com/bitbrain/beehave) which I've used before for a game jam and I think ultimately fits exactly what I need.

One of the core things that a NPC needs to be able to do is to move around. 

<video width="100%" muted autoplay controls loop>
    <source src="{{ site.baseurl }}/assets/2025/05/simple_patrolling.mp4" type="video/mp4">
</video>

With these routines I should be able to build a fairly simple area with NPCs that mill around, or move about a prescribed path to bring life to an environment. 

There's still a lot more to work on here - thinking of NPCs who have daily routines and how to facilitate that - but we certainly have a great start towards this. 

The second core aspect of a NPC's behavior would be its ability to do combat. 

<video width="100%" muted autoplay controls loop>
    <source src="{{ site.baseurl }}/assets/2025/05/doing_combat.mp4" type="video/mp4">
</video>

Right now it's fairly basic I have behaviors and routines which will pursue and fight targets, or simply respond to assailants by fighting back. 

It's the perfect first step and eventually I want more complex ability-picking routines as well as better sorts of pathing when in combat to be a bit more than just "move into range and attack".

<video width="100%" muted autoplay controls loop>
    <source src="{{ site.baseurl }}/assets/2025/05/npc_behaviors.mp4" type="video/mp4">
</video>

All of the behavior logic came together incredibly intuitively and should be easy to expand upon in the future.

### New Entity Models

Getting closer to building out a full-blown area to play in, I thought that having _just_ human NPCs maybe wasn't the most interesting and wanted to add more. 

The first thought went to how Runescape introduces you to the world - where you spawn in Lumbridge and have a handful enemies to dispatch - goblins, cows, and chickens. 

I thought that animals would be a great place to start so found an [asset pack](https://www.polyperfect.com/low-poly-animated-animals) from polyperfect which contained a huge slew of animals to use and has been an absolute ease to implement into the game.

<video width="100%" muted autoplay controls loop>
    <source src="{{ site.baseurl }}/assets/2025/05/chicken_model.mp4" type="video/mp4">
</video>

I'm looking forward to implementing a few of these in the next few months so that my world will start being populated by a more diverse set of characters.

### In Closing

I'm making some serious progress on a handful of core systems and features for the game and I think  might be ahead of schedule (perhaps?). With each next new feature I feel more and more tempted to start making an environment that's actually a "complete" playable space. 

<video width="100%" muted autoplay controls loop>
    <source src="{{ site.baseurl }}/assets/2025/05/chicken_combat.mp4" type="video/mp4">
</video>

We're almost there, but just a few more things need to be worked on. 

- Allegiances and Reputations (how is another entity good, bad, aggressive or otherwise in-game?)
- Vending items (and paying for spell training)
- Give experience when slaying enemies + Leveling Up
- Weapon proficiencies
- Crafting / Gathering systems
- More?

I think in the future I'm going to be looking to do these posts every other month rather than every month just to take some of the pressure away - especially as putting these together does take a decent amount of time. 

I'm looking forward to next time to show what the world continues to become!