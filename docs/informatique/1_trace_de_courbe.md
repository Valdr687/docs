# Tracés de courbes

## Graphiques (x,y)

Entrée des données expérimentales dans un tableau array, grâce à la bibliothèque numpy on crée un
np.array (une liste classique fonctionne aussi) pour chacune des grandeurs (abscisses et ordonnées).
Il est important de rentrer le même nombre de valeurs de x et de y et dans le même ordre.

```python
x = np. array ([ rentrer les valeurs de x séparées par des virgules ])
# contient les valeurs x auxquelles ont été mesurées celles de y
y = np. array ([ rentrer les valeurs de y séparées par des virgules ])
# ce sont les valeurs de y correspondantes

plt.plot (x, y, 'bo ',label ='nom de la courbe ') # Représenter y en fonction de x avec
ronds bleus
plt.xlabel ('légende à adapter ') # Légende axe de abscisses
plt.ylabel ('légende à adapter ') # Légende axe des ordonnées
plt.title ('titre à adapter ') # Titre
plt.legend () # Afficher la légende ( utile si plusieurs courbes sur le même graphique)
plt.grid () # Quadrillage
plt.show () # Affiche le graphique
```

### Options

- couleur : première lettre anglaise de la couleur (b, g, y, c, r, m, w ou k pour le noir)
- Style des points : `style_point`

| Paramètre | x   | X            | +   | P          | .   | o   | *   | d       |
|-----------|-----|--------------|-----|------------|-----|-----|-----|---------|
| Marqueur  | croix | Croix plein | plus | Plus plein | pixel | rond | étoile | carreau |

- Style des traits : `style_trait`

| Paramètre      | -   | -  | .   | P   | _   | ,   | v   |
|----------------|-----|---|-----|-----|-----|-----|-----|
| Marqueur       | trait pointillé | Ligne continue | Point | tiret | Plus plein | Ligne de tirets | pixel |

## Autres graphiques

### Barres d'erreurs

```python
import matplotlib.pyplot as plt
import random as rd
import math as m

x = []
y = []
e = []

for i in range(10):
    x.append(i)
    y.append(1-m.exp(-x[i]))
    e.append(0.1*rd.random())

plt.figure()
plt.axis([0, 10, 0, 1.1])
plt.errorbar(x, y, yerr=e, fmt='go', ecolor='r')
plt.show()
```

### Camembert

```python
import matplotlib.pyplot as plt

x = [4,9,21,55,30,18]
plt.figure(figsize=(5,5))
L = ['Chiens','Chats','Souris','Pies','Lapins','Vers']
plt.pie(x,labels=L,autopct='%.2f %%')
plt.show()
```

### Histogramme

```python
import matplotlib.pyplot as plt
from random import randint

y = [randint(1, 100) for i in range(1, 201)]

plt.figure()
plt.title("Histogramme")
plt.subplot(211)
plt.hist(y,10,color='r')
plt.subplot(212)
plt.hist(y,50,color=[0.2,0.1,0.8])
plt.show()
```

### Nuage de points

```python
import matplotlib.pyplot as plt
import random as rd

y = [rd.randint(1,100) for i in range(1,201) ]
x = [rd.randint(1,100) for i in range(1,201) ]

plt.figure()
plt.scatter(x,y,s=100)
plt.show()
```
