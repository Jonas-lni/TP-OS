# TP Système d'Exploitation du 30 octobre 2024

## Avec Monsieur GIRAULT

## Prérequis: Machine sous Linux, Shell Bash 

## Grep, Find, Pipe, Redirection

Ecrire les commandes permettant de :

1.1 Compter le nombre de ligne contenant "bin" dans le fichier /etc/passwd :

	cat /etc/passwd | grep bin | wc -l   
ou

	cat /etc/passwd | grep bin -c

1.2 Compter le nombre d'occurence de "bin" dans le fichier passwd : 
