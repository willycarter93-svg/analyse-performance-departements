# Analyse des Écarts de Performance entre Départements

![Python](https://img.shields.io/badge/Python-3.13.9-blue.svg)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange.svg)
![License](https://img.shields.io/badge/License-MIT-green.svg)

> **Une analyse statistique complète pour valider les différences de performance et de satisfaction entre départements d'une entreprise.**


## Résumé exécutif

Cette étude analyse **100 000 employés** répartis dans **9 départements** pour répondre à une question métier simple :

> *"Les écarts de performance observés entre départements sont-ils réels ou dus au hasard ?"*

**Verdict** : Les performances sont **statistiquement homogènes**, mais **Customer Support** présente une satisfaction significativement plus faible.


## Contexte métier

Une entreprise souhaite valider scientifiquement les différences de performance observées entre ses départements. L'objectif est de :

- Distinguer les **vraies différences** du **bruit statistique**
- Identifier les **départements à risque**
- Formuler des **recommandations RH** basées sur les données

## Problématique

Trois questions guident cette analyse :

1. **Les scores de performance diffèrent-ils selon le département ?**
2. **La satisfaction des employés dépend-elle du département ?**
3. **Quels facteurs influencent la performance et la démission ?**


## Données

| Caractéristique | Valeur |
|-----------------|--------|
| **Taille** | 100 000 lignes × 20 colonnes |
| **Valeurs manquantes** | Aucune |
| **Départements** | 9 |
| **Variables clés** | Department, Performance_Score (1-5), Employee_Satisfaction_Score, Monthly_Salary, Resigned |

## Stack technique

| Catégorie | Outils |
|-----------|--------|
| **Langage** | Python 3.13.9 |
| **Analyse** | pandas, numpy, scipy |
| **Statistiques** | statsmodels, scikit-posthocs |
| **Machine Learning** | scikit-learn |
| **Visualisation** | matplotlib, seaborn |
| **Environnement** | Jupyter Notebook |

## Méthodologie

### 1️- Analyse exploratoire (EDA)
- Statistiques descriptives par département
- Visualisations (boxplots, heatmaps)
- Vérification des hypothèses (normalité, homogénéité)

### 2️- Tests statistiques

| Question | Test utilisé | Résultat |
|----------|--------------|----------|
| Performance vs Département | Kruskal-Wallis | p = 0.468 → **NS** |
| Satisfaction vs Département | Kruskal-Wallis | p = 0.006 → **Significatif** |
| Paires significatives | Dunn post-hoc | CS < IT, Operations |
| Département vs Démission | Khi-deux | p = 0.327 → **NS** |
| Performance vs Satisfaction | Pearson | r = 0.002 → **NS** |

### 3️- Modélisation
- **Régression linéaire multiple** : R² = 0.262
- Seule variable significative : `Monthly_Salary` (effet négligeable)

## Résultats clés

### Performances homogènes
Aucune différence significative entre départements (p = 0.468).

### Customer Support : point d'attention
Satisfaction significativement plus faible que **IT** (p = 0.013) et **Operations** (p = 0.006).

### Démission indépendante du département
χ² = 9.179, p = 0.327 → les départs ne sont pas liés au département.

### Performance inexpliquée
**73.8%** de la variance de performance reste inexpliquée par les variables RH classiques.

## Recommandations métier

| Priorité | Action |
|----------|--------|
| 🔴 **Haute** | Mener une enquête qualitative sur **Customer Support** |
| 🟠 **Moyenne** | Intégrer de nouvelles variables (compétences, management) |
| 🟡 **Basse** | Explorer les facteurs de démission (évolution, ambiance) |

---

## Structure du projet

analyse-performance-departements/
│
├── README.md
├── notebooks/
│ ├── 01_exploration.ipynb
│ ├── 02_tests_statistiques.ipynb
│ └── 03_regression.ipynb
│
├── reports/
│ └── figures/
│
└── data/
└── employee_data.csv
