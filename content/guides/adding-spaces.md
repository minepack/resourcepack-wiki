---
title: 'Adding spaces'
slug: 'spaces' #Optional
description: 'Learn how to create negative spaces, which can be used to offset text!'
tags:
- fonts
---

<versions>

--- Manual

## Manually

Learn how to manually add spaces into your resource pack.

### Modern versions (1.19+)
Versions after 1.19 introduce a built-in “space” provider, in which you can define which unicodes offset and by how much. 
As specified on the <a href="https://minecraft.wiki/w/Resource_pack#Fonts" target="_blank">Minecraft Wiki</a>, a spaces font provider looks like this:

```json
{
   "type": "space",
   "advances": {
      "\uF001": -4,
      "\uF002": 128
   }
}
```

Here's what that same space provider looks like in a full font file:

```json
{
   "providers":[
      {
         "type": "space",
         "advances": {
            "\uF001": -4,
            "\uF002": 128
         }
      }
   ]
}
```

This allows you to easily create negative or even positive spaces, without the need to add anything external. Inside of the “advances”, 
specify the character which you want to act as a space and define by how much it will shift in *pixels*.

### Older versions (pre 1.19)
Following method utilizes a transparent 256x256 texture that is bound to a unicode with a crazy ascent, which makes it move things.

**1. Set up the texture**

First of all, you need to get the actual negative space texture.<br/>
You can either get it from [AmberWat’s repository](https://github.com/AmberWat/NegativeSpaceFont/tree/master/assets/space/textures/font){target="_blank"} or download the file from here:
[Download texture](/guides/adding-spaces/negative_space.png){download="negative_space.png"}


After you’ve downloaded the texture, put it into your resource packs textures folder into your desired path. For this example, we’ll use `assets/minecraft/textures/custom`

Here it is inside the folder:
![Negative space texture inside the textures/custom folder](/guides/adding-spaces/negative_space_folder.png)

**2. Set up the provider**

Next, we'll navigate to our `default.json` to actually bind this texture to a unicode of our choice:
![default.json](/guides/adding-spaces/font_folder.png)

The provider itself looks like this:
```json
{
   "file": "custom/negative_space.png",
   "ascent":-32768,
   "type": "bitmap",
   "chars":[
      "\uF001"
   ],
   "height":-3
}
```

From the above, you can see that we're assigning the negative_space texture to the character \uF001.
We're also making the ascent really low (it should not be changed).

**3. Done**

After that, you will have the unicode `\uF001` usable anywhere as a negative space symbol, that moves any text
back (to the left) by 1 pixel.

### Changing the offset amount
If you want to increase by how much the symbol shifts to the left or right, change the `"height"` value.

**x** = amount of pixels

Shifting to the left
* **x** must be less than 0, **height = x - 2**
* For example, to offset to the left by -8 pixels, your height would be: **height = -8 - 2 = -10**

Shifting to the right
* **x** must be greater than 0, **height = x - 1**
* For example, to offset to the right by 12 pxiles, your height would be: **height = 12 - 1 = 11**

### Using negative spaces


Used the same way as [any other font provider](/guides/using-fonts). As a bonus, remember that spaces can stack. 
Meaning that if you have a space **A** that offsets -5 to the left and **B** that offsets -10 to the left, 
combining them into **AB** will result in a total of -15 pixel offset. 
(Keep in mind, that there is always a +1 pixel gap between any character, which may actually make that a -14 pixel offset)


--- Plugins

## Using plugins

### Provided offsets
Resource pack plugins provide simple ways to define offsets, most of the time they’re already included and work in the form of placeholders. For example, here are how the popular resource pack plugins do it:

[ItemsAdder Docs](https://itemsadder.devs.beer/plugin-usage/placeholderapi#offsets){target="_blank"}
<br/>
[Oraxen Docs](https://docs.oraxen.com/configuration/glyphs#placeholderapi){target="_blank"}


<warning><b>Important!</b> You are using Vanilla!</warning>

<info>**Important!** This is a guide for ItemsAdder</info>


</versions>