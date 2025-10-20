
# Méthodes de résolutions analytique

## Recherche de 0

### Dichotomie

Entrées : fonction f, a et b (l'intervalle de recherche est [a,b]), ε (marge de précision), IteMax (Nombre max d'itération)  
Sortie : racine approchée de 0 notée c

```python
from math import abs 

def f(x)
    return x #expression de f

def dichotomie(f,a,b,ε,IteMax):
    ai,bi,ci=a,b,(a+b)/2
    fa,fb,fc=f(ai),f(bi),f(ci)
    ite = 0
    while bi-ai > 2 and abs(fc)>ε and ite<IteMax :
        ci = (ai+bi)/2
        fc=f(ci)

        if fa*fc <= 0 : # la racine est dans [ai,ci]
            bi = ci # on actualise l'intervalle de recherche
            fb = fc
        else : # la racine est dans [ci,bi]
            ai = ci
            fa = fc
        ite=ite+1
    return ci
```

## Newton

Cette méthode utilise le développement de Taylor à l’ordre 1. Si la fonction est de classe $\mathcal{C}^1$ sur l’intervalle $[a,b]$, alors le
développement de Taylor d’ordre 1 donne :  

$f(b)=f(a)+f\prime(a)\times(b-a) + o(b-a)$.  

A partir d’un point choisi x0, la méthode consiste à rechercher le point suivant x1 en le supposant racine de la fonction $f$ et en négligeant le terme $o(x1-x0)$ dans le développement de Taylor. Si bien que :  

$0 = f(x_1) = f(x_0) + f\prime(x_0)\times(x_1-x_0) \implies x_1 = x_0 - \frac{f(x_0)}{f\prime(x_0)}$.

Si $f(x_1)$ ne vérifie pas le critère de convergence $|f(x_1)| < \epsilon$, alors un nouveau candidat $x_2$ est calculé à partir de $x_1$ et ainsi de suite
jusqu’à convergence.

Entrées : fonction f, fonction $f\prime$, $x_0$ (début de la recherche), $\epsilon$ (marge de précision), IteMax (Nombre max d'itération)  
Sortie : racine approchée de 0

```python
from math import abs

def f(x)
    return x #expression de f

def df(x):
    return x #expression de f'

def newton(f,df,x0,ε,IteMax):
    ite=0
    xi=x0
    fx=f(xi)
    while abs(fx)>ε and ite < IteMax:
        ite +=1
        fpx=df(xi)
        if fpx=0: # on sort de la boucle si la dérivée est nulle
            break
        else:
            xi = xi - fx/fpx # on actualise le candidat
            fx=f(xi)
    return xi
```

## Résolution d'équation différentielle

On cherche à résoudre le problème (dit de Cauchy) suivant :  
$y\prime = f(t,y(t))$  
$y(t_0)=y_0$ pour $t \in [t_{0} ; t_{max} ]$

On procède ainsi (grace à la méthode d'Euler [^1]) :  

- Calcul du pas :  
$h=\frac{t_{m a x} \times t_0}{n}$ où n représente le nombre de points
- Passage de l'équation différentielle à une relation de récurrence :  
$a\frac{d y}{d t}+b y(t)=x(t) \leftrightarrow \frac{d y(t)}{d t}=\frac{x(t)-b_y(t)}{a}$  
d'où $f(y, t)=\frac{x(t)-by(t)}{a}$
et la relation de récurrence : $y_{k+1}=y_k+h f(t_k, y_k)$

Programme :  

```python
def euler(y0,T0,Tmax,h,f(t,y)):
    t=T0
    y=y0
    ListeY = [y]
    while t<Tmax:
        y = y + h*f(t,y)
        t = t + h
        ListeY.append(y)
    return ListeY
```

## Intégration numérique

### Méthode des rectangles

Dans cette méthode, la fonction à intégrer est interpolée par un polynôme de degré 0, à savoir une fonction constante. Géométriquement, l'aire sous la courbe est alors approximée par un rectangle.  

Le théorème de Riemann dit que si f est continue (par morceaux) sur un segment [a; b], alors on peut approcher I'aire située sous le graphe de f par la somme des aires des rectangles approchant f en n points uniformément répartis. f est intégrable sur [a; b], si et seulement si pour toute subdivision $\sigma_k = (\sigma_0 < \sigma_1 <...< \sigma_n)$ les sommes ci-dessous convergent:

$\sum_{k=1}^{n-1}\left(\sigma_{k+1}-\sigma_k\right) f\left(t_k\right) \xrightarrow[n \rightarrow \infty]{\forall t_t \in\left[\sigma_k, \sigma_{t+1}\right]} I=\int_a^b f(t) d t$

Avec l'expression de $\sigma$ :  
$\sigma_k=a+k \times \frac{b-a}{n} , 0 \le k \le n -1 $

On peut donc insérer le point des rectangles à gauche, au milieu ou à droite :  

|Gauche|Milieu|Droite|
|-|-|-|
|$R_n=\frac{b-a}{n} \sum_{k=0}^{n-1} f\left(\sigma_{k}\right)$|$R_n=\frac{b-a}{n} \sum_{k=0}^{n-1} f\left({\sigma_{k+1} + \sigma_{k}} \over {2}\right)$|$R_n=\frac{b-a}{n} \sum_{k=0}^{n-1} f\left(\sigma_{k+1}\right)$|

```python
def f(x):
    return x # Expression de f - à modifier à chaque fois

# Méthode avec insertion à gauche, il suffit de changer l'expression dans comme dans le tableau ci dessus pour les autres

a = int(input("Entrer le nombre de départ de la courbe"))
b = int(input("Entrer le nombre d'arrivée de la courbe"))
n = int(input("Entrer le nombre de subdivisions"))

def AireSousLaCourbe(a,b,n,f) :
    S = 0
    for k in range(0,n):
        sigma = a + k * ((b-a)/float(n))
        S = S + ((b-a)/float(n)) * f(sigma)
    return S
```

### Méthode des trapèzes

Le principe est similaire mais on utilise des trapèzes. On somme donc les $T_n$ tels que :

$T_n=\frac{b-a}{2n} \sum_{k=0}^{n-1}\left(f(\sigma_k) + f(\sigma_{k+1}) \right)$

```python
def f(x):
    return x # Expression de f - à modifier à chaque fois

# Méthode avec insertion à gauche, il suffit de changer l'expression dans comme dans le tableau ci dessus pour les autres

a = int(input("Entrer le nombre de départ de la courbe"))
b = int(input("Entrer le nombre d'arrivée de la courbe"))
n = int(input("Entrer le nombre de subdivisions"))

def AireSousLaCourbe(a,b,n,f) :
    S = 0
    for k in range(0,n):
        sigma = a + k * ((b-a)/float(n))
        sigma1 = a + (k+1) * ((b-a)/float(n))
        S = S + ((b-a)/float(2*n)) * (f(sigma) + f(sigma1))
    return S
```

[^1]: loves U
