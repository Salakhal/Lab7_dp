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

### Démonstration du blocage par verrou (Lock)
Ci-dessous, la session de droite tente un `UPDATE` mais reste bloquée car la session de gauche a posé un verrou explicite (`FOR UPDATE`).
*(Assure-toi que le nom du fichier dans le lien ci-dessous correspond exactement au nom de ton image uploadée)*
![Blocage de session](screenshots/capture_blocage_lock.png)

### Démonstration de la sécurité (Refus de permission)
Ci-dessous, l'utilisateur restreint `app_user` tente une commande `DELETE`, qui lui est refusée par le système.
*(Assure-toi que le nom du fichier dans le lien ci-dessous correspond exactement au nom de ton image uploadée)*
![Erreur de permission](screenshots/capture_erreur_permission.png)
