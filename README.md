# brvm-data

Données de marché publiques de la BRVM, servies en JSON pour le BRVM-Dashboard.

**Ce dépôt ne contient aucune donnée personnelle** : uniquement de l'information de marché publiée (PER, actualités, résultats, dividendes), agrégée depuis des sources publiques. Il est public pour que le dashboard puisse la récupérer côté navigateur, sans jeton d'accès.

## Fichiers

| Fichier | Contenu | Source |
|---|---|---|
| `fundamentals.json` | PER par titre | sikafinance |
| `earnings.json` | Variation du résultat net (annuel) | sikafinance |
| `actualites.json` | Communiqués / actualités par titre | richbourse |
| `dividendes.json` | Dividendes recoupés (montant, rendement, détachement) | brvm.org + sikafinance + fluxbourse |

## Format

```json
{ "date": "2026-07-10", "count": 42, "data": { "SNTS": 12.28, "...": "..." } }
```

- `date` : date de génération (fraîcheur de la donnée)
- `count` : nombre d'entrées
- `data` : la charge utile, indexée par symbole BRVM

## Consommation

Le dashboard les récupère au chargement :

```
https://raw.githubusercontent.com/Jordy-Pr0g/brvm-data/main/fundamentals.json
```

Les **cours** ne sont pas ici : ils viennent de `Fredysessie/brvm-data-public` (CSV mensuels), déjà public.

## Mise à jour

Généré par les scripts du dépôt `diaspoinvest-automation` (`collect_fundamentals.py`, `collect_actualites.py`, `lire_rapports.py`, `dividendes_js.py`).

Rien ici n'est écrit à la main.
