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
  title: configuration
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

# configuration

+++

avant de commencer le cours, faisons le point sur la configuration

c'est **très important** de bien **suivre toutes ces consignes**, 
ou alors vous risquez de sérieusement galérer plus tard…

+++

## avoir installé git

évidemment... et on l'a fait en début d'année

pour vérifier, vous devez pouvoir taper dans le terminal

```
git version
```

+++

## votre identité

pour pouvoir créer un commit, git a besoin de savoir votre nom et votre adresse de messagerie

```bash
git config --global user.name "Jean Mineur"
git config --global user.email jean.mineur@mines-paristech.fr
```

+++

## l'éditeur

toujours pour commiter, git a besoin de savoir **quel éditeur de code** vous voulez utiliser pour entrer le message qui va avec le commit (sauf si vous utilisez l'option `-m` pour donner le message sur la ligne de commande)

pour utiliser **vs-code**:

```bash
git config --global core.editor "code --wait"
```

**remarque**  
lorsque vous faites par exemple `git commit` et que l'éditeur se lance pour vous laisser entrer le message, le programme dans le terminal **attend que vous ayez fini** d'entrer le message  
et pour lui dire "ça y est, j'ai fini, on peut finir le commit", ce que vous devez faire, c'est simplement de
***fermer l'onglet qui édite le message***   
il ne suffit pas de simplement sauver le fichier (c'est nécessaire bien sûr, mais pas suffisant)  
et dans l'autre sens ce n'est pas non plus la peine de terminer toute votre session vs-code (vous pouvez avoir plein d'autres fichiers ouverts à ce moment-là dans vs-code)

**note**  
pour que ça fonctionne, il faut que la commande `code` soit bien installée dans votre PATH; si vous avez `command not found` quand vous tapez `code .` dans votre terminal, allez dans vs-code, ouvrez la palette et cherchez `Shell Command: Install 'code' command in PATH`

+++

## la branche par défaut

pour que `git init` crée une branche qui s'appelle `main` et pas `master` (qui était le défaut il y a quelques années)

```bash
git config --global init.defaultbranch main
```

+++

## la clé SSH

depuis Août 2021, il est devenu très compliqué d'utiliser la méthode dite 'HTTPS' pour s'authentifier chez github;
aussi nous allons ensemble voir comment créer une clé pour la méthode SSH

+++

### c'est quoi SSH ?

au départ, un système de terminal distant pour pouvoir administrer les serveurs à distance; l'authentification est basée sur le principe d'une paire de clés publique/privée

sans entrer dans les détails, ces deux morceaux sont en gros deux éléments symétriques l'un de l'autre dans un très gros groupe fini, et on ne peut pas facilement calculer l'un à partir de l'autre  

par définition, la clé publique peut être divulguée sans aucun souci au monde entier; par contre **la clé privée** doit être gardée secrète, donc **jamais exposée/copiée** en dehors de votre ordi

et donc ce qu'on va faire tout simplement, c'est:

* générer une paire de clés
* et déposer une copie de la clé publique sur github, en l'associant à votre compte github

+++

### en pratique

+++

#### création de la paire de clés

pour générer la clé publique vous faites simplement dans le terminal
```bash
ssh-keygen
```

ce programme va vous poser des questions, à ce stade je vous recommande de toujours répondre par simplement la touche *Entrée* pour accepter les défauts et ne pas attacher de mot de passe votre clé privée (ce qui n'est pas une pratique hyper-sûre, mais à ce stade de votre cursus ça parait raisonnable; si vous êtes geek et/ou très soucieux de sécurité, mettez un mot de passe mais soyez prêt à taper votre mot de passe *ad nauseam*, ou à passer du temps à des configurations scabreuses pour ne pas avoir à le faire...)

+++

#### affichage de la clé publique

ceci va avoir pour effet de créer deux fichiers situés dans le dossier `~/.ssh` (le tilda signifie: directement sous votre homedir); du coup vous affichez le contenu de la clé publique en faisant maintenant

```bash
cat ~/.ssh/id_rsa.pub
```

et vous copiez tout le contenu (en incluant bien tout, même le `ssh-rsa` et tout)

+++

#### attachez la clé à votre compte github

maintenant vous allez sur github  
dans le coin en haut à gauche il y a votre icône  
qui ouvre un sous-menu dans lequel vous choisissez *Settings*  
dans la partie gauche de la page qui s'ouvre, cliques 'SSH and GPG Keys'  
et vous ajoutez une clé SSH; mettez ce que vous voulez comme titre, mais vous collez la clé publique dans la zone qui va bien

<img src="media/github-profile-1.png" width="60%">
<img src="media/github-profile-2.png" width="60%">

+++

#### pour vérifier

à ce stade pour tester vous pouvez tout simplement faire

```
git clone ssh://git@github.com/ue12-p21/git-sandbox.git
```

qui ne fonctionnera pas si votre clé n'est pas correctement reconnue

+++

#### pour conclure

à partir de maintenant, prenez l'habitude de toujours choisir le mode d'authentification 'SSH' lorsque vous clônez un repo:

<img src="media/github-choose-ssh.png" width="60%">

+++ {"tags": ["level_intermediate"]}

## la config, comment ça marche ?

+++ {"tags": ["level_intermediate"]}

pour les curieux, il y a deux niveaux de configuration

1. `local`, limité au repo courant
1. ou `global`, au contraire valable pour tous les repos

il y a une commande `git config` qui permet d'inspecter la configuration  
par défaut on regarde ou change la première famille  
mais avec l'option `--global` on regarde la seconde

+++ {"tags": ["level_intermediate"]}

### lire / vérifier un réglage

+++ {"tags": ["level_intermediate"]}

pour vérifier (lire) la configuration, vous pouvez faire

```bash
# voir toute la config (locale + globale)
git config -l
# du coup pour voir seulement la config globale 
git config -l --global
# ou juste locale
git config -l --local
```

et surtout pour vérifier la valeur d'**un** réglage, par exemple

```bash
git config user.name
```

+++ {"tags": ["level_intermediate"]}

### écrire / changer un réglage

+++ {"tags": ["level_intermediate"]}

eh bien on l'a déjà fait plus haut  
il suffit de décider si on veut ranger le réglage dans la zone locale ou globale  
et se souvenir que la syntaxe c'est `git config param value`

il faut juste comprendre que si vous aviez tapé

```bash
git config --global user.name Jean Mineur  # ne marche pas
```

ça n'aurait pas fonctionné car le shell (bash) ici aurait vu **deux paramètres** différents  
et c'est pourquoi il faut mettre les `"` autour de `Jean Mineur` comme ceci

```
git config --global user.name "Jean Mineur"  # ok maintenant
```

+++ {"tags": ["level_intermediate"]}

### dans quels fichiers

+++ {"tags": ["level_intermediate"]}

enfin si vous êtes vraiment curieux, sachez que les deux familles de config sont rangées dans

* `.gitconfig` - dans votre *home directory* - pour la config globale
* `.git/config` - à la racine du repo - pour la config locale
