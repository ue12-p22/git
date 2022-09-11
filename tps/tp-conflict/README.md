# résolution de conflit


## propos

on va délibérément créer un conflit, pour s'entraîner à gérer ce cas-là


## rappel : c'est quoi un conflit ?

lorsque deux branches modifient **la même ligne de code**, alors au moment de les fusionner le code qui fait la fusion automatique **ne sait pas** quelle version prendre


## comment ça se manifeste ?

* on reçoit un message d'erreur dans le terminal au moment du *merge* ou du *pull* (et souvenez-vous que *pull* aussi fait un *merge*)
* dans ce cas là le fichier **les deux versions** sont conservées dans le fichier sous la forme
    ```text
    <<<<<<< HEAD
    le code de la branche courante
    =======
    le code de la branche qu'on fusionne
    >>>>>>> origin/main
    ```


## le TP

(à un joueur)

### créer un repo


### commit #1 : le README en version 1

* on committe juste un fichier `README.md` dans lequel on met

    ```text
    Ceci est le README de la
    version 1
    de mon magnifique logiciel buriverseur
    ```


### commit #2 : version 2

* éditez le README pour mettre 2 comme numéro de version  
* committez


### on revient en arriére

* revenez sur le premier commit en créant une nouvelle branche `devel`

**indice** on rappelle la commande `git switch -c` pour créer une nouvelle branche et l'adopter en même temps comme branche courante


### commit #3 : version 3

* éditez le README pour mettre 2 comme numéro de version  
* committez


### à quoi ça doit ressembler

vous devez avoir un diagramme qui contient 
* un commit racine avec *version 1*
* une branche `main` avec *version 2* -  directement liée à la racine
* une branche `devel` avec *version 3* - directement liée à la racine


### on essaie de fusionner

* puisque nous sommes sur `devel`, fusionnez la branche `main`

**indice**: on donne à `git merge` le commit à fusionner (sous-entendu, dans la branche courante)

normalement on est en situation de conflit, et vous devez vois les symptômes décrits au dessus à la rubrique *comment ça se manifeste ?*


### observez `git status`

* regardez notamment la catégorie dans laquelle est rangé le `README.md`


### résoudre le conflit

* allez à ce stade éditer le fichier `README.md` dans vs-code
* observez les outils proposés pour gérer le conflit
* mettez `4` comme numéro de version  
  attention, soyez bien sûr d'avoir éliminé toutes les scories qui ne sont là
  que pour nous aider à raisonner; le fichier que vous sauvez doit ressembler au
  README du départ, bien sûr


### observez `git status`

* à nouveau, regsrdez la catégorie dans laquelle est rangé le `README.md`

  a-t-on besoin de faire `git add README.md` ?


### commit #4

* à ce stade, vous pouvez poursuivre le merge en tapant au choix

  ```bash
  git merge --continue   # vous pouvez aussi ajouter --no-edit 
                         # si vous ne voulez pas entrer dans l'éditeur
  ```

  ou encore

  ```bash
  git commit
  ```


### épilogue

dans tous les cas, à ce stade vous devez avoir

* un dépôt propre (rien qui traine dans le status)
* 4 commits en forme de diamant
  ```text
  1 -> 2 -> 4
     \ 3 /
  ```
* avec le numéro de version dans le README.md correspondant
