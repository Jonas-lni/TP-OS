# TP Système d'Exploitation du 30 octobre 2024

## Avec Monsieur GIRAULT

## Prérequis: Machine sous Linux, Shell Bash 

## 1/ Grep, Find, Pipe, Redirection

Ecrire les commandes permettant de :

**1.1 Compter le nombre de ligne contenant "bin" dans le fichier /etc/passwd :**

	cat /etc/passwd | grep bin | wc -l   
ou

	cat /etc/passwd | grep bin -c

**1.2 Compter le nombre d'occurence de "bin" dans le fichier passwd :** 
	
	cat /etc/passwd|grep bin -o|wc -l

**1.3 Afficher les lignes contenant le mot "bin" et pas "sbin"**

	cat /etc/passwd|grep bin| grep -v sbin

ou

	grep bin /etc/passwd |grep -v sbin

**1.4 Création d'un fichier nommé nologin.txt contenant uniquement les lignes ne contenant pas "nologin"**

	cat /etc/passwd | grep -v nologin > nologin.txt

**1.5 Afficher le numéro des 4 premières lignes ne contenant pas "nologin"**

	
	cat /etc/passwd |grep -vn nologin|head -4

ou 

	grep -vn "nologin" /etc/passwd|head -4

**1.6 Trouver tous les fichiers de l'arborescence /etc contenant mon nom de login ecrit indifféremment en majuscule ou miniscule**

	grep -r jonas *

et 
	sudo grep -r jonas *

**1.7 Recherche des fichiers de l'arborescence /etc/ contenant dans leur nom l'expression "tab" et ecrire le résultat dans le fichiers filtabl.txt**

	find /etc -name "*tab*" > filtab.txt


**1.8 Affichage de Yes si le fichier /etc/passwd contient le terme login et No si ce n'est pas le cas :**
		
	grep -q "login" /etc/passwd && echo "Yes" || echo "No"

ou

	cat /etc/passwd|grep -q "login" && echo "Yes" || echo "No"

**1.9 Le résultat était "No" lorsque j'ai tapé la commande:**

	grep -q "login" /etc/password && echo "Yes" || echo "No"

**1.10 pour éviter les message complémentaire nous pouvons rediriger vers /dev/null**

_**exemple:**_

	grep -q "login" /etc/password && echo "Yes" || echo "No"> /dev/null

## 2/ Tubes nommés

	#!/bin/bash
	mkfifo ~/testing/tube0 2>/dev/null
	mkfifo ~/testing/tube1 2>/dev/null
	mkfifo ~/testing/tube2 2>/dev/null
	fot i in {1..20}
	do
	   tirage=${RANDOM}
	   choix_tube=`expr $tirage % 3`
	   echo -e "iteration=$i \t tirage=$tirage \t prochain tube=$choix_tube"
	   echo -n $tirage", " > ~/testing/tube$choix_tube
	   sleep 0.3
	done


**2.1 Explication des ligne en gras**

	mkfifo ~/testing/tube0 2>/dev/null


-> est la création d'un tube nommé **tube0** dans le dossier **testing** qui se trouve dans ~/ **home**. **2>** est la redirection des messages d'erreur vers **/dev/null** pour que les données d'erreur soient ignorées 

	choix_tube=`expr $tirage % 3`

->**choix_tube=** est l'attribution d'une valeur à une variable nommée **choix_tube** . **expr** est utilisée pour manipuler des chaines de caractères, dans ce cas, elle est utilisée pour faire une division modulaire avec le **%** et **$tirage** la valeur de la variable tirage . **%3** c'est pour renvoyer le reste de la division 

	echo -n $tirage", " > ~/testing/tube$choix_tube

-> Elle écrit dans un fichier qui a un nom en fonction de la variable choix_tube. le résultat est une valeur suivi d'une virgule


**2.2 Le fonctionnement du script** est la création de trois tubes 

**3.2 La commande cat ~/testing/tube N° nous permet de lire et d'observer le tube**


## 3/ Alias et configuration Bash 

**3.1 Proposition d'un alias permettant de lister les fichiers d'un répertoire sans la couleur mais en suffixant les répértoires par le caractére / pour les identifier**

	alias lsnocolor='ls --classify --color=never'

**3.2 Proposition d'un alias ayant pour nom ptxt qui retourne la chaine "X fichiers txt présent" ou le nombre X représente la quantité de fichiers avec l'extension .txt présents dans le répertoire courant duquel la commande est lancée, rien sinon** **_elle est un peu difficile pour moi_**

**3.3 Proposition d'une méthode pour que ces alias soient persistants après un reboot**

Pour rendre les alias persistants après une résolution, il faut les enregistrer dans le fichier de configuration du shell que vous utilisez (par exemple, .bashrcou .zshrcselon votre shell). Voici comment procéder

## 4/ Utilisateurs

**4.1 Création des utilisateurs Albert Einstein et Niels Bohr ayant pour nom de login respectifs einstein et bohr**

**4.2 Initialisation des mots de passe à albert pour einstein et niels pour bohr**

**4.3 Création de groupe nommmé physiciens**

**4.4 Ajout d'einstein et de bohr dans le groupe**

**4.5 Connection comme einstein grâce à la commande su - einstein dans un nouveau terminal**

**4.6 Vérificationdes identifiants en tant qu'einstein**

**4.7 Si Bohr est absent plusieurs semaines, dans le cadre de la sécurité je propose le vérouillage du compte bohr dans le compte administrateur**

**4.8 Réinitialisation du mot de passe de bohr à la valeur henrik**

**4.9 Se connecter dans un nouveau terminal comme bohr**

**4.10 Création d'un fichier dans le homedir**

**4.11 Changement de groupe pour aller dans le groupe physiciens**

**4.12 Création d'un nouveau fichier dans le homedir**

**4.13 réalisation d'un listing détaillé des 2 fichiers crées**

