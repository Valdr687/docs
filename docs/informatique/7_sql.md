# SQL

## Commandes de base

|Commande||
|-|-|
|SELECT *colonne*,*colonne2*| Précise les colonnes qui vont apparaitre dans la requête (* permet de tout sélectionner)|
|FROM *table*|Précise la table dont on sélectionne les donnés|
|WHERE|Précise les [conditions](#conditions) à appliquer sur les lignes|
|ORDER BY *tri*|Tri croissant *ASC* ou décroissant *DESC* |
| HAVING | Applique des conditions sur les groupes de résultats.|
| MIN(*colonne*) | Renvoie la plus petite valeur de la colonne spécifiée.|
| MAX(*colonne*) | Renvoie la plus grande valeur de la colonne spécifiée.|
| SUM(*colonne*)  | Renvoie la somme des valeurs de la colonne spécifiée.|
| COUNT(*colonne*) | Renvoie le nombre de valeurs dans la colonne. `COUNT(DISTINCT colonne)` élimine les doublons.         |
| COUNT(*)  | Compte toutes les lignes de la table.|
| AVG(*colonne*)       | Renvoie la moyenne des valeurs de la colonne spécifiée.|

## Jointures

JOIN est utilisée pour combiner les lignes de deux ou plusieurs tables, en fonction d'une colonne liée entre elles.

```SQL
JOIN table2 ON table1.colonne_de_table1 = table2.colonne_de_table2
```

Exemple :

```sql
SELECT 
    table1.colonne1, 
    table2.colonne2
FROM 
    table1
JOIN 
    table2 
ON 
    table1.colonne_commune = table2.colonne_commune;
```

## Conditions

**Comparaisons:**
=,>,<,>=,<=,!= : comme en Python sauf que l'égalité est testée avec *un simple* égal

**Opérateurs logiques**  
AND, NOT, OR

**Les prédicats**  
IN, NOT IN, LIKE, NULL, ALL, SOME, ANY, EXIST

## Modification

|Commande||
|-|-|
| CREATE    | Crée une nouvelle table.|
| ALTER     | Modifie une table existante.|
| DROP      | Supprime une table.|
| INSERT    | Insère des lignes dans une table.|
| UPDATE    | Met à jour des lignes dans une table.|
| DELETE    | Supprime des lignes dans une table.|
