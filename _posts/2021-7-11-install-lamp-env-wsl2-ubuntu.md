---
layout: post
title: Installe un environnement LAMP à jour sur WSL2 / Ubuntu
published: true
---

## Sommaire

- [Introduction](#introduction)
- [Prérequis](#prérequis)
    - [Linux](#linux)
    - [Windows](#windows)
        - [Installer Ubuntu / WSL2](#installer-ubuntu--wsl2)
            - [Activer WSL](#activer-wsl)
            - [Activer la fonctionnalité de machine virtuelle](#activer-la-fonctionnalité-de-machine-virtuelle)
            - [Télécharger et installer le package de mise à jour du noyau Linux](#télécharger-et-installer-le-package-de-mise-à-jour-du-noyau-linux)
            - [Définir la version de WSL par défaut](#définir-la-version-de-wsl-par-défaut)
            - [Installer Linux sur WSL 2](#installer-linux-sur-wsl-2)
            - [Installer le nouveau terminal de Windows](#installer-le-nouveau-terminal-de-windows)
            - [Désactiver le démarrage rapide de Windows pour éviter certains problèmes](#désactiver-le-démarrage-rapide-de-windows-pour-éviter-certains-problèmes)
- [Installation du serveur web Apache 2.4](#installation-du-serveur-web-apache-24)
    - [Téléchargement du paquet](#téléchargement-du-paquet)
    - [Activer un module Apache](#activer-un-module-apache)
- [Installation de PHP 8](#installation-de-php-8)
    - [Activer le *repository*](#activer-le-repository)
    - [Installer PHP 8](#installer-php-8)
    - [Installer une extension PHP](#installer-une-extension-php)
- [Installation de MySQL 8](#installation-de-mysql-8)
    - [Corriger le warning ](#corriger-le-warning)
    - [Lancer le CLI de MySQL](#lancer-le-cli-de-mysql)
- [Installation de PhpMyAdmin 5](#installation-de-phpmyadmin-5)
- [Crédits](#crédits)

---

## Introduction

Bonjour à toi développeur ou développeuse (par souci de facilité, je vais employer le masculin le reste du temps), tu souhaites développer sur PHP avec un environnement de développement à jour de type <abbr title="Linux Apache MySQL/MariaDB PHP/Python">LAMP</abbr> ? Alors tu es sur le bon endroit ! Et si tu es sur Windows, alors pas de soucis ! Vérifie que tu as les bons [prérequis](#prérequis) et enchaîne sur le reste de l'article !

Bonne lecture à toi !

---

## Prérequis

### Linux

Tu dois disposer de la dernière version <abbr title="Long Term Support">LTS</abbr> d'Ubuntu ou supérieure qui -- au moment où j'écris cet article -- est la version 20.04.
Je n'ai pas testé sur d'autres distributions, mais le processus doit être assez proche.

### Windows

Tu dois disposer d'une version à jour de Windows 10 et d'un processeur supportant la virtualisation. Pour activer la virtualisation afin d'activer <abbr title="Windows Subsystem for Linux">WSL</abbr>2, tu peux suivre [cet article](https://www.tech2tech.fr/comment-activer-la-technologie-de-virtualisation-sur-mon-pc/ "Comment activer la technologie de virtualisation sur mon PC").

#### Installer Ubuntu / WSL2

##### Activer WSL 

En premier lieu tu dois activer la fonctionnalité WSL sur windows, pour cela ouvre le terminal *PowerShell* en mode administrateur avec la combinaison de touches : <kbd>Ctrl</kbd> + <kbd>Shift</kbd> + <kbd>Echap</kbd> 


![Gestionnaire de tâches](/images/install-lamp/execute-from-task-mgr.png "Exécuter une commande depuis le gestionnaire de tâches")

  *Si tu n'as pas cette apparence clique sur "Plus de détails"*

Cliquez sur `Fichier > Exécuter une nouvelle tâche`

![Gestionnaire de tâches](/images/install-lamp/execute-with-admin-privileges.png "Exécuter une commande avec les privilèges administrateur")

  *N'oublie pas de cocher la case !*

Coche la case et entre ensuite la commande `powershell` et valide en appuyant sur la touche <kbd>Enter</kbd>

Exécute alors la commande suivante :

```PowerShell
dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart
```

*Voilà ! WSL est activé !*

##### Activer la fonctionnalité de machine virtuelle

Toujours dans le terminal avec les privilèges administrateur, lance la commande suivante :

```PowerShell
dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart
```

Redémarre maintenant ton ordinateur.

##### Télécharger et installer le package de mise à jour du noyau Linux

Pour cette étape, rien de complexe, tu télécharges et tu installes le fichier issu du lien suivant (Des privilèges administrateur seront demandés) :

<https://wslstorestorage.blob.core.windows.net/wslblob/wsl_update_x64.msi>

##### Définir la version de WSL par défaut

Pour profiter de la toute puissance de la dernière version de WSL, c'est à dire la **2**, il te faut ouvrir *PowerShell* via le raccourci clavier <kbd>Windows</kbd> + <kbd>R</kbd> et entrer `powershell` dans le champs.

Une fois PowerShell ouvert, exécute la commande suivante :

```PowerShell
wsl --set-default-version 2
```

Voilà tu as fini de définir la version par défaut ! Pense bien à le faire, la version 2 est **7 fois** plus rapide que la première !

##### Installer Linux sur WSL 2

![Emplacement du Microsoft store](/images/install-lamp/emplacement-du-microsoft-store.png "Emplacement du Microsoft store")

Il ne te reste plus qu'à choisir quelle distribution de linux tu vas installer ! Ouvre le [*Microsoft store*](https://aka.ms/wslstore) et choisis une distribution *Linux*. 

Pour ma part, j'ai choisi *Ubuntu* ! 

![Page d'Ubuntu sur le Microsoft store](/images/install-lamp/page-d-ubuntu-sur-le-microsoft-store.png "Page d'Ubuntu sur le Microsoft store")

Lance la distribution depuis sa page sur le store et laisse lui du temps (plusieurs longues minutes parfois) pour s'installer en surveillant de temps à autre le déroulement.

Linux t'invitera au bout d'un moment à entrer un nom d'utilisateur, évite les accents et les espaces, privilégie les minuscules. Entre ensuite deux fois le même mot de passe de ton choix lorsque tu y seras invité.

N'hésite pas à te créer un raccourci vers Ubuntu ou la distribution que tu as installé pour plus de simplicité

##### Installer le nouveau terminal de Windows

Optionnel, mais carrément indispensable !

Je t'invite à aller sur le store pour télécharger [Windows Terminal](ms-windows-store://pdp/?ProductId=9N0DX20HK701) dans un premier temps.

Ensuite, si tu souhaites mettre par défaut ta distribution Linux, accède aux paramètres (<kbd>Ctrl</kbd> + <kbd>,</kbd>) et change l'option *Profil par défaut* dans l'onglet *Démarrage*.

Pour que ton terminal s'ouvre sur ton profil, je t'invite à insérer dans l'option *Répertoire de démarrage* qui se trouve dans les paramètres, dans l'onglet de profil de ta distribution, la chaîne de caractères suivante :

`\\wsl$\Ubuntu\home\username` 

(en prenant soin de remplacer `username` par le nom d'utilisateur que tu as fourni précédemment !)

> **Astuce** : Si tu souhaites ouvrir deux instances dans le même onglet (divisant l'onglet en deux colonnes), maintiens <kbd>Alt</kbd> en appuyant sur le signe **+** pour ajouter une instance.

##### Désactiver le démarrage rapide de Windows pour éviter certains problèmes

*Optionnel*.

Il semblerait que certains utilisateurs aient des problèmes sur WSL2 lors de l'utilisation de l'environnement LAMP. Pour éviter que ça n'arrive, il faut désactiver le démarrage rapide.

*Personnellement, je n'ai rien remarqué (il est désactivé sur mon pc fixe, mais activé sur le portable, je n'ai aucun souci de WSL pour le moment !), mais je vais quand même t'indiquer comment procéder ici.*

Pour cela, utilise le raccourci clavier <kbd>Windows</kbd> + <kbd>R</kbd> et entre `powercfg.cpl`. Appuie sur <kbd>Enter</kbd> et dans le pannneau *Options d'alimentation* clique sur *Choisir l'action du bouton d'alimentation* :

![Options d'alimentation](/images/install-lamp/options-d-alimentation.png "Options d'alimentation")

Ensuite clique sur *Modifier les paramètres non disponibles* : 

![Modifier les paramètres non disponibles](/images/install-lamp/modifier-les-paramètres-non-disponibles.png "Modifier les paramètres non disponibles")

Puis décoche la case *Activer le démarrage rapide* :

![Désactiver le démarrage rapide](/images/install-lamp/désactiver-le-démarrage-rapide.png "Désactiver le démarrage rapide")

---

## Installation du serveur web Apache 2.4

> **Important !**
> 
> À partir de maintenant, toutes les commandes se feront dans le terminal Linux, je considère que tu as au moins *Bash* (par défaut) ou un terminal plus récent comme *Zsh*.

Installer *Apache* est assez simple, mais avant, nous allons mettre à jour la liste des paquets disponibles (prends l'habitude sur Linux d'exécuter ces commandes au moins à chaque fois que tu souhaites installer un nouveau paquet ou que tu souhaites mettre à jour l'ensemble des paquets) :

```bash
# Mise à jour de la liste des paquets disponibles
sudo apt update

# Mise à jour des paquets installés
sudo apt upgrade -y

# Nettoyage des paquets temporaires inutilisés
sudo apt autoremove

# Nettoyage des installations
sudo apt autoclean
```

### Téléchargement du paquet

Il suffit d'exécuter la commande suivante :

``` bash
sudo apt install apache2
```

Pour ensuite lancer le service, j'utilise la commande suivante :

``` bash
sudo apache2ctl start
```

### Activer un module Apache

Avant d'activer un module, il est intéressant de voir les modules disponibles avec la commande suivante :

```bash
ls /etc/apache2/mods-available
```

Elle va afficher ce que contient le répertoire `mods-available` situé dans le répertoire d'installation d'*Apache 2.4*.

![Modules Apache 2 disponibles](/images/install-lamp/mods-available.png "Modules Apache 2 disponibles")

Il suffit alors d'utiliser la commande `a2enmod` suivie du nom du module (sans l'extension).

Par exemple, pour le module *Rewrite*, on a bien vu qu'il était disponible (`rewrite.load`), il te reste donc à écrire :

```bash
sudo a2enmod rewrite
# Le terminal nous invitera à recharger ou redémarrer Apache, ce que l'on va faire
sudo apache2ctl restart
```

*Voilà nous avons installé le module Rewrite !*

---

## Installation de PHP 8

Pour installer Php 8, il va falloir ruser, et installer un *repository* maintenu par un développeur *Debian* (Ondřej Surý) pour avoir accès à cette version de php sur *Ubuntu*.

### Activer le *repository*

Entre donc les commandes suivantes :

```bash
sudo apt install software-properties-common
sudo add-apt-repository ppa:ondrej/php

# Il nous reste à actualiser la liste des paquets disponibles
sudo apt update
```

### Installer PHP 8

Pour cela, c'est simple, il suffit de télécharger le paquet de Php8 et le module Php8 pour Apache 2, puis de redémarrer Apache.

```bash
sudo apt install php8.0 libapache2-mod-php8.0
sudo apache2ctl restart
```

### Installer une extension PHP

Toutes les extensions PHP pour la version 8 sont préfixées de la même manière, il suffit alors d'écrire la commande de cette manière là :

```bash
sudo apt install php8.0-[nomdelextension] php8.0-[nomdelextension2] [...]

# On active la ou les extensions dans PHP
sudo phpenmod [nomdelextension] [nomdelextension2] [...]
```

On n'oublie pas de redémarrer Apache avec un petit `sudo apache2ctl restart`.

---

## Installation de MySQL 8

Pour installer MySQL 8 il suffit de lancer la ligne de commande suivante :

```bash
sudo apt install mysql-server-8.0
```

Et pour lancer le service :

```bash
sudo service mysql start
```

### Corriger le warning 

Quand tu lances le service tu peux avoir cet avertissement :

```bash
su: warning: cannot change directory to /nonexistent: No such file or directory
```

Cela signifie que l'utilisateur `mysql`cherche son répertoire ***home***. Pour corriger cela, il te faut arrêter le service, définir le répertoire et relancer le service avec ces commandes :

```bash
sudo service mysql stop
sudo usermod -d /var/lib/mysql/ mysql
sudo service mysql start
```

### Lancer le CLI de MySQL

Pour lancer le <abbr title="Command Line Interface">CLI</abbr> de MySQL il faut rentrer en tant que root :

```bash
sudo mysql

# Si ce n'est pas pris alors :
sudo mysql -u root
```

## Installation de PhpMyAdmin 5

Pour récupérer la dernière version de 
```bash
DATA="$(wget https://www.phpmyadmin.net/home_page/version.txt -q -O-)"
VERSION="$(echo $DATA | head -n 1)"
wget https://files.phpmyadmin.net/phpMyAdmin/$VERSION/phpMyAdmin-$VERSION-all-languages.tar.gz
```


tar xvf phpMyAdmin-${VERSION}-all-languages.tar.gz

sudo mv phpMyAdmin-*/ /usr/share/phpmyadmin

sudo mkdir -p /var/lib/phpmyadmin/tmp

sudo chown -R www-data:www-data /var/lib/phpmyadmin

sudo mkdir /etc/phpmyadmin/

sudo cp /usr/share/phpmyadmin/config.sample.inc.php  /usr/share/phpmyadmin/config.inc.php

sudo vim /usr/share/phpmyadmin/config.inc.php
```

```php
// /usr/share/phpmyadmin/config.inc.php
$cfg['blowfish_secret'] = 'e65f14r6hg841GHHJJ';
// ajouter la ligne suivante si elle n'y est pas
$cfg['TempDir'] = '/var/lib/phpmyadmin/tmp';
```



---

## Crédits

- [Microsoft.com](https://docs.microsoft.com/fr-fr/windows/wsl/install-win10) - Guide d’installation du sous-système Windows pour Linux pour Windows 10 
- [Dev.to](https://dev.to/axiol/setting-up-a-lamp-configuration-with-wsl-2-5fbm) - Setting up a LAMP configuration with WSL 2
- [Linuxize](https://linuxize.com/post/how-to-install-php-8-on-ubuntu-20-04/) - Installer PHP8 sur Ubuntu 20.04 (EN).
- [DevAnswers.co](https://devanswers.co/manually-upgrade-phpmyadmin/) - Mettre à jour phpmyadmin manuellement (EN).
