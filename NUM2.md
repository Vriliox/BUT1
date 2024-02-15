## Suites numériques

Les suites numériques sont des séquences ordonnées d'éléments numériques. Chaque élément d'une suite est généralement désigné par un indice entier, et on peut définir une suite de deux manières principales : par une formule explicite ou par une relation de récurrence.

### 1. Définition explicite :
- Une suite définie explicitement est décrite par une formule qui permet de calculer chaque terme directement en fonction de son indice.
- Exemple : La suite arithmétique $a_n = 2n + 1$ où chaque terme est obtenu en multipliant l'indice par 2 et en ajoutant 1.

### 2. Définition par récurrence :
- Une suite définie par récurrence spécifie le premier terme (ou les premiers termes) de la suite, ainsi qu'une relation qui permet de calculer les termes suivants en fonction des termes précédents.
- Exemple : La suite de Fibonacci $F_{n+2} = F_{n+1} + F_n$, avec les premiers termes $F_0 = 0$ et $F_1 = 1$.

### 3. Sens de variation :
- Une suite est dite croissante si chaque terme est plus grand ou égal à son prédécesseur, c'est-à-dire $a_{n+1} \geq a_n$ pour tout $n$.
- Une suite est dite décroissante si chaque terme est plus petit ou égal à son prédécesseur, c'est-à-dire $a_{n+1} \leq a_n$ pour tout $n$.

### 4. Suites majorées et minorées :
- Une suite est dite majorée si tous ses termes sont inférieurs ou égaux à une certaine valeur appelée borne supérieure.
- Une suite est dite minorée si tous ses termes sont supérieurs ou égaux à une certaine valeur appelée borne inférieure.

### 5. Limites :
- Une suite peut avoir une limite finie ou infinie. La limite d'une suite est la valeur vers laquelle les termes de la suite tendent lorsque l'indice devient très grand.
- Exemple : La suite $a_n = \frac{1}{n}$ a pour limite $0$ lorsque $n$ tend vers l'infini.

### 6. Suites convergentes et divergentes :
- Une suite est dite convergente si elle a une limite finie.
- Une suite est dite divergente si elle n'a pas de limite finie.
- Exemple : La suite $b_n = (-1)^n$ est divergente car elle oscille entre $1$ et $-1$ sans converger vers une valeur spécifique.

## Raisonnement par récurrence

Le raisonnement par récurrence est une méthode de démonstration mathématique largement utilisée pour prouver des énoncés pour tous les entiers naturels.

### 1. Cas de base :
- On commence par prouver que l'énoncé est vrai pour un certain entier de départ (généralement \(n = 0\) ou \(n = 1\)). C'est la première étape appelée le cas de base.

### 2. Hypothèse de récurrence :
- On suppose que l'énoncé est vrai pour un entier quelconque \(k\), où \(k\) est un entier fixé mais arbitraire. C'est l'étape de l'hypothèse de récurrence.

### 3. Étape de récurrence :
- On démontre ensuite que si l'énoncé est vrai pour \(k\), alors il est également vrai pour \(k + 1\). C'est la partie de l'étape de récurrence.

### 4. Conclusion :
- En combinant le cas de base, l'hypothèse de récurrence et l'étape de récurrence, on peut conclure que l'énoncé est vrai pour tous les entiers naturels \(n\) à partir du cas de base.

### Exemple :
- **Énoncé :** La somme des $n$ premiers entiers positifs est $\frac{n(n + 1)}{2}$.
- **Cas de base :** Vérifié pour $n = 1$.
- **Hypothèse de récurrence :** Supposons vrai pour un $k$ quelconque.
- **Étape de récurrence :** Démontrons pour $k + 1$.
  $
  1 + 2 + \ldots + k + (k + 1) = \frac{k(k + 1)}{2} + (k + 1)
  $
- **Conclusion :** Par le principe de récurrence, la formule est vraie pour tous les entiers naturels \(n\).


## Interpolation Polynomiale avec le Polynôme d'Interpolation de Lagrange

L'interpolation polynomiale est une méthode mathématique qui consiste à construire un polynôme qui passe exactement par un ensemble donné de points. Le polynôme d'interpolation de Lagrange est une approche courante pour réaliser cela.

### 1. Forme générale du Polynôme d'Interpolation de Lagrange :
- Soit $x_0, x_1, \ldots, x_n$ les points d'interpolation avec des valeurs correspondantes $y_0, y_1, \ldots, y_n$.
- Le polynôme d'interpolation de Lagrange est donné par la formule :
  $
  P(x) = \sum_{i=0}^{n} y_i \prod_{j=0, j \neq i}^{n} \frac{x - x_j}{x_i - x_j}
  $

### 2. Idée Intuitive :
- Chaque terme dans la somme contribue avec le produit de termes de la forme $\frac{x - x_j}{x_i - x_j}$, où $i$ varie de $0$ à $n$.
- Ces termes sont conçus pour s'annuler sauf lorsque $x = x_i$, où le produit devient $1$, assurant que le polynôme passe par le point $(x_i, y_i)$.

