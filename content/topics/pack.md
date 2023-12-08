---
title: 'Pack'
slug: 'pack'
---

## What is a resource pack?

A resource pack, is a folder filled with assets and files that describe how those assets are displayed in the game.

There are various content types that can be added or edited in resource packs. These include but are not limited to; blocks, sounds, fonts, languages, items, particles, shaders and textures.

## How are resource packs used / applied?

Resource packs can be applied in several ways;
* Manually inserting a resource pack folder into the `resourcepacks` directory within `.minecraft`.
* Bundled with a world, by placing it into the worlds folder as `resources.zip`.
* Sent by a server, using a URL that links to a `.zip` file hosted online. 

## Structure

In the root of a resource pack, there are the following files:
* `pack.mcmeta` - description file, which tells Minecraft about the pack
* `pack.png` - the packs icon shown in resource pack settings (optional)
* `assets` - a folder within which all assets reside (optional)

Minecraft Wiki documents the contents of all of these files in more detail:

[Contents of the pack.mcmeta](https://minecraft.wiki/w/Resource_pack#Contents){ext}<br/>
[Contents of the assets folder](https://minecraft.wiki/w/Resource_pack#Template){ext} **(Important!)**

## Terms

### Namespace
A namespace is a term that is used in computing to identify objects. Within resource packs, it is mainly used to refer to the folder that comes after `assets/<namespace>`. The default namespace is always `minecraft`, which is why in most standard resource packs, you see the folder `assets/minecraft/...` being used. 

Namespaces can have any lower case Latin name. For example, if you are working on a server that has two different gamemodes, which have different assets, you could consider having the following pack structure and namespaces:
```yml
assets
| - minecraft
	| - font
    | - textures
	| - ...
| - gamemode1
	| - textures
	| - ...
| - gamemode2
	| - ...
```

When referring to a namespace in Minecraft, you have to define it before a texture path for example. When playing a sound from outside the `minecraft` namespace, you would use `mynamespace:sound_pathsound_name` where it is needed. Same thing when defining a texture path like `gamemode1:customtextures/blue_ball.png`.