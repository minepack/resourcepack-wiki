---
title: 'Unlocking Packs'
slug: 'unlocking-packs'
description: 'Guide on how to unlock corrupted server resource packs.'
tags:
- pack
---

## Introduction

When a player joins a server with a resource pack, that resource pack is downloaded into `.minecraft/server-resource-packs`. In that folder the pack is stored to avoid re-downloading the same pack multiple times when joining a server. However as a side effect, this means that clients have access to all the files by just renaming the files inside the aforementioned folder to end with .zip and unzipping the pack with any fit software. 

In order to combat that, some servers have begun utilising a trick, to make their resource packs "corrupted" in an attempt to make exploring packs more difficult. This corruption makes regular zipping software unable to unzip the files. (Some resource pack plugins like Oraxen & ItemsAdder do this by default)

One caveat to that is that Minecraft must still be able to read that pack normally in order to display the content.

## Unlocking packs

The trick is to use software that uses Java to unzip files. 

### JD-GUI

One such simple program is called JD-GUI. It is a decompiler for Java programs, but can be used for our purposes as well. Start by downloading the program [on its website](https://java-decompiler.github.io/){ext}.

Once done, head into `server-resource-packs` and find out which resource pack is the one you wish to open. Once you find it, rename it to end with `.jar`. Then, drag the file into opened JD-GUI. You should be met with the following view:

![JD-GUI program window](/guides/unlocking-packs/jdgui.webp)

From there, choose `File -> Save All Sources` and save the contents wherever you want. When done, you have an unlocked zip with all of the files. 🎉