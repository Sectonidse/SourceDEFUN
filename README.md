![sourceDEFUN Concept](https://github.com/user-attachments/assets/7a2a137a-fd81-4cbd-9346-d452e281fa14)
(logo concept art)

**November 5, 2004: Valve releases Source Engine's SDK into public. People started making mods for the bestselling game, Half-Life 2. Years have passed and now we're stuck with Source SDK 2013, being the last publicly released and outdated since release** (based on Orange box's Source SDK, while Portal 2 branch is already finished) **SDK. Strata Source team formed to fix this, tried to be community's hero, but failed, because Valve's Licensing doesn't allow making licensed SDK to be released publicly. *It's time to do something about it.***

> [!NOTE]
> Just saying, I am not trying to demean Strata Source and so sorry if that sounded mean.

**Introducing SourceDEFUN: Based on Alien Swarm SDK, forked off Deferred repo. It promises to be as modern as the SDK's limitations allow it to be.** DEFUN means a function in LISP's programming language, referring to Source Engine's roots: from Quake, to GoldSRC, to Source itself.

Quake >>> GoldSRC >>> Source >> Alien Swarm > Deferred > SourceDEFUN

## Special thanks to...
[maksw2](https://github.com/maksw2) - for being the first contributor and helping with compilation errors!

## Features:
- [x] Deferred lighting (from Alien Swarm Deferred)
- [x] PBR (Physically based Rendering)
- [ ] Ambient Occlusion
- [ ] First Person Camera, ported to Alien Swarm branch

...and probably more soon!

## Requirements for Windows:

You have to use Visual Studio 2022.
To compile the shaders you must install Strawberry Perl, then execute ./materialsystem/swarmshaders/buildshaders.bat

## Information

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
