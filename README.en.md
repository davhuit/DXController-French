# DXController-French

*[Version française](README.md)*

French-compatible version of [DXController](https://github.com/dsgls/DXController), the
Xbox controller mod for the original *Deus Ex* (2000, GOTY edition).

## The problem this solves

DXController relies on a modified `DeusEx.u`. The official French translation patch ships
its own `DeusEx.frt_u` (Unreal Engine 1's per-language localization mechanism), compiled
from the original, unmodified `DeusEx.u`. The two are incompatible: with both installed,
the game refuses to launch with an error like

```
Ne peut trouver BoolProperty dans le fichier 'BoolProperty DeusEx.DeusExPlayer.bGamepadLBHeld'
```

because the French `DeusEx.frt_u` doesn't know about the extra properties DXController adds
to several classes.

This repo provides a `DeusEx.frt_u` that contains both the French text **and** DXController's
additions, so you can use the gamepad mod together with the official French translation.

## Download

Grab the latest [release](../../releases): it contains the already-built files
(`DeusEx.exe`, `DeusEx.frt_u`, `DeusEx.pdb`, `DXController.u`, `SDL3.dll`), ready to copy
into the game.

## Requirements

- *Deus Ex: Game of the Year Edition* (standard GOG or Steam release)
- [The official French translation patch](https://www.dxm.be/navigator.php5?lang=fr&content=201), installed

## Install

1. Install the game, then the official French translation patch, as usual.
2. Extract the ZIP archive into the game's `System` folder, overwriting the existing files
   of the same name.

## What was changed

9 classes touched by DXController were merged with the French text
(ComputerScreenSecurity, ComputerUIWindow, ConWindowActive, DeusExPlayer, DeusExRootWindow,
Human, MenuScreenLoadGame, MenuSettings, PersonaScreenSkills); see the sources for details.

## Development

See [`development.md`](development.md) for the repo layout and build instructions — setup
follows the original DXController repo (WSL2 + Ubuntu, Nix, `nix run .#sync-and-build`),
paired with a [DeusEx-Buildtools-French](../DeusEx-Buildtools-French) repo holding the game
files needed to build, linked via a `gamedir` symlink.

## Credits

All credit for the gamepad mod goes to
[dsgls/DXController](https://github.com/dsgls/DXController). This repo only adds
compatibility with the French translation on top.

## License

GPLv3+

Files modified from the original game remain copyright Ion Storm and no license claim is
made for them.
