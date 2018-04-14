---
title : "Gamemode sur Solus !"
tags : ["linux", "solus"]
categories : ["linux", "solus"]
---

Ferral Interactive vient de sortir un logiciel libre destiné aux gamers sur Linux. L'outil a pour objectif d'optimiser votre ordinateur sous Linux pour obtenir une meilleure performance pour les jeux. 

Gamemode a été développé en collaboration avec Ikey Doherty, le développeur en chef de la distribution Solus. Il permet pour le moment d'agir sur le CPU governor mais sera compléter par la suite par des plugins et une API. 


Ikey à récemment proposé [un patch qui a été approuvé](https://github.com/FeralInteractive/gamemode/pull/1). Du coup, Ikey a pu packager gamemode pour Solus et les utilisateurs peuvent utiliser ce paquet depuis la synchronisation du dépôt d'hier soir. Sachez qu'il y a aussi un paquet gamemode-32bits pour les jeux nécéssitant des libs en 32bits. Les utilisateurs d'Archlinux trouveront gamemode sur l'AUR.

Donc après avoir installé les deux paquets avec eopkg ou via le Solus Software Center, il faudra lancer votre jeu avec une commande adaptée pour utiliser gamemode avec:

`LD_PRELOAD=/usr/\$LIB/libgamemodeauto.so ./game`

ou pour un jeu steam:

`LD_PRELOAD=$LD_PRELOAD:/usr/\$LIB/libgamemodeauto.so %command%`

Le premier jeu qui utilisera directement gamemode sans avoir recours à la commande plus haut sera _Rise of Tomb Raider_ qui devrait débarquer sur linux dans pas longtemps. On espère qu'il y en aura plein d'autres jeux utilisant cet outil par la suite. Qui a dit que Linux (et surtout Solus) n'était pas un OS de gamers ? 

[Dépôt Github de Gamemode](https://github.com/FeralInteractive/gamemode)



 
