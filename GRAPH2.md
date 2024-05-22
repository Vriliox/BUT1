# GRAPH2

## 1. Vocabulaire de Base

### Définition d'un Graphe
Un **graphe** est une structure composée de deux ensembles :
- Un ensemble de **sommets** (ou **nœuds**), noté \( V \)
- Un ensemble d'**arêtes** (ou **liens**), noté \( E \), qui relient les sommets entre eux

### Sommets (Nœuds)
- **Sommet** (ou **nœud**): Un point ou une entité dans le graphe. Exemples : villes, ordinateurs.
- **Ordre** du graphe : Le nombre total de sommets dans le graphe.

### Arêtes (Liens)
- **Arête** (ou **lien**): Une connexion entre deux sommets. Exemples : routes entre villes, connexions réseau.
- **Boucle**: Une arête qui relie un sommet à lui-même.
- **Degré** d'un sommet : Le nombre d'arêtes incidentes à ce sommet.
  - **Degré entrant** (pour un graphe orienté) : Nombre d'arêtes entrant dans le sommet.
  - **Degré sortant** (pour un graphe orienté) : Nombre d'arêtes sortant du sommet.
  
### Types de Graphes
- **Graphe simple**: Un graphe sans boucles et sans arêtes multiples entre deux sommets.
- **Graphe complet**: Un graphe dans lequel chaque paire distincte de sommets est reliée par une arête unique.
- **Graphe orienté** (ou **digraphe**): Un graphe où les arêtes ont une direction, indiquée par une flèche.
- **Graphe non orienté**: Un graphe où les arêtes n'ont pas de direction.

### Sous-graphes
- **Sous-graphe couvrant**: Un graphe formé à partir d'un des sommets originaux et d'arrêtes choisies.
- **Sous-graphe induit**: Un sous-graphe obtenu en restreignant le graphe à un sous-ensemble de sommets et en conservant toutes les arêtes entre sommets de ce sous-ensemble.

### Chaînes, Chemins et Cycles
- **Chaîne (Graphe non orienté)**: Une séquence de sommets où chaque sommet est connecté au suivant par une arête.
- **Chemin (Graphe orienté)**: Une chaîne sans répétition de sommets.
- **Cycle**: Un chemin dont le premier et le dernier sommet sont les mêmes.

### Connexité
- **Graphe connexe**: Un graphe où il existe un chemin entre chaque paire de sommets.
- **Composante connexe**: Un sous-graphe connexe maximal.

### Pondération
- **Graphe pondéré**: Un graphe où chaque arête a un poids (ou une valeur), souvent utilisé pour représenter des distances, des coûts, etc.

### Matrices et Listes de Représentation
- **Matrice d'adjacence**: Une matrice \( A \) où \( A[i][j] \) représente l'existence (et éventuellement le poids) d'une arête entre les sommets \( i \) et \( j \).
- **Liste d'adjacence**: Une liste où chaque sommet a une liste des sommets adjacents (et éventuellement les poids des arêtes).

## 2. Parcours en Largeur (Breadth-First Search, BFS)

### Définition
Le **parcours en largeur** est une méthode de parcours des sommets d'un graphe de manière systématique et exhaustive, niveau par niveau à partir d'un sommet de départ. C'est une technique souvent utilisée pour trouver le chemin le plus court dans un graphe non pondéré.

### Principe

1. **Initialisation**: 
   - Choisir un sommet de départ, noté \( S \).
   - Marquer \( S \) comme visité.
   - Placer \( S \) dans une file (queue).
2. **Exploration**:
   - Tant que la file n'est pas vide :
     - Défile le sommet en tête de file, noté \( u \).
     - Pour chaque voisin \( v \) de \( u \) non visité :
       - Marquer \( v \) comme visité.
       - Placer \( v \) dans la file.
3. Répéter jusqu'à ce que tous les sommets accessibles soient visités.

#### En rajoutant les distances et père de chaque sommet

