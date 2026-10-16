# TKT-003 — Arrivée d'un nouvel employé : Thomas Girard

| Champ | Valeur |
| --- | --- |
| Type | Demande de service |
| Demandeur | Sophie Lefèvre (RH) |
| Bénéficiaire | Thomas Girard (Comptabilité) |
| Date d'ouverture | 16/10/2026 |
| Date de clôture | 19/10/2026 |
| Priorité | Basse (demande planifiée, aucun utilisateur bloqué) |
| Statut | [À COMPLÉTER : Clos une fois la connexion de Thomas vérifiée] |

## Description
Nous recrutons Thomas Girard en comptabilité, il arrive lundi. Il lui faut les mêmes accès qu'Alice.

## Diagnostic
- Demande émise par les RH, source habituelle des arrivées d'employés.
- Groupes d'Alice Martin vérifiés avant la copie : `Domain Users` et `GG_Compta` uniquement. Ses accès correspondent à son rôle de comptable, la copie ne risque donc pas de donner des droits non prévus.

> En situation réelle, toujours vérifier les groupes d'un utilisateur avant de le copier : des droits accordés ponctuellement et jamais retirés seraient transmis au nouveau compte.

## Suivi

### 16/10/2026 — Préparation du compte

**Actions :**
- Copie de l'utilisateur Alice Martin dans Active Directory Users and Computers (clic droit sur Alice Martin → Copy).
- Nom : « Thomas Girard », identifiant : `tgirard`.
- Mot de passe temporaire défini.
- Compte créé **désactivé** jusqu'à l'arrivée de l'employé.

**Vérification :**
- Le compte est créé et désactivé.
- Groupes de Thomas Girard : [À COMPLÉTER : groupes constatés dans l'onglet Member Of]

**Message au demandeur :**

> Bonjour Sophie,

> Le compte de Thomas Girard, le nouveau comptable, est prêt. Il sera activé dès son arrivée lundi.

> Le support informatique

**Statut :** En attente (arrivée de l'employé prévue le 19/10/2026)

### 19/10/2026 — Activation à l'arrivée de l'employé

**Actions :**
- Activation du compte dans Active Directory Users and Computers (clic droit sur l'utilisateur → Enable Account).

**Vérification :**
- Connexion de Thomas sur PC-CLIENT01 et changement du mot de passe temporaire

**Statut :** Clos

## Message de clôture

> Bonjour Sophie,
>
> Le compte de Thomas Girard est actif. Ses identifiants lui ont été remis en main propre ce matin, et il a choisi son propre mot de passe à sa première connexion.
>
> N'hésitez pas à nous recontacter en cas de besoin.
>
> Le support informatique
