# TP 10 octobre 202
## 1- Manipulation de fichier 

L'objectif de ce TP de s'initier aux commandes ligne, relatives à la manipulation et l'édition de fichiers.

1/ #Manipulation de fichiers

1.1 Vérifier le répertoire de travail courant initial par la commande _*pwd*_:/home/jonas

1.2 Lister les fichiers présents dans ce répertoire via la commande _*ls*_: README.md TP-OS ecolo.md kabylie

1.3 Tous les fichiers sont-ils visibles ? Comment les faire apparaître ?

1.4 Créer à l'aide des commandes mkdir et touch l'arborescence suivante : figure1
(touch permet notamment de créer un fichier vide)

1.5 Renommer le fichier foto10.jpg en foto20.jpg

1.6 Se placer dans le répertoire ete24 et déplacer les fichiers situés dans le répertoire montagne dans le répertoire mer

1.7 En utilisant uniquement des chemins absolus

1.8 En utilisant uniquement des chemins relatifs

1.9 Supprimer le répertoire montagne

1.10 Quelque que soit votre répertoire courant, proposer 2 commandes permettant de retourner au répertoire initial et appliquer.

1.11 Supprimer le répertoire ete23. Que constatez-vous ? 

1.12 En vous aidant du man rm, proposer une commande supprimant un répertoire et toute l' arborescence qui en dépend (fichiers et sous-répertoires).
Appliquer cette commande pour supprimer le répertoire ete23 et ses fichiers 

1.13 Que pensez-vous des risques associés à cette commande 

1.14 Renommer le répertoire ete22 en hiver22

1.15 Copier le fichier foto20.jpg en foto20.txt dans le répertoire ete24 

l. 16 Déplacer les fichiers sous mer dans le répertoire ete21

1.17 Déplacer les fichiers foto3 sous hiver22 et les renommer foto33	

1.18 Liste en détail uniquement les fichiers ayant pour extension .txt du répertoire ete21

1.19 Déplacer l'ensemble des fichiers ayant pour extension .jpg du répertoire ete21 vers ete24 1.20 Supprimer les fichiers avec l'extension .txt du répertoire hiver22

1.20 Proposer un diagramme de la nouvelle arborescence (dans un style semblable à la figure 1).	 

1.21 A partir du man ls, trouver la(les) option(s) à ajouter à la commande ls afin d'obtenir la liste détaillée des fichiers du répertoire /usr/bin rangés dans Itordre de taille croissante avec une lecture aisée de la taille du fichier. L'usage de chaque option doit être justifiée.

# 2- Edition de fichiers

2.1 Créer un répertoire nommé exo2 et dans ce dossier, à l'aide de l'éditeur vi, créer 2 fichiers composés d'au moins 5 lignes contenant les informations suivantes :
Fichier 1 : pregen 
prénom de l'étudiant     genre (masculin, féminin, ) 

Fichier 2 : prenum 
prénom de l'étudiant     nombre entier (entre 1 et 1000) tous différents

2.2 Que proposez-vous pour optimiser la création de ces 2 fichiers ?

2.3 Visualiser rapidement les fichiers générés par la commande cat

# 3 -Quelques opérations sur les fichiers texte

3.1 Afficher les 2 premières lignes du fichier pregen

3.2 Afficher depuis la ligne 3 jusqu'à la fin du fichier prenum

3.3 En utilisant la commande wc compter le nombre de mots dans le fichier pregen puis compter le nombre de lignes du fichier prenum

3.4 Afficher uniquement la colonne des nombres du fichier prenum

3.5 Afficher le fichier prenum en triant sur les nombres du plus grand au plus petit

3.6 Réaliser un affichage synthétique des informations contenues dans les fichiers. Le résultat obtenu doit être de la forme : prénom nombre genre

3.7 Que proposez-vous si l'on souhaite les champs dans l'ordre suivant : prénom genre nombre

# 4 -Divers

4.1 Afficher l'historique des commandes

4.2 Proposer 2 façons de rejouer la dernière commande sort

