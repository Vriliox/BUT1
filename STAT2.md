# Série statistique à une variable

Supposons que nous ayons une série statistique à une variable $X$ contenant $n$ observations.

## Moyenne ($\bar{X}$)

La moyenne est calculée comme la somme des valeurs divisée par le nombre total d'effectifs :

$$
\bar{X} = \frac{1}{n} \sum_{i=1}^{n} X_i
$$

## Moyenne géométrique ($\bar{X}_g$)

La moyenne géométrique est la $n$-ème racine du produit des valeurs :

$$
\bar{X}_g = \left( \prod_{i=1}^{n} X_i \right)^{\frac{1}{n}}
$$

## Écart type corrigé ($\sigma$)

L'écart type corrigé mesure la dispersion des données autour de la moyenne. Il est calculé comme suit :

$$
\sigma = \sqrt{\frac{1}{n-1} \sum_{i=1}^{n} (X_i - \bar{X})^2}
$$

## Médiane

La médiane est la valeur centrale de la série statistique, c'est-à-dire la valeur qui divise la série en deux parties égales :

- Si $n$ est impair, la médiane est la valeur centrale.
- Si $n$ est pair, la médiane est la moyenne des deux valeurs centrales.

## Variance (V(X))

La variance mesure la dispersion des données par rapport à la moyenne :

$$
V(X) = \frac{1}{n} \sum_{i=1}^{n} (X_i - \bar{X})^2
$$

## Écart type ($\sigma$)

L'écart type est simplement la racine carrée de la variance :

$$
\sigma = \sqrt{V(X)}
$$

# Série statistique à une variable pondérée

Supposons que nous ayons une série statistique à une variable $X$ avec $n$ observations pondérées.

## Espérance ($E(X)$)

L'espérance, ou la moyenne pondérée, est calculée comme la somme des produits des valeurs par leurs poids, divisée par la somme des poids :

$$
E(X) = \frac{\sum_{i=1}^{n} n_i \cdot X_i}{\sum_{i=1}^{n} n_i}
$$

## Moyenne géométrique pondérée ($\bar{X}_g$)

La moyenne géométrique pondérée est calculée comme suit :

$$
\bar{X}_g = \left( \prod_{i=1}^{n} X_i^{n_i} \right)^{\frac{1}{\sum_{i=1}^{n} n_i}}
$$

## Médiane

La médiane pondérée est déterminée de la même manière que pour une série non pondérée.

## Variance ($V(X)$)

La variance pondérée est calculée comme la somme des poids pondérés des écarts à la moyenne, divisée par la somme des poids :

$$
V(X) = \frac{\sum_{i=1}^{n} w_i \cdot (X_i - E[X])^2}{\sum_{i=1}^{n} w_i}
$$

## Écart type ($\sigma$)

L'écart type pondéré est la racine carrée de la variance pondérée :

$$
\sigma = \sqrt{V(X)}
$$


# Série statistique à deux variables

Supposons que nous ayons une série statistique à deux variables $(X, Y)$ contenant $n$ observations.

## Espérance ($E[X]$, $E[Y]$)

L'espérance de chaque variable est calculée comme suit :

$$
E[X] = \frac{1}{n} \sum_{i=1}^{n} X_i \\
E[Y] = \frac{1}{n} \sum_{i=1}^{n} Y_i
$$

## Covariance ($\text{cov}(X, Y)$)

La covariance mesure la variation conjointe des deux variables par rapport à leurs moyennes respectives :

$$
\text{cov}(X, Y) = \frac{1}{n} \sum_{i=1}^{n} (X_i - E[X])(Y_i - E[Y])
$$

## Variance de $X + Y$ ($\text{Var}(X+Y)$)

La variance de la somme de deux variables est calculée comme suit :

$$
\text{Var}(X+Y) = \text{Var}(X) + \text{Var}(Y) + 2\cdot\text{cov}(X, Y)
$$

## Coefficient de corrélation linéaire ($\rho_{X,Y}$)

Le coefficient de corrélation linéaire mesure la force et la direction de la relation linéaire entre deux variables. Il est calculé comme suit :

$$
\rho_{X,Y} = \frac{\text{cov}(X, Y)}{\sigma_X \cdot \sigma_Y}
$$

où $\sigma_X$ et $\sigma_Y$ sont les écart-types respectifs de $X$ et $Y$.