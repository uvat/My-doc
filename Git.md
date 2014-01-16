![git icon](http://git-scm.com/images/logo@2x.png)

##Présentation


Git est un logiciel de gestion de versions décentralisées, enregistrant un historique complet du projet localement. Il permet une sauvegarde, un versioning, un travail collaboratif simplifié. Comme il est stocké localement il permet de travailler sans dépendre constamment du serveur distant.

#####Cycle de vie d'un petit projet git :

1. Clone d'un dépo distant ou initialisation d'un nouveau projet.  
Tous les fichiers sont alors indexés dans la base git locale.
Il crée alors un __instantané__ du projet.

2. Quand des fichiers sont édités, git les considère comme modifiés, car ils ont été modifiés depuis le dernier instantané. Il faut alors indexer ces fichiers pour que git les prennent en compte au prochain instantané.

3. Pour travailler sur les branches, celles-ci doivent être créées en local pour ensuite les connecter au repos distant.

_Lors d'un changement de branche. Les fichiers seront placés sur le disque par git depuis sa base de données (où se trouve toutes les sources de toutes les branches)._

_Lors de l'ajout d'un nouveau fichier, celui-ci n'est pas indexé automatiquement dans la base. IL faut alors l'ajouter dans la base de git pour que celui-ci le prenne en compte._

Git gère ses fichiers de la façon suivante :

* __Modifié__ signifie que le fichier a été modifié mais qu'il n'a pas encore été validé en base. 
* __Indexé__ signifie qu'un fichier modifié a été marqué par l'utilisateur dans sa version actuelle pour qu'il fasse partie du prochain instantané du projet. 

Aperçu du cycle de vie des états du fichier:

![git status](http://git-scm.com/figures/18333fig0201-tn.png)

Aperçu des branches

![git branch](https://wiki.duraspace.org/download/attachments/23267391/img.branch.png?version=1&modificationDate=1294385216624&api=v2)


##Configuration

*L'option `--global` permet de renseigner les infos pour tous les projets git susceptibles d'être sur le disque.*

#####Nom & adresse mail

	git config --global user.name "John Doe"
	git config --global user.email johndoe@example.com

#####Éditeur de texte
(Quand git demande de saisir un message)

	git config --global core.editor emacs

#####Voir tous les paramètres

	git config --list
	
##Terminologie

* __Repo, Repository :__  Base de données où est stocké tout l'historique et les configurations. C'est là où seront stockés les éventuelle branches

* __Index, Staging area :__ C'est là où sont stockées toutes les données modifiées ajoutées à git. C'est d'ici que seront prises les données lors de commits

* __Clone :__ Comme son nom l'indique c'est le clone d'un repo. vers un nouveau repo.

* __Commit :__ Enregistre l'état du projet à un certain moment

* __Branch :__ Contient les différentes "sources" et commits. (Master, dev ect…)

* __A head :__ Le dernier commit d'une branche

* __HEAD :__ Un nom symbolisant le dernier commit courant

* __Tag:__ Nom décrivant un commit. Il peut aussi contenir un message.

* __Stash :__  Enregistre sans commiter l'état en cours du répertoire de travail, (fichiers modifiés et l'index).

##Cheat Sheet

####Obtenir de l'aide

	git help <commande>

####Démarrer un repo.

	git init
	git clone <repo url>
	git clone <repo url> <folder name>

####Voir les changements

Fichiers modifiés

	git status
	
Comparer les changements des fichiers avec le dernier commit

	git diff
	git diff <filename>

Comparer les changements entre deux différents commits

	git diff <commit id> <commit id>
	
Historique des changements

	git log
	

####Annuler les changements

Retourner vers le dernier commit (ne supprime pas les fichiers non indexés)

	git reset –hard
	
Annuler le dernier commit et en créer un nouveau

	git revert HEAD
	
Annuler vers un commit précit

	git revert <commit id>
	
	
####Indexer des fichiers

Indexer tous les fichiers (nouveaux, modifiés & supprimés)

	git add -A
	
Indexer les fichiers nouveaux et modifiés (pas les supprimés)

	git add .
	
Indexer les fichiers modifiés et supprimés (pas les nouveaux)

	git add -u

Supprimer un fichier de la base git

	git rm <filename>

####Publier

Commiter les changements qui sont indexés

	git commit -m “message”

Indexer tous les fichiers modifiés ou supprimés (pas les nouveaux) et commit

	git commit -am “message”
	
Enregistrer sans commiter l'état en cours du répertoire de travail (fichiers modifiés et l'index).

	git stash

Voir la liste des stashs

	git stash list
	
Ré-appliquer le contenu du dernier stash

	git stash apply

Ré-appliquer le contenu d'un stash précis

	git stash apply <stash id>

Supprimer un stash

	git stash drop <stash id>

Envoyer les changements vers l'origine

	git push
 	
Envoyer une branche spécifique vers l'origine

	git push origin <local branch name>
	

####Récupération des sources

Récupérer les derniers changements de l'origine (ne merge pas)

	git fetch

Récupérer les derniers changements de l'origine et merge

	git pull
	
Récupèrer une branche de l'origine vers une branche locale (la créer et switch dessus)
	
	git checkout -b <new branch name> origin/<branch name>
	
####Les branches

Voir toutes les branches (locales)

	git branch
	
Voir toutes les branches locales et remote

	git branch -a
	
Créer une nouvelle branche

	git branch <branch name>
	
Merger un branche spécifique vers la branche master

	git checkout master
	git merge <branch name>
	
Supprimer un branche local et remote

	git push origin –delete <branch name>
	
Merge un seul commit d'une autre branche vers la branche courante

	git cherry-pick <commit id>
	
####Bonus

Visualiser l'historique

	git log --graph --format="%Cgreen%h%Creset %Cred-%Creset %Cblue%s%Creset %n%m %cN (%cE)"
    git log --graph --format="%Cgreen%h%Creset %Cred-%Creset %Cblue%cN (%cE)%Creset %n%B"
	
##Pour bien comprendre

### La doc Git

<http://git-scm.com/docs>

<http://gitref.org/>

### Faire ce tutoriel de github

<http://try.github.io/levels/1/challenges/1>
	


	




