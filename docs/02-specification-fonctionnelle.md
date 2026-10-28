# Spécification fonctionnelle

## 1. Gestion des accès et des dossiers

- Remplacer la logique de correspondance par organisation par un mécanisme de **partage explicite des dossiers clients**.
- Pour chaque dossier, définir les utilisateurs autorisés et les actions permises :
  - consultation ;
  - édition ;
  - lancement de calcul ;
  - export ;
  - gestion du plan d’accompagnement.
- Appliquer les contrôles d’accès côté serveur à chaque requête.
- Appliquer un refus par défaut lorsqu’aucune autorisation explicite n’est trouvée.
- Les plans d’accompagnement, documents, calculs et historiques héritent du périmètre d’accès du dossier parent.

## 2. Moteur de règles

Pour chaque méthode ou règle, afficher son origine :

- le nom de l’expert ;
- le nom de l’organisme ;
- ou « Proposition de Probitas ».

## 3. Rôles et utilisateurs

Chaque utilisateur possède :

- un rôle : Grand Public, B2B ou Administrateur ;
- un pays de rattachement ;
- une visibilité : tous les pays ou son pays uniquement ;
- une offre : Free ou Premium pour les comptes Grand Public.

## 4. Administrateurs

Les administrateurs peuvent :

- sélectionner les sources de données : registres d’entreprises, LinkedIn et autres sources autorisées ;
- faire passer un utilisateur de Grand Public à Client B2B ;
- gérer les offres Free et Premium ;
- marquer les dossiers comme publics ou privés ;
- définir les champs publics et restreints ;
- consulter une page de suivi de la base de données ;
- lancer le calcul sur une sélection de dossiers selon des critères.

### Suivi de la base de données

La page de suivi doit afficher au minimum :

- le nombre de dossiers créés après une date sélectionnée ;
- le nombre de dossiers visibles du grand public ;
- la répartition des dossiers par pays ;
- la répartition des dossiers par statut public ou privé ;
- le nombre de calculs lancés ;
- le nombre d’utilisateurs par rôle et par offre.

## 5. Utilisateurs B2B

Un utilisateur B2B peut :

- accéder uniquement à ses propres dossiers et plans d’accompagnement ;
- accéder aux dossiers explicitement partagés avec lui ;
- créer des dossiers automatiquement rattachés à son compte ;
- bénéficier d’une finalité de dossier pré-remplie selon son type d’activité.

Il ne peut pas accéder aux dossiers d’un autre client B2B, même si ces dossiers appartiennent au même pays.

## 6. Rôle Grand Public

Le rôle Grand Public est attribué automatiquement aux utilisateurs qui créent un compte sans être clients B2B.

- Accès uniquement à la consultation publique.
- Consultation des dossiers explicitement marqués comme publics.
- Application du filtrage par pays.
- Accès aux fonctionnalités incluses dans l’offre Free ou Premium.

Un utilisateur Grand Public ne peut pas :

- créer de dossier ;
- consulter un dossier privé ;
- consulter les dossiers d’un autre utilisateur ;
- accéder aux plans d’accompagnement ;
- accéder aux fonctionnalités Premium sans souscription.

## 7. Consultation publique

La consultation publique permet une recherche multicritère avec trois zones :

1. Pays.
2. Nom.
3. Activité.

Les résultats appliquent simultanément :

- le filtrage par pays ;
- le statut public du dossier ;
- les règles de partage pour les informations restreintes ;
- les droits liés à l’offre gratuite ou Premium.
