# TempoPoint

> Application bureau distribuée sous forme d’une archive, destinée à la gestion des machines, aux statistiques, à l’automatisation et aux fonctions prédictives.

**Dépôt :** `Thomas27-py/tempoPoint_version_fin`  
**Version :** archive finale `temppoint.zip`  
**Plateforme principale :** Linux  

## Présentation

TempoPoint est une application finale dont les sources distribuables sont regroupées dans l’archive `temppoint.zip`. Le dépôt ne fournit pas actuellement les dossiers applicatifs directement à la racine : il faut extraire l’archive pour accéder au code et aux ressources.

L’application est organisée autour d’une interface HTML et de modules JavaScript spécialisés. Elle contient également des lanceurs Python et Bash permettant son démarrage sur Linux.

> Les fonctionnalités ci-dessous sont décrites à partir des modules présents dans l’archive. Elles devront être précisées lors de l’ajout des sources directement dans le dépôt.

## Fonctionnalités attendues

- Interface graphique principale via `app/index.html`.
- Gestion et suivi des machines.
- Configuration des règles applicatives.
- Consultation de statistiques.
- Automatisation de tâches.
- Modules de sécurité.
- Module d’analyse prédictive.
- Module d’aide intégré.
- Gestion de l’installation.
- Ressources graphiques, notamment `assets/logo.svg`.
- Lanceur natif Linux et script Bash de démarrage.

## Technologies utilisées

| Technologie | Usage observé |
|---|---|
| HTML | Interface principale |
| JavaScript | Modules fonctionnels de l’application |
| Python 3 | Lanceur natif Linux |
| Bash | Script de démarrage |
| SVG | Logo et ressources graphiques |

Aucun manifeste de dépendances n’est actuellement présent à la racine du dépôt (`package.json`, `requirements.txt`, `pyproject.toml`, etc.). Les dépendances externes doivent donc être identifiées depuis les fichiers décompressés avant toute exécution reproductible.

## Structure du dépôt

```text
tempoPoint_version_fin/
├── temppoint.zip       Archive contenant l’application finale
└── README.md           Documentation du projet
```

Après extraction de l’archive :

```text
temppoint/
├── app/
│   ├── index.html             Interface principale
│   └── modules/
│       ├── install.js         Installation ou configuration
│       ├── rules.js           Règles applicatives
│       ├── machines.js        Gestion des machines
│       ├── stats.js           Statistiques
│       ├── automation.js      Automatisation
│       ├── security.js        Sécurité
│       ├── predictive.js      Fonctionnalités prédictives
│       └── help.js            Aide
├── assets/
│   └── logo.svg               Logo SVG
├── linux_native_launcher.py   Lanceur Python Linux
├── preload.js                 Script de préchargement
└── run_linux.sh               Script de lancement Bash
```

## Prérequis

### Minimum

- Linux
- Python 3
- Bash
- Utilitaire `unzip`
- Droit d’exécuter les scripts locaux

### Selon les modules

Avant le lancement, vérifiez dans les fichiers décompressés :

- Les modules JavaScript externes utilisés.
- Les dépendances Python importées par `linux_native_launcher.py`.
- Les commandes appelées par `run_linux.sh`.
- Les permissions nécessaires aux scripts.
- Toute variable d’environnement attendue.
- Les fichiers de configuration ou données externes nécessaires.

## Installation

### 1. Cloner le dépôt

```bash
git clone https://github.com/Thomas27-py/tempoPoint_version_fin.git
cd tempoPoint_version_fin
```

### 2. Extraire l’application

```bash
unzip temppoint.zip
cd temppoint
```

Pour remplacer une extraction existante :

```bash
rm -rf temppoint
unzip temppoint.zip
cd temppoint
```

### 3. Vérifier les scripts

Avant de lancer l’application, examinez les commandes et dépendances déclarées :

```bash
sed -n '1,240p' run_linux.sh
sed -n '1,240p' linux_native_launcher.py
```

Si les scripts utilisent des modules Python externes, installez-les explicitement dans un environnement isolé :

```bash
python3 -m venv .venv
source .venv/bin/activate
python3 -m pip install <dépendances>
```

