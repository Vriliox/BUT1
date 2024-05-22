> [!WARNING]
> Ce document peut difficilement fonctionné sous cerrtains lecteurs/appareil dû au Latex présent.  
> Préférez utiliser **Visual Studio Code**

# Série statistique à une variable

Supposons que nous ayons une série statistique à une variable $X$ contenant $n$ observations.

## Moyenne ($\bar{X}$)

La moyenne est calculée comme la somme des valeurs divisée par le nombre total d'effectifs :

$$
\bar{X} = \frac{\sum_{i=1}^{n} x_i}{n} = \frac{Somme \space des \space x}{Nombre \space de \space x}
$$

- **Intérêt :** La moyenne est une mesure de tendance centrale qui résume l'ensemble des données par une seule valeur représentative. Elle permet de comprendre la valeur typique d'un ensemble de données et est utilisée pour comparer différentes séries de données.

## Moyenne géométrique ($\bar{X}_g$)

La moyenne géométrique est la $n$-ème racine du produit des valeurs :

$$
\bar{X}_g = \left( \prod_{i=1}^{n} x_i \right)^{\frac{1}{n}} = \sqrt[Nombre \space de \space x]{Produit \space des \space x}
$$

- **Intérêt :** La moyenne géométrique est utile pour des données qui sont multipliées entre elles, comme les taux de croissance. Elle donne une mesure centrale qui réduit l'impact des valeurs extrêmes et est appropriée pour des distributions asymétriques.

## Écart type corrigé ($\sigma$)

L'écart type corrigé mesure la dispersion des données autour de la moyenne. Il est calculé comme suit :

$$
\sigma = \sqrt{\frac{1}{n-1} \sum_{i=1}^{n} (x_i - \bar{X})^2}
$$

## Médiane

La médiane est la valeur centrale de la série statistique, c'est-à-dire la valeur qui divise la série en deux parties égales :

- Si $n$ est impair, la médiane est la valeur centrale.
- Si $n$ est pair, la médiane est la moyenne arithmétique des deux valeurs centrales.

- **Intérêt :** La médiane divise les données en deux parties égales, fournissant une mesure de tendance centrale qui n'est pas affectée par les valeurs extrêmes. Elle est idéale pour des distributions asymétriques ou lorsque des valeurs aberrantes sont présentes.

## Variance ($V(X))$

La variance mesure la dispersion des données par rapport à la moyenne :

$$
V(X) = \frac{1}{n} \sum_{i=1}^{n} (x_i - \bar{X})^2 = \bar{X^2} - \bar{X}^2 = Moyenne \space des \space x \space au \space carré - Moyenne \space de \space X, \space au \space carré
$$

- **Intérêt :** La variance mesure la dispersion des données autour de la moyenne. Elle quantifie la variabilité ou l'étalement des données, permettant de comprendre à quel point les valeurs individuelles diffèrent de la moyenne.

## Écart type ($\sigma$)

L'écart type est simplement la racine carrée de la variance :

$$
\sigma = \sqrt{V(X)}
$$

- **Intérêt :** L'écart type est la racine carrée de la variance et donne une mesure intuitive de la dispersion des données. Il est utilisé pour évaluer la consistance des données et comparer la variabilité entre différentes séries de données.

# Série statistique à une variable pondérée

Supposons que nous ayons une série statistique à une variable $X$ avec $n$ observations pondérées.

## Espérance ($E(X)$)

L'espérance, ou la moyenne pondérée, est calculée comme la somme des produits des valeurs par leurs poids, divisée par la somme des poids :

$$
E(X) = \frac{1}{N}\sum_{i=1}^{n} p_i \cdot x_i = \sqrt[Nombre \space de \space x]{Somme \space des \space produits \space de \space x \space par \space leur \space poid}
$$

Avec $N = p_1 + p_2 + p_3 + ... + p_n$

- **Intérêt :** L'espérance pondérée prend en compte les poids des observations, offrant une moyenne ajustée qui reflète mieux l'importance relative de chaque observation. Cela est crucial lorsque certaines observations sont plus significatives que d'autres.

## Moyenne géométrique pondérée ($\bar{X}_g$)

La moyenne géométrique pondérée est calculée comme suit :

$$
\bar{X}_g = \left( \prod_{i=1}^{n} X_i^{p_i} \right)^{\frac{1}{N}}
$$

- **Intérêt :** La moyenne géométrique pondérée est adaptée aux données pondérées par des poids, particulièrement utile pour les taux de croissance où les poids représentent l'importance relative de chaque observation.

## Médiane

La médiane pondérée est déterminée de la même manière que pour une série non pondérée.

- **Intérêt :** La médiane pondérée ajuste la valeur centrale en tenant compte des poids des observations, offrant une mesure centrale plus représentative lorsque les données ne sont pas également pondérées.

