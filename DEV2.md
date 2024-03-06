# Containers

| Container     | Description                                                                                                                                                             | Utilisation                                                                                                                                                             | Complexité                                                                                         |
|---------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------|
| std::list     | Stocke ses éléments de manière ordonnée. Les éléments peuvent être insérés et supprimés n'importe où dans la liste.                            | Stocker des éléments qui doivent être insérés et supprimés fréquemment à différentes positions.                                                            | Insertion et suppression en O(1) si l'itérateur est connu, sinon en O(n). Accès aléatoire en O(n). |
| std::vector   | Stocke ses éléments de manière contiguë en mémoire. Les éléments peuvent être accédés par leur indice.                                         | Stocker des éléments qui doivent être accédés fréquemment par leur indice.                                                                                 | Insertion et suppression en O(n) car les éléments doivent être décalés. Accès aléatoire en O(1).   |
| std::map      | Stocke ses éléments sous forme de paires clé-valeur. Les éléments sont triés par clé.                                                          | Stocker des éléments qui doivent être recherchés fréquemment à l'aide d'une clé.                                                                           | Insertion, suppression et recherche en O(log(n)).                                                  |
| std::multimap | Stocke ses éléments sous forme de paires clé-valeur. Les éléments sont triés par clé. Plusieurs valeurs peuvent être associées à une même clé. | Stocker des éléments qui doivent être recherchés fréquemment à l'aide d'une clé, et pour lesquels plusieurs valeurs peuvent être associées à une même clé. | Insertion, suppression et recherche en O(log(n)).                                                  |
| std::queue    | Interface de file d'attente FIFO (First In, First Out). Les éléments sont ajoutés à la fin de la file et supprimés du début.       | Utilisé pour stocker des éléments qui doivent être traités dans l'ordre d'arrivée.                                                                                      | Insertion en O(1). Suppression en O(1) ou O(n) selon le conteneur sous-jacent.                     |
| std::stack    | Interface de pile LIFO (Last In, First Out). Les éléments sont ajoutés et supprimés du sommet de la pile.                          | Stocker des éléments qui doivent être traités dans l'ordre inverse d'arrivée.                                                                              | Insertion et suppression en O(1).                                                                  |
| std::set      | Stocke ses éléments de manière triée. Les éléments sont uniques.                                                                               | Stocker des éléments qui doivent être triés et pour lesquels l'unicité est importante.                                                                     | Insertion, suppression et recherche en O(log(n)).                                                  |


# Associations

|Multiplicité|Association|Implémentation|
|-|-|-|
|1 → 1<br>1..* → 1|A->B<br>A♢->B|Attribut privé de type B* dans la classe A|
||A♦->B|Construction/ destruction de l’attribut par le **constructeur/ destructeur** de A|
|1 → 0..1<br>1..* → 0..1|A->B<br>A♢->B|Attribut privé de type B* dans la classe A NULLABLE. Utilisation du **setter**.
||A♦->B|Construction de l’objet B* par une **méthode ajouter**. Destruction de l’objet B* par **une méthode supprimer ou par le destructeur**|
|1 → *|A->B<br>A♢->B|Collection privée d’objets de type B* dans la classe A<br>Instanciation de la collection dans le constructeur de A<br>Nécessite une **méthode pour ajouter/ supprimer/ rechercher** des objets dans la collection<br>Destruction de la collection dans le **destructeur** de A|
||A♦->B|Construction des objets B* par la **méthode ajouter**<br>Destruction des objets B* par la **méthode supprimer et/ ou par le destructeur**|
|1<->1|A<->B|Attribut privé de type B* dans la classe A **initialisé par le constructeur de A**<br>Attribut privé de type A* dans la classe B, **affectation d’une valeur par le modificateur**

> [!IMPORTANT]
> - Lors d'une association simple ou d'une agrégation, chaque objet de gère soi-même.
> - Lors d'une composition, l'objet "parent" doit instancier, détruire et gérer.
> - La multiplicité 0 signifie que la valeur peut être NULL. Utilisation de setter.
> - La multiplicité * signifie une collection. Des méthodes pour ajouter/ supprimer/ rechercher sont requises. Penser à détruire la collection et/ou son contenu.

# Héritage et polymorphisme en C++
> L'héritage et le polymorphisme sont deux concepts clés de la programmation orientée objet en C++.

## Héritage
L'héritage permet de créer de nouvelles classes à partir de classes existantes en héritant de leurs propriétés et méthodes. 

> [!NOTE]  
> Une classe Chien dérivée d’une classe Animal peut être considérée comme une
extension et une spécialisation de la classe Animal.  
> Inversement la classe de base Animal constitue une généralisation de la
classe Chien

