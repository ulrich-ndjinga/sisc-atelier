# Fiabilisation d'un export outbound (Power Query)

## Le problème

Un export d'expéditions outbound peut contenir des données incohérentes : casse différente pour un même transporteur, espaces parasites, doublons et une ligne de total intégrée aux données. Ces anomalies empêchent une analyse fiable des expéditions par transporteur : la machine considère « DHL » et « dhl » comme deux valeurs distinctes.

## Ce que fait la requête

Une chaîne Power Query de 7 étapes pour fiabiliser l'export :

1. Import de la source brute
2. Suppression des espaces parasites
3. Uniformisation de la casse
4. Suppression de la ligne de total (dernière ligne)
5. Suppression des doublons
6. Chargement de la table nettoyée

## Pourquoi c'est un flux, pas un nettoyage manuel

Le fichier brut reste inchangé. Le nettoyage est enregistré comme une suite d'étapes reproductibles et traçables. À chaque nouvel export au même format, il suffit d'actualiser la requête pour reproduire automatiquement le traitement.

L'objectif n'est donc pas de « nettoyer un fichier », mais de construire un traitement fiable et rejouable.

## Fichiers

- `outbound_export_brut.csv` — export synthétique non nettoyé
- `outbound_nettoyage.xlsx` — requête Power Query et résultat nettoyé
