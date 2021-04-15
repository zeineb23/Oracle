# TP3

Vous trouverez dans ce [lien](https://docs.google.com/presentation/d/1WO4ZPoTGBLJoM6L_9MnQtKQD4ziRDP0reLbJGzPV6aQ/edit?usp=sharing) la présentation utilisée dans ce TP.

## Introduction

Dans cette partie, nous allons détailler le langage de contrôle des données.

## Gestion des privilèges

Un privilège donne le droit d'exécuter certaines commandes SQL ou le droit d'accéder à certaines ressources.

Oracle possède deux types de privilèges :
- les privilèges systèmes
- les privilèges objets.

Un privilège peut être affecté (retiré) à:
- un Utilisateur,
- un Rôle
- tous les utilisateurs (PUBLIC).

Les privilèges donnent le droit de réaliser des opérations systèmes.

Ces privilèges sont classés par catégories d'objets.

Exemple de privilèges systèmes de la catégorie TABLE:
- CREATE TABLE 
- CREATE ANY TABLE
- ALTER ANY TABLE 
- BACKUP ANY TABLE
- DROP ANY TABLE 
- SELECT ANY TABLE
- INSERT ANY TABLE 
- UPDATE ANY TABLE
- DELETE ANY TABLE 
- ...

Affectation d'un privilège : 
```GRANT { system_priv | role } TO { user | role | PUBLIC }```

Révocation d’un privilège :
```REVOKE { <system_priv> | <rôle> } FROM { <utilisateur> | <rôle> | PUBLIC }```

## Gestion des rôles

Un rôle est un concept Oracle qui permet de regrouper plusieurs privilèges et /ou rôles afin de les affecter ou retirer en bloc à un utilisateur et /ou un rôle.

Un rôle facilite la gestion des privilèges.

Pour créer un rôle, il faut avoir le privilège ```CREATE ROLE```

<p align="center">
  <img width="750" src="images/1.png" alt="picture">
</p>

<p align="center">
  <img width="750" src="images/2.png" alt="picture">
</p>

Pour créer un rôle : ```CREATE ROLE rôle [ { NOT IDENTIFIED | IDENTIFIED { BY password | EXTERNALLY | GLOBALLY | USING package} ]```
avec : 
- NOT IDENTIFIED : permet de créer un rôle sans mot de passe
- EXTERNALLY : mot de passe est contrôlé au niveau de l'OS
- GLOBALLY : Rôle autorisé au niveau de l’annuaire
- USING package : rôle applicatif.

Pour supprimer un rôle : ```DROP ROLE role```

## Gestion des profils

Un profile est un concept Oracle qui permet à l'administrateur d'une base de contrôler la consommation des ressources systèmes et des mots de passes.

Pour créer un profil : ``` CREATE PROFILE profile LIMIT[ SESSIONS_PER_USER { integer | UNLIMITED | DEFAULT} ][ CPU_PER_SESSION { integer | UNLIMITED | DEFAULT } ][ CPU_PER_CALL { integer | UNLIMITED | DEFAULT } ][ CONNECT_TIME { integer | UNLIMITED | DEFAULT } ][ IDLE_TIME { integer | UNLIMITED | DEFAULT } ][LOGICAL_READS_PER_SESSION {integer | UNLIMITED|DEFAULT}][LOGICAL_READS_PER_CALL {integer | UNLIMITED|DEFAULT}][ COMPOSITE_LIMIT { integer | UNLIMITED | DEFAULT } ][PRIVATE_SGA {integer [K | M] | UNLIMITED | DEFAULT}]```
avec : 
- Session_per_user : Nombre maximum de sessions par utilisateur
- Logical_read_per_session : Nbre de blocs de données à lire pour une session
- cpu_per_session : temps CPU max par session en % de sécondes
- cpu_per_call : temps CPU pour un appel (en cas de parse, execute ou fetch) en % de secondes
- connect_time : temps écoulé maximum (en minutes)
- idle_time : temps maximum d'inactivité.
- private_sga : taille privée de la SGA allouée à un utilisateur
- unlimited : limite de la ressource illimitée
- default : prend la limite par défaut de la ressource.

## Gestion des utilisateurs
Lors de la création d'un utilisateur, il est possible de lui affecter : un mot de passe, un tablespace par défaut, un tablespace temporaire, un profile (explicite ou implicite), des quotas sur les tablespaces.

```CREATE USER user IDENTIFIED { BY password | EXTERNALLY| GLOBALLY AS‘nom_externe’ } [ DEFAULT TABLESPACE tablespace ] [ TEMPORARY TABLESPACEtablespace ] [ QU0TA { integer [ K | M ] | UNLIMITED } ON tablespace ] ...[ PROFILE profile ] [PASSWORD EXPIRE] [ACCOUNT {LOCK | UNLOCK}]```
avec : 
- Externally : utilisateur authentifié par l'OS
- globally as : accès autorisé par l’annuaire LDAP

Lors de la modification d'un utilisateur, il est possible de lui affecter : un mot de passe, un tablespace par défaut, un tablespace temporaire, un profile (explicite ou implicite), des quotas sur les tablespaces et un rôle par défaut (parmi les rôles attribués par la commande grant).

 Exemples : 
 ```ALTER USER etu1_21 IDENTIFIED BY md2000p DEFAULT TABLESPACE usersQUOTA UNLIMITED ON users QUOTA 1M ON system;```
``` ALTER USER etu1_21 DEFAULT ROLE role_etu1;```

 La suppression d'un utilisateur entraîne la suppression des objets de son schéma (tables, vues, séquences, synonymes, indexes ... ) . Le privilège drop user est requis.
 
 ```DROP USER ETU1_33;``` -> suppression d'un utilisateur lié à un schéma vide
 
 ```DROP USER ETU1_33 CASCADE; ```
 
 - CASCADE : supprime  les objets du schéma de l'utilisateur et les contraintes d'intégrité de référence (et vide la corbeille).
 Rq : les rôles créés par l'utilisateur ne sont pas supprimés.
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 