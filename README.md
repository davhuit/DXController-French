# DXController-French

*[English version](README.en.md)*

Version compatible FR de [DXController](https://github.com/dsgls/DXController), le mod
manette Xbox pour *Deus Ex* original (2000, édition GOTY).

## Le problème résolu

DXController s'appuie sur une version modifiée de `DeusEx.u`. Le patch de traduction
française officiel fournit son propre `DeusEx.frt_u` (mécanisme de localisation par langue
d'Unreal Engine 1), compilé à partir du `DeusEx.u` d'origine, non modifié. Les deux sont
incompatibles : avec les deux installés, le jeu refuse de se lancer avec une erreur du type

```
Ne peut trouver BoolProperty dans le fichier 'BoolProperty DeusEx.DeusExPlayer.bGamepadLBHeld'
```

parce que le `DeusEx.frt_u` français ne connaît pas les propriétés supplémentaires ajoutées
par DXController dans plusieurs classes.

Ce dépôt fournit un `DeusEx.frt_u` qui contient à la fois le texte français **et** les
ajouts de DXController, pour pouvoir utiliser le mod manette et la traduction française
officielle ensemble.

## Téléchargement

Récupérez la dernière [release](../../releases) : elle contient les fichiers déjà
compilés (`DeusEx.frt_u`, `DXController.u`, `DeusEx.frt_u`, `DeusEx.exe`, `SDL3.dll`), prêts à
copier dans le jeu.

## Prérequis

- *Deus Ex: Game of the Year Edition* (version GOG ou Steam standard)
- [Le patch de traduction française officiel](https://www.dxm.be/navigator.php5?lang=fr&content=201), installé

## Installation

1. Installez le jeu, puis le patch de traduction française officiel, comme d'habitude.
2. Extraire l'archive ZIP dans le dossier System du jeu, en écrasant les fichiers existants du même nom.

## Ce qui a été modifié

9 classes touchées par DXController ont été fusionnées avec le texte français
(ComputerScreenSecurity, ComputerUIWindow, ConWindowActive, DeusExPlayer, DeusExRootWindow,
Human, MenuScreenLoadGame, MenuSettings, PersonaScreenSkills) ; voir les sources pour le
détail.

## Développement

Voir [`development.md`](development.md) pour l'organisation du dépôt et les instructions de
build — l'installation reprend celle du dépôt DXController d'origine (WSL2 + Ubuntu, Nix,
`nix run .#sync-and-build`), associée à un dépôt
[DeusEx-Buildtools-French](../DeusEx-Buildtools-French) contenant les fichiers du jeu
nécessaires au build, relié par un lien symbolique `gamedir`.

## Crédits

Tout le mérite du mod manette revient à
[dsgls/DXController](https://github.com/dsgls/DXController). Ce dépôt ne fait qu'ajouter la
compatibilité avec la traduction française par-dessus.

## Licence

GPLv3+

Les fichiers modifiés à partir du jeu d'origine restent la propriété d'Ion Storm et aucune
revendication de licence n'est faite dessus.
