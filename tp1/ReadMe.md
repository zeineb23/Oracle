# TP1

Vous trouverez dans ce [lien]() la présentation utilisée dans ce TP.

## SGBD ?

Un système de gestion de base de données est un logiciel qui permet de 
stocker des informations dans une base de données ainsi, il nous permet de
**Lire / Écrire / Modifier / Trier / Transformer / Afficher
les données**

## Rappel

Les commandes SQL sont divisées en quatre sous-groupes, DDL, DML, DCL et TCL :

- **Data Definition Language** : DDL qui traite des schémas et des descriptions des bases de données, de la manière 
dont les données doivent résider dans la base (Create / Alter / Drop / Truncate / ..).
- **Data Manipulation Language** : DML qui manipule des données et comprend les instructions SQL les plus courantes 
telles que SELECT, INSERT, UPDATE, DELETE, etc. et qui est utilisé pour stocker, modifier, récupérer, supprimer et mettre à jour des données dans une base de données.
- **Data Control Language** : DCL qui comprend des commandes telles que GRANT 
et qui concerne principalement les droits, les autorisations et autres contrôles du système de base de données.
- **Transaction Control Language** : TCL qui traite d'une transaction au sein d'une base de données.

## Transaction ?

C'est une séquence d’opérations de lecture ou de mise à jour sur une base de données, 
se terminant par l’une des deux instructions suivantes : **Commit / Rollback**.

![Image 1](images/1.png)

## Propriétés des transactions

![Image 2](images/2.png)

- **Atomicité** : soit tous les éléments sont validés, soit aucun ne l'est. La transaction se fait donc entièrement ou pas du tout.
- **Cohérence** : une transaction crée un état des données nouveau et valide, soit, en cas de panne, elle rétablit toutes les données dans l'état qui était le leur avant le début de la transaction.
- **Isolation** : une transaction en cours, doit rester isolée de toutes les autres.
- **Durabilité** : les données validées sont enregistrées par le système de sorte que, même en cas de panne et de redémarrage du système, ces données restent disponibles dans leur état correct. 


