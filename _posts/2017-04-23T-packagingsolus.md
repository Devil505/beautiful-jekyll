---
title : "Packaging pour Solus"
date : "2017-04-23T16:25:46+02:00"
draft : false
thumbnail : "img/solus.jpg"
toc : true # Optional
tags : ["linux", "solus"]
categories : ["linux", "solus"]
---

Il me manquait un paquet chez Solus, le logiciel de traitement d'image HDR, luminance_hdr. Je me suis donc laissé tenter par le packaging. Tout d'abord il y a un guide pas trop mal [sur le site officiel](https://solus-project.com/articles/packaging/).

Petite démo...

Tout d'abord il faut créer un dossier caché **.solus** dans le home. Dedans, créez un fichier **packager** qui va contenir vos infos de packageur:

```
[Packager]
Name=Your Name Here
Email=your.email@address
```
Ensuite, il faut installer les outils nécéssaires pour packager

```
sudo eopkg it -c system.devel
sudo eopkg it solbuild
sudo solbuild init
```

Vous verrez par la suite que solbuild est un outil assez puissant.

Après, créez un dossier de travail, par exemple, **packages_solus**.
Une fois dedans, il y a aussi un clonage d'un dépôt git à faire:

```
sudo eopkg it git
git clone https://git.solus-project.com/common
```

Enfin, un petite série de symlinks à effectuer:

```
ln -sv common/Makefile.common .
ln -sv common/Makefile.toplevel Makefile
ln -sv common/Makefile.iso .
```

Les choses sérieuses commencent, créez un dossier du nom de votre paquet, moi j'ai pris luminance_hdr et dedans j'ai fais cette commande

```
echo "include ../Makefile.common" > Makefile
```

Après il faut créez un fichier **package.yml** et bien le renseigner. Voyez le mien:

```
name       : luminance_hdr
version    : 2.5.0
release    : 1
source     :
    - http://sourceforge.net/projects/qtpfsgui/files/luminance/2.5.0/luminance-hdr-2.5.0.tar.bz2 : f5caf3316d1763058b1b0f2a6963df34465fbf918b7abeee5245a51fc14a7942
license    : GPL-2.0
component  : multimedia.graphics
summary    : a complete opensource solution for HDR photography
description: |
    Open source graphical user interface application that aims to provide a workflow for HDR imaging.
builddeps  :
    - pkgconfig(exiv2)
    - libtiff-devel
    - libpng-devel
    - libjpeg-turbo-devel
    - pkgconfig(gsl)
    - fftw-devel
    - pkgconfig(lcms2)
    - pkgconfig(Qt5WebEngineCore)
    - pkgconfig(Qt5Svg)
    - pkgconfig(Qt5Help)
    - pkgconfig(Qt5WebKit)
    - pkgconfig(Qt5Core)
    - pkgconfig(gl)
    - pkgconfig(libraw)
    - pkgconfig(OpenEXR)
    - gtest-devel
    - libboost-devel
setup      : |
    %cmake
build      : |
    %make
install    : |
    %make_install
```

Le début est assez simple, nom du paquet, version de l'application, version de la release, la licence, la catégorie, la description (courte et normale)...etc
La série de caractères après la source (le tarball) est la somme sha256. Donc téléchargez avant la source puis faite un sha256sum dessus pour obtenir la somme à indiquer dans le fichier.

Pour la compilation, Solus utiliser des raccourcis comme **%make**, Frugalware avait fait la même chose pour faciliter la vie du packageur.

Le plus chiant c'est les dépendances, Solus fonctionne beaucoup avec les pkgconfig et il faut indiquer les vrais noms des dépendances entre parenthèses, certains noms comportent des majuscules...

Pour débuter le packaging, faites:

```
sudo solbuild build
```

L'outil vas vérifier le fichier package.yml et si tout vas bien, il passe à l'installation des dépendances dans un chroot, puis télécharge la source pour l'extraire et débuter le processus de compilation. À la fin, j'ai eu un beau fichier .eopkg que j'ai installé (sudo eopkg it fichier.eopkg) et luminance_hdr fonctionne :-)

J'ai proposé [un patch à l'équipe de Solus](https://dev.solus-project.com/T3419), on verra si le paquet sera rajouté au dépôt.

En conclusion, packager pour Solus n'est pas bien compliqué mis à part pour trouver les dépendances (cette partie est encore un peu mystérieuse pour moi). J'ai également fait un paquet pour libmypaint 1.3.0 qui j'espère sera approuvé car j'aimerais packager juste pour moi la version de développement 2.9.x de Gimp (libmypaint 1.3.0 étant indispensable pour sa compilation).
