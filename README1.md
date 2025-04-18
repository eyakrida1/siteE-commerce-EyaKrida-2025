# Présentation du projet
- **Auteurs** : Eya Krida / Shadha Mefteh / Eya Dimassi
- **Date** : 04/04/2025
- **Sujet** : Site de e-commerce

## Introduction au projet
Développer un site web e-commerce permettant la vente de produits en ligne avec une interface utilisateur intuitive, un back-office de gestion et un système de paiement sécurisé.

## Spécification du projet

### Notions de base
#### E-commerce (commerce électronique)
Le site web aura pour vocation de vendre des produits physiques ou numériques via Internet. Il inclut un catalogue de produits, un panier d’achat, un système de paiement, ainsi qu’une interface de gestion pour l’administration du site.

### Contraintes du projet
- Site adapté à tous types d’appareils (pc / téléphone / tablette)
- Intégration d’un système de paiement sécurisé
- Une bonne **user experience** (une interface claire et intuitive)
- Gestion simple et efficace du back-office.
- Le projet devra être réalisé dans un délai fixé.

### Les acteurs
#### Client
- Utilisateur qui peut consulter les produits du site, passer des commandes, consulter son historique, modifier son profil.

#### Administrateur
- Responsable de la gestion du site (gérer produits et utilisateurs).

### Les fonctionnalités attendues
#### Client :
- Consulter les catégories et les marques des produits
- Consulter tous les produits
- Consulter un produit (voir son prix, description…)
- Rechercher des produits spécifiques
- Filtrer par prix, par catégorie, par marque
- Ajouter un produit au panier
- Passer une commande
- Modifier la quantité d’un produit dans le panier
- Supprimer un produit du panier
- Créer un compte ou se connecter à un compte existant
- Consulter son historique de commandes avec statut
- Se déconnecter du site
- Recevoir un mail de confirmation

#### Administrateur :
- Connexion sécurisée à son compte
- Ajouter / modifier / supprimer des produits
- Gérer les informations liées aux produits (modifier / ajouter / supprimer)
- Gestion des catégories / marques des produits (par exemple, ajouter une marque)
- Gestion des utilisateurs (voir la liste des clients inscrits, modifier ou supprimer un compte si besoin)
- Gestion des commandes (suivre / modifier les commandes)

## Diagramme de cas d’utilisation

![Diagram](Diagrammes/usecase1.png)

## Les Priorités des cas d’utilisation

Pour le 1er sprint, nous avons choisi :
- Passer une commande
- Ajouter un produit au panier



## Cas d'utilisation de Haute Priorité

### Cas d'utilisation 1 : Ajouter un produit au panier
![Diagram](Diagrammes/panier.png)

#### Table de décision pour l'ajout d'un produit au panier :
|                              | 1 | 2 | 3 | 4 |
|------------------------------|---|---|---|---|
| **Préconditions**            |   |   |   |   |
| Client connecté              | F | T | T | T |
| Produit disponible en stock  | T | F | T | T |
| Produit non déjà dans panier | T | T | F | T |
| Quantité demandée > 0        | T | T | T | F |
| **Postcondition**            |   |   |   |   |
| Produit ajouté au panier     | F | F | F | F |
| **Nombre de jeux de tests**  | 1 | 1 | n | 1 |

---

DIAGRAMME DE SEQUENCE


TRADUCTION EN ALGORITHME
Début
    si vérifierConnexion() alors
        si vérifierDroits() alors
            se connecter()
            afficherInterfaceAdmin()
            accéderGestionProduits()
            afficherFormulaireAjoutProduit()
            produit = saisirNouveauProduit()
            si vérifierInfosProduit(produit) alors
                si verifierProduitExist(produit) alors
                    messageErreur("Produit déjà existant")
                    ajusterProduit(produit)
                sinon
                    associerMarque(produit)
                    associerCategorie(produit)
                    ajouterProduitDansBaseDeDonnées(produit)
                    confirmationAjoutProduit()
                fin si
                afficherListeProduits()
                ajoutProduitEffectué()
            fin si
        fin si
    fin si
Fin

### Cas d'utilisation 2 : Passer une commande
![Diagram](Diagrammes/commande.png)

#### Table de décision pour passer une commande :
|  | 1 | 2 | 3 | 4 | 5 |
| --- | --- | --- | --- | --- | --- |
| **Préconditions** | Client connecté | F | T | T | T | T |
|  | Panier non vide |  | F | T | T |
|  | Quantité disponible en stock |  |  | F | T |
|  | Informations de livraison fournies |  |  |  | F | T |
|  | Un mode de paiement choisi |  |  |  |  | T |
| **Postcondition** | Recevoir un mail de confirmation | F | F | F | F | T |
| **Nombre de jeux de tests** | 2 | 2 | 2*n | 1 | 1 |

DIAGRAMME DE SEQUENCE


TRADUCTION EN ALGORITHME

Début
    si vérifierConnexion() alors
        si vérifierPanierVide() alors
            messageErreur("Panier vide")
        sinon
            si vérifierQuantitéDisponible() alors
                si vérifierStockDisponible() alors
                    validerQuantité()
                    infosLivraison = saisirInformationsLivraison()
                    modePaiement = choisirModePaiement()
                    commande = créerCommande()
                    enregistrerCommande(commande)
                    lierProduitsPanier(commande)
                    associerModeDePaiement(commande, modePaiement)
                    associerAdresseLivraison(commande, infosLivraison)
                    envoyerMailConfirmation(commande)
                    recevoirMailConfirmation()
                sinon
                    messageErreur("Quantité insuffisante en stock")
                fin si
            fin si
        fin si
    fin si
Fin

