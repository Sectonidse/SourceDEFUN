![SourceDEFUN Logo in 3D](https://github.com/user-attachments/assets/397abd0b-926b-4347-a0a6-16bb58abb661)

Compile status: [![Game](https://github.com/Sectonidse/SourceDEFUN/actions/workflows/compile.yml/badge.svg)](https://github.com/Sectonidse/SourceDEFUN/actions/workflows/compile.yml) [![Shaders](https://github.com/Sectonidse/SourceDEFUN/actions/workflows/shader.yml/badge.svg)](https://github.com/Sectonidse/SourceDEFUN/actions/workflows/shader.yml)

**November 5, 2004: Valve releases Source Engine's SDK into public. People started making mods for the bestselling game, Half-Life 2. Years have passed and now we're stuck with Source SDK 2013, being the last publicly released and outdated since release** (based on Orange box's Source SDK, while Portal 2 branch is already finished) **SDK. Strata Source team formed to fix this, tried to be community's hero, but failed, because Valve's Licensing doesn't allow making licensed SDK to be released publicly. *It's time to do something about it.***

> [!NOTE]
> Just saying, I am not trying to demean Strata Source and so sorry if that sounded mean.

**Introducing SourceDEFUN: Based on Alien Swarm SDK, forked off Deferred repo. It promises to be as modern as the SDK's limitations allow it to be.** DEFUN means a function in LISP's programming language, referring to Source Engine's roots: from Quake, to GoldSRC, to Source itself.

Quake >>> GoldSRC >>> Source >> Alien Swarm > Deferred > SourceDEFUN



## Special thanks to...
[Kristjan Skutta](https://github.com/Biohazard90) - for creating Alien Swarm Deferred!

[maksw2](https://github.com/maksw2) - for being the first contributor and helping with compilation errors!


## Features (sorted by most needed ones):
- [x] Deferred lighting (from Alien Swarm Deferred)
- [x] PBR (Physically based Rendering)
- [ ] Linux Support
  - [ ] DXVK Support (man i wish it was possible to support Vulkan instead of DXVK)
- [ ] First Person Camera, ported to Alien Swarm branch
- [ ] Increased map size (yes it's possible i checked however i'm not sure if that'll work) at the probable cost of decreased precision (won't be visible anyway)
- [ ] Chromium Embedded Framework
  - [ ] Menu
  - [ ] CSS Theme
  - [ ] JS execution
- [ ] Ambient Occlusion
- [ ] Sandboxed Python Support (like VScript!)
- [ ] SourceDEFUN Mod Installer (does moving mod to sourcemods for you and more stuff)

...and probably more soon!

You can watch the progress [here](https://github.com/users/Sectonidse/projects/2/views/1).


## Building

### Windows:
> [!WARNING]
> Even though the solution was upgraded to support VS2022, it will be deprecated soon in favor of CMake.

To compile the shaders you must install Strawberry Perl, then execute ./materialsystem/swarmshaders/buildshaders.bat

### Linux:
Make sure to install these packages through your package manager:

`cmake` `make` `perl` (This is just a wild guess)

**UNFINISHED.**


> [!NOTE]
> macOS won't be supported anymore because there is no reason: if you want to play anyway, just switch to Linux.


## Information

### Cannot do anything?
This might be happening because of my latest ruleset. I don't really know how to set these up, so if you cannot open an issue/pr, the contact me at discussions!

### Legacy README.txt file
*The following new directories are required for the deferred implementation to work:*

`materialsystem/`
`game/client/deferred/`
`game/server/deferred/`
`game/shared/deferred/`

\+ shader compiling:
`dx9sdk/`
`devtools/`

A few changes in standard files have to be made first too.
All of them have comments like this:
`// @Deferred - Biohazard`

*affected files that require updating* (not all changes have a comment since there are too many, use diff):

`game/client/cdll_client_int.cpp`
`game/client/viewrender.h`
`game/client/viewrender.cpp`
`game/client/flashlighteffect.h`
`game/client/flashlighteffect.cpp`
`game/server/gameinterface.cpp`
`public/renderparm.h`



*Most core tweaks and changes can be done in the following headers:*

`materialsystem/swarmshaders/deferred_global_common.h`
`game/client/deferred/deferred_client_common.h`
`game/shared/deferred/deferred_shared_common.h`
`game/server/deferred/deferred_server_common.h`


------------------
## SECRET: Impossible things that would be cool to have
* Mapbase support
* Upgraded VRAD that makes realistic lightmaps
* Native Vulkan (Not DXVK) support
* Material System that can use PNG/JPG instead of VTF
* Independent Texture sizes that doesn't fit into powers of 2
* Subsurface Scattering
* Exporting into a standalone game (this will require leaked Source Engine which shouldn't be used for commercial purposes)
