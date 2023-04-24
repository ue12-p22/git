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
  title: "r\xE9sum\xE9 (2)"
---

Licence CC BY-NC-ND, Thierry Parmentelat & Valérie Roy

```{code-cell}
%%python
from IPython.display import HTML
HTML(url="https://raw.githubusercontent.com/ue12-p22/git/main/notebooks/_static/style.html")
```

# résumé du chapitre précédent

+++

## les remotes

+++

* dans un repo git, on peut configurer des *remotes*  
  chaque ***remote*** correspond à (l'URL d') **un autre repo** git avec lequel on peut se synchroniser
  

* lorsqu'on utilise **`git clone`** pour créer un repo  
  le ***remote* `origin`** est créé, et il désigne le repo que l'on a clôné


* on peut afficher la liste des *remotes* avec la commande `git remote`  
  bien souvent du coup, on n'a que le seul *remote* `origin`

+++

## les commandes

+++

| commande | action |
| ----------: | :-------- |
| ￮￮￮￮￮￮￮￮￮￮￮￮ | ***regarder*** |
| `git remote` | liste les *remotes* connus de ce repo |
|              | très souvent il y a un seul *remote* |
|              | créé par `clone` et qui s'appelle `origin` |
| `git fetch`  | *ou* `git fetch origin` |
|              | va chercher dans le *remote* les nouveaux commits |
|              | et les ajoute dans le dépôt courant |
|              | **non intrusif:** le commit courant, l'index et les fichiers |
|              | ne **sont pas modifiés** |
| ￮￮￮￮￮￮￮￮￮￮￮￮ | ***adopter des nouveautés*** |
| `git pull` | *ou* `git pull origin main` |
|            | fait d'abord un `fetch origin` |
|            | puis un `merge origin/main` |
|            | **intrusif** : comme pour un `merge` |
| ￮￮￮￮￮￮￮￮￮￮￮￮ | ***publier des nouveautés*** |
| `git push` | *ou* `git push origin main` |
|            | essaie de pousser dans le *remote* `origin` |
|            | le commit courant au dessus de la branche `main` |
|            | **conditions nécessaires:** |
|            | 1. avoir les droits d'accès dans le *remote* |
|            | 2. il doit s'agit d'une fusion *fast-forward* |
