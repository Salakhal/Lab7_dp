# Lab 7 : Transactions, Verrouillage et Sécurité (MySQL)

Ce projet présente la mise en œuvre de la gestion des transactions, des niveaux d'isolation et de la sécurité des accès dans un environnement MySQL.

## 📁 Contenu du dépôt

* **`lab7_transactions_securite.sql`** : Le script principal contenant la création de la base `banque_demo`, les tables, et les exemples de transactions (COMMIT/ROLLBACK).
* **`session1.txt`** : Log de la première console MySQL montrant l'ouverture des transactions et la mise en place des verrous (`FOR UPDATE`).
* **`session2.txt`** : Log de la deuxième console montrant les tentatives d'accès concurrents, le blocage par verrou et les tests d'isolation.
* **`/screenshots/`** : Dossier contenant les preuves visuelles des tests de verrouillage et de sécurité.

## 🛠️ Points Clés du Lab

### 1. Gestion des Transactions
Mise en œuvre du principe ACID à travers des virements bancaires entre Alice et Bob :
* **COMMIT** : Validation définitive des changements après un virement réussi.
* **ROLLBACK** : Annulation des modifications en cas d'erreur ou de solde insuffisant.

### 2. Niveaux d'Isolation et Verrouillage
Tests effectués dans les fichiers `session1.txt` et `session2.txt` :
* **Isolation** : Observation des différences entre `READ COMMITTED` et `REPEATABLE READ`.
* **Verrous explicites** : Utilisation de `SELECT ... FOR UPDATE` pour bloquer une ligne et empêcher des modifications concurrentes jusqu'à la fin de la transaction.

### 3. Sécurité et Privilèges
Création d'un utilisateur `app_user` avec des droits restreints :
* **Privilèges accordés** : `SELECT`, `INSERT`, `UPDATE`.
* **Privilèges refusés** : `DELETE`, `DROP`.

## 📸 Captures d'écran des tests

### 1. Test d'Isolation (READ COMMITTED)
Le solde passe de **800.00** à **900.00** dans la Session 1 après le COMMIT de la Session 2, confirmant le niveau d'isolation.
![Ex1](https://github.com/user-attachments/assets/dd2ab517-4e1e-43c6-b1cc-c0f537582560)


### 2. Démonstration du blocage par verrou (Lock)
La Session 2 est bloquée par le `FOR UPDATE`. de la Session 1, entraînant l'erreur `Lock wait timeout exceeded`.
![Ex2](https://github.com/user-attachments/assets/63721078-0556-44ee-90dc-c5ea7cb86090)


### 3. Démonstration de la sécurité (Refus de permission)
Refus de la commande (DELETE) pour l'utilisateur `app_user`. (Erreur 1142), confirmant la restriction des privilèges.
![Ex3](https://github.com/user-attachments/assets/2809eead-0c42-42a2-8d86-55ceeb0a0282)


