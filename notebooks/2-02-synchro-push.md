---
jupytext:
  cell_metadata_filter: all,-hidden,-heading_collapsed
  notebook_metadata_filter: all,-language_info,-toc,-jupytext.text_representation.jupytext_version,-jupytext.text_representation.format_version
  text_representation:
    extension: .md
    format_name: myst
kernelspec:
  display_name: Calysto Bash
  language: bash
  name: calysto_bash
nbhosting:
  title: "synchro entre d\xE9p\xF4ts : pousser"
---

<div class="licence">
<span>Licence CC BY-NC-ND</span>
<div style="display:grid">
    <span>Thierry Parmentelat</span>
    <span>Valérie Roy</span>
</div>
</div>

<img src="media/inria-25-alpha.png">
<img src="media/ensmp-25-alpha.png">

+++

# synchro entre dépôts : pousser

+++

## on contextualise

+++

### exporter avec `git push`

maintenant qu'on a bien compris comment on peut aller chercher des nouveautés depuis un dépôt distant, on va voir à présent **dans l'autre sens** comment on peut **exporter des choses** sur un dépôt distant

ici c'est facile il n'y a qu'une seule commande à connaître, et c'est… devinez un peu

oui, c'est `git push`

le principe est presque exactement le réciproque de `git pull`, avec toutefois **deux grosses différences**

+++

### on a besoin de droits particuliers

première grosse différence avec le `pull`  
nous essayons de **faire des modifications** dans le dépôt distant, et du coup il va nous falloir **les droits en écriture** !

c'est un sujet qu'on a déjà effleuré dans les slides d'introduction où, souvenez-vous, on avait vu que Bob pouvait collaborer avec Alice si :
* soit si elle lui donnait les droits d'écrire dans son dépôt,
* soit en passant par son *fork*, dans lequel il peut écrire

j'en profite pour signaler que le *fork* est une notion introduite par la surcouche github, et non pas une notion native de git, on n'aura pas le temps d'approfondir, mais à ce stade vous devez avoir deviné l'idée générale

+++

### un push ne peut faire qu'un fast-forward 

l'autre différence importante, c'est que par sécurité on a décidé qu'avec `git push` on peut **seulement** faire des merge ***fast-forward***

pourquoi ça ? l'idée c'est simplement que, si on se retrouve à devoir créer un commit de fusion à distance, il y a le risque de se trouver en présence de conflits; et dans ce cas-là une intervention manuelle est nécessaire; mais on n'a pas accès aux fichiers à distance pour résoudre le conflit, bref c'est possiblement dangereux 

sans discuter plus avant de la pertinence de ce choix, voyons d'abord comment tout cela fonctionne

+++

## le `push` est pratiquement l'inverse du `pull`

cette vidéo décortique le fonctionnement de `push` dans un cas simple

<video width="800px" controls src="media/manim-Push.mp4" type="video/mp4"></video>

+++

## mais attention le push peut coincer !!!

dans la suite de la vidéo on envisage un cas (**très très fréquent**) où le push **ne peut pas se faire** avant que l'on ne fasse d'abord un `pull`

<video width="800px" controls src="media/manim-Needmanim-Pull.mp4" type="video/mp4"></video>

+++

## conclusion

à part ces deux différences (besoin de permission, et refus de créer un commit de fusion), le fonctionnement de `push` est le symétrique de celui de `pull`
