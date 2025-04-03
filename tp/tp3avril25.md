TP 3 avril 2025 
# Installation d'applications

Mise en place des services : ssh 

## Notions:

SSO 

Jetons

Applicarions : graphisme, jeu,....

Il y aplusieurs façon de gerer les applications sur une machine linux

Les applicarions sont développès par des développeurs 

Compiltation

Fichiers souirces : la ou est le code 

On vous donne le code et vous recompiler 

Compliser, assembler du code pour faire du code 

Recompiler linux depuis le début

Méthode pour refaire l'applicartion  : avantage et inconvenients

Apt install : le systeme a ete capable d'aller chercher l'application et l'installer 

Il a ete capable de chercher , il a su prendre la bonne application et l'installer , dans l'application , il y a le binaire, le pass, il y a la doc, il y a les man (manuel) 

Librairie, 

modules

Dépendances

Un programme souvent a plusieurs dépendances 

Packages compilés

Pour les distribution debian, ubuntu c'est **.deb**

Pour Fedora et Redhat la terminaison est **.rpm**

_Les autres format:_  Appimage, Snap, FlatPak, Shell 

Les sources sont compréssées et archivées  **.tar.gz**

Décompression

Lecture et README : manuel d'installation 

Compilation associées au langage utilisé par le développeur - nécessaire 

**Il faut lire la doc du développeur pour récompiler**

**MAKEFILE** a générer via la commande configure 

* * *

### 📌 **Définition de la Compilation**  

La **compilation** est le processus de traduction d’un code source écrit dans un langage de programmation de haut niveau (comme C, C++, Java) en un langage machine compréhensible par l’ordinateur (binaire, exécutable).  

Ce processus est réalisé par un **compilateur**, un programme qui analyse, transforme et optimise le code avant de générer un fichier exécutable.  

---

### 🔍 **Étapes de la Compilation**  

1. **Prétraitement** (uniquement pour certains langages comme C/C++)  

   - Remplace les macros et inclut les fichiers (`#include`, `#define` en C).  

2. **Analyse lexicale**  

   - Transforme le code source en **tokens** (mots-clés, identifiants, opérateurs...).  

3. **Analyse syntaxique**  

   - Vérifie que le code respecte la grammaire du langage et construit un arbre syntaxique.  

4. **Génération de code intermédiaire**  

   - Crée une version simplifiée du code avant l’optimisation.  

5. **Optimisation du code**  
   - Améliore l’efficacité (réduction de la mémoire, optimisation des boucles, etc.).  

6. **Génération du code machine**  

   - Produit le fichier exécutable (`.exe` sous Windows, `a.out` sous Linux).  

---

### 🎯 **Exemple : Compilation en C**

Avec `gcc` :  
```bash
gcc -o programme programme.c
```
Cela traduit `programme.c` en un fichier exécutable `programme`.  

---

### ⚡ **Compilation vs. Interprétation**  
- **Compilation** : traduit tout le code avant l’exécution → Plus rapide une fois compilé (ex. C, C++).  
- **Interprétation** : traduit et exécute ligne par ligne → Plus flexible, mais plus lent (ex. Python, JavaScript).  

Veux-tu un schéma explicatif ? 😊

Les dépots officiels sont vérifiés mais des failles de sécurité peuvent s'y trouver 

- Package au format .deb (debian) 
- outil dpkg poiur installer, supprimer .etc
  **dpkg -i (install)**
  **dpkg -r (remove)**
  **dpkg -contents** il liste le contenu d'un paquet 

- Package au format .rpm
 **rpm -ivh** Installation 
 ....... voir la fiche 

 **Gestion des paquets : permet**
 - installation 
 - La mise à jour
 - La désinstallation d'application
 - La gestion des dépendances 
 - La mise à jour du SE

* * *
### apt veut dire (advance packaging tool)
### Redhat : yum, dnf

Il y a des dépots officiels et des dépots miroir 

Le miroir sert à installer sur une machine les packages de linux (ubuntu..)  et les autres machines du réseau viendront chercher les packages de la machine sur laquelle ils ont été installés -> cette méthode permet au machine d'avoir leurs application sans se connecter à internet 

il y a des applications pour faire des copies de dépots ( des packages)

**Recherches à faire:** pour comprendre 
Gestionnaire de packets : voir sur chat gpt et google
Probleme de sécurité 
contenarisation 
snap : régulation 
la commande **mount** 

apt remove 
***
#Fichiers de configuration apt : voir la fiche  

***

avantage /inconvénients d'un gestionnaire de paquets 

*** 

Rester dans le monde **apt** généralement tout se passe bien 

- **AppImage**: une application, il y a un fichier , c'est un fichier qui contient tout -> on poeut les avoir dans une clè USB
- **Snap**: contient l'intégralité des dépendances : le gros avantages c'est qu'il se met à jour tout le temps. ce qui est bien, c'est que ça exécute les applications d'une manière isolées, il est plus volumineux que AppImage
C'est long au démarrage
C'est un code qui est propriétaire de Canonical
avec snap on peut avoir deux installations d'un meme programme en même temps, ce qui permet d'avoir deux configurations de la meme application pour répondre à deux besoins différents 
- **Flatpak** : chercher pour comprendre 

***
# il faut vérifier la sécurité de que nous téléchargeons
***


La copilation : 

Copier les lib installées de raylib dans lib de **usr**
copier les includes installées  de raylib dans include de **usr**

puis compiler avec la commande : gcc -o pacman PACMAN_final.c -lraylib -lm -lpthread -ldl -lrt

puis on éxecute ./pacman et ça marchera 

**voir et chercher sur la librairie REYLIB** chercher et comprendre 
**voir sur la librairie PACMAN et chercher** 

https://github.com/thirumuruganra/PACMAN-using-C-and-RAYLIB?tab=readme-ov-file#installing-raylib

Voir la documentation du lien ci-dessus 
Suivre les étapes : étape par étape
