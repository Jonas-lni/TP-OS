# Paris, le 12 décembre 2024       PostgreSQL


Peux-tu me donner les listes des commandes postgresql ?

## ChatGPT a dit :

ChatGPT

Voici une liste utile des commandes PostgreSQL pour différents contextes, avec une courte description pour chaque catégorie :
________________________________________
## Commandes de base :

•	**_\l_** : Liste les bases de données

•	**_\c_** [nom_bdd] : Connecté

•	**_\dt_** : Liste les tableaux

•	**_\d_** [nom_table] : Montre la structure

•	**_\du_** : Liste des utilisateurs et de leurs rô

•	**_\q_** : Quittez l'interface psql.
________________________________________
## Gestion des bases de données :

•	**CRÉER UNE BASE DE DONNÉES nom_bdd;** : Crée une nouvelle base de

•	**DROP DATABASE nom_bdd;** : Supprime une base de données.

•	**ALTER DATABASE nom_bdd RENAME TO nouveau_nom;** : Renomme une bas
________________________________________
## Gestion des tables :

•	**CREATE TABLE nom_table (...);** : Crée une nouvelle table.

•	**DROP TABLE nom_table;** : Suppr

•	**ALTER TABLE nom_table ADD COLUMN nom_colonne type;** : Ajout d'une colonne.

•	**ALTER TABLE nom_table DROP COLUMN nom_colonne;** : Supprime une colonne.

•	**TRUNCATE TABLE nom_table ;** : Vider une table de ses données.
________________________________________
## Manipulation des données :

•	**INSERT INTO nom_table (col1, col2, ...) VALEURS (val1, val2, ...);** : Ajoute une

•	**UPDATE nom_table SET col1 = val1 WHERE condition ;** : Modifier une ou plusieurs lignes.

•	**DELETE FROM nom_table WHERE condition ;** : Supprime des lignes.

•	 SELECT * FROM nom_table ; : Récupère

•	**SELECT col1, col2 FROM nom_table WHERE condition ;** : Récupère des colonnes spécifiques avec
________________________________________
## Gestion des utilisateurs :

•	**CREATE USER nom_utilisateur AVEC MOT DE PASSE 'mot_de_passe';** : Crée un nouvel utilisateur.

•	**ACCORDER TOUS LES PRIVILÈGES SUR LA BASE DE DONNÉES nom_bdd À nom_utilisateur;** : Accordez tous les privilèges à un utilisateur.

•	**RÉVOQUER TOUS LES PRIVILÈGES SUR LA BASE DE DONNÉES nom_bdd DEPUIS nom_utilisateur;** : Révoquez les privilèges d'un

•	**DROP USER nom_utilisateur;** : Supprime un utilisateur.
________________________________________
## Indexation et optimisation :

•	**CREATE INDEX nom_index ON nom_table (nom_colonne);** : Crée un ind

•	**DROP INDEX nom_index;** : Supprime un index.

•	**EXPLIQUER SÉLECTIONNER ... ;** : Analyser et retourner le plan d'exécution
________________________________________
## Commandes d'administration :

•	**_\conninfo_** :

•	**_\encodage_** : Affiche

•	**_VIDE;_** : Nettoyez et optimisez la base de données.

•	**_ANALYSER;_** : Collecte des statistiques pour le suivi des requêtes.

•	**RÉINDEXER LA TABLE nom_table;**: Réindexer une table.


