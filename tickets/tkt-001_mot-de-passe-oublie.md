# TKT-001 — Mot de passe oublié

| Champ | Valeur |
| --- | --- |
| Type | Demande de service |
| Demandeur | Bob Gilda |
| Date d'ouverture | 16/10/26 |
| Date de clôture | 16/10/26 |
| Priorité | Moyenne |
| Statut | Clos |

## Description
J'ai oublié mon mot de passe, je ne peux plus me connecter à ma session.

## Diagnostic
Vérifier l'identité du demandeur, vérifier l'état du compte utilisateur (verrouillé, expiré, ...)

## Suivi

### 16/10/26 — Réinitialisation du mot de passe

**Actions :**
- Clique droit sur l'utilisateur dans Active Directory Users and Computers -> Reset password.
- Mot de passe temporaire, en cochant "User must change password at next logon".

**Vérification :**
- L'utilisateur a pu se reconnecter avec le nouveau mot de passe et le modifier

**Statut :** Clos

## Message de clôture

Bonjour Bob,

Votre mot de passe a été réinitialisé. Le mot de passe temporaire vous a été communiqué par téléphone. À votre prochaine connexion, Windows vous demandera d'en choisir un nouveau.

N'hésitez pas à nous recontacter si le problème persiste.

Le support informatique

