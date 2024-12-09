---
layout: post
title:  "Finally the World"
date:   2024-12-08 09:00:00 -0500
categories: dev update
---

A month gone by, and a lot of progress with it. We started with some more `Entity` work which by all means is not the most glamorous but is some of the most critical for the good gameplay I'm striving for. 

#### Facilities

Like previously mentioned in last month's goals, work was done on entity facilities which will serve as the way that eventually _game objects_ will be able to facilitate various interactions. This will be how dialogue systems are managed, looting, shops, ability training, and more (I'd eventually love to be able to put mini-games into these facilities.)

The first is the `AbilityTrainerFacility`. Which currently just serves a list of abilities that can be taught by a trainer. This is useful for the time being so that I can actually load my characters with their real warrior / cleric class definitions without having to hardcode my abilities into them. 

![Ability Trainer Facility]({{ site.baseurl }}/assets/2024/12/ability_trainer_facility.001.gif)
##### Using the ability trainer facility

The second is the `LootFacility` which will be how the player will loot items from enemies.

![Loot Facility]({{ site.baseurl }}/assets/2024/12/loot_facility.001.gif)
##### Using the Loot Facility

I've implemented this in a way where it's entirely componentized on the entity without any reliance on that entity. I should theoretically be able to slap it onto any game object so that even a humble rock could serve as a `LootFacility` one day. 

#### Player Movement

The other item that I've worked on in terms of the Entity is work improving their physics controller. Notably the entity would get stick on surfaces that, by all means, they shouldn't get stuck on. Such as a simple rug which had _mildly_ elevated edges which the entity would bump and get stuck on. 

Which led me to the stairs problem. 

At this point I've chosen a solution where my entity will be effectively teleported up or down steps as certain raycasts can detect elevated terrain and really this seems like a simple and effective solution that isn't unique to my systems at all. 

![Stair Climbing]({{ site.baseurl }}/assets/2024/12/stair_climbing_jitter.001.gif)

There's still much to do here. I'm having some issues where when colliding with certain specific objects my FPS decreases to PowerPoint speeds. And I'm unsure why that would be happening at all (makes me wonder if I should switch to Jolt physics). 

Separately there's also cases where the player can be caught stuck falling. I'd like to find a good solution for this where perhaps when this case is found that the player controller is given more UMPH to their input directions in a hope that they can be freed. I just (half) worry about the potential exploits that could occur as a result of this if players figure out how to get way more speed than expected out of this.   

And last known related issue is that the player visual just needs some love. It is fairly eager to play the falling/landing animations even in cases where it really shouldn't. 

![Falling off the Rug]({{ site.baseurl }}/assets/2024/12/falling_off_the_rug.001.gif)

And separately (this one is easier but) otherwise the visual model should likely lerp to the physics position so to reduce the amount of jitter when stairs teleporting occurs. 

### Blunders

This month I looked into improving the user interface and had even purchased the Synty Warrior User Interface to help assist with that. 

Unfortunately though, I'm not sure if it's my fault or the pack's - but the pack is advertised as a HUD pack which theoretically is going to be great for tooltips, popups, the world map, and the action bars. But from what I've played with seems difficult to style windows for. 

I think there's just a few things between myself, Godot, and the pack that I still need to figure out but I really unfortunately didn't make too much progress here and any progress I did make I ended up reverting just because things weren't behaving quite like how I'd want. 

I'm definitely going to want to return to the UI and return to trying to figure out how to leverage this asset pack correctly, but for the time being I stepped away from this to work on 

### Something More to See

There were a few options to move forward this month. I could have worked entity behaviors, or making it so that entities would actually drop XP and I could achieve my first level up. But instead I decided to finally take my first step into the world.

So far I had been developing with a single, very simple `dev_island` which included just some ramps and large steps. I could add entities here and was jamming on whatever entity functionality I needed to work on. 

But I needed some improvements across the board.

![New Dev Island]({{ site.baseurl }}/assets/2024/12/new_dev_island.001.PNG)

#### Environment and Day/Night Cycles

The first thing that I worked on was improving Godot's environment settings for my level. I played around with this a great bit and in the end I've really just got some simple tuneups. 

I've enabled SSAO (Screen Space Ambient Occlusion) and SSIL (Screen Space Indirect Lighting), tuned the Glow, and added a bit of volumetric fog which all improve the overall visuals of the scene a great deal. 

![Old Environment]({{ site.baseurl }}/assets/2024/12/default_environment.001.PNG)
![New Environment]({{ site.baseurl }}/assets/2024/12/enhanced_environment.001.PNG)

They're real simple things, but I just think they're neat. (The pictures here admitably not doing the most justice, but is most noticeable in the more nuanced shading of shadows due to indirect/bouncing lights mattering.)

