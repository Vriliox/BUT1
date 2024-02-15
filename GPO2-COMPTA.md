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
|        |                                   | 411    | Créances envers les clients                   |
|        |                                   | 401    | Dettes envers les fournisseurs                |
| 5      | Comptes financiers                |        |                                               |
|        |                                   | 512    | Mouvements d'argent sur le compte bancaire    |
| 6      | Comptes de charges                |        |                                               |
|        |                                   | 607    | Achat des marchandises                        |
| 7      | Comptes de produits               |        |                                               |
|        |                                   | 707    | Ventes de produits finis                      |

## Exemple de journal

| Date       | Compte | Libellé                       | Débit (€)  | Crédit (€)  |
|------------|--------|-------------------------------|------------|-------------|
| 01-01-2024 | 707    | Vente de produits (paiement diff)|            | 3000       |
| 01-01-2024 | 411    | Dette du client               | 3000        |             |
|------------|--------|-------------------------------|------------|-------------|
| 03-01-2024 | 607    | Achat de marchandise (paiement diff)| 1500 |          |
| 03-01-2024 | 401    | Dette au fournisseur |       |   1500  |
|------------|--------|-------------------------------|------------|-------------|
| 06-01-2024 | 512    | Paiement intégral par le client| 3000      |             |
| 06-01-2024 | 411    | Annulation dette client            |            | 3000         |
|------------|--------|-------------------------------|------------|-------------|
| 12-01-2024 | 512    | Réglement marchandise (Banque)|         |  1500     |
| 12-01-2024 | 401    | Annulation de la dette au fournisseur | 1500   |     |

### Exemples de compte en T

> [!NOTE]
> Débit à gauche  
> Crédit à droite.

<img src="https://www.cactus-compta.fr/img/operation-compte-T.png" alt="logo-markdown" width=500px />

### Exemple de balance

> La balance se fait après le calcul des soldes débitaires et soldes créditaires des comptes.

> [!WARNING]
> La somme des débits et crédits doit s'équilibrer


| Compte          | Libellé                                      | Débit (€)  | Crédit (€)  |
|-----------------|----------------------------------------------|------------|-------------|
| 101 - Capital   | Capital social                               |            | 10,000      |
| 401 - Fournisseurs | Dettes envers les fournisseurs             | 5,000      |             |
| 411 - Clients    | Créances envers les clients                  |            | 3,000       |
| 512 - Banque     | Mouvements d'argent sur le compte bancaire   | 15,000     |             |
| 607 - Achats      | Coût d'achat des marchandises               | 4,000      |             |
| 707 - Ventes      | Revenus des ventes de produits finis        |            | 11,000      |
| **Total**        |                                             | **24,000** | **24,000**  |
