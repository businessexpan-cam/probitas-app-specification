# probitas-app-specification
Due Dilligence
# Probitas — Spécification de la nouvelle application

Ce dépôt centralise la spécification fonctionnelle de la nouvelle version de l’application Probitas.

## Objectifs

- Remplacer la correspondance par organisation par un partage explicite des dossiers clients.
- Mettre en place un filtrage strict par pays.
- Distinguer les rôles Grand Public, Client B2B et Administrateur.
- Ouvrir une consultation publique pour les dossiers explicitement publics.
- Préparer les offres Free et Premium.
- Rendre traçable l’origine des règles du moteur de règles.

## Documents

- [Vision produit](docs/01-vision-produit.md)
- [Spécification fonctionnelle](docs/02-specification-fonctionnelle.md)
- [Règle de filtrage par pays](docs/03-regle-filtrage-pays.md)
- [Rôles et autorisations](docs/04-roles-et-autorisations.md)
- [Consultation publique](docs/05-consultation-publique.md)
- [API](docs/06-api.md)
- [Tests de sécurité](docs/07-tests-securite.md)

## Règle de sécurité principale

Les contrôles d’accès doivent être appliqués côté serveur à chaque requête, avec un refus par défaut.
