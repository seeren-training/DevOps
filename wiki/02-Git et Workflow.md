# Git et Workflow

* 🔖 **Configurer**
* 🔖 **Initialiser**
* 🔖 **Status**
* 🔖 **Ignorer**
* 🔖 **Surveiller**
* 🔖 **Engager**
* 🔖 **Naviguer**
* 🔖 **Les branches**
* 🔖 **Remote**

___

## ⚙️ Prérequis

* Télécharger 🔗 [Git](https://git-scm.com/downloads) puis ouvrir un terminal

* Dans un terminal quelques rappels

*Changer de repertoire*

```bash
cd ..
```

*Créer un fichier vide*

```bash
touch my-file.txt
```

*Créer un fichier avec du contenu*

```bash
echo "Hello World" >my-file.txt
```

*Créer un dossie*r

```bash
mkdir my-folder
```

___

## 📑 Configurer

Vous devez avant d'ajouter et d'engager du contenu configurer votre nom d'utilisateur et votre email. Si vous voulez relier votre git local à un dépôt distant comme GitLab ou GitHub je vous conseille de mettre les informations de vos comptes existants.

* 🔗 [first time setup](https://git-scm.com/book/en/v2/Getting-Started-First-Time-Git-Setup)

```bash
git config --global user.name "USER_NAME"
```

```bash
git config --global user.email "USER_EMAIL"
```

___

## 📑 Initialiser

Démarrer le contrôle de version 

* 🔗 [init](https://git-scm.com/book/fr/v1/Les-bases-de-Git-D%C3%A9marrer-un-d%C3%A9p%C3%B4t-Git)

```bash
git init
```

Un dossier `.git` se trouve à la racine du répertoire.

___

## 📑 Status

Voir l'état de l'arbre

* 🔗 [status](https://git-scm.com/docs/git-status)

```bash
git status
```

Les fichiers et dossiers non ajoutés doivent apparaître dans la liste non suivie. Les modifications non validées doivent apparaitre dans la liste non engagée.

___

## 📑 Ignorer

Vous ne souhaitez peut-être pas activer le versionning pour tous vos fichiers de projet. Vous pouvez demander à Git d'ignorer des fichiers en créant un fichier `.gitignore` à la racine du répertoire du projet et fournir une liste de fichiers et de dossiers.

* 🔗 [ignore-files](http://help.github.com/ignore-files/)

```bash
# Dossier à ignorer
my-folder
# Fichier à ignorer
my-file.txt
```

___

## 📑 Surveiller


* 🔗 [add](https://git-scm.com/docs/git-add)

Surveiller tous les fichiers non surveillés

```bash
git add -A
```

Surveiller un fichier particulier

```bash
git add my-file.txt
```
Surveiller les fichiers d'un dossier

```bash
git add my-folder
```

___

## 📑 Engager

Engager correspond à valider la modification d'un contenu. Un engagement doit posséder un message de description.

* 🔗 [commit](https://git-scm.com/docs/git-commit)

Engager les modications d'un fichier

```bash
git commit README.md -m "Create README"
```

*Si vous ne spécifiez pas de message avec l'option `-m`, l'éditeur de message par défaut s'ouvrira et si c'est `vim` fermez le avec `:q`.*

Engager toutes les modiications

```bash
git commit -a -m "Initialize"
```

Chaque engement possède un identifiant.

* 🔗 [log](https://git-scm.com/docs/git-log)

Afficher la liste des engagements

```bash
git log
```

___

## 📑 Naviguer

Il est possible de naviguer entre les commits, tags, branches c'est à dire de restituer le contenu à un point précis de validation.

* 🔗 [checkout](https://git-scm.com/docs/git-checkout)

Naviguer sur la branche d'un commit particulier

```bash
git checkout 02e19ebbd
```

Pour revenir sur la branche principale

```bash
git checkout master
```
___

## 📑 Les branches

A l'initialisation, les engagements appartients à la branche maître.

![image](https://raw.githubusercontent.com/seeren-training/DevOps/master/wiki/resources/01/03-Branch.jpg)

Chaque nouvelle fonctionnalité devrait être développée sur une branche différente afin de ne pas compromettre l'intégrité de la branche maître qui possède les release exploitables. Quand le fonctionnalité est approuvée, elle peut fusionner avec la branche maître.

* 🔗 [branch](https://git-scm.com/docs/git-branch)

Lister les branches

```bash
git branch
```

Créer une branche

```bash
git checkout -b feature
```

Suprimer une branche

```bash
git branch -d feature
```

* 🔗 [merge](https://git-scm.com/docs/git-merge)

Fusionner deux branches

```bash
git merge --no-ff feature -m "Merge feature"
```

The `--no-ff` option disable fast forward [@see branching and merging](https://git-scm.com/book/en/v2/Git-Branching-Basic-Branching-and-Merging)

Si un merge a lieu et que vous tentez un autre merge dont le contenu correspond à celui avant le premier merge il y aura alors un conflit.

Dans ce cas vous devez régler les conflits manuellement en éditant les fichiers indiqués, en engageant le contenu avec un commit pour terminer le merge.

___

## 📑 Remote

Travaillez à distance en utilisant un dépot git de votre choix. Depuis peu github autorise la création de repository en ligne de commande mais vous pouvez aussi passer par l'interface web.

### 🏷️ **Initialisation**

* 🔗 [remote](https://git-scm.com/docs/git-remote)

Ajouter un serveur distant

```bash
git remote add origin https://github.com/[USER]/[REPO].git
```

* 🔗 [push](https://git-scm.com/docs/git-push)

Envoyer votre contenu sur le serveur pour la branche concernée

```bash
git push origin master
```

___

👨🏻‍💻 Manipulation

Le **Scrum Master** du projet doit créer un repository et pousser un README.md contenant la vision du produit et une rubrique "contributeurs" vide . Puis il doit créer une branche "dev" et la pousser.

___

Entant que **membre d'équipe** vous souhaitez récupérer une branche du projet pour ajouter une fonctionnalité. Vous devez dans un premier temps créer cette branche en faisant un `fork`.

* 🔗 [fork](https://help.github.com/en/github/getting-started-with-github/fork-a-repo)

![image](https://raw.githubusercontent.com/seeren-training/DevOps/master/wiki/resources/02/01-fork.jpg)

Un fois la branche crée vous souhaitez récupérer son contenu en local.

* 🔗 [clone](https://git-scm.com/docs/git-clone)

```bash
git clone https://github.com/[USER]/[REPO].git
```

___

👨🏻‍💻 Manipulation

Le membres d'équipe doivent forker la branche dev du projet et obtenir une copie locale en clonnant leur fork.

___

### 🏷️ **Pull**

Une fois une fonctionnalitée ajoutée par un membre d'équipe il souhaite soumettre son travail pour demander à la branche forkée de lire puis fusionner ce contenu.

* 🔗 [pull](https://help.github.com/articles/creating-a-pull-request/)

Pour ouvrir une pull request le bouton se trouve à droite de la branche associée.

![image](https://raw.githubusercontent.com/seeren-training/DevOps/master/wiki/resources/02/03-pull.png)

___

👨🏻‍💻 Manipulation

Le membres d'équipe doit ajouter leur nom à la liste des contributeurs du README et faire une pull request.

___


### 🏷️ **Merge**

Le propriétaire de la branche possédant les pull requests doit accepter de les fusionner.

* 🔗 [merge](https://help.github.com/en/github/collaborating-with-issues-and-pull-requests/merging-a-pull-request)


![image](https://raw.githubusercontent.com/seeren-training/DevOps/master/wiki/resources/02/04-merge.png)

Dans la liste des pull request, selectionner une pull request, la stratégie de commit et confirmez.

Quand vous tentez une fusion avec un contenu qui prend pour base une version antétieur à celui en cours il y aura un conflit, plusieurs solutions:
* Régler le problème à la main
* Refuser la pull request en demandant de synchroniser le contenu avec celui le plus récent

___

👨🏻‍💻 Manipulation

Le Scrum Master doit accepter la fusion les pull requests.

___


### 🏷️ **Synchronisation**

La branche qui a fusionnée le travail a un contenu différent de sa version locale. Il faut faire une lecture puis une fusion localement pour se synchroniser

* 🔗 [pull](https://git-scm.com/docs/git-pull)

```bash
git pull origin master
```

___

👨🏻‍💻 Manipulation

Le Scrum Master doit synchroniser son contenu local.

___

Concernant le membre d'équipe, soit il considère que son travail est terminé et il  suprime sa branche et il en créera une autre lors d'une prochaine tache. Ou alors il souhaite maintenir à jour sa branche par rapport à celle forkée.

* 🔗 [sync](https://help.github.com/en/github/collaborating-with-issues-and-pull-requests/syncing-a-fork)

```bash
git remote add upstream https://github.com/ORIGINAL_OWNER/ORIGINAL_REPOSITORY.git
```
Un repository de lecture est spécifié.

* 🔗 [fetch](https://git-scm.com/docs/git-fetch)

```bash
git fetch upstream
```

Après avoir récupéré le contenu up to date il faut le fusionner avec la branche désirée.

```bash
git merge upstream/master
```

___

👨🏻‍💻 Manipulation

Les membres d'équipes doivent synchroniser le contenu local.

___