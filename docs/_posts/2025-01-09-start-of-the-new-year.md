---
layout: post
title:  "A New Year"
date:   2025-01-09 09:00:00 -0500
categories: dev update
---

Welcome to 2025!

It's been a busy holiday season this year. Traveling with my wife and enjoying our time with family this past month. It's been _busy_! And looking back at this past month I'm conflicted. In some ways it feels like I haven't made too much progress (which would be fine) but in other ways, I feel like I have actually made some really good progress.

So what's new?

### A New Workflow

Last month I had started experimenting with how to get dynamic elements into the world. Which was mostly a great success through my work on trees and foliage. This was great.

Besides that I had started work on a blender to Godot workflow where I would build a map in blender to then import into Godot. This workflow at this point has totally been revamped. Instead as much as possible will now be created straight from within Godot. 

#### Why?

The first issue that I had was texturing. By doing everything in Blender it removed a lot of power from me to be able to use different color palette that Synty usually offers with their assets and instead forcing me to work with these in Blender. I would have less control of "what I see is what I get" if I wanted to change anything in Godot. This would be slow and _incredibly_ unwieldy even with the object replacement tool I had previously mentioned.

This issue extended itself bigly to terrains where I was able to find a Blender shader which performed de-tiling for my textures and such, none of this would be extended to Godot. 

I needed a new solution.

I found the tool [Terrain3D](https://github.com/TokisanGames/Terrain3D) which seems to capture really what I could imagine that I would want for terrain generation.

![Terrain Building]({{ site.baseurl }}/assets/2025/01/terrain3d_quick.gif)

This reminds me of back in the day trying to use the map editor for Star Wars Empire At War - and similarly reminding me of the struggles of trying to build a map. 

Terrain3D has stuff to help with object instancing with MultiMeshes (which will likely be huge for performance), drawing textures onto the map, and detiling features (besides being a terrain editor at its core).

It's not something I'm great at, but I'm looking forward to spending more time with this _and_ getting better over time to build my world.

#### Assets and Placing Them

The next thing that Blender ironically did handle pretty well was asset placement. I feel like I was getting a hang of placing assets on a grid. Separately I found the Asset Browser setup and usage to be mostly intuitive. 

So much so that a lot of the prior month had been setting up my asset library in Blender to be able to rock and roll. Unfortunately all of that was for moot.

Mostly.

Synty provides its source file assets one-per-file and I found that they had issues sourcing their correct textures on initial import. Luckily, I had previously wrestled with this in order to get all the assets looking right and proper in my Blender libraries. Which all was a great starting point.

![The Jumbled Mess of an Asset Library file]({{ site.baseurl }}/assets/2025/01/fantasy-kingdom_library_props.PNG)

I exported these libraries to my project and wrote a post-import script which would then take apart these files to create my own asset library in Godot. Which with the packs that I have, I have hundreds if not thousands of assets to work with. Which is great in some ways but overwhelming in others. 

Godot ironically now does not have the best ways to view, place, and otherwise manage assets into my scenes. But I found (aptly named) [AssetPlacer](https://cookiebadger.itch.io/assetplacer) by CookieBadger. This did everything I needed, but unfortunately meant I needed to use the Godot mono version. Which is fine considering the power the plugin offers. But I do sure wish an alternative was in default Godot or that the plugin didn't force me into mono. 

![House Building]({{ site.baseurl }}/assets/2025/01/quick_house_build.gif)

The plugin let's me very quickly build prefabs (and otherwise place objects in a scene) which has been useful as I build out my tool set. 

![Already Built House]({{ site.baseurl }}/assets/2025/01/house_usage.gif)

And combining Terrain3D and AssetPlacer ends up allowing me to quickly iterate and develop game areas easily. At this point I can drop non-interactive *or* interactively implemented assets incredibly easily into my scenes. This is the workflow. 

![Scuffed and unplanned environment building]({{ site.baseurl }}/assets/2025/01/quick_env_build.gif)

### A Return to the Entity

Although in the past when I've worked on the entity, it has been all related to underlying supporting data and systems - this is a bit more interesting as it's the model + controllers.

Since the beginning of the new year, invigorated by a sense of getting more things working from and within Godot, I returned to previous work on the character models. 

I'm a bit tired of looking at the plain untextured guy. To resolve this I've simply used some of the prebuilt models Synty had in their Fantasy Kingdom source files

![Character Demo Scene]({{ site.baseurl }}/assets/2025/01/character_sandbox_001.gif)

At this point still have Mixamo animations but am importing the animations as Godot assets, which can easily be reused in other models that are recognized as using the Human bone map. Which I think is going to be huge moving forward. 

Besides generic-ifying the animations, I've also made improvements to the character animation tree which I _hope_ will prevent weird cases from happening (previoulsly I had _3_ Locomotion nodes which would feed the output that I think ended up getting jumbled.)

![WIP but better nonetheless]({{ site.baseurl }}/assets/2025/01/character_animation_tree_001.PNG)

There's a lot more work to do here. My goal is to have my character effectively be an action figure which I will be able to control through another script. "Now I'm going to have them cast a spell!" "Make them look over here!", etc. 

Past that there's other physical issues (which were mentioned in the prior post) of knowing when/how the character should actually fall (and how to _not_ fall off a carpet)

As much as I love the style of the Synty assets, I'm not a huge fan of their characters (why do the men have unibrows?). I've found another asset pack that I do like and are in the correct style low poly style.

A test of whether this work on my characters is generic enough will be whether I can easily incorporate these new models into the game without that much work. 

Lastly, I need to get my characters equipped with gear. Which is a headache to talk about another day. 

### Various Things

Besides these larger items I also have looked into Godot's environment settings some more but I'm still not entirely satisfied with how everything looks. I'm not exactly sure what I need-to/can do (especially since I think it relates to how Godot handles global illumination) but I'll likely spend more time thinking about this as I play the game and see the artifacts more. 

I'd love to share more as I get results that I'm looking for. 

I've also looked into performance (because my game _has_ started showing some need for it), and found some ways to asychronously load scenes which has been great to be able to continue to quickly develop. 

Lastly, I'd really want to spend some time to do proper write ups / tutorials on the technical implementations of some of the content I've been banging my head against (Synty asset importing, Animation Trees, Dynamic Synty Tree Shader) but just haven't found the time to do this yet since I've been developing in earnest. 

I'm still hoping to do these... eventually!

### In Closing

It's been a mixed month - some good things have been locked in but not a ton of progress has been entirely made. 

![Already Built House]({{ site.baseurl }}/assets/2025/01/castle_market_001.PNG)

Next month I hope to show off the new models in-action in-game potentially even with the starting of wielding equipment. 

Especially special, February (17th) will mark the 1 year anniversary of the game's first commit. I'm looking forward to see what else can be done before then and perhaps spending some time to look back at where we were compared to how we are now!
