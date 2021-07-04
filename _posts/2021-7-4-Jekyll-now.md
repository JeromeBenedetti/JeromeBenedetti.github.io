---
layout: post
title: Traduction - Crée ton blog sur Github avec Jekyll Now !
---

⚠️ Cet article est une traduction du fichier `README.md` du repository [tongqqiu/jelly-now](https://github.com/tongqqiu/jelly-now) ⚠️


# Jekyll Now

**Jekyll** est un générateur de site statique parfait pour les blogs hébergés sur GitHub ([le dépôt Jekyll](https://github.com/jekyll/jekyll))

**Jekyll Now** facilite la création de votre blog Jekyll, en éliminant ainsi une grande partie de la configuration du *front*.

- Vous n'avez pas besoin de toucher de lignes de commande.
- Vous n'avez pas besoin d'installer / configurer Ruby, rvm/rbenv, ruby gems. ☺️
- Vous n'avez pas besoin d'installer des dépendances comme un processeur markdown, Pygments, etc.
- Si vous êtes sous Windows, cela facilitera la mise en place de Jekyll.
- C'est facile d'essayer, vous pouvez simplement supprimer votre fork de dépôt si vous ne l'aimez pas.

En quelques minutes, vous aurez mis en place un blog minimal et responsive comme celui ci-dessous, vous donnant plus de temps pour écrire des publications géniales !

![Jekyll Now Theme Screenshot](/images/jekyll-now-theme-screenshot.jpg "Jekyll Now Theme Screenshot")

## Démarrage rapide

### Étape 1) Fork *Jekyll Now* sur ton dépôt personnel

Faites un fork de ce [dépôt](https://github.com/barryclark/jekyll-now), puis renommez le ainsi *nomdutilisateurgithub.github.io*.

Votre blog Jekyll sera normalement visible immédiatement via <http://nomdutilisateurgithub.github.io> (si ce n'est pas le cas, vous pouvez forcer *GitHub* à faire un build en complétant l'étape 2)

![Step 1](/images/step1.gif "Étape 1")

### Étape 2) Personnaliser et afficher votre site

Entrez votre nom, une description, votre avatar et de nombreuses autres options en modifiant le fichier `_config.yml`. Vous pouvez facilement activer le suivi Google Analytics, les commentaires Disqus et les icônes de réseaux sociaux ici également.

Faire une modification sur `_config.yml` (ou tout fichier de votre dépôt) obligera *GitHub Pages* à reconstruire votre site avec Jekyll. Votre site reconstitué sera visible quelques secondes plus tard via <http://nomdutilisateurgithub.github.io> - sinon, donnez-lui dix minutes, comme le suggère GitHub et il apparaîtra bientôt.

> Vous pouvez modifier les fichiers de votre blog de 3 différentes manières :

> 1. Modifiez des fichiers dans votre nouveau dépôt *nomdutilisateurgithub.github.io* via le navigateur sur GitHub.com (illustré ci-dessous).
> 2. Utilisez un éditeur de contenu GitHub tiers, comme [Prose par Development Seed](http://prose.io). Il est optimisé pour une utilisation avec Jekyll, éditer les fichiers *markdown*, écrire des brouillons et envoyer des images vraiment facilement.
> 3. Clonez votre dépôt et faites des mises à jour localement, puis poussez-les sur votre dépôt GitHub.

![_config.yml](/images/config.png "_config.yml")
  
### Étape 3) Publiez votre premier article de blog

Éditez `/_posts/2014-3-3-Hello-World.md` pour publier votre premier article de blog. Ce [memento Markdown](http://www.jekyllnow.com/Markdown-Style-Guide/) pourrait vous être utile.

![First Post](/images/first-post.png "Premier article")

> Vous pouvez également ajouter des articles supplémentaires dans le navigateur sur GitHub.com! Il suffit de cliquer sur l'icône **+** dans `/_posts/` pour créer un nouveau contenu. Assurez-vous simplement d'inclure le bloc [front-matter](http://jekyllrb.com/docs/frontmatter/) en haut de chaque article de blog et assurez-vous que le nom du fichier de la publication est dans ce format : `annee-mois-jour-titre.md`

## Développement en local

1. Installez Jekyll et les plug-ins en une fois. `gem install github-pages` cela fera un mirroir des plug-ins utilisés par *Github Pages* sur votre machine locale, y compris Jekyll, Sass, Gemoji, etc.
2. Clonez votre fork `git clone git@github.com:nomdutilisateurgithub/nomdutilisateurgithub.github.io.git`
3. Faite un serveur pour votreblog et surveillez les changements de mise en page, de contenu ou les changements sass `jekyll serve`
4. Affichez votre site Web à l'adresse http://0.0.0.0.4000
5. Committez tout changement et poussez le tout sur la branche `master` de votre dépôt utilisateur GitHub. *GitHub Pages* va ensuite reconstruire et héberger votre site Web.

## Plus encore !

J'ai créé une procédure *pas-à-pas* plus détaillée, [**Construire un blog avec Jekyll et GitHub Pages**](http://www.smashingmagazine.com/2014/08/01/build-blog-jekyll-github-pages/) sur le site Web de Smashing Magazine. Allez le voir si vous souhaitez une procédure pas à pas plus détaillée et plus d'éléments sur Jekyll. 🤘

Cela couvre :

- Une procédure pas à pas plus détaillée de la mise en place de votre blog Jekyll
- Les problématiques courantes que vous pourriez rencontrer lors de l'utilisation de Jekyll
- L'importation depuis WordPress, en utilisant votre propre nom de domaine et ainsi bloguer dans votre éditeur préféré
- Gestion des thèmes sur Jekyll, avec des exemples de templates *Liquid*
- Une revue rapide des nouvelles fonctionnalités de Jekyll 2.0, y compris le support de Sass/Coffeescript et les Collections.

## Les fonctionnalités de Jekyll Now

✓ _Premier workflow à forker_ sans lignes de commande, utilisant GitHub.com pour créer, personnaliser et poster sur votre blog
✓ Thème de base entièrement responsive et optimisé mobile (**[Theme Demo](http://jekyllnow.com)**)  
✓ Support de Sass/Coffeescript en utilisant Jekyll 2.0  
✓ Hébergement gratuit de votre site sur *GitHub Pages*
✓ Blogguez en Markdown  
✓ Coloration syntaxique  
✓ Commentaires Disqus  
✓ Intégration de Google Analytics  
✓ Icônes de réseaux sociaux au format SVG sur le footer de vos pages
✓ seulement 3 requêtes http, en incluant votre avatar  
✓ Emoji dans vos publications ! 💖💖💖

✘ Pas d'installation de dépendances  
✘ Pas besoin de mettre en place d'environnement de développement local  
✘ Pas de configuration de plugins  
✘ Pas besoin de passer du temps sur le thème 
✘ Plus de temps pour coder d'autres choses ... Oh attendez: ✓!  

## Questions?

[Ouvrez un ticket](https://github.com/barryclark/jekyll-now/issues/new) et discutons!

## Autres thèmes forkables

Vous pouvez utiliser les étapes du [Démarrage rapide](https://github.com/barryclark/jekyll-now#quick-start) avec d'autres thèmes qui sont installés pour être forkés aussi ! Voici quelques-uns de mes favoris :

- [Hyde](https://github.com/poole/hyde) par MDO
- [Lanyon](https://github.com/poole/lanyon) par MDO
- [mojombo.github.io](https://github.com/mojombo/mojombo.github.io) par Tom Preston-Werner
- [Left](https://github.com/holman/left) par Zach Holman
- [Minimal Mistakes](https://github.com/mmistakes/minimal-mistakes) par Michael Rose
- [Skinny Bones](https://github.com/mmistakes/skinny-bones-jekyll) par Michael Rose

## Crédits

- [Tongqqiu](https://github.com/tongqqiu/jelly-now) - (Ndt. Auteur original de cet article)
- [Jekyll](https://github.com/jekyll/jekyll) - Merci à ses créateurs, ses contributeurs et ses responsables.
- [SVG icons](https://github.com/neilorangepeel/Free-Social-Icons) - Merci, Neil Orange Peel. Ils sont magnifiques. 
- [Solarized Light Pygments](https://gist.github.com/edwardhotchkiss/2005058) - Merci, Edward.
- [Joel Glovier](http://joelglovier.com/writing/) - Très bons articles sur Jekyll. J'ai utilisé le `feed.xml` dans ce dépôt.
- [David Furnes](https://github.com/dfurnes), [Jon Uy](https://github.com/jonuy), [Luke Patton](https://github.com/lkpttn) - Merci pour le design / la revue de code.
- [Bart Kiers](https://github.com/bkiers), [Florian Simon](https://github.com/vermluh), [Henry Stanley](https://github.com/henryaj), [Hun Jae Lee](https://github.com/hunjaelee), [Javier Cejudo](https://github.com/javiercejudo), [Peter Etelej](https://github.com/etelej) - Merci pour vos [super contributions](https://github.com/barryclark/jekyll-now/commits/master) à ce projet!

