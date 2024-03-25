## Dictionnaire de donnée

> Les métadonnées dans une base de données Oracle fournissent des informations sur la structure, la configuration et les caractéristiques des objets de la base de données.

### Niveau d'accès

- **"DBA_" (Database Administrator):** Dispose des informations sur l'ensemble de la base de données et des utilisateurs.
- **"ALL_":** Permettent aux utilisateurs de consulter des informations sur les objets de la base de données auxquels ils ont accès.
- **"USER_":** Permettent aux utilisateurs de consulter des informations sur les objets de la base de données dont ils sont propriétaires.


### Vues principales ([Oracle](https://docs.oracle.com/database/timesten-18.1/TTSYS/systemtables.htm#TTSYS383))
- **ALL_TAB_COLUMNS:**
  Contient des informations sur les colonnes de toutes les tables accessibles par l'utilisateur.
- **ALL_TABLES:**
  Affiche des informations sur toutes les tables auxquelles l'utilisateur a accès.
- **ALL_INDEXES:**
  Fournit des détails sur tous les index accessibles par l'utilisateur.
- **ALL_VIEWS:**
  Donne des informations sur toutes les vues accessibles par l'utilisateur.
- **ALL_TAB_COMMENTS:**
  Contient des commentaires associés aux tables accessibles par l'utilisateur.
- **ALL_COL_COMMENTS:**
  Contient des commentaires associés aux colonnes des tables accessibles par l'utilisateur.
- **ALL_CONSTRAINTS:**
  Affiche des informations sur toutes les contraintes accessibles par l'utilisateur.
- **ALL_USERS:**
  Fournit des détails sur tous les utilisateurs dans la base de données.
- **ALL_SEQUENCES:**
  Fournit des détails sur toutes les séquences accessibles par l'utilisateur.

> A noter que 'ALL_' peut être remplacé par les autres niveaux d'accès et donnera donc des résultats différents.

Les séquences dans Oracle sont des objets de base de données permettant de générer des nombres séquentiels uniques. Elles sont souvent utilisées pour créer des valeurs de clé primaire dans une table. Voici comment créer, utiliser et supprimer des séquences dans Oracle :

## Séquences

### Création d'une Séquence

Pour créer une séquence, utilisez la commande SQL `CREATE SEQUENCE`.

```sql
CREATE SEQUENCE ma_sequence
  START WITH 1 //Valeur de départ (1)
  INCREMENT BY 1 //Valeur par laquelle elle augment à chaque fois (1)
  MAXVALUE 1000 //Valeur maximale (infini)
  CYCLE //Si la séquence doit faire une boucle (nocycle)
  CACHE 20; //Nombre de valeur gardé en cache (25)
```

> Entre parenthèse se situent les valeurs par défaut.

### Utilisation de la Séquence

Utilisez la fonction `NEXTVAL` de la séquence pour générer des valeurs lors des insertions dans une table.

```sql
INSERT INTO ma_table (id, nom, ...) VALUES (ma_sequence.NEXTVAL, 'Exemple', ...);
```

Ou lors de la création de la table.

```sql
CREATE TABLE ma_table (
  id NUMBER PRIMARY KEY DEFAULT ma_sequence.NEXTVAL,
  nom VARCHAR2(50),
  -- Autres colonnes de la table...
);
```

Ou en la modifiant.

```sql
ALTER TABLE ma_table MODIFY 
ma_table.id NUMBER DEFAULT ON NULL ma_sequence.NEXTVAL;
```

### Suppression d'une Séquence

Pour supprimer une séquence, utilisez la commande SQL `DROP SEQUENCE`. Assurez-vous que la séquence n'est plus utilisée dans aucune table avant de la supprimer.

```sql
DROP SEQUENCE ma_sequence;
```

### Options Supplémentaires

- **ALTER SEQUENCE :** Utilisé pour modifier les propriétés d'une séquence existante, par exemple, changer l'incrémentation ou le maximum.
- **NOORDER :** L'option par défaut, spécifiant que les valeurs ne sont pas nécessairement dans l'ordre d'incrémentation en cas de `CACHE`.
- **NOCACHE :** Désactive la mise en cache des valeurs de séquence, ce qui peut être utile dans certaines situations.