Exemple:
```cpp
class Animal {
public:
    void manger() {
        cout << "Je mange" << endl;
    }
};

class Chien : public Animal {
public:
    void aboyer() {
        cout << "Wouaf !" << endl;
    }
};

int main() {
    Chien chien;
    chien.manger(); // affiche "Je mange"
    chien.aboyer(); // affiche "Wouaf !"
    return 0;
}
```

> [!IMPORTANT]  
> **Les constructeurs ne sont pas hérités par les classes dérivées.**   
> Pour initialiser la partie de l'objet issue de la classe de base, le constructeur de la classe de base doit être appelé à partir du constructeur de la classe dérivée.  
> Si le constructeur de la classe de base n'est pas appelé explicitement, le constructeur par défaut de la classe de base est automatiquement appelé.   
> L'initialisation des attributs spécifiés dans la classe dérivée est effectuée dans le constructeur de la classe dérivée.

> [!IMPORTANT]  
> **Les destructeurs ne sont pas hérités.**  
>  C++ appelle le destructeur de la classe dérivée avant celui de la classe de base. La suppression des objets membres est gérée par le destructeur de la classe dérivée.   
> Si la classe de base a un destructeur mais pas la classe dérivée, le compilateur génère un destructeur par défaut pour la classe dérivée qui appelle le destructeur de la classe de base et des objets membres.

## Polymorphisme
> Le polymorphisme permet de traiter des objets de différentes classes de manière uniforme. 

### Polymorphisme d'héritage

> Redéfinition, spécialisation ou overriding.  
> Possibilité de redéfinir une méthode dans des classes héritant d’une
classe de base en utilisant des méthodes virtuelles.

```cpp
class Animal {
public:
    virtual void display() {
        cout << "Animal" << endl;
    }
};

class Chien : public Animal {
public:
    void display() {
        cout << "Chien" << endl;
    }
};

int main() {
    Animal* animal1 = new Animal();
    Animal* animal2 = new Chien();
    animal1->display(); // affiche "Animal"
    animal2->display(); // affiche "Chien"
    delete animal1;
    delete animal2;
    return 0;
}
```

> [!NOTE]  
> Les destructeurs virtuels sont permis et parfois indispensables.  
>  Lorsqu'un pointeur sur une classe de base est utilisé pour pointer sur une classe dérivée, l'appel du destructeur de la classe de base ne supprime que la partie de l'objet issue de la classe de base.  
>  Pour supprimer l'objet entier, le destructeur de la classe de base doit être déclaré comme virtuel.

### Classe abstraite et interface

>Une méthode virtuelle pure est une méthode qui est déclarée, mais non définie dans une classe, avec, la classe n'est plus instanciable et l'ensemble de ses filles doit la redéfinir.  
Avec une une ou plusieurs méthodes virtuelles pures, on parle de **classe abstraite**.  
Avec seulement des méthodes virtuelles pure, on parle **d'interface**.  

```cpp
class Animal {
public:
    virtual void display() = 0;
};

class Chien : public Animal {
public:
    void display() {
        cout << "Chien" << endl;
    }
};

int main() {
    Animal* animal1 = new Animal(); // IMPOSSIBLE
    Animal* animal2 = new Chien();
    animal2->display(); // affiche "Chien"
    delete animal1;
    delete animal2;
    return 0;
}
```


### Polymorphisme paramétrique

> Généricité ou template  
> Possibilité de définir plusieurs fonctions de même nom mais possédant des paramètres différents (en nombre et/ou en type)


Exemple:
```cpp
public void buyBike(String brandt){ }
public void buyBike(String brandt, int model){ }
public void buyBike(int model, String brandt){ }
public void buyBike(int model){ }
public void buyBike(Bike b){ }
```

## Conversion d'objets

> [!NOTE]
> Il existe deux types de transtypage : 
> - la généralisation (upcast) consiste à changer vers une classe moins spécifique, c'est-à-dire de la classe dérivée vers la classe de base. C'est implicite et sans risque, mais on ne peut accéder qu'aux méthodes de la classe de base. 
> - La spécialisation (downcast), quant à elle, consiste à changer de la classe de base vers la classe dérivée. C'est un processus explicite et à risque.

```cpp
class Animal {
public:
    virtual void faireDuBruit() = 0;
};

class Chien : public Animal {
public:
    void faireDuBruit() {
        cout << "Wouaf !" << endl;
    }
};

int main() {
    Animal* animal = new Chien(); // généralisation (upcast) implicite
    animal->faireDuBruit(); // appelle la méthode de la classe Chien
    Chien* chien = dynamic_cast<Chien*>(animal); // spécialisation (downcast) explicite
    if (chien != nullptr) { // En cas d'erreur, dynamic_cast renvoie nullptr.
        chien->faireDuBruit(); // appelle la méthode de la classe Chien
    }
    delete animal;
    return 0;
}
```