1. **Initialisation**: 
   - Choisir un sommet de départ, noté \( S \).
   - Marquer \( S \) comme visité.
   - Mettre la distance de \( S \) à 0
   - Placer \( S \) dans une file (queue).
2. **Exploration**:
   - Tant que la file n'est pas vide :
     - Défile le sommet en tête de file, noté \( u \).
     - Pour chaque voisin \( v \) de \( u \) non visité :
       - Marquer \( v \) comme visité.
       - Placer \( v \) dans la file.
       - Définir la distance de \( v \) à distance de \( u \) + 1
       - Définir le père de \( v \) à \( u \)
3. Répéter jusqu'à ce que tous les sommets accessibles soient visités.

### Propriétés
- **Complexité temporelle**: \(O(V + E)\), où \(V\) est le nombre de sommets et \(E\) le nombre d'arêtes.
- **Complexité spatiale**: \(O(V)\) pour stocker les sommets visités et la file.
- **Caractéristique principale**: BFS trouve le chemin le plus court (en termes de nombre d'arêtes) entre le sommet de départ et tout autre sommet dans un graphe non pondéré.

### Utilisations
- **Recherche de chemin le plus court** dans les graphes non pondérés.
- **Détection de cycles** dans les graphes non orientés.
- **Vérification de la connexité** d'un graphe.
- **Parcours de niveau** dans les arbres.


## 3. Algorithme de Dijkstra

### Définition
L'**algorithme de Dijkstra** est un algorithme de parcours de graphe utilisé pour trouver le plus court chemin entre un sommet source et tous les autres sommets dans un graphe pondéré à arêtes de poids non négatifs.

### Principe
1. **Initialisation**:
   - Définir une distance initiale infinie pour tous les sommets sauf pour le sommet source (distance initiale de zéro pour le sommet source).
   - Utiliser un ensemble pour stocker les sommets non visités.
   - Choisir un sommet de départ, noté \( S \).
   - Définir la distance à \( S \) à 0
2. **Exploration**:
   - Tant que des sommets non visités et avec une distance de + infini existent :
     - Sélectionner le sommet non visité avec la distance actuelle la plus petite, noté \( u \).
     - Mettre à jour la distance de tous les voisins de \( u \) en comparant la distance actuelle et la nouvelle distance possible via \( u \).
     - Marquer \( u \) comme visité.
3. Répéter jusqu'à ce que la plus petite distance soit déterminée pour tous les sommets.

### Propriétés
- **Complexité temporelle**:
  - Avec une file de priorité implémentée par un tas binaire : \(O((V + E) \log V)\)
  - Avec une file de priorité non ordonnée : \(O(V^2)\)
- **Complexité spatiale**: \(O(V + E)\)
- **Limitations**: Ne fonctionne pas correctement avec des arêtes de poids négatif.

### Utilisations
- **Routage dans les réseaux** pour trouver le chemin le plus court.
- **Navigation GPS** pour calculer les itinéraires optimaux.
- **Problèmes de planification** où les coûts ou les distances doivent être minimisés.

## 4. Parcours en Profondeur (Depth-First Search, DFS)

### Définition
Le **parcours en profondeur** est une méthode de parcours des sommets d'un graphe en explorant aussi loin que possible le long de chaque branche avant de revenir en arrière.

### Méthode Récursive
1. **Initialisation**:
   - Marquer tout les sommets en BLANC
   - Choisir un sommet de départ, noté \( S \).
   - Marquer \( S \) comme GRIS
2. **Exploration**:
   - Dans la fonction DFS du sommet s :
     - Pour chaque voisin y de s marqué en BLANC
       - Définir le père de y à s
       - Appeler DFS de y
     - Marquer s en NOIR

### Tri Topologique
Le **tri topologique** est un ordre linéaire des sommets d'un graphe orienté acyclique (DAG) tel que pour chaque arête \( uv \), le sommet \( u \) précède \( v \) dans l'ordre.

### Méthode par DFS pour le Tri Topologique
1. **Initialisation**:
   - Marquer tous les sommets comme non visités.
   - Créer une pile pour stocker l'ordre des sommets.
2. **Exploration**:
   - Pour chaque sommet, si non visité, appeler la fonction récursive DFS.
   - Dans la fonction DFS :
     - Marquer le sommet courant comme visité.
     - Pour chaque voisin non visité du sommet courant, appeler récursivement DFS sur ce voisin.
     - Ajouter le sommet courant à la pile après avoir exploré tous ses voisins.
3. **Extraction de l'ordre**:
   - Une fois tous les sommets traités, dépiler les sommets pour obtenir l'ordre topologique.

### Propriétés du DFS
- **Complexité temporelle**: \(O(V + E)\), où \(V\) est le nombre de sommets et \(E\) le nombre d'arêtes.
- **Complexité spatiale**: \(O(V)\) pour la pile et les marquages de sommets.

### Utilisations du DFS
- **Détection de cycles** dans les graphes.
- **Exploration de composantes connexes**.
- **Résolution de puzzles et problèmes de recherche** (ex. labyrinthe).
- **Tri topologique** dans les graphes orientés acycliques.

### Propriétés du Tri Topologique
- **Complexité temporelle**: \(O(V + E)\)
- **Applications**:
  - **Ordonnancement des tâches** avec des dépendances.
  - **Analyse des dépendances dans les compilateurs**.
  - **Planification de projets**.

## 5. Flots dans les Réseaux

### Définition
Un **réseau de flots** est un graphe orienté où chaque arête possède une capacité (représentant la quantité maximale de flot qu'elle peut transporter) et un flot (représentant la quantité de flot actuellement transportée).

### Terminologie
- **Source** (\( s \)) : Le sommet où le flot entre dans le réseau.
- **Puits** (\( t \)) : Le sommet où le flot sort du réseau.
- **Capacité** (\( c(u, v) \)) : La capacité maximale de flot d'une arête \( (u, v) \).
- **Flot** (\( f(u, v) \)) : La quantité de flot passant par une arête \( (u, v) \).

### Propriétés des Flots
- **Conservation du flot** : Pour chaque sommet \( v \) (autre que la source et le puits), la somme des flots entrant dans \( v \) est égale à la somme des flots sortant de \( v \).
- **Capacité de l'arête** : Pour chaque arête \( (u, v) \), le flot \( f(u, v) \) doit être inférieur ou égal à la capacité \( c(u, v) \).

### Problème du Flot Maximum
Le **problème du flot maximum** consiste à trouver la quantité maximale de flot qui peut être envoyée de la source au puits dans un réseau de flots.

### Algorithme de Ford-Fulkerson
L'**algorithme de Ford-Fulkerson** est une méthode pour résoudre le problème du flot maximum en utilisant l'idée de chemins augmentants. 

#### Étapes de l'algorithme
1. **Initialisation** : 
   - Initialiser le flot de chaque arête à zéro.
2. **Recherche de Chemin Augmentant** :
   - Tant qu'il existe un chemin augmentant du sommet source \( s \) au puits \( t \) (chemin où le flot peut être augmenté) dans le graphe résiduel, augmenter le flot le long de ce chemin.  
   - S'arrêter lorsque le graphe est complet
3. **Recherche de chaine améliorantes** :
   - On cherche à faire des chaines améliorantes en augmentant les arcs du bon sens et en réduisant les arcs du mauvais sens empruntés.
4. **Vérification**
   - Le valeur de flot trouvé doit correspondre au minimum des capacités des coupes.

### Propriétés de l'Algorithme de Ford-Fulkerson
- **Complexité temporelle** : La complexité dépend de la méthode utilisée pour trouver les chemins augmentants (par exemple, recherche en largeur ou en profondeur).
- **Convergence** : L'algorithme converge vers la solution optimale pour les réseaux de flots avec des capacités entières.

