# TKT-004 — Départ d'un employé : Bob Gilda

| Champ | Valeur |
| --- | --- |
| Type | Demande de service |
| Demandeur | Sophie Lefèvre (RH) |
| Bénéficiaire | Bob Gilda (Comptabilité) |
| Date d'ouverture | 16/10/2026 |
| Date de clôture | 19/10/2026 |
| Priorité | Moyenne (délai imposé : départ le soir même ; enjeu de sécurité sur les accès) |
| Statut | Clos |

## Description
Bob Gilda quitte l'entreprise ce soir, il faut désactiver son compte utilisateur.

## Diagnostic
- Identité de la demandeuse vérifiée.
- Départ confirmé par les RH : dernier jour le 16/10/2026.
- Accès de Bob Gilda relevés avant intervention : `Domain Users`, `GG_Compta`.

## Suivi

### 16/10/2026 — Expiration du compte en fin de journée

**Actions :**
- Clic droit sur Bob Gilda → Properties → onglet Account → Account expires : *End of* 16/10/2026.

**Message au demandeur :**

Bonjour Sophie,

Le compte de Bob ne permettra plus de se connecter à partir de ce soir. Je me chargerai lundi de la clôture complète de ses accès et de la récupération de son matériel.

Le support informatique

**Statut :** En attente (désactivation complète prévue le 19/10/2026)

### 19/10/2026 — Désactivation complète du compte

**Actions :**
- Désactivation du compte (clic droit → Disable Account).
- Retrait des groupes : `GG_Compta`. `Domain Users` conservé (groupe principal, non retirable).
- Déplacement de l'utilisateur dans l'UO `Deactivated`.
- Description du compte : « Parti le 16/10/2026 – TKT-004 – suppression prévue le 15/01/2027 ».

**Actions hors Active Directory (à réaliser en entreprise, hors périmètre du lab) :**
- Récupération du matériel (poste, badge, téléphone).
- Transfert des fichiers et de la boîte mail au manager.
- Révocation des accès aux applications externes.

**Statut :** Clos

## Message de clôture

Bonjour Sophie,

Les accès de Bob Gilda sont désormais clos : son compte est désactivé et retiré des groupes de la comptabilité. Il est conservé jusqu'au 15/01/2027 pour permettre la récupération de ses données, puis sera supprimé.

N'hésitez pas à nous contacter si son manager a besoin d'accéder à certains de ses fichiers d'ici là.

Le support informatique

