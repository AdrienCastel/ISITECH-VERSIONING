Brouillon :

Note = Markdown (.md)

Commandes :

i = insertion

echap = sortie insertion

w = ecrire et quitter

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
#### 1. Vérifier l'état du dépot
```
git status
```

#### 2. Ajouter tous les fichiers poru validation
```
git add .
```

#### 3. Pour commit
```
git commit
git commit -m "message"
```

#### 4. Synchro Locale en Ligne
```
git push -u origin main
```