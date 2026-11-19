# TempoPoint — version finale

TempoPoint est une application bureau destinée à la gestion et au suivi d’activités liées aux machines, à l’automatisation et à la sécurité.

Ce dépôt contient la distribution finale du projet sous forme d’une archive ZIP.

## Contenu du projet

L’archive `temppoint.zip` contient notamment :

```text
temppoint/
├── app/
│   ├── index.html
│   └── modules/
│       ├── install.js
│       ├── rules.js
│       ├── machines.js
│       ├── stats.js
│       ├── automation.js
│       ├── security.js
│       ├── predictive.js
│       └── help.js
├── assets/
│   └── logo.svg
├── preload.js
├── linux_native_launcher.py
└── run_linux.sh
```

### Modules principaux

- **Installation** — installation ou configuration de TempoPoint.
- **Règles** — gestion des règles applicatives.
- **Machines** — suivi et gestion des machines.
- **Statistiques** — visualisation ou analyse des données.
- **Automatisation** — automatisation de tâches.
- **Sécurité** — fonctions liées à la protection et à la sécurité.
- **Prédictif** — fonctionnalités d’analyse prédictive.
- **Aide** — ressources d’assistance intégrées.

## Technologies

- HTML
- JavaScript
- Python
- Shell Bash
- SVG

## Prérequis

- Linux pour le lanceur natif fourni
- Python 3
- Bash
- Les dépendances mentionnées par les scripts inclus dans l’archive

## Installation

Clonez le dépôt puis décompressez l’application :

```bash
git clone https://github.com/Thomas27-py/tempoPoint_version_fin.git
cd tempoPoint_version_fin
unzip temppoint.zip
```

L’application décompressée se trouve dans le dossier `temppoint/`.

## Lancement sous Linux

Depuis la racine du projet :

```bash
cd temppoint
bash run_linux.sh
```

Vous pouvez également examiner le lanceur Python avant son exécution :

```bash
python3 linux_native_launcher.py
```

## Structure simplifiée

```text
assets/                  Ressources graphiques
app/index.html           Interface principale
app/modules/             Modules fonctionnels JavaScript
preload.js               Pont préchargé utilisé par l’application
linux_native_launcher.py Lanceur natif pour Linux
run_linux.sh             Script de démarrage Linux
```

## Développement

Avant toute modification :

1. Décompressez `temppoint.zip`.
2. Modifiez les fichiers nécessaires dans le dossier `temppoint/`.
3. Testez l’application sous Linux.
4. Recréez l’archive si vous souhaitez livrer une nouvelle version.

Exemple pour recréer l’archive :

```bash
zip -r temppoint.zip temppoint
```

## Auteur

Projet développé par **Thomas27-py**.

## Licence

Aucune licence n’est actuellement indiquée dans ce dépôt. Ajoutez un fichier `LICENSE` si vous souhaitez préciser les conditions d’utilisation, de modification et de redistribution.
