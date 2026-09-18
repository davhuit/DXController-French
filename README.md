# DXController-French

Version compatible FR de [DXController](https://github.com/dsgls/DXController), le mod
manette Xbox pour *Deus Ex* original (2000, édition GOTY).

## Le problème résolu

DXController s'appuie sur une version modifiée de `DeusEx.u`. Le patch de traduction
française officiel fournit son propre `DeusEx.frt_u` (mécanisme de localisation par langue
d'Unreal Engine 1), compilé à partir du `DeusEx.u` d'origine, non modifié. Les deux sont
incompatibles : avec les deux installés, le jeu refuse de se lancer avec une erreur du type
« Failed to load 'DeusEx.frt_u' » (ou similaire), parce que le `DeusEx.frt_u` français ne
connaît pas les propriétés supplémentaires ajoutées par DXController dans plusieurs classes.

Ce dépôt fournit un `DeusEx.frt_u` qui contient à la fois le texte français **et** les
ajouts de DXController, pour pouvoir utiliser le mod manette et la traduction française
officielle ensemble.

## Prérequis

- *Deus Ex: Game of the Year Edition* — la version GOG ou Steam standard.
- [Le patch de traduction française officiel](https://www.dxm.be/navigator.php5?lang=fr&content=201), installé.
- **Un rendu graphique moderne** — ce n'est pas spécifique à DXController, mais le rendu
  Direct3D d'origine ne fonctionne plus sur le matériel actuel. Voir [Rendu graphique](#rendu-graphique).

## Téléchargement

Récupérez la dernière version depuis la
[page des releases](https://github.com/davhuit/DXController-French/releases).

L'archive `.zip` de la release contient tout ce qu'il faut :

| Fichier             | Ce que c'est                                               |
|---------------------|-------------------------------------------------------------|
| `DeusEx.exe`        | Lanceur avec le pilote manette intégré                        |
| `SDL3.dll`          | Backend manette chargé par le lanceur (SDL3)                  |
| `DXController.u`    | Le mod                                                        |
| `DeusEx.frt_u`      | Fichier de langue français, fusionné avec les ajouts du mod   |

## Captures d'écran

![roue d'armes](/screenshots/weaponwheel.webp)
![écran des réglages manette](/screenshots/controllersettings.webp)
![terminal de sécurité](/screenshots/securityterminal.webp)
![clavier à l'écran](/screenshots/keyboard.webp)

## Installation

1. Installez le jeu, puis le patch de traduction française officiel, comme d'habitude.
2. Copiez tous les fichiers de l'archive .zip de la release dans le dossier `System` du jeu
3. (par exemple `C:\GOG Games\Deus Ex GOTY\System\`), en écrasant les fichiers existants du même nom.
4. Installez un rendu graphique moderne et sélectionnez-le dans le lanceur — voir
   [Rendu graphique](#rendu-graphique).

Si vous avez d'autres mods installés, repartez d'une installation neuve du jeu et
n'installez que DXController-French. La compatibilité avec d'autres mods n'a pas été testée.

## Réglages recommandés

Il est fortement recommandé d'activer « Position constante » dans les
réglages de contrôle.

Dans le jeu, allez dans Réglages → Manette et configurez au minimum la zone morte de votre
manette. Le mod n'applique pas la zone morte volontairement très large utilisée par la
plupart des jeux ; si les sticks de votre manette ne sont pas en parfait état, il faudra
donc l'augmenter. Le même écran propose un réglage de sensibilité du stick droit — à
réduire si tourner à pleine amplitude du stick est trop rapide — ainsi qu'une option
« Inverser l'axe Y de la vue ».

## Sauvegarde automatique

Le mod peut sauvegarder automatiquement pendant la partie. Cette option est désactivée par
défaut ; activez-la et réglez l'intervalle (5 minutes par défaut) dans Réglages →
Sauvegarde auto. Chaque écriture de sauvegarde peut provoquer un bref à-coup.

Le lanceur corrige également un bug du jeu d'origine qui limite le nombre d'emplacements
de sauvegarde à 1000 : au-delà, chaque nouvelle sauvegarde, automatique ou manuelle,
écrase silencieusement le même emplacement et détruit la sauvegarde qui s'y trouvait. Avec
le lanceur actif, les sauvegardes continuent de s'incrémenter normalement.

## Linux et Steam Deck

Le mod fonctionne sous Linux et sur Steam Deck via Proton. Certains utilisateurs ont
signalé devoir régler l'option de compatibilité Proton sur « Proton Experimental ».

## Contrôles

| Bouton          | Action                                |
|-----------------|----------------------------------------|
| Stick gauche    | Déplacement                            |
| Stick droit     | Regarder                               |
| RT              | Tirer                                  |
| LT              | Basculer sur lunette / laser           |
| A               | Sauter                                 |
| B               | Recharger                              |
| X               | Utiliser / interagir                   |
| Y               | Changer de munitions                    |
| LB              | Inventaire / roue d'armes              |
| RB              | Roue d'augmentations                   |
| Back            | Basculer sur inventaire / Menu perso.  |
| Start           | Menu principal                         |
| Clic stick G    | S'accroupir                            |
| Clic stick D    | non assigné                            |
| Croix haut      | Emplacement de ceinture 1              |
| Croix gauche    | Emplacement de ceinture 2              |
| Croix droite    | Emplacement de ceinture 3              |
| Croix bas       | Emplacement de ceinture 4              |

Dans les menus, les conversations et les appareils, la croix directionnelle déplace la
sélection, A confirme et B annule. LB/RB permettent de naviguer entre les onglets dans les
écrans d'inventaire et du prsonnage.

Les infobulles à l'écran indiquent l'action de chaque bouton pour l'élément sélectionné.
Dans l'écran d'inventaire, les actions spécifiques à la manette sont :

| Bouton          | Action                                                                                                    |
|-----------------|-------------------------------------------------------------------------------------------------------------|
| A               | Équiper — ou Utiliser, pour les kits de soin, biocellules et armures/camouflages (Armure balistique, Camouflage thermo-optique, Combinaison HazMat, Rebreather, Lunettes techniques) |
| Y               | Déplacer l'objet — puis croix directionnelle pour positionner, A pour placer, B pour annuler                |
| Clic stick G    | Changer de type de munitions (armes pouvant charger plusieurs types)                                          |
| X               | Assigner l'objet à un emplacement de ceinture                                                                |
| Clic stick D    | Jeter l'objet                                                                                                 |

## Rendu graphique

Il en faut obligatoirement un : le rendu Direct3D d'origine du jeu ne s'initialise plus en
plein écran sur le matériel actuel, et le jeu bascule alors sur le rendu logiciel avec un
écran noir. Les rendus modernes sont aussi plus beaux et plus performants sur les machines
actuelles.

Ceux-ci ont été testés et sont recommandés :

- [Rendu D3D10](https://www.kentie.net/article/d3d10drv/)
- [Rendu D3D11](https://www.kentie.net/article/d3d11drv/)
- [Rendu OpenGL amélioré](https://www.cwdohnal.com/utglr/)

Le rendu D3D10 est meilleur que le D3D11 : choisissez-le sauf raison contraire.

Chacun possède ses propres instructions d'installation. Une fois installé, sélectionnez-le
dans le menu déroulant « Renderer » sous Configure, dans le lanceur.

Note : Ce fichier LisezMoi a été traduit de façon automatique. Il sera probablement retraduit plus tard
manuellement.

## Licence

GPLv3+

Les fichiers modifiés à partir du jeu d'origine sont la propriété d'Ion Storm, et aucune
revendication de licence n'est faite sur eux.

Ce projet utilise une version modifiée de Deus Exe par kentie. Aucune information de licence
n'a été trouvée pour ce dernier, mais le copyright du Deus Exe original appartient à son
auteur original. Mes modifications sont sous licence GPLv3, ou toute licence choisie par
l'auteur original.
