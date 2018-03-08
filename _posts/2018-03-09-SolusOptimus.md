---
title : "Solus et Optimus"
tags : ["linux", "solus"]
categories : ["linux", "solus"]
---

Sur le portable xiaomi j'ai justement un GPU hybride GPU Intel / NVIDIA. Le hic c'est que sur Solus la gestion des deux avec Optimus n'existe pas (encore). En effet, le Linux Driver Management (LDM) de Solus ne gère pas encore la possibilité de switcher de l'un à l'autre en un clic.

Une alternative existe depuis peu sur github. MarechalLima a cée un [dépôt](https://github.com/MarechalLima/Solus-Optimus-Switch) qui a retenu mon attention. C'est un cript tout simple qui blackliste le driver nvidia pour permettre d'utiliser le driver _nouveau_ plus économe.
Le script permet aussi de revenir sur le driver NVIDIA, par exemple, si vous avez envie de jouer. Sachez que cela nécéssite un reboot de la machine à chaque changement du driver.

 *Pour l'utiliser c'est super simple:

Téléchargez l'archive [ici](https://github.com/MarechalLima/Solus-Optimus-Switch/releases)

Ensuite utilisez la commande `make install` (vous devez avoir le paquet *make* installé).

Cela installera les script gpu-switch et gpu-status.

La commande *gpu-switch* permet de changer de driver, une fenêtre de notification vous indiquera par exemple "nouveau" et de rebooter.

La commande *gpu-status* lance une fenêtre de notification pour indiquer quel driver est en cours d'utilisation.

Utile et pratique en attendant la mise à jour de LDM avec le support d'Optimus.

 
