<details>
<summary>Chapitre 2 - SQL (0/8)</summary>

- Installation et configuration de PostgreSQL et pgAdmin
- Concepts de base des SGBDR et types de données
- Requêtes SQL : SELECT, CREATE, ALTER TABLE, INSERT, UPDATE, DELETE, DROP
- Utilisation de NULL et requêtes conditionnelles (CASE)
- Jointures : JOIN, sous-requêtes, CTE, et opérations ensemblistes
- Travailler avec les dates et heures
- Fonctions de fenêtrage avancées
- Fonctions SQL : CAST, CONCAT, SUBSTRING, COALESCE, etc.
</details>

# Installation et configuration de PostgrSQL et pgAdmin

## Qu'est ce que c'est?
`PostgreSQL` prend en charge les bases de données relationnelles classiques tout en offrant des fonctionnalités de programmation orientée objet. Ce qu'il faut retenir c'est qu'en plus des types de données classiques (int, str, etc) l'on peut créer son propre type complexe (Adresse : rue, ville, cp, etc) d'où le `relationnel et objet`. 
Il peut aussi prendre en compte des données sémi-structurées comme du JSON.


Exemples de création de tables dans PostgreSQL qui couvrent les trois aspects : **relationnel**, **objet** (héritage), et **semi-structuré** (JSON).

### 1. **Modèle relationnel classique** :

Le modèle relationnel consiste à utiliser des tables liées entre elles par des **clés étrangères**. Par exemple, une table `Utilisateurs` et une table `Commandes` où chaque commande est associée à un utilisateur via une clé étrangère.

#### Exemple :

```sql
CREATE TABLE Utilisateurs (
    id SERIAL PRIMARY KEY,
    nom VARCHAR(100) NOT NULL,
    email VARCHAR(100) UNIQUE NOT NULL
);

CREATE TABLE Commandes (
    id SERIAL PRIMARY KEY,
    utilisateur_id INT REFERENCES Utilisateurs(id),  -- Clé étrangère
    date_commande DATE NOT NULL,
    total NUMERIC(10, 2) NOT NULL
);
```

- **Clé primaire** : `id` dans chaque table.
- **Clé étrangère** : `utilisateur_id` relie la table `Commandes` à la table `Utilisateurs`.

### 2. **Modèle orienté objet** (héritage) :

PostgreSQL supporte l’héritage entre tables. Une table peut "hériter" d'une autre, ce qui signifie qu'elle héritera des colonnes de la table parente tout en ayant ses propres colonnes. C’est un concept emprunté à la programmation orientée objet.

#### Exemple :

```sql
-- Table parente
CREATE TABLE Personne (
    id SERIAL PRIMARY KEY,
    nom VARCHAR(100),
    age INT
);

-- Table enfant qui hérite de Personne
CREATE TABLE Employe (
    salaire NUMERIC(10, 2)
) INHERITS (Personne);
```

- **Personne** est la table parente avec des colonnes communes (`nom`, `age`).
- **Employe** hérite des colonnes de `Personne` et ajoute une colonne `salaire`.

Les entrées de la table `Employe` contiendront donc les champs `id`, `nom`, `age` et `salaire`.

### 3. **Modèle semi-structuré** (JSONB) :

Pour stocker des données semi-structurées, on utilise une colonne de type `JSON` ou `JSONB`. Cela permet de stocker des données flexibles, comme des objets JSON, sans avoir besoin de schéma rigide.

#### Exemple :

```sql
CREATE TABLE Produits (
    id SERIAL PRIMARY KEY,
    nom VARCHAR(100) NOT NULL,
    details JSONB  -- Colonne JSONB pour stocker des données flexibles
);

-- Insertion de données JSONB
INSERT INTO Produits (nom, details)
VALUES ('T-shirt', '{"couleur": "rouge", "taille": "M"}'),
       ('Chaussures', '{"pointure": 42, "marque": "Nike"}');
```

- La colonne `details` permet de stocker des informations sur les produits dans un format JSON.
- Chaque produit peut avoir des informations différentes, sans nécessiter une structure de colonnes fixes pour ces attributs.

### Combinaison des trois modèles :

Tu peux même combiner les trois approches dans une même base de données. Par exemple, en ayant une structure relationnelle avec des tables liées, une structure héritée pour les entités liées, et une colonne `JSONB` pour stocker des informations flexibles.

#### Exemple complet :

