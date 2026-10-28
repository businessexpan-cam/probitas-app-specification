
# Tests de sécurité

## Objectif

Vérifier qu’aucun utilisateur ne peut accéder à un dossier, à un champ ou à une fonctionnalité sans droit explicite.

## Tests de filtrage par pays

- Un utilisateur limité à la France ne voit aucun dossier allemand.
- Un utilisateur limité à la France ne voit aucun dossier public allemand, même via recherche.
- Un utilisateur multi-pays voit uniquement les dossiers des pays autorisés.
- La modification du paramètre `country` dans l’URL ou l’API ne permet pas d’accéder à un pays non autorisé.

## Tests de rôles

- Un Grand Public ne voit aucun dossier privé.
- Un Grand Public ne peut pas créer de dossier.
- Un Grand Public ne peut pas accéder aux plans d’accompagnement.
- Un B2B ne voit pas les dossiers d’un autre B2B.
- Un B2B limité à la France ne voit pas les dossiers d’un autre pays.
- Un administrateur accède aux dossiers selon ses permissions administratives.

## Tests de partage explicite

- Un dossier non partagé n’est visible que par son propriétaire.
- Un dossier partagé en lecture seule ne permet pas l’édition.
- Un dossier partagé sans droit de calcul ne permet pas de lancer un calcul.
- La révocation d’un partage retire immédiatement l’accès.

## Tests d’offre

- Un utilisateur Free ne peut pas accéder aux champs Premium.
- Un utilisateur Free ne peut pas utiliser les services Premium.
- Un utilisateur Premium accède uniquement aux fonctionnalités incluses dans son offre.
- Les quotas de recherche sont appliqués côté serveur.

## Tests de contournement

- L’accès direct à un dossier privé par identifiant est refusé.
- L’accès direct à un dossier privé par URL est refusé.
- Les appels API appliquent les mêmes règles que l’interface.
- Les exports appliquent le filtrage par pays, le statut public et les droits de partage.
- Les calculs appliquent le même périmètre d’autorisation que la consultation.
- Les champs restreints ne sont jamais exposés sans droit explicite.

## Tests de robustesse

- En cas d’erreur de configuration des droits, l’accès est refusé.
- En cas d’absence de contexte utilisateur, l’accès est refusé.
- En cas de pays invalide, l’accès est refusé.
- Les tentatives d’accès refusées sont journalisées.