Remplacez `<dépendances>` par les noms réellement importés par le lanceur Python.

## Lancement

À partir du dossier `temppoint/` :

```bash
bash run_linux.sh
```

Autre possibilité :

```bash
python3 linux_native_launcher.py
```

Si nécessaire, accordez l’autorisation d’exécution au script :

```bash
chmod u+x run_linux.sh
./run_linux.sh
```

Si l’application peut être ouverte dans un navigateur, la page d’entrée est :

```text
temppoint/app/index.html
```

Cependant, le dépôt ne contient pas actuellement de manifeste confirmant un runtime Electron ou navigateur. Certains scripts peuvent rester nécessaires pour initialiser l’application.

## Présentation des modules

### `install.js`

Gère vraisemblablement l’installation ou la préparation de l’application. Avant toute modification, documenter :

- Les opérations réellement effectuées.
- Les fichiers créés ou modifiés.
- Les erreurs possibles.
- Les permissions nécessaires.
- Les opérations idempotentes ou non.

### `rules.js`

Contient les règles métier ou les règles de configuration. Les développeurs doivent définir clairement :

- La provenance des règles.
- Leur validation.
- Leur persistance.
- Les règles pouvant être modifiées à chaud.
- Leur impact sur les machines et l’automatisation.

### `machines.js`

Concentre vraisemblablement les données et opérations liées aux machines. Une refonte future devrait isoler au minimum :

- Le modèle de données.
- Les appels externes.
- Les fonctions métier.
- La mise à jour de l’interface.
- La gestion des états hors ligne ou d’erreur.

### `stats.js`

Gère les données statistiques. Pour préserver la maintenabilité, ajouter idéalement :

- Une description des sources de données.
- Le format des statistiques.
- Les périodes prises en compte.
- Les fonctions d’agrégation.
- Les cas limites.

### `automation.js`

Contient les actions automatisées. Toute modification doit préciser :

- Les entrées attendues.
- Les actions exécutées.
- Les opérations réversibles.
- Les erreurs bloquantes.
- Les journaux générés.
- Les mécanismes d’arrêt ou d’annulation.

### `security.js`

Implémente les fonctions de sécurité. Toute contribution à ce module doit faire l’objet d’une revue attentive, notamment pour :

- Les entrées utilisateur.
- La gestion des identifiants.
- Les secrets.
- Les permissions.
- Les données sensibles.
- Les commandes système éventuelles.

### `predictive.js`

Contient l’analyse prédictive. Documenter explicitement :

- Le modèle ou l’algorithme utilisé.
- Les données d’entrée.
- Les résultats attendus.
- Les seuils de décision.
- Les limites du modèle.
- Les données utilisées pour les tests.

### `help.js`

Fournit l’aide intégrée. Les textes doivent idéalement être centralisés afin d’éviter les incohérences avec l’interface.

## Développement

### Extraire puis travailler sur une copie

```bash
unzip temppoint.zip
cp -R temppoint temppoint-dev
cd temppoint-dev
```

Ne modifiez pas `temppoint.zip` directement. Travaillez sur les fichiers extraits, testez-les, puis recréez l’archive.

### Créer une nouvelle archive

Depuis la racine du dépôt :

```bash
rm -f temppoint.zip
zip -r temppoint.zip temppoint
```

Pour vérifier le contenu :

```bash
unzip -l temppoint.zip
```

Pour vérifier l’intégrité :

```bash
unzip -t temppoint.zip
```

### Ajouter les sources directement au dépôt

Pour améliorer la maintenance du projet, l’objectif devrait être d’ajouter les fichiers décompressés au dépôt Git, plutôt que de conserver uniquement une archive. Une structure plus recommandée serait :

```text
.
├── app/
├── assets/
├── docs/
├── tests/
├── linux_native_launcher.py
├── run_linux.sh
├── package.json ou pyproject.toml
├── Makefile
└── README.md
```

Cela permettrait notamment :

- Une revue ligne par ligne des modifications.
- Le suivi de l’historique Git.
- Les contributions par pull request.
- Les tests automatisés.
- La gestion versionnée des dépendances.
- La publication de releases reproductibles.

## Tests

