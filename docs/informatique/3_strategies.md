# Stratégies

## Récursivité

La récursivité est la caractéristique des objets défini à partir d'eux mêmes, concrètement une fonction est dite récursive si elle comporte, dans son corps, au moins un appel à elle-même.

Attention :  

Si cette pratique permet d'écrire des programmes relativement complexes avec peu de lignes (notamment pour les graphes) cette méthode est gourmande en ressources et le nombre d'appels récursifs peut être limité comme en `Python`.

### Éléments Caractéristiques

Il faut au moins une situation qui ne consiste pas en un appel récursif, sans quoi la fonction s'appelle indéfiniment jusqu'à ce que soit atteinte une limite technique.

```python
   if n <= 1:
      return 1
```

Cette situation est appelée situation de terminaison ou situation d’arrêt ou cas d’arrêt ou cas de base. Chaque appel récursif doit se faire avec des données qui permettent de se rapprocher d’une situation de terminaison

```python
        return n * fact(n-1)
```

Il faut s’assurer que la situation de terminaison est atteinte après un nombre fini d’appels récursifs.

### Exemple de cours : factorielle

```python
def fact(n):
    if n <= 1:
        return 1
    else:
        return n * fact(n-1)
```

## Programmation dynamique

La programmation dynamique est une méthode d'optimisation de la complexité d'un algorithme en mémorisant les résultats des sous-problèmes déjà résolus.
