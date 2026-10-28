
# Règle de filtrage par pays

## Données nécessaires

### Utilisateur

- `country_code` : pays de rattachement.
- `visibility_scope` :
  - `OWN_COUNTRY_ONLY` ;
  - `ALL_COUNTRIES`.
- `role` : Grand Public, B2B ou Administrateur.
- `plan` : Free ou Premium.

### Dossier

- `country_code` : pays du dossier.
- `owner_user_id` ou `owner_account_id` : propriétaire du dossier.
- `is_public` : dossier public ou privé.
- `public_fields` : champs visibles publiquement.
- `restricted_fields` : champs restreints.
- `record_shares` : partages explicites.

## Règle de décision

```text
SI user.visibility_scope = ALL_COUNTRIES
ALORS le pays du dossier ne constitue pas une restriction.

SINON SI user.visibility_scope = OWN_COUNTRY_ONLY
ALORS record.country_code DOIT être égal à user.country_code.

SINON
ALORS accès refusé.
```

## Exemple

Pour un utilisateur rattaché à la France avec une visibilité limitée à son pays :

```text
Dossier France + utilisateur propriétaire → accessible
Dossier France + dossier partagé explicitement → accessible
Dossier France + propriétaire autre B2B → non accessible
Dossier Allemagne → non accessible
Dossier Allemagne + partage explicite → non accessible, sauf si la visibilité est « Tous les pays »
```

## Application

Le filtrage par pays s’applique à :

- la recherche ;
- les listes de dossiers ;
- la fiche détaillée ;
- les exports ;
- les calculs ;
- les plans d’accompagnement ;
- les liens directs et appels API.

## Règles complémentaires

| Rôle | Périmètre géographique | Périmètre de dossiers |
|---|---|---|
| Grand Public | Selon visibilité | Dossiers publics uniquement |
| B2B | Selon visibilité | Ses dossiers et dossiers partagés |
| Administrateur | Tous les pays | Tous les dossiers, selon permissions |
| Utilisateur multi-pays | Tous les pays | Dossiers autorisés, sous réserve des règles de propriété et partage |
