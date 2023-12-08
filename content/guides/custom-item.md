---
title: 'Creating custom items'
description: 'Learn how to create your own custom items.'
slug: 'custom-items'
hidden: true
tags:
- items
---

<versions>

--- Vanilla

.

--- Oraxen

## Introduction

<info>

All of this information is also available on **Oraxens documentation [here](https://docs.oraxen.com/configuration/create-your-first-item){ext}**.

</info>

## 2D item

Let's create a lipstick item. Download the texture [here](/guides/custom-item/lipstick.png){download="lipstick.png"}.

Head into `plugins/Oraxen/items` and choose an existing yml file or create a new one with any name. This file will contain your item configurations.

Here's the base Oraxen item configuration:
```yml
lipstick:
  displayname: "<red>Lipstick"
  material: PAPER
```

Drop your texture into `plugins/Oraxen/pack/textures` (you can create any folders within, for example `/textures/myitems` or `/textures/magic`)

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
* `parent_model: item/generated` dictates the path of the parent model. In this case, it's using Mojang's built-in model, which has some presets for how the model looks in-hand and other places. *
* `textures` field declares a list of textures. Some models may require multiple textures (like for example blocks that have different faces, read more [here](https://docs.oraxen.com/configuration/item-appearance#create-a-simple-2d-item){ext}). In our case `item/generated` only needs one texture.


\* This is best understood by going into the Minecrafts default resource pack files and looking for them. Best place to do so, is [mcasset.cloud](https://mcasset.cloud/){ext}. For example the `item/generated` is located [here](https://mcasset.cloud/1.20.3/assets/minecraft/models/item){ext} (search for `generated.json`).

After that, type `/oraxen reload pack`, which should reload your resource pack. Once resource pack is reloaded and applied, you can find your item in `/oraxen inv` or `/oraxen give [player] [item]`

## 3D item (model)

--- ItemsAdder

</versions>
