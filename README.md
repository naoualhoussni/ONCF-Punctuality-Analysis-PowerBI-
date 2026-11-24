# 🚆 ONCF — Analyse et Storytelling Visuel de la Ponctualité du Réseau Ferroviaire Marocain

[![Python](https://img.shields.io/badge/Python-3.10%2B-blue?logo=python&logoColor=white)](https://www.python.org/)
[![Power BI](https://img.shields.io/badge/Power_BI-Desktop-F2C811?logo=powerbi&logoColor=black)](https://powerbi.microsoft.com/)
[![Pandas](https://img.shields.io/badge/Pandas-2.0%2B-150458?logo=pandas&logoColor=white)](https://pandas.pydata.org/)
[![Status](https://img.shields.io/badge/Status-Completed-success)]()

> **Projet Data Analytics & Business Intelligence**  
> Étude exploratoire, détection d'anomalies, modélisation DAX et conception d'un tableau de bord décisionnel interactif sur 50 000 circulations ferroviaires (2024–2025).

---

## 📌 Présentation du Projet

Ce projet a pour objectif d'analyser la ponctualité, d'étudier la distribution et la sévérité des retards, et d'identifier les goulets d'étranglement opérationnels du réseau ferroviaire marocain (ONCF).

Le projet s'appuie sur une démarche complète de **Data Analytics & Visual Storytelling** :
1. **Préparation & Qualité de données (Python / Google Colab) :** Nettoyage, conversions de types, contrôles de cohérence mathématique et métier, validation des seuils.
2. **Analyse Exploratoire (EDA) :** Étude des distributions, variations saisonnières, impact des heures de pointe et benchmarking des matériels (*Al Boraq*, *Al Atlas*, *TNR*).
3. **Tableau de Bord Décisionnel (Power BI) :** Conception d'un rapport interactif multipages aux couleurs officielles de l'ONCF (*Orange Signature* & *Bleu Ciel*), intégrant des alertes visuelles conditionnelles et un arbre de décomposition causale.

---

## 📊 Chiffres Clés du Réseau (Synthèse Exécutive)

| Indicateur (KPI) | Valeur Globale | Constat Métier |
| :--- | :---: | :--- |
| **Total Circulations** | **50 000** | Volume représentatif couvrant la période 2024–2025. |
| **Taux de Ponctualité (≤ 5 min)** | **53,83 %** | Seuil de ponctualité moyen du réseau. |
| **Retard Moyen à l'Arrivée** | **8,66 min** | Médiane de **5,0 min** (distribution asymétrique à queue longue). |
| **Taux de Retard Sévère (> 15 min)** | **16,80 %** | **Alerte Rouge** : près d'un train sur six subit un retard critique. |
| **Retard Maximal Observé** | **160 min** | Enregistré sur le réseau régional dense (TNR). |

---

## 🏆 Comparatif des Services : La Fracture de Performance

```
Al Boraq (Grande Vitesse)   █████████████████████████ 62,98 %  (Retard moyen : 6,58 min)
Al Atlas (Grandes Lignes)   █████████████████████     54,51 %  (Retard moyen : 8,41 min)
TNR (Navettes Régionales)   ███████████████████       49,08 %  (Retard moyen : 9,96 min)
```

- **Al Boraq (Excellence opérationnelle) :** Bénéficie d'une ligne dédiée et protégée, réduisant drastiquement les aléas extérieurs.
- **TNR (Zone de vulnérabilité) :** Partage des voies en zone dense (axe Casablanca – Rabat – Kénitra), forte fréquence et sensibilité extrême aux heures de pointe (chute sous les 49 % de ponctualité).

---

## 🔍 Diagnostic des Causes : Fréquence vs Sévérité

1. **Causes les plus fréquentes :**
   - *Exploitation / Circulation* (7 579 cas)
   - *Affluence voyageurs* (4 028 cas)
2. **Causes les plus critiques (Retard moyen par circulation retardée > 5 min) :**
   - ⚠️ **Incidents techniques : 22,86 min** de retard moyen (jusqu'à **26,85 min** sur les TNR).
   - ⚠️ **Travaux / Infrastructure : 17,24 min** de retard moyen.
   - ⚠️ **Météo : 15,21 min** de retard moyen.

---

## 🖥️ Architecture du Dashboard Power BI

Le tableau de bord interactif est articulé autour de 3 pages complémentaires :

### 📄 Page 1 : Vue Exécutive (Executive Overview)
- **Cartes KPI dynamiques :** Total des trains, Ponctualité globale, Retard moyen, et Retard > 15 min avec alerte conditionnelle en **Rouge (`#D00000`)**.
- **Courbe de tendance mensuelle :** Évolution sur 24 mois mettant en évidence les creux saisonniers (printemps et rentrée de septembre).
- **Donut Chart de gravité :** Répartition par classe de retard (Ponctuel, Faible, Modéré, Important, Sévère).
- **Classement des lignes ferroviaires :** Baromètre de performance par liaison.
- **Filtres interactifs :** Segment par type de train (*Al Boraq*, *Al Atlas*, *TNR*).

### 🔍 Page 2 : Causes des Retards & Décomposition
- **Graphique combiné (Pareto) :** Volume d'occurrences (barres) vs Retard moyen généré (courbe).
- **Arbre de décomposition (*Decomposition Tree*) :** Exploration interactive descendante :  
  `Retard Moyen` ➔ `Cause du retard` ➔ `Gamme de train` ➔ `Ligne ferroviaire`.
- **Tableau de synthèse :** Statistiques détaillées (moyenne, médiane, maximum).

### 📍 Page 3 : Analyse par Gares & Lignes
- **🗺️ Carte géographique interactive du Maroc (Azure Map) :** Géolocalisation des 9 gares principales avec coloration dynamique rouge/vert selon le niveau de ponctualité.
- **Matrice Origine × Destination :** Tableau croisé identifiant les paires de gares critiques (ex: Casa-Port ↔ Kénitra en rouge).
- **Nuage de points (Scatter Plot) :** Corrélation entre la durée théorique du voyage et le retard moyen.

---

## 📁 Structure du Projet

```
ONCF-Punctuality-Analysis-PowerBI-/
│
├── README.md                            # Présentation détaillée du projet
├── .gitignore                           # Exclusion des fichiers temporaires
│
├── notebooks/
│   └── ONCF_Data_Analysis_complet.ipynb # Notebook Jupyter / Colab (81 cellules)
│
├── data/
│   ├── circulations_retards_synthetiques_50000.csv  # Données sources (50 000 lignes)
│   ├── oncf_circulations_powerbi_ready.csv          # Données enrichies pour Power BI
│   └── dim_gares_maroc.csv                          # Coordonnées GPS des gares ONCF
│
└── powerbi/
    ├── oncf1.pbix  # Fichier source Power BI interactif
    └── oncf_theme.json                  # Charte graphique (Orange & Bleu Ciel)
```

---

## 🛠️ Stack Technique

- **Langage & Environnement :** Python 3.10+, Google Colab, Jupyter Notebook.
- **Bibliothèques d'analyse & Data viz :** Pandas, NumPy, Matplotlib, Seaborn.
- **Business Intelligence & Reporting :** Microsoft Power BI Desktop, DAX (Data Analysis Expressions), Azure Maps.
- **Contrôle de version :** Git, GitHub.

---

## 💡 Recommandations Métier & Pistes d'Action

1. **Désengorgement de l'axe TNR Casa – Kénitra :** Régulation dynamique des flux en période de pointe et réaménagement des correspondances.
2. **Priorisation de la maintenance préventive :** Cibler les équipements roulants pour réduire les incidents techniques, cause n°1 de la sévérité des retards.
3. **Information voyageurs proactive :** Automatiser les alertes dès qu'un retard dépasse 15 minutes pour améliorer la satisfaction usagers.

---

## 📝 Note Méthodologique

*Les données utilisées dans ce projet sont synthétiques et ont été générées à des fins académiques et pédagogiques d'analyse de données. Elles ne proviennent pas des systèmes opérationnels de l'ONCF et ne sauraient refléter les performances réelles du transport ferroviaire marocain.*

---

## 👤 Auteur

- **Naoual Houssni** — [GitHub](https://github.com/naoualhoussni)
