# Virtools Script Deobfuscation

[中文文档](README_ZH.md)

## What's this anyway?

This project is the result of some reverse engineering of Virtools.
It comes as a CK2 plugin.

The CK2 plugin adds the following two building blocks to Virtools:
 - BBDecoder  
 A modifed version of Object Load which tries to reveal editing
 interface for all "hidden scripts".
 - FreeBlock  
 This block does nothing other than helping the reverse engineering
 process. You can add as many bIO/pIO's as you want.

## How does it work?

When you save a composition file with the "hide script representation
in schematic view" option disabled, Virtools will save extra
information together with the script logic. The extra information saved
includes  dimension and placement of building blocks, shape of behavior
links and parameter links etc. It is obvious that these data are vital
to display the script schematic correctly in Virtools.

If a composition file is saved with the previously mentioned option
enabled, scripts will be saved without this information, leaving the
script logic alone. This effectively protects the script from being
copied easily. However such protection is similiar to obfuscated Java
bytecode -- it is possible to produce human-readable script from an
obfuscated one, hence the name "Virtools Script Deobfuscation".

What this plugin does is fairly simple: it adds the information required
to display the script back. That's it!

## Build

0. You need the SDK component of Virtools Dev 3.5 to build this project
1. Put everything in Virtools Dev 3.5\Sdk\Samples\Behaviors\Custom
2. Add Custom.vcxproj to Behaviors.sln
3. Build with VS2017 under Debug mode

## Notice

- The data structures are reverse engineered and tested against Virtools
Dev 3.5. It may not work in other Virtools versions.
- Check for missing DLLs before you decode a script. If a script contain
parameter types unknown to Virtoos, the resulting script might be
unusable.
- Due to a limitation of Virtools, level scripts are currently not
loaded into the scene.
