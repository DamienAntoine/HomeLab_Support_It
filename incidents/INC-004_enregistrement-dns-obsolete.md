# INC-004 — Enregistrement DNS obsolète après réinstallation du poste

| Champ | Valeur |
| --- | --- |
| Date | 15 octobre 2026 |
| Catégorie | Réseau / DNS / DHCP |
| Machine | PC-CLIENT01, SRV-DC01 |
| Statut | [À VÉRIFIER : Résolu] |

## Symptôme

Lors des vérifications côté serveur après la réinstallation de PC-CLIENT01, des incohérences apparaissent :

| Console | Constat |
| --- | --- |
| DHCP | Deux baux : `.100` (ancienne VM) et `.101` (nouvelle VM) |
| DNS, zone `homelab.internal` | `PC-CLIENT01` → `192.168.100.100` |
| DNS, zone inversée | PTR pour `.101` uniquement |

Le nom `PC-CLIENT01` pointe donc vers une adresse où il n'y a plus aucune machine.

## Analyse

- La nouvelle VM a une nouvelle adresse MAC. Le serveur DHCP identifie les clients par leur adresse MAC : il l'a considérée comme un nouveau client et lui a attribué l'adresse libre suivante, `.101`.
- Le serveur DHCP a créé l'enregistrement PTR de `.101`.
- L'enregistrement A `PC-CLIENT01` n'a pas été mis à jour : avec les mises à jour dynamiques sécurisées, il appartient à l'**ancien** compte ordinateur. Le nouveau poste, bien qu'il porte le même nom, est un autre compte dans AD et n'a pas le droit de le modifier.

## Impact

Toute connexion au poste par son nom (prise en main à distance, partage, ping) échoue, alors qu'elle fonctionne avec son adresse IP.

## Résolution

1. Suppression du bail DHCP `.100` de l'ancienne VM
2. Suppression de l'enregistrement A `PC-CLIENT01` → `.100` dans la zone `homelab.internal`
3. Nouvel enregistrement du poste dans le DNS, depuis PowerShell en administrateur :

```
ipconfig /registerdns
```

## Vérification

```
Server:  UnKnown
Address:  ::1

Name:    pc-client01.homelab.internal
Address:  192.168.100.101
```

## Leçons retenues

- Après le remplacement ou la réinstallation d'un poste, vérifier le DHCP **et** le DNS : la réinstallation ne nettoie pas les traces de l'ancienne machine.
- En entreprise, le mécanisme de **vieillissement et nettoyage** du DNS (*aging and scavenging*) supprime automatiquement les enregistrements qui ne sont plus rafraîchis.
- Symptôme typique en support : « ça fonctionne avec l'adresse IP, mais pas avec le nom ».
