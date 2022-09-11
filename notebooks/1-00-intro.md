---
jupytext:
  cell_metadata_filter: all,-hidden,-heading_collapsed
  formats: md:myst
  notebook_metadata_filter: all,-language_info,-toc,-jupytext.text_representation.jupytext_version,-jupytext.text_representation.format_version
  text_representation:
    extension: .md
    format_name: myst
kernelspec:
  display_name: Calysto Bash
  language: bash
  name: calysto_bash
nbhosting:
  title: introduction
---

<div class="licence">
<span>Licence CC BY-NC-ND</span>
<span>Thierry Parmentelat</span>
</div>

<img src="media/inria-25-alpha.png">

+++

# UE12 - la gestion de versions avec `git`

+++

## un survol en slides

Pour les néophytes, [voici un slideshow](media/kn2-introduction-git.pdf) pour illustrer rapidement **le besoin**, et **les cas d'usage** les plus simples; [accessible aussi ici](https://github.com/ue12-p21/git/raw/main/notebooks/media/introduction-git.pdf)

la présentation contient des animations, assurez-vous de bien la visionner en mode slideshow  
durée : grand maximum 10', il ne s'agit **pas de tout comprendre** mais juste de brosser le contexte

+++

## pourquoi git ?

Après plusieurs décennies de tâtonnements, et des strates d'outils dédiés à la gestion de versions (sccs, rcs, cvs, subversion, mercurial, …), le constat que l'on peut faire en 2020 est que le vainqueur est git, et sans doute pour un bon moment encore; jugez par vous même :

* la plateforme github annonce 40 millions de comptes de développeurs
* pratiquement tous les outils dont on a parlé jusqu'ici (Python, numpy, pandas, matplotlib, git lui-même bien sûr, mais aussi linux, Jupyter, etc…) ont leurs sources ouvertes et disponibles sous git (à l'exception notable de vs-code, mais il existe une variante open-source vs-codium)

Ça signifie que, même si l'apprentissage de git peut apparaitre aride aux débutants, c'est aujourd'hui **un standard de fait** dans toute l'industrie du logiciel, et au delà…

+++

## git pour du code, mais pas que

Signalons en effet que git est utilisé **aussi** pour notamment :

* le processus d'**élaboration des lois**: gestion du corpus de lois: le Council de Washington DC
  * https://github.com/DCCouncil/dc-law-html
* la mise à disposition **d'open-data**:
  * https://github.com/collections/open-data

En réalité il potentiellement utile pour *pratiquement* tout ce qui est numérique, même si clairement il s'applique le mieux à des contenus de nature textuelle.

+++

## d'autres ressources pour ce cours

* en version HTML statique :  
  https://nbhosting.inria.fr/builds/ue12-p21-git/handouts/latest/

* les sources de ce cours :
  https://github.com/ue12-p21/git
  
* également utile, une *cheat sheet* éditée par github :
  https://github.github.com/training-kit/downloads/github-git-cheat-sheet.pdf
