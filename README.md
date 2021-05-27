
# Unreal Tournament 432 Public Headers for Meason


## Overview

This is a Meson subproject tree that allows other Meson
projects to utilize the Unreal Tournament v432 sources
publicly released by Epic as a dependency.

## Quick-Start

### Getting

To add this project to your Meson project as a subproject,
simply use a `ut432.wrap` file inside a `subprojects/`
subdirectory of your project root. Wrap files are
remarkably simple, and in this case three lines suffice.

For instance:

```ini
[wrap-git]
url = https://github.com/Gustavo6046/ut432-headers-meson
revision = head
```

Still, for your convenience, a wrapfile is already provided
as [ut432-headers.wrap][1], which you can even download using
a simple command like:

```sh
curl -osubprojects/ut432-headers.wrap https://github.com/Gustavo6046/ut432-headers-meson/raw/master/ut432-headers.wrap
```

[1]: (ut432-headers.wrap)

### Using

In order to use the Unreal Tournament 432 public headers in
your project, you declare the subproject in your`meson.build`
file and simply extract its dependency accordingly.

Here's an example of a very simple meson.build file that builds
only a single, hypothetical C++ class as a native UnrealScript
class:

```meson  
# Builds MyNativeFoo.so with a native class
# MyNativeFoo.MyFoo

project('MyNativeFoo', 'cpp')

ut432 = subproject('ut432')
ut432_dep = ut432.get_variable('ut432_dep')

shared_library('MyNativeFoo',
    'MyFoo.cpp',
    dependencies: ut432_dep
)
```

## Background

Unreal Tournament was a first-person shooter video game released
in 1999 for personal computers of the era. It quickly became a very big
hit worldwide, what with its fun and varied gameplay, its greatly improved
multiplayer performance, and its higher tolerance to lower-grade hardware
of the era, qualities which fiercely rivaled and even oftentimes surpassed
those of its competitor from id Software, Quake III Arena.

One of the things that set Unreal Tournament apart from other PC games
of the era was its extensibility and ease of modding. Epic Games were generous
with its community back then, providing a full-blown level editor that in fact
came with the game itself. The Unreal Editor allowed all sorts of people, even
those who had little to no experience in actual programming, to dabble into
level design.

The Unreal  Editor was one of the main early reasons that level design as a
trade exists today. This is made clear by the sheer legacy that the Unreal
Engine has in the video game scene; even today, newer iterations of the engine
are still used to create new titles.

However, the engine 's source code has (so far) never been fully released by
Epic Games, unlike most id Software titles, which back then always released the
full source code of their games sometime after each game's release, to extend
the game's lifespan in the hands of the community. Instead, Epic Games
provided a set of **public headers**, which any modder was free to download and
link their C++ code against to use in UnrealScript code, assuming they knew how.
But despite the engine remaining proprietary, Epic did not leave this service
even half-done: they even included documentation on using those public headers!

In that vein, this project aims to facilitate using those same headers in 2021.
It shouldn't be too difficult to do the same for the [v469 update][2] public
headers once _those_ are released by OldUnreal.

[2]: https://github.com/OldUnreal/UnrealTournamentPatches

## Legal Info

Despite their inclusion in this repository, the authors of it, including the
original owner, Gustavo Ramos Rehermann, and any other contributors and/or
users, do not claim any ownership whatsoever over the public header files that
Epic Games, Inc. has *freely* distributed to its community over the course of
Unreal Tournament's ongoing lifespan.

However , files outside the `root/` subdirectory, in particular `meson.build`,
are integral parts of the repository, and licensed under its
terms. See [LICENSE.md][2] for details.

**Note that the [LICENSE.md][2] notice only applies to repository-owned
files, not to files under Epic Games, Inc.'s ownership (`root/`); Epic Games
is granted the full right to request the repository be taken down or otherwise
modified should it not comply with any legal requirements of Epic Games, Inc.'s
discretion.**

Feel free to contact *rehermann6046 AT gmail DOT com* for any inquiries and
notices, and in fact send any modification or takedown request to that email
address, with proof that it was sent by Epic Games, Inc. or a representative
thereof, prior to attempting any litigation. Failure to comply with such a
request may be used as valid court evidence of an actual unalwful infraction
on the part of the project owners.
