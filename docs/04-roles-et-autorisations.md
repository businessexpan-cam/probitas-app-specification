# Rôles et autorisations

## Rôles

| Rôle | Accès principal | Création de dossiers | Consultation publique |
|---|---|---:|---:|
| Grand Public | Dossiers publics uniquement | Non | Oui |
| Client B2B | Ses dossiers et dossiers partagés | Oui | Selon droits |
| Administrateur | Ensemble de la plateforme | Oui | Oui |

## Attributs utilisateur

```text
User
- id
- email
- role : GRAND_PUBLIC | B2B | ADMIN
- country_code
- visibility_scope : OWN_COUNTRY_ONLY | ALL_COUNTRIES
- plan : FREE | PREMIUM
- created_at
```

## Attributs dossier

```text
Record
- id
- country_code
- owner_user_id / owner_account_id
- is_public : true | false
- public_fields
- restricted_fields
- activity_code
- activity_label
- entity_name
- created_at
- updated_at
```

## Partage explicite

```text
RecordShare
- record_id
- user_id
- can_read
- can_edit
- can_run_calculation
- can_export
- granted_by
- granted_at
```

## Règle d’autorisation

```text
Accès autorisé =
  rôle compatible
  AND pays autorisé
  AND dossier public OU propriétaire OU partage explicite
  AND offre compatible
  AND action autorisée
```

## Principes

- Refus par défaut.
- Contrôle côté serveur à chaque requête.
- Héritage du périmètre du dossier parent pour les objets liés.
- Aucune élévation de droits implicite.
- Journalisation des accès refusés et des actions sensibles.
