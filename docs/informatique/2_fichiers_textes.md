# Lecture, écriture dans un fichier

## Ouvrir un fichier

Avant d’accéder à un fichier, on utilise la fonction `open`, disponible sans aucune bibliothèque supplémentaire. Elle prend en paramètre :  

- le chemin (absolu ou relatif) menant au fichier à ouvrir ;
- le mode d’ouverture. Le mode est donné par un caractère. Voici les principaux modes :
  - `r` : ouverture en lecture (read) ;
  - `w` : ouverture en écriture (write), le contenu du fichier est écrasé et si le fichier n’existe pas, il est créé ;
  - `a` : ouverture en écriture en mode ajout (append), on écrit à la fin du fichier sans écraser l’ancien contenu du fichier et si le fichier n’existe pas, il est créé ;
  - `r+` : ouverture en lecture et écriture.

```python
with open('test.txt',"r") as fich : # on créé une variable fich qui va contenir le fichier
    contenu = fich.read()           # la variable contenu va récupérer ce qu'on lit dans le fichier
    print(contenu)                 # affiche ce qui a été lu
fich.close()                       # fermeture du fichier
```

## Extraire les données

### Lecture

- `readline()` : (au singulier) retourne une chaine de caractères contenant une ligne
du fichier (celle en cours de lecture) ;
- `readlines()` : (au pluriel) lit toutes les lignes du fichier et les range dans une liste
(un élément = une ligne).

```python
# On peut parcourir les  lignes d'un fichier par une boucle for
for ligne in fichier :

```

### Manipulations

- `rstrip("\n\r")` : supprime le caractère de fin de ligne \n et le retour chariot \r situés au bout de chaque ligne ;
- `replace("str1", "str2")` : remplace le caractère str1 par le caractère str2 dans la chaîne de caractères ;
- `split("carac")` : permet de séparer en plusieurs morceaux une chaîne de caractères. Les chaines obtenues sont mises dans une liste. Le séparateur est indiqué par le caractère "carac".

```python
ligne = ligne.replace(",",".") # changement de , en .
noms_grandeurs = ligne.split("\t") # découpage aux tabulations
```

## Écrire dans un fichier

On utilise la fonction `write`:

```python
with open("legende.txt","w") as fichier : # si le fichier n’existe pas il sera créé
    fichier.write("Bonjour")
    fichier.write("Connaissez-vous la légende de Darth Pleigeis le sage ?")
    fichier.write("il était une fois...")
fichier.close()                       # fermeture du fichier
```

ou encore la fonction `writelines`, attention pour écrire sur plusieurs lignes il faut ajouter le caractère de fin de ligne "`\n`" à la fin de chacune des chaines de caractères dans la liste.
