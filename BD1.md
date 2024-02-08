# Introduction à SQL et Oracle SQLPlus

## Système de Gestion de Base de Données (SGBD)

Un SGBD (Système de Gestion de Base de Données) est un logiciel permettant de stocker, organiser et gérer des données de manière structurée. Il assure la gestion des accès concurrents, la sauvegarde, la récupération et l'intégrité des données.

## Base de Données Relationnelle

Une base de données relationnelle organise les données sous forme de tables, liées entre elles par des relations. Chaque table est composée de lignes (tuples) et de colonnes (attributs).

### Exemples

| Produit        | Catégorie     | Prix (USD) | Stock Disponible |
|----------------|---------------|------------|------------------|
| Stylo bleu     | Papeterie     | 1.99       | 150              |
| Ordinateur portable | Électronique | 899.99     | 20               |
| Lampe de bureau| Maison        | 14.50      | 75               |
| T-shirt noir   | Vêtements     | 19.99      | 100              |
| Plante d'intérieur | Jardinage  | 29.95      | 50               |

## Modèle EA

**Le modèle entité association représente la structure de la base de données.**  
Permet de concevoir des bases de données en représentant les entités, les relations et les attributs.


![Schema](https://web.csulb.edu/colleges/coe/cecs/dbdesign/img/association-custorder.svg)

### Entité
Une entité représente un objet du monde réel qui peut être différencié des autres objets. Par exemple, dans une base de données d'une entreprise, des entités pourraient être "Employé", "Client", "Produit", etc.
### Attribut :
Un attribut est une propriété ou une caractéristique d'une entité. Par exemple, un employé peut avoir des attributs tels que "Nom", "Numéro d'employé", "Poste", etc.
### Relation :
Une relation représente une association entre deux entités ou plus. Par exemple, une relation entre les entités "Employé" et "Département" pourrait être "Travaille pour".
### Cardinalité :
La cardinalité d'une relation indique le nombre d'entités associées de chaque côté de la relation. Par exemple, la relation "Un employé travaille pour plusieurs départements" peut être exprimée comme "1:N" (un-à-plusieurs) en termes de cardinalité.
### Attributs de Relation :
Certains modèles entité-association permettent d'attribuer des propriétés aux relations elles-mêmes. Par exemple, une relation "Achète" entre "Client" et "Produit" pourrait avoir un attribut "Date d'achat".

### Types de Données

Les types de données définissent le genre d'informations qu'une colonne peut contenir. Dans notre exemple, nous utilisons les types suivants :
- `VARCHAR2(N)` pour les chaînes de caractères de taille N (par exemple, "Produit", "Catégorie").
- `NUMBER(N, D)` pour les nombres de N chiffres dont D après la virgules(par exemple, "Stock Disponible" ou "Prix").
- `CHAR(N)` Une suite de N caractères. Taille fixe.
- `DATE` Spécifiant une date. le `TO_DATE('01-01-2001', 'DD-MM-YYYY')` peut être utilisé pour spécifier une date. Attention à rester dans des dates valides.

### Domaines

Le domaine représente l'ensemble des valeurs possibles pour un type de données donné. Dans notre exemple :
- Le domaine de la colonne "Produit" est l'ensemble des noms de produits.
- Le domaine de la colonne "Prix" est l'ensemble des valeurs décimales pour les prix.
- Le domaine de la colonne "Stock Disponible" est l'ensemble des valeurs entières pour le stock.

## Passage du modèle EA au Schéma relationnel

- **Une entité devient une table**
- Associations binaires:
  - **Un à plusieurs (1-n)**: La clé primaire de la table coté cardinalité max 1 est dupliqué dans la table coté cardinalité max n où elle devient clé étrangère.
  - **Un à un (0,1-1,1)**: La clé primaire de la table coté cardinalité 1,1 est dupliqué dans la table coté cardinalité 0,1 où elle devient clé étrangère.
  - **Un à un (0,1-0,1)**: La clé primaire d'une des tables est dupliqué dans l'autre où elle devient clé étrangère. 
  - **Plusieurs à plusieurs**: On crée une table contenant les clés primaires des 2 tables en tant que clé étrangère.
- Héritage simple:
  - **Distinction**: Tout les enfants donnent une table différentes tout comme la table parent. La clé primaire parent est dupliqué dans les enfants et devient clé primaire et étrangère.
  - **Push down**: On crée une table pour chaque enfant avec les attributs du parent.
  - **Push Up**: On crée une table pour le parent avec un attribut de traçabilité. Tout les attributs des enfants sont à valeurs facultatives dans la table créée.


## Requête de Base

- **SELECT:** Sélectionne les colonnes à afficher dans la table avec la condition.
- **FROM:** Dans quelle.s table.s
- **WHERE:** Les n-uplets sortants sont soumis à une ou des conditions.
  ```sql
  SELECT colonne1, colonne2 
  FROM table
  WHERE condition;
  ```

## Jointures en SQL

Les jointures sont utilisées pour combiner des lignes de deux ou plusieurs tables en fonction d'une condition de liaison entre elles. Voici quelques types courants de jointures :

### JOIN (INNER JOIN)

La jointure (ou INNER JOIN) renvoie les lignes lorsque des correspondances sont trouvées dans les deux tables. C'est la jointure par défaut si le type n'est pas spécifié.

Exemple :

```sql
SELECT *
FROM table1
JOIN table2 ON table1.colonne = table2.colonne;
```

### NATURAL JOIN

La jointure naturelle (ou NATURAL JOIN) relie automatiquement les colonnes ayant le même nom dans les deux tables. Il n'est pas nécessaire de spécifier les colonnes à comparer.

Exemple :

```sql
SELECT *
FROM table1
NATURAL JOIN table2;
```

### LEFT AND RIGHT JOIN (OUTER JOIN)

La jointure renvoie toutes les lignes de la table du côté spécifié et les lignes correspondantes de l'autre table. Si aucune correspondance n'est trouvée, les colonnes de cette dernières auront NULL comme valeur.

Exemple :

```sql
SELECT *
FROM table1
(RIGHT/LEFT) JOIN table2 ON table1.colonne = table2.colonne;
```


## Opérateurs Logiques

- **IN:** Filtre les résultats en fonction d'une liste de valeurs.
  ```sql
  SELECT * FROM table WHERE colonne IN (valeur1, valeur2, ...);
  ```
- **LIKE:** Filtre les résultats en fonction d'un motif.
  - `%:` Chaine de caractères
  - `-:` Un caractère
  ```sql
  SELECT * FROM table WHERE colonne LIKE 'motif%';
  ```
- **ORDER BY:** Trie les résultats selon une ou plusieurs colonnes.
  - `ASC:` Trie de manière ascendante
  - `DESC:` Trie de manière descendante
  ```sql
  SELECT * FROM table ORDER BY colonne ASC/DESC;
  ```    

## Création, Suppression et Vidage de Tables en SQL

### Création de Tables

La création de tables se fait à l'aide de la commande SQL `CREATE TABLE`. Voici un exemple générique :

```sql
CREATE TABLE nom_table (
    colonne1 TYPE1,
    colonne2 TYPE2,
    -- Autres colonnes
    CONSTRAINT nom_contrainte TYPE_CONTRAINTE (colonne1)
);
```

### Supression de Tables

Pour supprimer une table, utilisez la commande `SQL DROP TABLE`. Attention : cela supprimera définitivement toutes les données de la table. Le `CASCADE CONTRAINTS` permet de supprimer les contraintes et références liées.

```sql
DROP TABLE nom_table CASCADE CONTRAINTS;
```

### Vider les Tables

Pour supprimer toutes les lignes d'une table tout en conservant la structure de la table, utilisez la commande SQL `DELETE FROM`.

```sql
DELETE FROM nom_table;
```

## Contraintes et Relations de Références

### Contraintes 
**Les contraintes sont à ajoutés à la fin de la création de la table.**
- **CHECK**: Restreint les valeurs possibles pour une colonne.  
```sql 
CONSTRAINT chk_nom_contrainte CHECK (condition)
```
- **UNIQUE**: Garantit que chaque valeur dans une colonne est unique. 
```sql
CONSTRAINT uk_nom_contrainte UNIQUE (colonne)
```
- **PRIMARY KEY**: Identifie de manière unique chaque enregistrement dans une table.
```sql
CONSTRAINT pk_nom_contrainte PRIMARY KEY (colonne)
```

### Relations de Références (Clés Étrangères)
**Les relations de références sont à ajoutés après la création de la table.**

- **FOREIGN KEY**: Établit une relation de référence entre deux tables.  
L'attribut fait une référence vers l'attribut d'une autre table.
```sql
CREATE TABLE table1 (
    id INT PRIMARY KEY,
    nom VARCHAR(50)
);

CREATE TABLE table2 (
    id INT PRIMARY KEY,
    table1_id INT,
);

ALTER TABLE table2
ADD CONSTRAINT fk_nomref FOREIGN KEY (table1_id)
REFERENCES table1(id);
```


## Utilisation de DISTINCT

La clause `DISTINCT` est utilisée pour sélectionner des nuplets uniques dans une relation résultats. Cela élimine les doublons et ne renvoie que des valeurs distinctes.

Exemple :

```sql
SELECT DISTINCT colonne
FROM nom_table;
```

## Fonctions d'Agrégation en SQL

Les fonctions d'agrégation sont utilisées pour effectuer des calculs sur un ensemble de valeurs et retourner un seul résultat. Voici quelques-unes des fonctions d'agrégation les plus couramment utilisées en SQL :

- `COUNT()` compte le **nombre de lignes** dans un ensemble de résultats.
- `SUM()` calcule la **somme** des valeurs dans une colonne.
- `AVG()` calcule la **moyenne** des valeurs dans une colonne.
- `MIN()` retourne la **valeur minimale** d'une colonne.
- `MAX()` retourne la **valeur maximale** d'une colonne.


Le `AS` permet de renommer la colonne dans la relation résultat

Exemple :

```sql
SELECT AVG(colonne) AS moyenne
FROM nom_table
```

### Utilisation de GROUP BY 

La clause `GROUP BY` est utilisée regrouper les résultats en fonction des valeurs d'une ou plusieurs colonnes.  
Lors de la sélection d'autres colonnes avec une fonction d'agrégation, le GROUP BY est obligatoire sur l'ensemble de ces colonnes.

Exemple :

```sql
SELECT id, nom, MAX(colonne) AS max
FROM nom_table
GROUP BY id, nom, prenom;
```

### Utilisation de HAVING avec GROUP BY

La clause `HAVING` est utilisée en conjonction avec la clause `GROUP BY` pour filtrer les résultats agrégés en fonction d'une condition spécifiée. Elle agit comme une clause `WHERE` pour les résultats agrégés.

Exemple :

```sql
SELECT colonne, COUNT(*) AS total
FROM nom_table
GROUP BY colonne
HAVING COUNT(*) > 1;
```

## CASE
- Structure de contrôle conditionnelle.
- Utilisée pour effectuer différentes actions en fonction de conditions spécifiées.

Exemples:
```sql
SELECT
  Nom,
  CASE
    WHEN Age < 18 THEN 'Mineur'
    WHEN Age = 18 THen 'Juste majeur'
    ELSE 'Majeur'
  END AS Statut
FROM
  Utilisateurs;
```

## COMPUTE
- Permet le calcul sur la relation de résultat
- Opérations: `SUM`, `AVG`, `COUNT`, `MIN`, `MAX`, `NUMER`...
- Le `BREAK ON REPORT` permet de générer une ligne de séparation dans la relation de résultat

```sql
BREAK ON REPORT
COMPUTE operation LABEL nom OF colonne ON REPORT
```
