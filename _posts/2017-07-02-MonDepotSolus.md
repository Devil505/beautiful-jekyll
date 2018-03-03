---
title : "Mon Dépôt pour Solus"
date : "2017-07-02T13:19:00+01:00"
draft : false
thumbnail : "img/solus.jpg"
toc : true # Optional
tags : ["linux", "solus"]
categories : ["linux", "solus"]
---


Après avoir packager luminance HDR pour solus, je me suis essayé à d'autres paquets.

J'ai packagé [gem](https://gem.tuxfamily.org/), l'application graphique de gestion d'émulateurs de consoles et de roms conçue par [Pacmiam](https://pacmiam.tuxfamily.org/). J'ai fait [une demande de paquet](https://dev.solus-project.com/T3875) pour mais elle est toujours en attente.

Comme j'utilise le service de stockage en ligne de Mega avec ses 50Go gratuit, j'ai besoin de Megasync pour synchroniser mon dossier sur PC avec le cloud. Beaucoup ont essayé de demander le rajout du client megasync au dépôt officiel de solus mais pour certaines raisons, les demandes ont été rejetées.

Du coup, j'ai quand même tenter de le packager et, bingo, il fonctionne et même très bien.

Pourquoi ne pas proposer ces paquets ? C'est justement l'objectif de ce billet. J'ai récemment crée un dépôt sur github pour heberger les recettes de construction (package.yml) de ces paquets et j’héberge directement les paquets _eopkg_ sur un compte dropbox. Vous pouvez télécharger ces derniers et les installer avec la commande **sudo eopkg it _paquet_.eopkg**


Si vous utilisez solus, pensez à faire un tour ici: <https://github.com/Devil505/solus-3rd-party-repo>