Les séquences offrent une méthode efficace pour générer des valeurs uniques dans une base de données Oracle, particulièrement dans le contexte de l'attribution automatique de clés primaires.

## Jointures avancées

### Cross Join (Produit Carthésien)

```sql
SELECT *
FROM RES1 CROSS JOIN RES2;
```

### Natural Join (Interne)

> Effectue une equi-jointure sur l'ensemble des attributs de même noms des 2 relations. Condition implicite.

```sql
SELECT *
FROM RES1 NATURAL JOIN RES2;
```

### Inner Join (Interne)

> La condition est explicite et est défini sur les attributs choisies.

```sql
SELECT * 
FROM A (INNER) JOIN B
ON A.KEY = B.KEY;
```

### Outer Join (Externe)

> Conserve l'ensemble des occurrences du côté spécifié. C'est un concept, l'opération n'existe pas.

```sql
SELECT * 
FROM A <LEFT|RIGHT> JOIN B 
ON A.KEY = B.KEY;
```

### Full Join (Externe)

> Prend comme référence toutes les relations du FROM.

```sql
SELECT * 
FROM A FULL JOIN B 
ON A.KEY = B.KEY;
```

### Semi-Jointure

> Jointure de n'importe quel type de laquelle on garde les colonnes d'une seule table jointe.

Que A ou B sans l'intersection.
```sql
SELECT * 
FROM A <LEFT|RIGHT> JOIN B 
ON A.KEY = B.KEY
WHERE B.KEY IS NULL;
```

Les deux tables sans l'intersection.
```sql
SELECT * 
FROM A FULL JOIN B 
ON A.KEY = B.KEY
WHERE B.KEY IS NULL OR A.KEY IS NULL;
```

## Sous-Requête (Selection imbriquée)

- Les sous-requêtes, sont utilisées dans Oracle pour effectuer une requête à l'intérieur d'une autre requête. Elles peuvent être utilisées dans différentes clauses SQL, telles que SELECT, FROM, WHERE, HAVING, etc.
- Une sous-requête corrélée est une requête imbriquée dont l’exécution dépend des résultats de la requête externe.

### Exemples :

```sql
SELECT column1, (SELECT AVG(column2) FROM table2) AS average_value
FROM table1;
```

```sql
SELECT column1, AVG(column2) AS avg_value
FROM table1
GROUP BY column1
HAVING AVG(column2) > (SELECT AVG(column2) FROM table1 WHERE condition);
```

### IN

> La clause IN permet de vérifier si une valeur correspond à n’importe quelle valeur renvoyée par une sous-requête.

```sql
SELECT column1
FROM table1
WHERE column2 IN (SELECT column2 FROM table2 WHERE condition);
```

### ALL, ANY et SOME

> Ces opérateurs permettent de comparer une valeur avec tous les résultats ou au moins un résultat d’une sous-requête.

```sql
-- ALL : Vérifie si la condition est vraie pour toutes les valeurs de la sous-requête.
SELECT column1
FROM table1
WHERE column2 > ALL (SELECT column2 FROM table2 WHERE condition);

-- ANY ou SOME : Vérifie si la condition est vraie pour au moins une valeur de la sous-requête.
SELECT column1
FROM table1
WHERE column2 > ANY (SELECT column2 FROM table2 WHERE condition);
```

## Algèbre d'interval

### Types de Données Temporelles dans SQL Oracle

#### DATE
Le type DATE stocke les éléments suivants : siècle, année, mois, jour, heure, minute et seconde. 

> Définir le format de date
```sql
ALTER SESSION SET NLS_DATE_FORMAT = 'YYYY-MM-DD HH24:MI:SS';
ALTER SESSION SET NLS_DATE_LANGUAGE = 'FRENCH'; -- Définit la langueZ
```

#### TIMESTAMP
Le type TIMESTAMP stocke les éléments suivants : siècle, année, mois, jour, heure, minute, seconde **et fraction de seconde.**

