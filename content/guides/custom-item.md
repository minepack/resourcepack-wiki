---
title: 'Creating custom items'
description: 'Learn how to create your own items with customized textures and models ✨'
slug: 'custom-items'
tags:
- items
---

## Creation

<versions>

--- Vanilla


WIP


--- Oraxen

<info>All of this information is also available on **Oraxens documentation [here](https://docs.oraxen.com/configuration/create-your-first-item){ext}**.</info>

### 2D item

![Lipstick item texture](/guides/custom-item/oraxen/lipstick.webp){style="max-width: 30dvh"}

Let's create a lipstick item. Download the texture [here](/guides/custom-item/oraxen/lipstick.png){download="lipstick.png"}. (Texture made by Discord user danieyas 🙏)


<br/>

Head into `plugins/Oraxen/items` and choose an existing yml file or create a new one with any name. This file will contain your item configurations.

Here's the base Oraxen item configuration:
```yml
lipstick:
  displayname: "<red>Lipstick"
  material: PAPER
```

Drop your texture into `plugins/Oraxen/pack/textures` (you can create any folders within, for example `/textures/myitems` or `/textures/magic`). For this guide, we'll put it into `/textures/myitems`

![myitems folder inside Oraxen/pack/textures](/guides/custom-item/oraxen/myitems_folder.webp)

<br/>
<br/>

Next, modify the above Oraxen item configuration:
```yml
lipstick:
  displayname: <red>Lipstick
  material: PAPER
  Pack:
    generate_model: true
    parent_model: item/generated
    textures:
    - myitems/lipstick.png
```

This adds a new section called `Pack` into your item, which tells Oraxen how to generate your model. 

* The `generate_model: true` is a simple switch to enable generation

* `parent_model: item/generated` dictates the path of the parent model. In this case, it's using Mojang's built-in model, which has some presets for how the model looks in-hand and other places.This is best understood by going into the Minecrafts default resource pack files and looking for the parent files. Best place to do so, is [mcasset.cloud](https://mcasset.cloud/){ext}. For example the `item/generated` is located [here](https://mcasset.cloud/1.20.3/assets/minecraft/models/item){ext} (search for `generated.json`).

* `textures` field declares a list of textures. Some models may require multiple textures (like for example blocks that have different faces, read more [here](https://docs.oraxen.com/configuration/item-appearance#create-a-simple-2d-item){ext}). In our case `item/generated` only needs one texture.

* This is best understood by going into the Minecrafts default resource pack files and looking for the parent files. Best place to do so, is [mcasset.cloud](https://mcasset.cloud/){ext}. For example the `item/generated` is located [here](https://mcasset.cloud/1.20.3/assets/minecraft/models/item){ext} (search for `generated.json`).

🎉 Done! Now just [get your item](#getting-items).

![Lipstick in-game](/guides/custom-item/oraxen/lipstick_ingame.webp)

### 3D item (model)

![Fruit basket page](/guides/custom-item/oraxen/fruit_basket.webp){style="max-width: 10dvh"}

<br/>

For this example we'll use a ready, free [model from MC Models](https://mcmodels.net/model/izzys-fruit-basket/){ext}.\
Download the pack from the website.

<br/>

Models have textures defined inside of them, and in order for the model to work - it must be able to find those textures. From the just downloaded models folder, open `fruit_basket.json`. At the very top, we can see the following:
```json
{
    "credit": "Made with Blockbench",
	"texture_size": [64, 64],
	"textures": {
        "0": "item/fruit_basket_texture",
		"particle": "item/fruit_basket_texture"
	},
...
```

<br/>

As you can see, the default texture for this model is `item/fruit_basket_texture`.\
Let's change it to `myitems/fruit_basket_texture` (notice .png is not specified).\
*Remember to save your changes!*

Now onto importing the files into Oraxen:
* Put `fruit_basket_texture.png` -> `Oraxen/pack/textures/myitems`
* Put `fruit_basket.json` -> `Oraxen/pack/models`

All our assets are in! Now time to use them in an Oraxen item. Once again, head into `Oraxen/items` and find a suitable yml file. Configure the item like so:

```yml
basket:
  displayname: <red>Fruit basket
  material: PAPER
  Pack:
    generate_model: false
    model: fruit_basket.json
```

🎉 Done!  Now just [get your item](#getting-items).

![Basket in-game](/guides/custom-item/oraxen/basket_ingame.webp)

### Extras

Oraxen allows you to configure items to have other advanced properties, such as lore, enchants, furniture and many other things. All these properties and their usage are documented on the [Items (Advanced) page](https://docs.oraxen.com/configuration/items-advanced){ext}.

To further change how an item looks or for details on how to configure items like bows and fishing rods, check out the [Item Appearance page](https://docs.oraxen.com/configuration/item-appearance){ext}.

--- ItemsAdder

WIP

</versions>









## Getting items

<versions>

--- Oraxen

Once any changes have been made, execute the command `/oraxen reload all`. Once resource pack is reloaded and applied, you can find your item in `/oraxen inv` or `/oraxen give [player] [item]`


</versions>