Otherwise here I've added a Day and Night cycle using StayAtHomeDev's [GodotSky](https://stayathomedev.itch.io/godotsky) addon. I did some amount of work trying to figure this out myself, but this guy put in a lot of legwork researching what makes realistic day and night cycles and how the sun influences the colors in the world and such. Stuff that I could rediscover myself, but I feel like there's certain things that I'll take the time to learn and certain other things that I'll gladly take shared knowledge from. 

The results are astonishing and I'm incredibly satisfied with the results. The only thing I'm trying to figure out at this point is how to make the nights less intensely dark. Since the environment is shrouded in realistic darkness you really can't see anything unless there is external illumination. 

![Day and Night]({{ site.baseurl }}/assets/2024/12/day_night_cycle.001.gif)

This is more of a game design decision but I'm wondering how frustrating (or not) it would be for the players if the game does have this realistic night and players need to figure out how to provide their own illumination while exploring during the night. 

This feels more frustrating that practical. I'd love to have "dark dungeons" which I have this cloak of darkness but just not entirely sure what to do about the routine night time global illumination. 

All the still absolutely stoked with the results. 

#### Synty Assets

I love the synty assets, I know that they're a bit recognizable but the thing is that:

- A: It's the exact low-poly style I want for the game (something which I might write more on later)
- B: It would take me a long time to make anything of similar quality

The only problem is that they have prepackages for Unity (and sometimes Unreal) but nothing for Godot. Fortunately they ship the source files, which I've been slowly figuring out how to use so that it takes the least amount of effort to leverage them in the future.

I think it'll be worth writing an entire post just about these in the future but at this point I think I've figured out a pretty decent workflow to use to import the assets, assign materials, and later use those assets in other files. 

I've spent a lot of time this month trying to figure out the best practices here and I'm hoping that come next month I'll have a better environment to show off. 

#### Dynamic Objects

When importing these synty assets, they're all obviously static meshes (or rigs) and in order to breathe life into the game world I wanted to add effects to these objects.

The first candidates were trees, and foliage movement. For the tree, this depended on some of the previous work with the Synty models to properly setup the tree. But past that the work was fairly straight forward. 

I found a shader on godotshaders.com ["Synty Biomes Tree Compatible Shader"](https://godotshaders.com/shader/synty-biomes-tree-compatible-shader/) which I was able to plug in as override materials on tree and everything worked basically exactly right.

I think I'll make a post/video about this entire process at some point because I think it's worth sharing. But I love the results. Plus in my script which controls the shader I've wired some useful properties to control the intensity of the dynamic effect.

![Generic Tree]({{ site.baseurl }}/assets/2024/12/tree_controller.tree_generic_01.001.gif)

I was able to _very very_ simply extend this to affect foliage elements such as grass and bushes as well and have a convincing effect out of it. I'm still curious exactly how I'm going to handle large swathes of grass but for the time being we'll talk about that later. 

<!-- Grass, Ferns, and Grass -->
![Pine Tree]({{ site.baseurl }}/assets/2024/12/tree_controller.tree_pine_01.001.gif)
<p align="middle">
  <img src="{{ site.baseurl }}/assets/2024/12/plant_controller.plant_bush_leaves_03.001.gif" width="364" /> 
  <img src="{{ site.baseurl }}/assets/2024/12/plant_controller.plant_grass_02.001.gif" width="364" /> 
</p>



And secondly was a simple flame visual effect.

This was fairly straight forward as I've worked with the Godot particle effect system before. The proudest thing I can claim on this one is that I handmade the fire particle myself. 

![Flame Particle]({{ site.baseurl }}/assets/2024/12/flame_mesh.001.gif)

Which really isn't that complicated of a mesh at all but seeing the end result when properly wired up with the `GPUParticles3D` ends up looking great. Plus I've add some amount of "flickering" to the light so that the light the fire provides isn't totally static. I figure more movement in the world will make it feel more alive so anything that can move should move.

![Flame Particle]({{ site.baseurl }}/assets/2024/12/prop_camp_brazier_01.001.gif)

I think this _feels_ like it's just about right. I'm still trying to think if there should be more smoke or secondary particles for the embers of the fire.

But all that said super fine for now. 

#### A Dynamic World

My current workflow is to build environments in Blender and then to export the GLB/GLTF to my Godot project and handle it from there. Godot has some import [rules](https://docs.godotengine.org/en/stable/tutorials/assets_pipeline/importing_3d_scenes/node_type_customization.html) which have proven to be useful.

But a problem that I've got is that I want to take the static mesh objects from the GLTF and convert them to be my dynamic Godot versions. To solve this I've created a script which will iterate through the elements of a map to place any of those that have a replacement. 

For the time being the way the script determines what to replace is incredibly simple:

```swift
const TreeGeneric01 = preload("res://implementation/props/tree_generic_01.tscn")
const PropCampBrazier01 = preload("res://implementation/props/prop_camp_brazier_01.tscn")
const TreePine01 = preload("res://implementation/props/tree_pine_01.tscn")
func _get_replacement_scene (node: Node) -> PackedScene:
	if node is not Node3D: return null
	if node.name.to_lower().contains("-no-adapt"): return null
	if node.name.to_lower().contains("tree_generic_01"): return TreeGeneric01
	if node.name.to_lower().contains("tree_pine_01"): return TreePine01
	if node.name.to_lower().contains("prop_camp_brazier_01"): return PropCampBrazier01
	return null
```

Eventually this is definitely going to need to be much more involved but for the time being, this serves its purpose. I'm sure I will have more to write in a future post about the development of this. 

![World Adapter]({{ site.baseurl }}/assets/2024/12/blender_model_adapter.001.gif)

### Continuing on the World

I have a handful of next steps to look at in this next month. Just because of the nature of this time of year, I'm not sure which all/any I'll be able to get to but I'm hoping to be able to share more next month. 

I'm looking to add more dynamic elements:

- Flags (waving proudly in the wind!)
- Signs
- More Lights (candles, chandeliers, more torches, etc.)
- Ropes / Lines (clotheslines, vines, a hanging/swaying birdfeeder)
- Water? ([like this](https://godotshaders.com/shader/toon-style-3d-water-shader-no-textures-needed/), or [this?](https://godotshaders.com/shader/absorption-based-stylized-water/))
- Etc?

And separately I am looking into blocking out levels and creating a better game space to play around in. I've actually started looking into this the past week so I have a _bit_ of a headstart. But between thinking about building prefabs and actually (for once) reducing complexity by paring down - this is something still TBD.

This month will, for the first time ever, likely not have any entity work but I think will yield content that will have me much more excited to show off. 
