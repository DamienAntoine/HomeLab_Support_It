# INC-002 — Recherche DNS inversée en échec

| Champ | Valeur |
| --- | --- |
| Date | 13 octobre 2026 |
| Catégorie | Réseau / DNS |
| Machine | SRV-DC01 |
| Statut | Résolu |

## Symptôme

Après la création de la zone de recherche inversée, la résolution d'une adresse IP en nom échoue, même après plusieurs minutes d'attente :

```
PS C:\> nslookup 192.168.100.10
Server:  UnKnown
Address:  ::1

*** UnKnown can't find 192.168.100.10: Non-existent domain
```

La résolution dans l'autre sens (nom vers IP) fonctionne normalement.

## Diagnostic

- **Fausse piste écartée** : le message « Server: UnKnown » apparaît aussi sur la commande qui fonctionne. Il ne concerne que le nom du serveur DNS interrogé (adresse de bouclage IPv6 `::1`), pas le problème.
- **« Non-existent domain »** signifie que le DNS ne trouve aucun enregistrement PTR pour cette adresse.
- Hypothèses vérifiées : nom de la zone inversée, puis présence de l'enregistrement PTR.
- Constat dans la console DNS : aucune zone dans *Reverse Lookup Zones*. La zone avait été créée par erreur dans *Forward Lookup Zones*.

## Cause

Erreur de manipulation : la zone a été créée comme zone de recherche directe. Le DNS la traitait comme une zone de noms ordinaire et ne l'utilisait pas pour la recherche inversée.

## Résolution

1. Suppression de la zone créée par erreur dans *Forward Lookup Zones*, en veillant à conserver `homelab.internal` et `_msdcs.homelab.internal`.
2. Création de la zone `100.168.192.in-addr.arpa` dans *Reverse Lookup Zones*.

## Vérification

```
PS C:\> nslookup 192.168.100.10
Server:  UnKnown
Address:  ::1

Name:    SRV-DC01.homelab.internal
Address:  192.168.100.10
```

