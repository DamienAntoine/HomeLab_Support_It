# TKT-002 — Compte verrouillé

| Champ | Valeur |
| --- | --- |
| Type | Incident |
| Demandeur | Alice Martin (Comptabilité) |
| Date d'ouverture | 16/10/2026 |
| Date de clôture | 16/10/2026 |
| Priorité | Moyenne (impact faible : un seul utilisateur ; urgence élevée : il ne peut pas travailler) |
| Statut | Clos |

## Description
Mon compte est bloqué, je me suis trompée plusieurs fois de mot de passe.

## Diagnostic
- Identité de la demandeuse vérifiée.
- Compte constaté verrouillé dans Active Directory Users and Computers (fenêtre *Reset Password* : « locked out »).

> Verrouillage déclenché par la stratégie mise en place le 16/10/2026 (5 essais, déverrouillage automatique au bout de 10 minutes). Voir le journal du jour.

## Suivi

### 16/10/2026 — Déverrouillage du compte

**Actions :**
- Réinitialisation du mot de passe dans Active Directory Users and Computers, avec :
  - déverrouillage du compte (*Unlock the user's account*) ;
  - changement obligatoire du mot de passe à la prochaine connexion (*User must change password at next logon*).
- Mot de passe temporaire communiqué à l'utilisatrice par téléphone.

**Vérification :**
- L'utilisatrice se reconnecte et choisit un nouveau mot de passe.

**Statut :** Clos

## Message de clôture

Bonjour Alice,

Votre compte a été déverrouillé, et votre mot de passe a été réinitialisé. Le mot de passe temporaire vous a été communiqué par téléphone. À votre prochaine connexion, Windows vous demandera d'en choisir un nouveau.

N'hésitez pas à nous recontacter si le problème persiste.

Le support informatique

## Notes
- Si l'utilisatrice connaît son mot de passe, un simple déverrouillage suffit : inutile de lui imposer un changement.
- En cas de verrouillages à répétition, rechercher l'**événement 4740** dans le journal *Security* du contrôleur de domaine (PDC Emulator). Le champ *Caller Computer Name* indique la machine à l'origine des tentatives, souvent un appareil qui utilise encore un ancien mot de passe.