### 3. Exemple :
- **Points d'Interpolation :** $(x_0, y_0), (x_1, y_1), \ldots, (x_n, y_n)$
- **Polynôme d'Interpolation de Lagrange :**
  $
  P(x) = L_0(x) y_0 + L_1(x) y_1 + \ldots + L_n(x) y_n
  $
  Où les $L_i(x)$ sont les polynômes de Lagrange associés aux points d'interpolation.

### 4. Polynômes de Lagrange :
- Les polynômes de Lagrange $L_i(x)$ sont définis par :
  $
  L_i(x) = \prod_{j=0, j \neq i}^{n} \frac{x - x_j}{x_i - x_j}
  $

### 5. Avantages et Limitations :
- **Avantages :** Le polynôme d'interpolation de Lagrange est simple à comprendre et à implémenter.
- **Limitations :** L'augmentation du nombre de points d'interpolation peut conduire à des polynômes de degré élevé, entraînant des problèmes de stabilité numérique.

L'utilisation du polynôme d'interpolation de Lagrange permet d'approximer une fonction inconnue à partir d'un ensemble discret de points, facilitant ainsi l'interpolation entre ces points.

## Résolution Approchée d'Équations Non Linéaires

### Problème Mathématique :

Considérons l'équation non linéaire $f(x) = 0$ où $f$ est une fonction réelle. Trouver une valeur de $x$ telle que $f(x) = 0$ est souvent difficile à résoudre analytiquement, et donc, des méthodes numériques sont employées pour obtenir des solutions approchées.

### Méthode de Dichotomie :

- **Condition :** La fonction $f(x)$ doit être continue sur l'intervalle $[a, b]$, et $f(a) \cdot f(b) < 0$ (la fonction change de signe sur l'intervalle initial).

- **Principe Mathématique :**
  1. **Choix de l'intervalle initial :** Sélectionner $[a, b]$ tel que $f(a) \cdot f(b) < 0$.
  2. **Division de l'intervalle :** Calculer le point médian $c = \frac{a+b}{2}$.
  3. **Sélection du sous-intervalle :** Choisir le sous-intervalle où la fonction change de signe et répéter.

  Formellement, l'itération de la dichotomie est donnée par :
  $
  c_n = \frac{a_n + b_n}{2}, \quad \text{si } f(a_n) \cdot f(c_n) < 0 \text{ alors } b_{n+1} = c_n \text{, sinon } a_{n+1} = c_n
  $
  
- **Comparaison :**
  - *Avantages :* Simple, converge de manière garantie, applicable même lorsque la fonction n'est pas dérivable.
  - *Limitations :* Convergence lente pour certaines fonctions, nécessite que la fonction change de signe sur l'intervalle initial.

### Méthode de Newton :

- **Conditions :** La fonction $f(x)$ doit être différentiable et $f'(x)$ ne doit pas être nul dans la région de convergence. Une estimation initiale raisonnable ($x_0$) est nécessaire.

- **Principe Mathématique :**
  1. **Choix de l'estimation initiale :** Sélectionner $x_0$.
  2. **Itération :** Calculer la prochaine approximation à l'aide de la formule de récurrence :
     $
     x_{n+1} = x_n - \frac{f(x_n)}{f'(x_n)}
     $
  3. **Répétition :** Répéter jusqu'à ce que la tolérance prédéfinie soit atteinte.

  La formule itérative de la méthode de Newton est donnée par :
  $
  x_{n+1} = x_n - \frac{f(x_n)}{f'(x_n)}
  $
  
- **Comparaison :**
  - *Avantages :* Convergence rapide avec une bonne estimation initiale, efficace pour les fonctions bien comportées.
  - *Limitations :* Diverge avec une mauvaise estimation initiale, nécessite le calcul de la dérivée, peut être instable pour certaines fonctions.

### Comparaison Globale :

- La méthode de dichotomie est plus robuste et ne nécessite pas la dérivabilité de la fonction, mais elle converge lentement.
- La méthode de Newton peut converger beaucoup plus rapidement avec une bonne estimation initiale, mais elle peut être instable avec une mauvaise estimation et nécessite le calcul de la dérivée.

### Critères d'Arrêt :

1. **Tolérance Absolue :** Arrêter l'algorithme lorsque la différence entre deux itérations successives est inférieure à une valeur seuil prédéfinie. $|x_{n+1} - x_n| < \epsilon$
2. **Tolérance Relative :** Arrêter l'algorithme lorsque la différence relative entre deux itérations successives est inférieure à une valeur seuil prédéfinie. $ \frac{|x_{n+1} - x_n|}{|x_{n+1}|} < \epsilon$
3. **Nombre Maximum d'itérations :** Limiter le nombre d'itérations pour éviter une exécution indéfinie. $n > n_{\text{max}}$

Le choix entre ces méthodes dépend du problème spécifique, de la nature de la fonction, et des connaissances préalables sur la solution attendue.