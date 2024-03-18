# Introduction à la comptabilité

> La comptabilité c'est fournir des **informations chiffrées** pour rendre compte de la **gestion et de la situation financière** d'une organisation. Elle donne une image **fidèle**, **sincère** des **performances et du patrimoine** de celle-ci. Elle suit des règles. Elle constate le passé et sert à prevoir l'avenir.

## Les flux

- Réels (entrées et sorties de biens et services)
- Financiers (entrées et sorties monétaires)

> [!CAUTION]
> Chaque flux est enregistré sur 2 colonnes: **débit et crédit**.  
> Tout emploi suppose une ressource et toute ressource trouve son emploi.
>
> **Un débit est un flux entrant.  
> Un crédit est un flux sortant.**

Chaque flux est justifié (factures, chèques, virements, prélèvements...)

### Extrait du plan comptable

| Classe | Description                       | Compte | Utilité                                       |
|--------|-----------------------------------|--------|-----------------------------------------------|
| 1      | Comptes de capitaux               |        |                                               |
| 2      | Comptes d'immobilisations         |        |                                               |
| 3      | Comptes de stocks et en-cours     |        |                                               |
| 4      | Comptes de tiers                  |        |                                               |
|        |                                   | 411    | Créances envers les **clients**                   |
|        |                                   | 401    | Dettes envers les **fournisseurs**                |
| 5      | Comptes financiers                |        |                                               |
|        |                                   | 512    | Mouvements d'argent sur le compte **bancaire**    |
| 6      | Comptes de charges                |        |                                               |
|        |                                   | 607    | **Achat** des marchandises                        |
| 7      | Comptes de produits               |        |                                               |
|        |                                   | 707    | **Ventes** de produits finis                      |

> [!NOTE]  
> Les comptes 600 en débit.  
> Les comptes 700 en crédit.

## Exemple de journal (compte 411)

| Date       | Libellé                       | Débit (€)  | Crédit (€)  |
|------------|-------------------------------|------------|-------------|
| 2023-01-01 | Vente de produits             |            | 1,000       |
| 2023-01-05 | Paiement partiel par le client| 500        |             |
| 2023-01-15 | Nouvelle vente                |            | 800         |
| 2023-02-03 | Paiement intégral par le client| 1,300      |             |

### Exemples de compte en T

> [!NOTE]
> Débit à gauche  
> Crédit à droite.  
> Débit commence par un D, comme Droite, donc c'est à gauche.

<img src="https://www.cactus-compta.fr/img/operation-compte-T.png" alt="logo-markdown" width=500px />

### Exemple de balance

> [!WARNING]
> La somme des débits et crédits doit s'équilibrer


| Compte          | Libellé                                      | Débit (€)  | Crédit (€)  |
|-----------------|----------------------------------------------|------------|-------------|
| 101 - Capital   | Capital social                               |            | 10,000      |
| 401 - Fournisseurs | Dettes envers les fournisseurs              | 5,000      |             |
| 411 - Clients    | Créances envers les clients                  |            | 3,000       |
| 512 - Banque     | Mouvements d'argent sur le compte bancaire   | 15,000     |             |
| 607 - Achats      | Coût d'achat des marchandises               | 4,000      |             |
| 707 - Ventes      | Revenus des ventes de produits finis        |            | 11,000      |
| **Total**        |                                             | **24,000** | **24,000**  |

## Compte de résultats

> [!NOTE]
>Charges et produits sur une période donnée (HT). Il permet d’apprécier la rentabilité et la performance d’une société.

> [!WARNING]
> Pas d’investissement, de règlements, de dettes, de créances et de trésorie, c’est le rôle du bilan

- **Produits:** Revenus des ventes, débit
- **Charges:** Ensemble des achats, crédit (elec, eau, poubelle, taxes, impôts, location…)
- 3 catégories: Exploitation, financier et exceptionnel. Chaque catégorie donne un résultat intermédiaire.
	- Résultat d’exploitation + Résultat financier = Résultat courant avant impôts
	- et + le Résultat exceptionnel - participations et impôts = Résultat.

Le $résultat=produits-charges$. Bénéfice si résultat positif, perte si négatif. 

$$Ratio rentabilité = \frac{Resultat}{CA HT}$$

$$Taux évolution = \frac{(valeur arrivée)-(valeur départ)}{valeur départ} *100$$

<img src="https://www.comprendrelacompta.com/wp-content/uploads/2020/09/compte-de-resultat-4.png" alt="Compte de résultat" width="750px">

## Le bilan 

> [!NOTE]
> Le patrimoine de l'entreprise à un instant t. Permet de vérifier que les ressources sont adapatés aux besoins de l'entrprise.
> - **Actif**: Les immobilisations (Bâtiment, voiture...), les stocks, les créances des clients.
> - **Passif**: Capitaux propres, dettes.  
> 
> **Ils sont égaux**

[![alt text](https://vriliox.fr/images/Bilan.png)]

## Bilan Fonctionnel

> [!IMPORTANT]
> Actif --> Emploi  
> Passif --> Ressources  
> Bilan dans lequel les emplois et ressources sont établis par fonctions.  
> Permet d'établir **l'équilibre financier** de l'entreprise.

![alt text](https://vriliox.fr/images/BilanFonctionnel.png)

$$FRNG = Ressources Stables - Emplois Stables$$ 
Il doit être **positif**. Il défini la capacité des ressources à couvrir les investissements à long terme.

$$BFR = Actif Circulant - Passif Circulant$$
Il doit être le plus **faible**. Différence entre l'encaissement des créances clients et des paiements de fournisseurs. S'il est positif, l'entreprise doit piocher dans le long (FRNG).

$$TN = Trésorie Active - Trésorie Passive$$
$$TN = FRNG - BFR$$

Il se doit d'être **positif**, ou l'entreprise est à découvert pour financer le BFR. Les fonds disponible immédiatement, moins les découverts.

> [!TIP]
> Comment faire augmenter la Trésorie Nette (TN) ?
> - Augmenter le FRNG:
> 	- En augmentant les ressources stables (Emprunts long terme, le capital...)
> 	- En baissant les emplois stables (Cessions d'immobilisations)
> - Baissant le BFR:
> 	- En augmentant le Passif Circulant (Allonger les crédits, des dettes court termes.)
> 	- En baissant l'Actif Circulant (Stocks, les créances des clients, raccourcissant les crédits accordés)

Résumé:
![alt text](https://vriliox.fr/images/FRNGBFRTN.png)