```sql
-- Table relationnelle principale
CREATE TABLE Clients (
    id SERIAL PRIMARY KEY,
    nom VARCHAR(100),
    email VARCHAR(100)
);

-- Table hérite de Clients
CREATE TABLE VIP (
    niveau VARCHAR(50)
) INHERITS (Clients);

-- Table relationnelle avec colonne JSONB pour des données semi-structurées
CREATE TABLE Commandes (
    id SERIAL PRIMARY KEY,
    client_id INT REFERENCES Clients(id),  -- Clé étrangère vers Clients ou VIP
    date_commande DATE,
    details JSONB  -- Détails de la commande en JSONB
);

-- Insertion de données avec JSONB
INSERT INTO Commandes (client_id, date_commande, details)
VALUES (1, '2024-09-12', '{"produit": "T-shirt", "quantité": 2, "couleur": "rouge"}');
```

- **Clients** est la table relationnelle principale.
- **VIP** hérite de la table `Clients` et ajoute un champ spécifique pour les clients VIP.
- **Commandes** est liée à `Clients` via une clé étrangère et inclut une colonne `JSONB` pour des données semi-structurées sur les commandes.


Cela montre la polyvalence de PostgreSQL pour modéliser des données relationnelles, objets et semi-structurées au sein d'une même base de données.

# Type de données
- Structurées : table SQL, fichers Excel
- Sémi-structurées : JSON, XML, YAML
- Unstructured : Graphe, Vidéos, Images, Audios, Textes, Documents

# Requêtes SQL
1. SELECT :
C'est la requête la plus courante, utilisée pour récupérer des données d'une ou plusieurs tables.

Exemple :
```sql
SELECT nom, prénom FROM employés WHERE département = 'Ventes';
```
Cette requête sélectionne le nom et le prénom de tous les employés du département Ventes.

2. CREATE :
Utilisée pour créer de nouveaux objets dans la base de données, comme des tables, des vues, des index, etc.

Exemple pour créer une table :
```sql
CREATE TABLE clients (
    id INT PRIMARY KEY,
    nom VARCHAR(50),
    email VARCHAR(100)
);
```

3. ALTER TABLE :
Permet de modifier la structure d'une table existante, comme ajouter ou supprimer des colonnes.

Exemple pour ajouter une colonne :
```sql
ALTER TABLE clients ADD COLUMN téléphone VARCHAR(15);
```

4. INSERT :
Utilisée pour insérer de nouvelles lignes de données dans une table.

Exemple :
```sql
INSERT INTO clients (nom, email) VALUES ('Dupont', 'dupont@email.com');
```

5. UPDATE :
Permet de modifier des données existantes dans une table.

Exemple :
```sql
UPDATE employés SET salaire = salaire * 1.1 WHERE performance = 'Excellent';
```
Cette requête augmente de 10% le salaire des employés ayant une performance excellente.

6. DELETE :
Utilisée pour supprimer des lignes d'une table.

Exemple :
```sql
DELETE FROM clients WHERE dernière_commande < '2020-01-01';
```
Cette requête supprime les clients n'ayant pas commandé depuis le 1er janvier 2020.

7. DROP :
Permet de supprimer des objets de la base de données, comme des tables ou des vues.

Exemple pour supprimer une table :
```sql
DROP TABLE anciens_clients;
```

# Schéma, Vue
1. Vue : Table virtuelle basée sur une requête SQL, ne stockant pas de données physiques. C'est comme un lonng `SELECT` que l'on garde de côté et que l'on appelle quand il le faut (différent d'une fonction)

Exemple :
```sql
CREATE VIEW employés_ventes AS
SELECT nom, salaire FROM employés WHERE département = 'Ventes';
```

2. Schéma : Conteneur logique pour regrouper des objets de base de données (tables, vues, etc.).

Exemple :
```sql
CREATE SCHEMA ventes;
CREATE TABLE ventes.produits (id INT, nom VARCHAR(50));
```

# - Utilisation de NULL et requêtes conditionnelles (CASE)
Il s'agit ici de faire des requettes conditionnelles.
```sql
SELECT 
    nom, 
    CASE 
        WHEN salaire > 55000 THEN 'Salaire élevé'
        WHEN salaire <= 55000 THEN 'Salaire standard'
        ELSE 'Non spécifié'
    END AS categorie_salaire 
FROM employes;
```
Cette requeste  crée une colonne `categori_salaire` qui pour chaque nom va valoir `Salaire élevé` si salaire > 55000, `Salaire standar` si salaire <= 55000 et `Non spécifié` sinon (au cas on a une valeur NULL de salaire par exempe).