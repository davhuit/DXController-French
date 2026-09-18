# DXController-French

*[English version](README.en.md)*

Version compatible FR de [DXController](https://github.com/dsgls/DXController), le mod
manette Xbox pour *Deus Ex* original (2000, édition GOTY).

## Le problème résolu

DXController s'appuie sur une version modifiée de `DeusEx.u`. Le patch de traduction
française officiel fournit son propre `DeusEx.frt_u` (mécanisme de localisation par langue
d'Unreal Engine 1), compilé à partir du `DeusEx.u` d'origine, non modifié. Les deux sont
incompatibles : avec les deux installés, le jeu refuse de se lancer avec une erreur du type

## Requirements

- *Deus Ex: Game of the Year Edition* — the standard GOG or Steam release.
- **A modern renderer** — not specific to DXController, but the original
  Direct3D renderer no longer works on current hardware. At least not
  on my machine. YMMV. See [Renderer](#renderer).

## Credits

Special thanks to @mkentie for all his contributions to Deus Ex and Unreal
Engine 1 modding. This project would not have been possible without his
[Deus Exe](https://kentie.net/article/dxguide/). I modified it to inject
controller events, handle deadzone and curve mapping, and to patch some
Deus Ex engine bugs I found during development.

Also thanks to @davhuit for getting [the French version working](#french-version)

## Download

Get the latest release from the
[releases page](https://github.com/dsgls/DXController/releases).

The release `.zip` contains everything you need:

| File                | What it is                                             |
|---------------------|--------------------------------------------------------|
| `DeusEx.exe`        | Launcher with the built-in controller driver           |
| `SDL3.dll`          | Controller backend the launcher loads (SDL3)           |
| `DeusEx.u`          | Stock package with small controller hooks added        |
| `DXController.u`    | The mod                                                |

## Screenshots

![weapon wheel](/screenshots/weaponwheel.webp)
![controller settings screen](/screenshots/controllersettings.webp)
![security terminal](/screenshots/securityterminal.webp)
![on-screen keyboard](/screenshots/keyboard.webp)

## Install

1. Copy `DeusEx.exe`, `SDL3.dll`, `DeusEx.u`, and `DXController.u` from
   the release `.zip` into the game's `System` folder (e.g.
   `C:\GOG Games\Deus Ex GOTY\System\`), overwriting the existing
   `DeusEx.exe` and `DeusEx.u`.
2. Install a modern renderer and select it in the launcher — see
   [Renderer](#renderer).

If you have any other mods installed, start with a fresh game install
and install only DXController. Compatibility with other mods has not
been tested.

## Recommended settings

I highly recommend enabling "Toggle Crouch" in the control settings.

In the game, go to Settings -> Controller and configure at least your
controller's deadzone. The mod does not apply the comically large deadzone
used by most games, so if your controller sticks are not in good condition
you will need to increase them. The same screen has a right-stick
sensitivity setting — lower it if turning at full stick deflection is too
fast, and an "Invert look Y-axis" toggle.


## Auto-save

The mod can autosave during play. It is off by default; turn it on and
set the interval (default 5 minutes) in Settings → Autosave. Writing each
save can cause a brief stutter.

The launcher also repairs a bug in the stock game that caps save slots
at 1000: past that point every new save, autosave or manual, silently
overwrites the same slot and destroys the save already there. With the
launcher running, saves keep counting up normally.

## Linux and Steam Deck

The mod works on Linux and the Steam Deck under Proton. Some users have
reported that they needed to set the Proton compatibility option to
"Proton Experimental".

## Controls

| Button         | Action                          |
|----------------|---------------------------------|
| Left stick     | Move                            |
| Right stick    | Look                            |
| RT             | Fire                            |
| LT             | Toggle scope / laser            |
| A              | Jump                            |
| B              | Reload                          |
| X              | Use / interact                  |
| Y              | Change ammo                     |
| LB             | Inventory / weapon wheel        |
| RB             | Augmentation wheel              |
| Back           | Toggle inventory / persona menu |
| Start          | Main menu                       |
| L-stick click  | Crouch                          |
| R-stick click  | unbound                         |
| D-pad up       | Belt slot 1                     |
| D-pad left     | Belt slot 2                     |
| D-pad right    | Belt slot 3                     |
| D-pad down     | Belt slot 4                     |

In menus, conversations, and devices the D-pad moves the selection, A
confirms, and B cancels. LB/RB cycle between tabs in the
inventory and persona screens.

On-screen button hints show what each button does for the selected item.
In the inventory screen the controller-specific actions are:

| Button         | Action                                                       |
|----------------|--------------------------------------------------------------|
| A              | Equip — or Use, for medkits, biocells, and armour/camo (Ballistic Armor, Thermoptic Camo, HazMat Suit, Rebreather, Tech Goggles) |
| Y              | Move item — then D-pad to position, A to place, B to cancel  |
| L-stick click  | Change ammo (weapons that can load more than one ammo type)  |
| X              | Assign item to a belt slot                                   |
| R-stick click  | Drop item                                                    |

## Renderer

You need one of these; the game's own Direct3D renderer no longer
initialises in fullscreen on current hardware, and the game drops to the
software renderer and shows a black screen. Modern renderers also look
better and run better on today's machines.

I have tested these and can recommend them:

- [D3D10 renderer](https://www.kentie.net/article/d3d10drv/)
- [D3D11 renderer](https://www.kentie.net/article/d3d11drv/)
- [enhanced OpenGL renderer](https://www.cwdohnal.com/utglr/)

The D3D10 renderer is better than the D3D11 renderer, so pick it unless
you have a good reason not to.

Each one comes with its own install instructions. After installing, pick
it from the "Renderer" dropdown under Configure in the launcher.

## French version

The game didn't ship a French localization, but there is a mod for it. But
it's not just a localization, it also changes some base-game scripts, so it's
not compatible with DXController. But @davhuit made a merge mod to integrate
the French patch into DXController. [It's available here](https://github.com/davhuit/DXController-French/releases/tag/v1.5.1-fr).
I haven't tested this, if you encounter any bugs using it, please don't report
them here unless you can reproduce them with the base DXController version.

## Advanced configuration

**You do not need to read any of this to use the mod. Ignore it unless
you have a specific need.**

### Extra buttons and analog sources

Controllers with buttons beyond the standard layout — DualSense Edge
paddles, the DualSense/DS4 touchpad click, Switch capture, Series X
share, 8BitDo/Flydigi/HORI back buttons — get bindable slots
automatically: `paddle1`-`paddle4`, `misc1`, and `touchpad` map to
`Joy11`-`Joy16`. Bind them like any other gamepad button, in
`[Extension.InputExt]` in `User.ini`, e.g. `Joy16=Button bFire`.

WARNING: Unlike the rest of the mod, I have **not tested** any of the
features described in this section, because I only have a regular Xbox
One controller. I added this due to user requests, I think it should
work but can't guarantee anything. If you do try it, let me know how
it goes.

Two `DeusEx.ini` sections give finer control, read at launcher startup
and on `GamepadReload` (Settings → Controller triggers a reload after
any change). UE1 ini files have no comment syntax — don't add `;`
comments to these sections.

#### `[DXController.GamepadButtonMap]` — remap or add buttons

```ini
[DXController.GamepadButtonMap]
misc2=UnknownD8
y=Joy16
touchpad=Joy4
guide=None
```

parce que le `DeusEx.frt_u` français ne connaît pas les propriétés supplémentaires ajoutées
par DXController dans plusieurs classes.

Ce dépôt fournit un `DeusEx.frt_u` qui contient à la fois le texte français **et** les
ajouts de DXController, pour pouvoir utiliser le mod manette et la traduction française
officielle ensemble.

#### `[DXController.GamepadAxisMap]` — extra analog sources

Récupérez la dernière [release](../../releases) : elle contient les fichiers déjà
compilés (`DeusEx.frt_u`, `DXController.u`, `DeusEx.frt_u`, `DeusEx.exe`, `SDL3.dll`), prêts à
copier dans le jeu.

## Prérequis

- *Deus Ex: Game of the Year Edition* (version GOG ou Steam standard)
- [Le patch de traduction française officiel](https://www.dxm.be/navigator.php5?lang=fr&content=201), installé

## Installation

1. Installez le jeu, puis le patch de traduction française officiel, comme d'habitude.
2. Extraire l'archive ZIP dans le dossier System du jeu, en écrasant les fichiers existants du même nom.

#### Xbox Elite paddle troubleshooting

9 classes touchées par DXController ont été fusionnées avec le texte français
(ComputerScreenSecurity, ComputerUIWindow, ConWindowActive, DeusExPlayer, DeusExRootWindow,
Human, MenuScreenLoadGame, MenuSettings, PersonaScreenSkills) ; voir les sources pour le
détail.

## Développement

### Unrecognized controllers and SDL3 updates

## Crédits

Tout le mérite du mod manette revient à
[dsgls/DXController](https://github.com/dsgls/DXController). Ce dépôt ne fait qu'ajouter la
compatibilité avec la traduction française par-dessus.

## Development

See [`development.md`](development.md) for the repo layout, build
instructions, and architecture notes.

## LLM usage in this project

An LLM was used to assist in the creation of this mod. I have been programming
for a couple of decades now, and I used that background to make every technical
and design decision in this project. I find the slop generators quite useful
for the menial implementation tasks when I've already prepared a detailed
specification, but they can't be trusted to make any real decisions or
you'll end up with code that nobody understands. I have also personally
done extensive playtesting with the mod. This is not some low-effort vibecoded
project where someone just asked claude to make a thing and called it a day.

It's sad that I have to write this section, but I can't deny that there is
a ridiculous amount of slopware being pushed out these days. These projects
look very professional, but as soon as you try them you find obvious bugs
that make you question whether anyone even tried to use the thing. Well, this
is not one of those projects.

The other reason for writing this is that some people have a strong, visceral
reaction to anything even tangentially related to LLMs. They do not accept
that it is possible to write useful software if an LLM came anywhere near
it, no matter how it was used. I disagree with this, but I respect their
opinion, and much as I would tell a vegan if there were meat in a sandwich,
here I am telling those with inflexible opinions on LLMs that their time
is better spent elsewhere.

## License

GPLv3+

Files modified from the original game are copyright Ion Storm and no
license claim is made for them.

This project uses a modified version of Deus Exe by kentie. I did not
find any license information for it, but copyright of the original
Deus Exe is held by the original author. My modifications are licensed
GPLv3 or any license the original author chooses.

