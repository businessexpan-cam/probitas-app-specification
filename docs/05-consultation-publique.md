# Consultation publique

## Objectif

Permettre aux utilisateurs Grand Public de rechercher et consulter les dossiers explicitement publics, dans la limite de leur pays et de leur offre.

## Recherche multicritère

La recherche est organisée en trois zones :

| Zone | Champ | Comportement |
|---|---|---|
| Pays | Sélecteur de pays | Visible uniquement pour les utilisateurs autorisés à consulter plusieurs pays |
| Nom | Nom de personne, entreprise ou entité | Recherche partielle, insensible à la casse et aux accents |
| Activité | Secteur, métier ou code d’activité | Recherche par libellé ou code |

## Logique de recherche

```text
Résultats =
  dossiers publics
  AND pays autorisé
  AND nom correspondant, si renseigné
  AND activité correspondante, si renseignée
  AND droits liés à l’offre respectés
```

## Règle d’affichage

```text
SI record.is_public = true
ET record.country_code est autorisé pour l’utilisateur
ALORS le dossier apparaît dans les résultats.

SINON
ALORS le dossier n’apparaît ni dans la recherche ni dans le détail.
```

## Champs restreints

Un dossier public peut contenir des champs restreints.

```text
SI l’utilisateur a le droit d’accéder aux informations restreintes
ALORS afficher champs publics + champs restreints autorisés.

SINON
ALORS afficher uniquement les champs publics.
```

## Offres

| Fonctionnalité | Free | Premium |
|---|---:|---:|
| Consultation publique | Oui | Oui |
| Recherche multicritère | Limitée | Étendue |
| Nombre de recherches | Quota à définir | Quota supérieur ou illimité |
| Détail des dossiers publics | Champs de base | Champs enrichis |
| Historique de recherche | Non ou limité | Oui |
| Alertes | Non | Oui |
| Export | Non | Selon règles métier |
| Services complémentaires | Non | Oui |
