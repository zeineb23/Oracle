# TP3

Vous trouverez dans ce [lien]() la présentation utilisée dans ce TP.

## Introduction

Dans cette partie, nous allons détailler l'architecture de la base de données Oracle 11g.

## Architecture BD Oracle 11g

<p align="center">
  <img width="650" src="images/1.jpg" alt="picture">
</p>


### 1/ Instance Oracle

- Il s'agit d'accéder à une base de données Oracle
- Il démarre toujours une et une seule **instance** de la base de données

### 2/ Architecture Processus

Un processus est un mécanisme dans un système d'exploitation qui peut exécuter une série d'instructions. Certains systèmes d'exploitation utilisent les termes job ou tâche. Un processus possède généralement sa propre zone de mémoire privée dans laquelle il s'exécute.

Un serveur de base de données Oracle possède deux types généraux de processus : les processus utilisateur et les processus Oracle.

<p align="center">
  <img width="650" src="images/2.jpg" alt="picture">
</p>

#### Processus Utilisateur

- Un programme qui demande une interaction avec le serveur oracle
- Il doit d'abord établir une connexion
- Il n'interagit pas directement avec l'instance Oracle 


#### Processus Serveur

- Il interagit directement avec l'instance Oracle
- Il peut s'agir d'un serveur dédié ou partagé
- Il répond toujours aux demandes des utilisateurs

