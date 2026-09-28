# ARIANE — Capture data

Ce dépôt contient exclusivement les résultats de captation ARIANE destinés au démonstrateur.

Le référentiel normatif et les règles d'exécution restent dans `mkaldiAc/Ariane/ia`.

## Principes

- une CAPTURE est immuable après son commit initial ;
- une structure validée `STR-xxx` archivée est immuable ;
- `current/` est une projection consolidée mutable ;
- `catalog.json` et les `index.json` de programme sont des index techniques mutables ;
- ChatGPT peut créer de nouveaux répertoires et fichiers dans ce dépôt conformément au contrat `mkaldiAc/Ariane/ia/contracts/capture-storage.yaml` ;
- une exécution de captation ne modifie jamais le dépôt `mkaldiAc/Ariane`.

## Arborescence

```text
Ariane_capture_data/
├── catalog.json
└── programmes/
    └── <PROGRAMME_ID>/
        ├── index.json
        ├── captures/
        │   └── <CAPTURE_ID>/
        │       ├── capture.json
        │       ├── sources.json
        │       ├── structure_proposee.json      # initialisation seulement
        │       ├── objets_candidats.json        # incrémental si nécessaire
        │       ├── observations.json
        │       ├── relations.json
        │       └── anomalies.json
        ├── structures/
        │   └── STR-xxx/
        │       └── structure.json
        ├── current/
        │   ├── structure.json
        │   ├── sources.json
        │   ├── observations.json
        │   ├── relations.json
        │   └── anomalies.json
        └── validations/
```

Le front ARIANE découvre les programmes via `catalog.json`, puis lit chaque `programmes/<PROGRAMME_ID>/index.json`.

## État initial

Le catalogue est volontairement vide. La première exécution `INITIALISATION_PROGRAMME` créera le premier programme et sa première CAPTURE.
