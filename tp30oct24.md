# TP Système d'Exploitation du 30 octobre 2024

## Avec Monsieur GIRAULT

## Prérequis: Machine sous Linux, Shell Bash 

## Grep, Find, Pipe, Redirection

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


**1.8 Affichage de Yes si le fichier /etc/passwd contient le terme login et No si ce n'est pas le cas :
		
	grep -q "login" /etc/passwd && echo "Yes" || echo "No"

ou

	cat /etc/passwd|grep -q "login" && echo "Yes" || echo "No"
**1.9 

