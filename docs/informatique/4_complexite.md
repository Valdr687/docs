# Notion de complexité d'un algorithme

## Introduction

En plus d'être correct, un algorithme doit être efficace. On mesure cette efficacité par la :

- complexité en temps : temps d'exécution
- complexité en mémoire : ressources nécessaires à son exécution

On s'intéresse à la **complexité en temps**.

## Calcul de la complexité

**Hypothèses** :

- Cout constant pour chaque opération
- Jeu d'entrée de taille $n$

On s'intéresse à $\Theta$ qui correspond à l'ordre de grandeur de la complexité :

- $T(2n + 2)$ correspond à $\Theta(n)$, à l'infini on considère que $2n+2 \approx n$

**Règles de calcul** :

| Opération | Coût |
| --------- | ---- |
| Affectation d'une variable / lecture `t = 1` | 1 |
| Opération arithmétique (addition/multiplication) `t = t + 1` | 1 |
| Comparaison `if` | 1 |
| Boucle `for` | $n$ |
| Boucle `while` (pire des cas) | $n$ |

Attention, des boucles imbriquées -*à priori*- ont une complexité multipliée !

## Compléments

### Les différentes classes de complexité

| Notation                  | Classe                       |
| ------------------------- | ---------------------------- |
| $\Theta(1)$               | Complexité constante         |
| $\Theta(\ln(n))$          | Complexité logarithmique     |
| $\Theta(n)$               | Complexité linéaire          |
| $\Theta(n \times \ln(n))$ | Complexité quasi-linéaire    |
| $\Theta(n^2)$             | Complexité quadratique       |
| $\Theta(n^{p})$           | Complexité polynomiale       |
| $\Theta(n^{\ln(n)})$      | Complexité quasi-polynomiale |
| $\Theta(2^n)$             | Complexité exponentielle     |

### Les différents types de complexité

- Complexité dans le pire des cas $C_{max}$ : majorant du temps d'exécution
- Complexité en moyenne $C_{moy}$ : moyenne du temps d'exécution, correspond au comportement moyen d'un algorithme
- Complexité dans le meilleur des cas $C_{min}$ : minorant du temps d'exécution, peu utile
