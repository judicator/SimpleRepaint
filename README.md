# Simple Repaint

Mod for Kerbal Space Program, implementing simple parts repainting.


## How do I repaint parts?

Open PAW menu by right-clicking on part (in VAB/Hangar or in flight), and choose desired color variant ("Part simple repaint"). See screenshot below.
![SimpleRepaint interface](https://i.imgur.com/iOAWoFB.png)


## How does it work?

Each part in the game has one or more 3D-models with materials, shaders and textures tied to them. There is "basic" stock shader (`KSP/Bumped Specular`) that majority of parts use. SimpleRepaint alters `color` modifier for materials with this shader, changing overall part color as a result.

This approach has some advantages:
1. SimpleRepaint is universal. The majority of parts and mods are supported "out of the box" with no additional configs needed.
2. Mod contains no textures at all and has low memory footprint. It does, however, generate tons of MM-patches.
3. Possible colors variants list could be relatively easily edited and supplemented.

There are serious drawbacks though:
1. Only white or mostly white parts will be repainted as expected. If part is not white (let's say, orange fuel tank or grey structural beam), repainting it will not give expected results.
2. Parts, using not "basic" shader, will not be repainted. Obvious example are probe cores, covered with silver or golden foil. Another example are mods, which use their own shaders even for generic materials (so far I found only one such mod: WBI Mk-33).
3. Only color can be altered, not shininess, transparency and such. Also, only colors from predefined list could be used.


## Can Simple Repaint be used together with Textures Unlimited?

Yes. Those parts, that have no TU support, will get SimpleRepaint features.


## What parts/mods are not supported?

1. Various fairings, including stock ones, procedural decoupler shrouds and fairings from SimpleAdjustableFairing mod.
2. Procedural parts from the eponymous mod, and procedural wings.
3. Deployable science parts from Breaking Ground DLC.
4. Deployable work lamps and kerbonauts equipment (EVA Jetpack, EVA Repair Kit, ...).
5. Parts with SSTU Recolor or Textures Unlimited modules, as they already have support for much more powerful repainting mod.


## Is it compatible with part variants?

Yes. However, there is a visual bug: changing part variant resets part color to default. Choosing another color after switching part variant fixes this.


## Dependencies

* [Module manager (4.2.2)](https://forum.kerbalspaceprogram.com/index.php?/topic/50533-*)
* [B9PartSwitch (2.20.0)](https://github.com/blowfishpro/B9PartSwitch)

Both mods are required and are bundled as part of download.


## Installation

1. Make a backup copy of `Colors.cfg` file `GameData/SimpleRepaint` folder inside your Kerbal Space Program folder. It's only needed if you changed and/or added your own colors.
2. Remove mod folder `SimpleRepaint` from `GameData` folder inside your Kerbal Space Program folder before installation.
3. Place the `GameData` folder from downloaded archive inside your Kerbal Space Program folder.
4. Restore `Colors.cfg` file from backup to `GameData/SimpleRepaint` folder (see para. 1).


## Possible colors

You can change possible colors variants in `GameData/SimpleRepaint/Colors.cfg` file. There are maximum 24 color variants available. Please set name to NOT_USED for all unused colors.


## Black and grey lists

1. Some parts do not support B9PartSwitch for some reason. These are added to so-called "grey list", and will (or will not, depending on `UseStockVariantSwitcherForB9PSIncompatibleParts` setting) get repainting via stock PartVariants. It's not as comfortable as B9PS (in my opinion), and also does not support repainting parts in flight. You can find those parts in `GameData/SimpleRepaint/GreyList.cfg` file.
2. Some parts are not supported at all, and for some others SimpleRepaint recoloring does not have much sense: silver or golden foil covered, metallic or dark parts will not get any value from it. Those parts are added to black lists. You can find them in `GameData/SimpleRepaint/IgnoreParts` folder.


## Settings

There are three settings in `GameData/SimpleRepaint/Settings.cfg` config file.

### Repaint in flight

By default you can repaint your vessel parts even in flight scene. If you feel that it's not very realistic, you can disable this feature: just set `RepaintInFlight` value to `false`.

### Using stock part variants switching instead B9PartSwitch

Where are some parts which does not seem to be compatible with B9PartSwitch, and they are added to "grey list". Notable examples are stock (not ReStock!) radial ore drills. Those parts still get repaint ability through stock part variants interface. Set `UseStockVariantSwitcherForB9PSIncompatibleParts` value to `false` if you don't want repaint ability for any B9PS-incompatible parts.

### Repainting only whitelisted parts

By default, all compatible parts (both stock and from mods) will get repainting ability.
If you disable this behavior by setting `RepaintWhitelistedPartsOnly` value to `true`, only specified parts will get color switching. Where are examples of whitelists in `GameData/SimpleRepaint/Whitelists` folder. They should be renamed to `.cfg` files in order to take effect.


## Credits

Many thanks to:
- @Electrocutor for initial Module Manager config file (implementing colors switching via stock PartVariant), which became the basis of this mod. See [this topic](https://forum.kerbalspaceprogram.com/index.php?/topic/173208-partvariant-color-tinting/).
- @Hohmannson for updating @Electrocutor's initial config and adding ReStock-friendly colors, for lots of suggestions and ideas, and extensive testing of SimpleRepaint.


## Licensing

This mod is distributed under a Creative Commons Attribution 4.0 International License ([CC-BY-4.0](https://creativecommons.org/licenses/by/4.0/legalcode)).

You are free to share and adapt the materials for any purpose, when providing appropriate attribution.

Bundled mods are distributed under their own licenses:
* ModuleManager by ialdabaoth, Sarbian and Blowfish is licensed under a "CC share-alike license". More information can be found [here](https://forum.kerbalspaceprogram.com/index.php?/topic/50533-*).
* B9PartSwitch by blowfish is distributed under LGPL v3.0. Details and source are [here](https://github.com/blowfishpro/B9PartSwitch).
