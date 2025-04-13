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

![Diagramme UML](diagrammes/usecase1.png)

## Les Priorités des cas d’utilisation

Pour le 1er sprint, nous avons choisi :
- Pour l’administrateur : Ajouter un produit au site
- Pour le client : Passer une commande

### Cas d’utilisation : Ajouter produit au site
**Acteur principal** : Administrateur

#### Préconditions
- L’administrateur est connecté au back-office (interface d’administration).
- Il a les droits nécessaires pour gérer les produits.
- Les informations du produit sont bien remplies.
- Le produit n’existe pas déjà dans la base.

#### Postconditions
- Le nouveau produit est visible sur le site e-commerce côté client.
- Il est listé dans l’espace "Gestion des produits" de l’admin.
- Les clients peuvent le consulter et l’ajouter à leur panier.

|  | 1 | 2 | 3 | 4 | 5 |
| --- | --- | --- | --- | --- | --- |
| **Préconditions** | Administrateur connecté | F | T | T | T | T |
|  | Administrateur possédant les droits | F | T | T | T |
|  | Produit non existant dans la base |  | F | T | T |
|  | Infos du produit bien remplies |  |  | F | T |
| **Postcondition** | Ajout effectué | F | F | F | F | T |
| **Nombre de jeux de tests** | 2 | 2 | 2*n | 1 | 1 |

---

### Cas d’utilisation : Passer une commande
**Acteur principal** : Client

#### Préconditions
- Le client est connecté au back-office (interface client).
- Il a un panier non vide.
- Le produit est disponible en stock avec la quantité désirée.
- Les informations de livraison sont spécifiées.
- Le client choisit un mode de paiement adéquat.

#### Postconditions
- La commande est vérifiée par l’admin et confirmée.
- Le client reçoit un mail de confirmation.

|  | 1 | 2 | 3 | 4 | 5 |
| --- | --- | --- | --- | --- | --- |
| **Préconditions** | Client connecté | F | T | T | T | T |
|  | Panier non vide |  | F | T | T |
|  | Quantité disponible en stock |  |  | F | T |
|  | Informations de livraison fournies |  |  |  | F | T |
|  | Un mode de paiement choisi |  |  |  |  | T |
| **Postcondition** | Recevoir un mail de confirmation | F | F | F | F | T |
| **Nombre de jeux de tests** | 2 | 2 | 2*n | 1 | 1 |

---



## Cas d'utilisation de Haute Priorité
### Cas d'utilisation 1 : Connexion de l'utilisateur
![Diagramme de connexion](diagrammes/connexion.png)

#### Table de décision pour la connexion de l'utilisateur :
|                              | 1 | 2 | 3 | 4 |
|------------------------------|---|---|---|---|
| **Préconditions**            |   |   |   |   |
| Identifiant saisi            | F | T | T | T |
| Mot de passe saisi           | T | F | T | T |
| Identifiants valides         | T | T | F | T |
| **Postcondition**            |   |   |   |   |
| Connexion réussie            | F | F | F | T |
| **Nombre de jeux de tests**  | 1 | 1 | n | 1 |

---
### Cas d'utilisation 2 : Ajouter un produit au panier
![Diagramme de panier](diagrammes/panier.png)

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
### Cas d'utilisation 3 : Passer une commande
![Diagramme de commande](diagrammes/commande.png)

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

