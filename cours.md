Brouillon :

Note = Markdown (.md)

Commandes :

i = insertion

echap = sortie insertion

wq = save et quitter

vim .(nomfichier) = entrer dans l edition du fichier

-------------
**Vocabulaire**

SVN = Apache Subversion (systeme de controle de version "centralisé")

CVS = Concurent Version System (remplacé par SVN en 2000)

Checkout = Action en Ligne

Commit = Action Locale

Branching et Merging = SVN gere les les branches et fusions

-------------
### 1. Intro Versioning

__Permet au dev :__
- Revenir a des versions anterieurs et revenir version actuel
- Comparaison des changements
- Determiner qui à mis à jour
- Travailler en parallèle du document

__Importance (terme):__
- Tracabilité
- Collaboration
- Backup et rétablissement
- Branching et Merging

__Nomenclature (Vocabulaire):__
Permet d'identifier les versions et ajouts
- **MAJEURE :** indique version de changement incompatible avec les versions anterieures
- **MINEURE :** indique les ajouts de nouvelles fonctionnalités de maniere retrocompatible
- **CORRECTIF :** indique les corrections de bug


### 2. Git
Avec Git, la casi totalité des opérations sont locales.
Git se charge de gerer l'intrégrité des données.

A savoir, Git effectue une "somme de controle" qui permet de verifier l'intégrité des données et qu'il est impossible de modifier un fichier sans que Git ne le sache.

Avec Git, peu d'opérations sont destructives.

Git appelle un empreinte SHA-1 et une chaine de caractere de 40 caracteres hexadecimaux ressemble à ça :
```
24asd25as87sd5544as5dsa65as4d5asd54854fe
```

### 3. Commandes Git

#### Savoir les informations git :
```
git config --list --show-origin
```
#### Configurer l'identité
```
git config --global user.name "x"
git config --global user.email "x"
```

#### Editeur de texte
```
git config --global core.editor "C:\Program Files\editeur"
```

#### Obtenir de l'aide
```
git help
```

#### Créer le dépot
```
git init
```

#### Supprimer le dépot
```
rm -rf .git/
```

-------------
## Mettre les fichiers locale en ligne
### 1. Vérifier l'état du dépot
```
git status
```
-------------
### 2. Ajouter tous les fichiers liste d'attente d envoie
```
git add .
```
-------------
### 3. Pour Valider la liste (commit)
```
git commit
git commit -m "message"

# Annuler la validation
git commit --amend
```
#### Annuler les validations
```
git commit --amend
```

#### Modifier le dernier commit
```
git reset HEAD <fichier>
```
-------------
### 4. Synchro Locale en Ligne de la liste validée
```
git push -u origin main (or master)
git push
```

-------------
#### Ignorer des fichiers
```
modifier le "gitignore" en rajouter par ligne le nom des fichiers et/ou dossier a ignorer
```

#### Affiche les modifications effectuer
```
git diff
```


#### Effacer un fichier
```
1. rm <fichier>

2. git status

3. git rm <fichier>
```
-------------
### Git Log

Voici une liste de git log puissante :
```
git log -p -2
git log --stat
git log --pretty=oneline
git log --pretty=format:"%h %s" --graph
```
-------------
### Tag
#### Lister les Tags
```
git tag
```
#### Créer un Tag sur le commit actuel
```
git tag -a v1.0 -m "Version 1.0"
```
#### Filtrer dans la liste
```
git tag -l "v1.8.5*"
```
-------------
###  Branches
#### Créer une Branche
```
git branch <nom de la branche>
```

#### Merge
```
git merge <branch>
```
#### Envoyer les modifications sur une branche
```
git push <distant> <branche>
git push origin master
git push -u origin master
```
#### Récuperer les modifications
```
git fetch <distant>
```
#### Récupération des fichiers + fusion locale 
```
git pull <distant> <branche>
```

Lorsqu'on recup les branches distantes avec fetch, pas de création auto d'une branche locale,
il faut créer la branche et la lié a la branche distante
```
git checkout -b <branche> <distant>/<branche>
```
#### Raccourci de la commande au dessus
```
git checkout --track <distant>/<branche>
```
#### Se connecter sur une branche
```
git checkout <branche>
```
#### Pour visualiser
```
git fetch -all
git branch -vv
```
#### Supprimer une Branche en ligne et non Locale
```
git push origin --delete <branche>
```
-------------
#### Deux manieres d integrer les modif d'une branche a une autre
- La fusion (merge)
- Le rebasage (rebase)

merge :
git checkout master
git merge experiment

rebase :
git checkout experiment
git rebase master

tout l'historique a été supprimer de la branche sur laquelle on est situé
Ca permet de linéariser l historique des commits
Le rebase n'est a utilisé qu'en cas de besoin important à cause d'une quantité de branche

#### Essate d extraire la branche client de la branche server et de la rebaser sur la branche master
```
git rebase --onto master server client
```
```
git checkout master
git merge client
```
On peut aussi rebaser server sur master
```
git rebase master server
```
Puis merge server dans master
```
git checkout master
git merge server
```
### Ne Jamais rebase des modifications qui ont été publiées sur un server distant (push)