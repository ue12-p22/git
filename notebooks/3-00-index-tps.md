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
  title: quelques TPs
---

<div class="licence">
<span>Licence CC BY-NC-ND</span>
<span>Thierry Parmentelat</span>
</div>

<img src="media/inria-25-alpha.png">

+++

# quelques TPs pour pratiquer `git`

+++

***

+++ {"tags": ["framed_cell"]}

## tp-add-by-lines

quand on a fait plusieurs modifications distinctes, et qu'on veut les grouper en plusieurs commits, il faut pouvoir gérer **finement les ajouts dans l'index**, c'est-à-dire au niveau du bloc ou de la ligne

https://github.com/ue12-p21/git-tp-add-by-lines

+++

***

+++ {"tags": ["framed_cell"]}

## tp-clone-pull

nos cours sont publiés sur github, et vous les **clonez** chez vous  
puis pour le cours suivant, le prof publie une **nouvelle version** du cours

comment faire pour réconcilier votre copie locale avec la nouvelle version du cours ?

et que se passe-t-il alors exactement dans votre copie locale, si vous avez vous-même fait des changements dans les notebooks ?

ce TP demande une préparation spécifique par groupe, une fois que c'est prêt visitez

https://github.com/ue12-p21/git-tp-clone-pull-groupe`n`

+++

***

+++ {"tags": ["framed_cell"]}

## tp-killing-push

vous travaillez à plusieurs dans un repo, et vous n'**arrivez pas à pousser un commit** ?  
c'est sûrement que quelqu'un d'autre a poussé avant vous…

https://github.com/ue12-p21/git-tp-killing-push

+++

***

+++ {"tags": ["framed_cell"]}

## tp-teamwork

un tp plus complet où on simule un travail en groupe  
à faire en groupes de 3 ou 4

https://github.com/ue12-p21/git-tp-teamwork

+++

***

+++ {"tags": ["framed_cell"]}

## tp-conflict

un tp à faire individuellement  
on crée délibérément un conflit pour savoir reconnaître les symptômes, et s'entrainer à résoudre le conflit

[le README est ici](../tps/tp-conflict/README.md)
