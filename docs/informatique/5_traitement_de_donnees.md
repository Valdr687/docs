# Traitement de données

## Liste et dictionnaires

### Opérations sur les tableaux

| Objectif                                                                                  | Code Python                            |
|-------------------------------------------------------------------------------------------|----------------------------------------|
| Créer un tableau vide                                                                     | `t = []`                               |
| Créer un tableau de taille n                                                              | `t = []*n` ou `t=[ for i in range(n)]` |
| Ajouter un élément à la fin d'un tableau                                                  | `t.append(e)`                          |
| Supprimer le dernier élément d'un tableau                                                 | `t.pop()`                              |
| Supprimer l'élément de rang i d'un tableau                                                | `t.pop(i)`                             |
| Supprimer l'élément e d'un tableau                                                        | `t.remove(e)`                          |
| Récupérer l'indice de l'élément e dans un tableau                                         | `t.index(e)`                           |
| Récupérer l'élément de rang i d'un tableau 1D                                             | `t[i]`                                 |
| Récupérer les éléments entre les rangs a (inclus) et b (exclus) d'un tableau 1D           | `t[a:b]`                               |
| Récupérer les éléments à partir du rang a (inclus) d'un tableau 1D                        | `t[a:]`                                |
| Récupérer les éléments jusqu'au rang b (exclus) d'un tableau 1D                           | `t[:b]`                                |
| Récupérer les éléments entre les rangs a (inclus) et b (exclus) par pas p d'un tableau 1D | `t[a:b:p]`                             |
| Récupérer l'élément de la ligne i et colonne j d'un tableau 2D                            | `t[i, j]` ou `t[i][j]`                 |
| Récupérer la ligne i d'un tableau 2D                                                      | `t[i, :]`                              |
| Récupérer la colonne j d'un tableau 2D                                                    | `t[:, j]`                              |

### Opération sur les dictionnaires

Un dictionnaire est ensemble de données structurées dont les valeurs peuvent être de n'importe quel type (simple ou complexe) et qui contrairement au tableau, sont accessibles par des clé et non des indices.

| Objectif                                                                 | Code Python                   |
|--------------------------------------------------------------------------|-------------------------------|
| Créer un dictionnaire vide                                               | `d = {}`                      |
| Ajouter une clé et sa valeur à un dictionnaire                           | `d[clé] = valeur`             |
| Supprimer une clé et sa valeur d'un dictionnaire                         | `del d[clé]`                  |
| Récupérer la valeur associée à une clé d'un dictionnaire                 | `d[clé]`                      |
| Parcourir les clés d'un dictionnaire                                     | `for clé in d:`               |
| Parcourir les valeurs d'un dictionnaire                                  | `for valeur in d.values():`   |
| Parcourir les clés et les valeurs d'un dictionnaire                      | `for clé, valeur in d.items():`|

## Dichotomie

Entrée : liste triée par ordre croissant ; élément à chercher  
Sortie : rang de l'élément cherché

```python
def dicho(liste, x):
    i_min = 0
    i_max = len(liste) - 1

    while i_max >= i_min:
        milieu = (i_max + i_min)//2  # calcul de l'indice "du milieu"

        if liste[milieu] == x:      # x est présent dans la liste
            return milieu
        else:
            if liste[milieu] > x:  # alors x est dans la première moitié de la liste
                i_max = milieu - 1
            else:                   # x est donc dans la deuxième moitié
                i_min = milieu + 1

    return False  # si on en est là, x n'est pas présent dans la liste
```

## Tris

On l'a vu, la dichotomie ne fonctionne qu'avec des listes triées, d'où l'intérêt des tris.

### Tri rapide (meilleur)

```python
def tri_rapide(tab):
    if tab == []:
        return []
    else:
        pivot = tab[0]
    t1, t2 = [], []
    for x in tab[1:]:
        if x < pivot:
            t1.append(x)
        else:
            t2.append(x)
    return tri_rapide(t1) + [pivot] + tri_rapide(t2)
```

### Tri à bulles

Le tableau `nombres` est modifié par la fonction ; on parle donc de **tri en place**.

```python
def tri_bulle(nombres : list) -> list:
    n = len(nombres)
    for i in range(n-1, 0, -1):
        for j in range(i):
            if nombres[j] > nombres[j+1]:
                # nombres[j] et nombre[j + 1] à échanger
                nombres[j], nombres[j+1] = nombres[j+1], nombres[j]
    return nombres
```

On rappelle les complexités temporelles des algorithmes suivants en fonction de n (taille du tableau à trier)

- tri par sélection : **$O(n^2)$**
- tri à bulles : **$O(n^2)$**
- tri fusion : **$O(n*log(n))$**
- tri rapide : **$O(n*log(n))$**

Vous pouvez visualiser leur fonctionnement grace à ce [site](https://interstices.info/les-algorithmes-de-tri/).

## Numpy

```python
import numpy as np
```

### Tableaux pré-définis

| Objectif                                                                                    | Code Python                |
|---------------------------------------------------------------------------------------------|----------------------------|
| Tableau à 1D de n zéros                                                                     | `t= np.zeros(n)`           |
| Tableau à 2D de n lignes et m colonnes                                                      | `t = np.zeros((n, m))`     |
| Tableau à 1D de n valeurs régulièrement espacées, entre a (inclus) et b (inclus)            | `t = np.linspace(a, b, n)` |
| Tableau à 1D de valeurs régulièrement espacées, entre a (inclus) et b (exclus) par pas de p | `t = np.arange(a, b, p)`   |

### Fonctions statistiques utiles

| Objectif                                                                           | Code Python         |
|------------------------------------------------------------------------------------|---------------------|
| Valeur minimale                                                                    | `min(t)`            |
| Valeur maximale                                                                    | `max(t)`            |
| Somme des éléments                                                                 | `np.sum(t)`         |
| Moyenne                                                                            | `np.mean(t)`        |
| Écart-type expérimental $\sqrt{\frac{1}{N-1}\sum_{i=0}^{N-1}(x_i-\overline{x})^2}$ | `np.std(t, ddof=1)` |