> Définir le format de timestamp
```sql
ALTER SESSION SET NLS_TIMESTAMP_FORMAT = 'YYYY-MM-DD HH24:MI:SS.FF6';
```

#### TIMESTAMP WITH TIME ZONE
Le type TIMESTAMP WITH TIME ZONE stocke un timestamp ainsi que le fuseau horaire.

> Définir le format de timestamp
```sql
ALTER SESSION SET NLS_TIMESTAMP_TZ_FORMAT = 'YYYY-MM-DD HH24:MI:SS.FF6 TZR';
ALTER SESSION SET TIME_ZONE = "America/Los_Angeles";
```

#### TIMESTAMP WITH LOCAL TIME ZONE
Le type TIMESTAMP WITH LOCAL TIME ZONE stocke un timestamp ainsi que le fuseau horaire local de la session.

### Interval

#### INTERVAL YEAR TO MONTH :
Représente un écart de temps entre deux dates en termes d'années et de mois.

Exemple:
```sql
SELECT SYSDATE, SYSDATE + INTERVAL '1' YEAR FROM DUAL; -- Ajoute 1 an à la date actuelle
```

```sql
SELECT (DATE_COL1 - DATE_COL2) YEAR TO MONTH AS DIFFERENCE FROM TABLE_NAME; -- Calculer la différence entre deux dates
```

#### INTERVAL DAY TO SECOND :
Représente un écart de temps entre deux dates en termes de jours, heures, minutes, secondes et fractions de seconde.

```sql
SELECT SYSDATE, SYSDATE + INTERVAL '5' DAY + INTERVAL '3' HOUR + INTERVAL '20' MINUTE + INTERVAL '15' SECOND FROM DUAL;
```

```sql
SELECT * FROM TABLE_NAME WHERE (DATE_COL1 - DATE_COL2) DAY TO SECOND > INTERVAL '1' DAY; -- Utilisation dans le WHERE
```

### Pour Trunc, Round et Extract

| Format | Description                                           |
|--------|-------------------------------------------------------|
| MI     | Minute                                                |
| MM     | Mois (chiffres)                                       |
| W      | Numéro de semaine de l'année (1-53)                   |
| WW     | Numéro de semaine de l'année (01-53)                  |
| Q      | Trimestre (1-4)                                       |
| YY     | Année (2 chiffres)                                    |
| CC     | Siècle (2 premiers chiffres de l'année)               |
| DD     | Jour du mois (01-31)                                  |
| D      | Jour de la semaine (1-7)                              |

Exemples:
```sql
SELECT TRUNC(TO_DATE('2023-09-15', 'YYYY-MM-DD'), 'Q') AS TRUNCATED_DATE FROM DUAL; -- Tronquer une date au trimestre

SELECT ROUND(TO_DATE('2023-09-15', 'YYYY-MM-DD'), 'D') AS ROUNDED_DATE FROM DUAL; -- Arrondir une date au jour

SELECT EXTRACT(DAY FROM TO_DATE('2023-09-15', 'YYYY-MM-DD')) FROM DUAL; -- Extraire le jour
```

## Les Vues

> Les vues sont des objets de base de données virtuels qui permettent de présenter les données d'une ou plusieurs tables d'une manière spécifique. Elles agissent comme des tables virtuelles, offrant une vue personnalisée des données stockées dans la base de données.

### Création

```sql
CREATE VIEW my_view AS
SELECT column1, column2
FROM my_table
WHERE condition;
```

### Utilisation 

```sql
SELECT * FROM my_view;
```

### Suppression 

```sql
DROP VIEW my_view;
```

### Mise à jour des données

```sql
UPDATE my_view
SET column1 = 'valeur_mise_à_jour'
WHERE condition;
```

> [!WARNING]
> La précense de ces éléments empèche la mise à jour:
> - DISTINCT  
> - AVG, COUNT, MAX, MIN, SUM...
> - UNION, UNION ALL, INTERSECT, MINUS
> - GROUP BY, HAVING
> - START WITH, CONNECT BY
> - ROWNUM 
>  
> De plus, la modification doit être possible dans le(s) table(s) de base.