## Variance ($V(X)$)

La variance pondérée est calculée comme la somme des poids pondérés des écarts à la moyenne, divisée par la somme des poids :

$$
V(X) = \frac{1}{N} \sum_{i=1}^{n} p_i(x_i-\bar{X})^2 = \bar{X^2} - \bar{X}^2 = Moyenne \space des \space x \space au \space carré - Moyenne \space de \space X, \space au \space carré
$$

> Propriétés de la variance:
> $$
> V(X+c) = V(X)
> $$
> $$
> V(aX) = a^2V(X)
> $$

- **Intérêt :** La variance pondérée mesure la dispersion des données en tenant compte de leurs poids, permettant une meilleure évaluation de la variabilité lorsque les observations ont des importances différentes.


## Écart type ($\sigma$)

L'écart type pondéré est la racine carrée de la variance pondérée :

$$
\sigma = \sqrt{V(X)}
$$

- **Intérêt :** L'écart type pondéré est la racine carrée de la variance pondérée et fournit une mesure intuitive de la dispersion des données pondérées, utile pour comparer la variabilité des séries de données pondérées.

## Densité d'effectifs

La densité d'effectifs pour une amplitude. Permet de comparer des classes.

$$
d_i = \frac{p_i}{max-min}
$$

Où max et min sont le maximum et le minimum de la classe.

## Quartiles

La densité d'effectifs pour une amplitude. Permet de comparer des classes.

$$
Q_{[1;3]} = a+(b-a)\frac{\alpha-f(a)}{f(b)-f(a)}
$$

Où $f(a)$ est la borne inférieur des effectifs cumulés.  
Où $f(b)$ est la borne supérieur des effectifs cumulés.  
Où $a$ est la borne inférieur de la classe.  
Où $b$ est la borne inférieur de la classe.  
Où $\alpha$ est le quartile qui est $0,25$ ou $0,5$ ou $0,75$.

- **Intérêt :** Les quartiles divisent les données en quatre parties égales, fournissant des points de coupure qui aident à comprendre la distribution et la dispersion des données. Ils sont utiles pour identifier les valeurs extrêmes et pour comparer différentes sous-ensembles de données.

# Série statistique à deux variables

Supposons que nous ayons une série statistique à deux variables $(X, Y)$ contenant $n$ observations.

## Espérance ($E(XY))$

L'espérance est calculée comme suit :

$$
\bar{XY} = \frac{1}{N} \sum_{i=1}^{n} p_i x_i y_i
$$

- **Intérêt :** L'espérance de chaque variable dans une série à deux variables donne une estimation de la valeur moyenne attendue, permettant d'analyser et de comparer les valeurs centrales de deux ensembles de données simultanément.

## Covariance ($\text{cov}(X, Y)$)

La covariance mesure la variation conjointe des deux variables par rapport à leurs moyennes respectives :

$$
\text{cov}(X, Y) = \bar{XY} - \bar{X} \cdot \bar{Y}
$$

- **Intérêt :** La covariance mesure la variation conjointe de deux variables par rapport à leurs moyennes respectives. Elle indique si les deux variables tendent à augmenter ou à diminuer ensemble, offrant une première indication de leur relation.

## Variance de $X + Y$ ($\text{Var}(X+Y)$)

La variance de la somme de deux variables est calculée comme suit :

$$
\text{Var}(X+Y) = \text{Var}(X) + \text{Var}(Y) + 2\cdot\text{cov}(X, Y)
$$

- **Intérêt :** La variance de la somme de deux variables permet de mesurer la dispersion totale lorsqu'on combine les deux variables, important pour évaluer les risques et les incertitudes dans des contextes où les variables sont combinées.


## Coefficient de corrélation linéaire ($\rho_{X,Y}$)

Le coefficient de corrélation linéaire mesure la force et la direction de la relation linéaire entre deux variables. Il est calculé comme suit :

$$
\rho_{X,Y} = \frac{\text{cov}(X, Y)}{\sigma_X \cdot \sigma_Y}
$$

où $\sigma_X$ et $\sigma_Y$ sont les écart-types respectifs de $X$ et $Y$.

- **Intérêt :** Le coefficient de corrélation linéaire mesure la force et la direction de la relation linéaire entre deux variables. Il est essentiel pour évaluer la dépendance entre les variables et pour identifier les relations significatives dans les analyses prédictives.

## Equation de la droite de régression (Moindre carrés)

La droite qui minimise les carrés de distances suivant x est d'équation y = ax + b avec:

$$
a = \frac{cov(X,Y)}{V(X)} \\ 
b=\bar{y}-a\bar{x}
$$

- **Intérêt :** La droite de régression permet de prédire des valeurs, comprendre et quantifier les relations entre variables, identifier des tendances, et soutenir des décisions informées basées sur des données empiriques.