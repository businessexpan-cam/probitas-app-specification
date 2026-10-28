# API

## Recherche publique

```http
GET /public/records/search
  ?country=FR
  &name=dupont
  &activity=conseil
  &page=1
  &limit=20
```

### Comportement attendu

Le serveur doit :

- identifier l’utilisateur connecté ;
- vérifier son rôle, son pays, sa visibilité et son offre ;
- ignorer ou refuser tout pays non autorisé ;
- filtrer sur `is_public = true` ;
- appliquer les quotas et limites de l’offre ;
- ne renvoyer que les champs autorisés.

## Détail public

```http
GET /public/records/{record_id}
```

### Comportement attendu

Le serveur doit vérifier :

- que le dossier existe ;
- qu’il est public ;
- que le pays est autorisé ;
- que l’utilisateur a le droit de consulter les champs demandés ;
- que son offre autorise les informations demandées.

## Réponses

### Dossier accessible

```json
{
  "id": "rec_123",
  "country_code": "FR",
  "entity_name": "Exemple SAS",
  "activity_label": "Conseil",
  "is_public": true,
  "fields": {
    "name": "Exemple SAS",
    "activity": "Conseil"
  }
}
```

### Dossier non accessible

```json
{
  "error": "not_found"
}
```

## Règles

- Le paramètre `country` transmis par le client est un sélecteur, pas une source de vérité.
- Le serveur recalcule toujours le pays autorisé à partir du compte utilisateur.
- Les erreurs d’autorisation ne doivent pas révéler l’existence d’un dossier privé.
- Tous les appels doivent être journalisés avec l’utilisateur, l’action, le dossier et le résultat.
