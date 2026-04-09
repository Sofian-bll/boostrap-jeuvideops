# DevOps Bootstrap — Jeux VideOps

![Banner](https://raw.githubusercontent.com/sofian-bll/bootstrap-jeuvideops/main/assets/banner.png)

> Premier projet DevOps réalisé dans le cadre du cursus **Web@cadémie Epitech Paris (Promo W1)**.  
> Mise en place d'un pipeline CI/CD complet sur une application Node.js/Express avec GitHub Actions.

---

## Stack & Outils

![Node.js](https://img.shields.io/badge/Node.js-16.13.x-339933?style=flat-square&logo=node.js&logoColor=white)
![Express](https://img.shields.io/badge/Express-4.x-000000?style=flat-square&logo=express&logoColor=white)
![GitHub Actions](https://img.shields.io/badge/GitHub_Actions-CI%2FCD-2088FF?style=flat-square&logo=github-actions&logoColor=white)
![ESLint](https://img.shields.io/badge/ESLint-Google_Style-4B32C3?style=flat-square&logo=eslint&logoColor=white)
![Mocha](https://img.shields.io/badge/Mocha-Unit_Tests-8D6748?style=flat-square&logo=mocha&logoColor=white)
![Cypress](https://img.shields.io/badge/Cypress-E2E_Tests-17202C?style=flat-square&logo=cypress&logoColor=white)
![nyc](https://img.shields.io/badge/nyc-Coverage_100%25-brightgreen?style=flat-square)
![JSDoc](https://img.shields.io/badge/JSDoc-Documentation-orange?style=flat-square)

---

## Présentation du projet

Ce projet est une **application calculatrice** en Node.js/Express exposant des routes HTTP pour effectuer des opérations
arithmétiques (`+`, `-`, `×`, `÷`, `^`).

L'objectif principal n'est pas l'application elle-même, mais la mise en place d'un **pipeline CI/CD automatisé**
permettant de garantir la qualité du code à chaque push.

---

## Pipeline CI/CD

Le workflow GitHub Actions est découpé en **deux jobs parallèles** :

### `my_first_job` — Prise en main

| Step        | Description                             |
|-------------|-----------------------------------------|
| Checkout    | Clone du repo sur le runner             |
| Setup Node  | Installation de Node.js 16.13.x         |
| Install     | `npm ci` — installation des dépendances |
| Hello World | Vérification que le runner répond       |
| List files  | Affichage de l'arborescence du projet   |

### `my_second_job` — Qualité & Automatisation

| Step                       | Outil                 | Description                                                      |
|----------------------------|-----------------------|------------------------------------------------------------------|
| Checkout + Setup + Install | —                     | Environnement propre (runner vierge)                             |
| Lint                       | ESLint (Google Style) | Vérification du style et des conventions JS                      |
| Unit Tests                 | Mocha                 | Tests de chaque méthode de la classe `Calculator`                |
| Coverage Report            | nyc                   | Vérification de 100% de couverture (branches, lignes, fonctions) |
| Export Coverage            | nyc lcov              | Génération du rapport HTML de couverture                         |
| Functional Tests           | Cypress               | Tests E2E sur les routes HTTP réelles                            |
| Documentation              | JSDoc                 | Génération automatique de la doc depuis les commentaires         |

---

## Fonctionnalités de l'application

| Route            | Opération      | Exemple                        |
|------------------|----------------|--------------------------------|
| `GET /add?a=&b=` | Addition       | `/add?a=2&b=3` → `2 + 3 = 5`   |
| `GET /sub?a=&b=` | Soustraction   | `/sub?a=5&b=2` → `5 - 2 = 3`   |
| `GET /mul?a=&b=` | Multiplication | `/mul?a=3&b=4` → `3 * 4 = 12`  |
| `GET /div?a=&b=` | Division       | `/div?a=10&b=2` → `10 / 2 = 5` |
| `GET /pow?a=&b=` | Puissance      | `/pow?a=2&b=3` → `2 ^ 3 = 8`   |

---

## Lancer le projet en local

```bash
# Cloner le repo
git clone https://github.com/sofian-bll/bootstrap-jeuvideops.git
cd bootstrap-jeuvideops

# Installer les dépendances
npm ci

# Lancer l'application
npm run app:serve
# → http://localhost:3000

# Lancer les tests unitaires
npm run mocha:test

# Vérifier la couverture (100% exigé)
npm run nyc:run

# Lancer le lint
npm run eslint:check

# Tests fonctionnels E2E
npm run cypress:test

# Générer la documentation
npm run jsdoc
```

---

## Structure du projet

```
bootstrap-jeuvideops/
├── .github/
│   └── workflows/
│       └── test.yml          # Pipeline CI/CD GitHub Actions
├── modules/
│   └── calculator.js         # Classe Calculator (logique métier)
├── tests/
│   └── test.js               # Tests unitaires Mocha
├── cypress/
│   └── e2e/
│       └── test.cy.js        # Tests fonctionnels Cypress
├── docs/                     # Documentation générée par JSDoc
├── coverage/                 # Rapport de couverture lcov
├── index.js                  # Point d'entrée Express
└── package.json
```

---

## Ce que j'ai appris

- Comprendre et distinguer **pipeline, workflow, job, step, runner, trigger, artefact**
- Mettre en place un pipeline CI/CD from scratch avec **GitHub Actions**
- Appliquer la **Google JavaScript Style Guide** avec ESLint
- Écrire des **tests unitaires** couvrant 100% du code avec Mocha + nyc
- Mettre en place des **tests E2E** avec Cypress (`start-server-and-test`)
- Générer de la **documentation automatique** avec JSDoc
- Comprendre pourquoi **chaque job tourne sur un runner vierge** et comment partager l'environnement

---

## Auteur

**Sofian B.** — Étudiant Web@cadémie Epitech Paris (Promo W1)  
En recherche d'alternance — Développement Web / Cybersécurité

[![GitHub](https://img.shields.io/badge/GitHub-sofian--bll-181717?style=flat-square&logo=github)](https://github.com/sofian-bll)