Aucune suite de tests n’est visible à la racine du dépôt à ce jour. Aucun fichier de test, manifeste ni workflow CI n’est donc disponible.

Avant une première contribution, le mainteneur devrait ajouter :

- Des tests unitaires pour les modules JavaScript.
- Des tests d’intégration pour le lanceur.
- Des tests des scripts Linux.
- Une commande unique pour exécuter tous les tests.
- Un workflow GitHub Actions pour automatiser les validations.

Exemple de tests à ajouter :

```text
tests/
├── test_install.js
├── test_machines.js
├── test_rules.js
├── test_stats.js
├── test_automation.js
├── test_security.js
└── test_predictive.js
```

## Débogage

### Lancer les scripts sans autorisation d’exécution

```bash
bash run_linux.sh
python3 linux_native_launcher.py
```

### Afficher les commandes disponibles dans le script

```bash
cat run_linux.sh
```

### Vérifier les imports Python

```bash
python3 -m compileall linux_native_launcher.py
```

### Vérifier la syntaxe JavaScript

Si Node.js est disponible :

```bash
node --check app/modules/install.js
node --check app/modules/rules.js
node --check app/modules/machines.js
node --check app/modules/stats.js
node --check app/modules/automation.js
node --check app/modules/security.js
node --check app/modules/predictive.js
node --check app/modules/help.js
```

Cette commande doit être exécutée depuis le dossier décompressé `temppoint/`.

## Sécurité

- Ne jamais intégrer de mots de passe, jetons ou clés privées dans l’archive.
- Ajouter les données locales sensibles à `.gitignore`.
- Vérifier toutes les commandes exécutées par le Python ou le shell.
- Ne pas exécuter une archive provenant d’une source inconnue sans l’avoir inspectée.
- Éviter les données personnelles dans les jeux de données de test.
- Prévoir une politique de gestion des versions lorsque l’application manipulera des machines réelles.

## Contribution

Les contributions sont les bienvenues après mise en place d’une structure de sources accessible.

1. Créez une branche :

```bash
git switch -c feature/ma-fonctionnalite
```

2. Décompressez et modifiez l’application.

3. Ajoutez ou mettez à jour les tests.

4. Vérifiez l’archive :

```bash
unzip -t temppoint.zip
```

5. Créez un commit clairement descriptif :

```bash
git add .
git commit -m "feat: ajouter la fonctionnalité X"
```

6. Poussez la branche et ouvrez une pull request :

```bash
git push origin feature/ma-fonctionnalite
```

Une contribution devrait idéalement contenir :

- L’objectif de la modification.
- Les fichiers concernés.
- La procédure de test.
- Les éventuels changements de configuration.
- Les captures d’écran pour les changements d’interface.
- Toute limitation connue.

## Résolution des problèmes

### `unzip` indique que l’archive est inexistante

Exécutez la commande depuis la racine du dépôt ou vérifiez :

```bash
ls -l temppoint.zip
```

### `run_linux.sh : permission denied`

```bash
chmod u+x run_linux.sh
bash run_linux.sh
```

### `ModuleNotFoundError` en Python

Identifiez le module importé par `linux_native_launcher.py`, puis installez-le dans un environnement virtuel :

```bash
python3 -m venv .venv
source .venv/bin/activate
python3 -m pip install <module-manquant>
```

### La page HTML ne fonctionne pas seule

Certaines applications nécessitent un processus de préchargement ou un lanceur natif. Vérifiez les références internes de `index.html` et les scripts chargés depuis `preload.js`.

## Informations sur la distribution

Le dépôt fournit actuellement l’application sous forme d’une archive ZIP. Avant publication d’une nouvelle release :

1. Extraire l’archive.
2. Tester chaque lanceur.
3. Vérifier les dépendances externes.
4. Supprimer les fichiers temporaires.
5. Régénérer l’archive.
6. Vérifier l’archive avec `unzip -t`.
7. Ajouter une somme de contrôle.
8. Publier une release GitHub.

## Auteur

Projet développé par **Thomas27-py**.

## Licence

Aucune licence n’est actuellement indiquée dans ce dépôt. Il est recommandé d’ajouter un fichier `LICENSE` avant toute redistribution ou utilisation externe.
