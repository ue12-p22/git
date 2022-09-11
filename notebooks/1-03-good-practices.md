---
jupytext:
  cell_metadata_filter: all,-hidden,-heading_collapsed
  notebook_metadata_filter: all,-language_info,-toc,-jupytext.text_representation.jupytext_version,-jupytext.text_representation.format_version
  text_representation:
    extension: .md
    format_name: myst
kernelspec:
  display_name: Python 3 (ipykernel)
  language: python
  name: python3
nbhosting:
  title: bonnes pratiques
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

# commits & bonnes pratiques

+++

Une notebook très court, où on revient rapidement sur la bonne façon de découper son code en commits, et de rédiger les messages qui vont avec.

+++

## le contenu des commits

+++

### ne pas tout mélanger

La première recommandation, sans doute la plus fondamentale, est de **bien regrouper les modifications qui vont ensemble**. 

En effet il arrive souvent qu'on se retrouve avec dans les fichiers une accumulation de changements; par exemple :
1. pour écrire une nouvelle feature, travail qui a pris deux jours entiers, 
1. on a **aussi** corrigé un typo dans un commentaire, 
1. et **aussi** récrit un bout de code pour utiliser une technique qu'on vient d'apprendre et qui est plus sûre.

À ce stade on va committer, il **faut absolument** tirer profit de l'index qui, on l'a vu, nous permet justement de **ne pas tout committer d'un coup**, pour découper ces changements **en 3 commits distincts** - ou plus le cas échéant, si la feature elle-même peut être logiquement découpée en plusieurs étapes.

+++

### pourquoi (1) ?

Le premier intérêt de  faire comme ça, c'est pour la maintenance

Imaginez: vous devez reporter la correction d'un bug dans une version client qui est vieille de deux mois;  
* le bug est déjà corrigé dans la version de développement  
* si la correction du bug a été bien proprement isolée dans un commit qui ne fait que ça, on va facilement pouvoir appliquer ce commit sur la branche de maintenance (pour les curieux, voyez `git cherry-pick`)  
* mais si au contraire c'est tout mélangé avec d'autres choses, ça va être problématique et on va devoir réappliquer le bugfix à la main, ballot !

+++

### pourquoi (2) ?

Un deuxième intérêt, c'est d'avoir un historique plus propre

En effet il est possible aussi de **récrire l'historique**  
(en utilisant `git rebase`, qu'on n'aura pas le temps de voir en détail pendant ce cours malheureusement,  
mais les curieux peuvent s'intéresser à `git rebase --interactive`)

Avec cet outil :

* on peut changer l'ordre des commits, et/ou les fusionner
* mais par contre c'est beaucoup **plus compliqué de couper un commit en morceaux**

C'est pourquoi dans le doute on a intérêt à faire plutôt trop de commits que pas assez; il est toujours temps ensuite d'agréger plusieurs commits en un seul, alors que dans l'autre sens c'est bien plus fastidieux

+++

## le message des commits

+++

### quoi mettre dans le message

Au début on n'a pas les idées claires sur ce qu'il est intéressant de mentionner dans le message attaché à un commit.

On peut commencer par dire **ce qui n'est pas intéressant** : ce n'est **pas la peine** de reprendre la **liste des fichiers** / fonctions / numéros de lignes modifiés: les outils d'UI graphique autour de git vous montreront tout ça très bien - et en plus ce sera garanti d'être correct.

Il est souvent plus pertinent d'expliquer **pourquoi** on a fait le changement, plutôt que **comment** on l'a fait. 

Dites-nous par exemple que c'est la correction du bug numéro tant et tant; ou que c'est un refactoring qui prépare la feature telle et telle. 

Mais ne nous dites pas que vous avez remplacé la fonction `schmoll` par la classe `Truc`, qui est quelque chose qu'on va voir facilement en lisant les différences..

Avec un peu d'expérience on comprend assez vite ce qu'il est utile de mentionner ou pas; 
clairement le fait de travailler en équipe, et donc d'être en situation de lire la production des autres, aide bien

+++

### une ligne de synthèse + une ligne blanche + du baratin

Dernier détail, ça varie selon les projets, mais un usage assez répandu consiste à rédiger son message en mettant

* une ligne de synthèse
* une ligne blanche pour bien séparer
* ensuite autant de détails qu'on veut

ça pourrait donner par exemple

```
a synthetic line that summarizes it

the gory details that you believe
are relevant to mention here
for example to motivate the technical choices made
(which could also be written in comments in the code
 if that deserves to be made permanent)
```

ce qui permet alors à - notamment - `git log --oneline` de présenter un résumé pertinent.

+++

***

+++

### spécifique à github

Lorsqu'on utilise une plateforme comme github, il est fréquent de mentionner dans le message des références à d'autres événements du projet.

On n'en a pas encore parlé, mais dans un projet github il y a la notion de *issue*, qui sont des simples fils de discussion, qui peuvent servir entre autres à signaler un bug; et la notion de *PR*, qui permettent aux autres de soumettre du code

ainsi si par exemple l'*issue* numéro 123 signale un bug, et qu'on commite une correction pour ce bug, on va écrire simplement quelque part `close #123`, ce qui permettra 
* de lier le commit avec l'*issue*, et donc d'améliorer la traçabilité 
* et même de fermer automatiquement l'issue en question.

On peut référencer de cette façon toutes sortes d'objets autres que les *issues*, voir les détails ici :
https://docs.github.com/en/github/writing-on-github/autolinked-references-and-urls

+++

## un TP sur ce thème

+++

Clonez ce dépôt et suivez les instructions du README:
https://github.com/ue12-p21/git-tp-add-by-lines

+++

**Outils**

Pour pouvoir proprement découper un gros changement en plusieurs commits, il est clair que la méthode qu'on a vue jusqu'ici - à savoir `git add fichier` - ne va pas nous permettre une finesse suffisante pour élaborer des commits bien propres

Car il nous faut la possibilité d'ajouter dans l'index, non pas tout le contenu d'un fichier d'un seul coup, mais bien plus finement, avec une granularité de l'ordre de la ligne

On a déjà parlé de cette feature dans vs-code, pour rappel:

+++

<video width="800px" controls src="media/vscode-line-by-line.mp4" type="video/mp4"></video>

+++

Pour information, on peut faire ce genre de choses également à partir d'outils 'graphiques' autour de `git`, comme par exemple avec `SourceTree` (qui est dispo sur Windows et Mac, malheureusement pas sur linux..)

+++

<video width="800px" controls src="media/sourcetree-line-by-line.mp4" type="video/mp4"></video>

+++

***

et pour finir voice ce que xkcd a à dire sur les messages de commit ;)  
(il les représente dans l'autre sens, les derniers en bas...)

<img src="media/xkcd-git-commit.png" width="60%">
