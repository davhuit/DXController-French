*[Version française](README.md)*

# DXController-French

French-compatible build of [DXController](https://github.com/dsgls/DXController), the
Xbox controller mod for the original *Deus Ex* (2000, GOTY edition).

## The problem this solves

DXController relies on a modified `DeusEx.u`. The official French translation patch ships
its own `DeusEx.frt_u` (Unreal Engine 1's per-language localization mechanism), compiled
from the stock, unmodified `DeusEx.u`. The two are incompatible: with both installed, the
game fails to launch with an error along the lines of

```
Can't find BoolProperty in file 'BoolProperty DeusEx.DeusExPlayer.bGamepadLBHeld'
```

because the French `DeusEx.frt_u` doesn't know about the extra properties DXController adds
to several classes.

This repo provides a `DeusEx.frt_u` that has the French text **and** the DXController
additions, so the controller mod and the official French translation can be used together.

## Download

Grab the latest [release](../../releases): it contains the prebuilt files (`DeusEx.u`,
`DXController.u`, `DeusEx.frt_u`, `DeusEx.exe`, `SDL3.dll`), ready to drop into the game.

## Requirements

- *Deus Ex: Game of the Year Edition* (standard GOG or Steam release)
- [The official French translation patch](https://www.dxm.be/navigator.php5?lang=fr&content=201), installed

## Install

1. Install the game, then the official French translation patch, as usual.
2. Copy the files from the release into the game's `System` folder, overwriting the
   existing files of the same name.

## What's modified

9 classes touched by DXController were merged with the French text (ComputerScreenSecurity,
ComputerUIWindow, ConWindowActive, DeusExPlayer, DeusExRootWindow, Human,
MenuScreenLoadGame, MenuSettings, PersonaScreenSkills) — see the sources for details.

## Development

See [`development.md`](development.md) for the repo layout and build instructions — the
setup mirrors the original DXController repo (WSL2 + Ubuntu, Nix,
`nix run .#sync-and-build`), paired with a
[DeusEx-Buildtools-French](../DeusEx-Buildtools-French) repo holding the game files needed
to build, linked via a `gamedir` symlink.

## Credits

All credit for the controller mod itself goes to
[dsgls/DXController](https://github.com/dsgls/DXController). This repo only adds French
translation compatibility on top.

## License

GPLv3+

Files modified from the original game are copyright Ion Storm and no license claim is made
for them.
