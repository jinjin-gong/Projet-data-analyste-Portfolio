1) Organisation du Projet GitHub
```
DWFA-Réaliser une analyse de la condition d'Accèes à l'eau Potable dans le monde
│
├── README.md          # Documentation principale
├── scripts/
│   ├── dax/
│   │   ├── taux_acces_potable.dax
│   │   ├── evolution_taux_mortalite.dax
│   ├── sql/
│   │   ├── taux_population_rurale.sql
│   │   ├── jointure_stabilite_politique.sql
│   ├── python/
│   │   ├── preprocess_data.py
│   │   └── visualisation_data.py
│
├── data/              # Données source
│   ├── raw/           # Données brutes
│   └── processed/     # Données après transformation
│
└── reports/           # Résultats ou images de visualisation
    └── dashboard_screenshot.png
```
2) Scripts DAX
Voici des exemples de formules DAX pour Power BI.
a) Calculer le taux d’accès à l’eau potable:
```
Taux_Acces_EauPotable = 
DIVIDE(
    SUM('EauPotable'[Population_AccesEau]),
    SUM('EauPotable'[Population_Totale]),
    0
)
```
b) Évolution du taux de mortalité dans le temps:
```
Evolution_Mortalite = 
CALCULATE(
    SUM('Mortalite'[Taux_Mortalite]),
    DATESYTD('Date'[Date])
)
```
3. Scripts SQL
   
a) Taux de population rurale vs urbaine:
```
SELECT 
    Pays, 
    SUM(Population_Rurale) / SUM(Population_Totale) * 100 AS Taux_Rurale,
    SUM(Population_Urbaine) / SUM(Population_Totale) * 100 AS Taux_Urbaine
FROM Population
GROUP BY Pays;
```
SELECT 
    Pays, 
    SUM(Population_Rurale) / SUM(Population_Totale) * 100 AS Taux_Rurale,
    SUM(Population_Urbaine) / SUM(Population_Totale) * 100 AS Taux_Urbaine
FROM Population
GROUP BY Pays;
```
b) Jointure pour stabilité politique et accès à l'eau:
```
SELECT 
    p.Pays, 
    e.Taux_AccesEau,
    s.Stabilite_Politique
FROM EauPotable e
JOIN StabilitePolitique s 
ON e.Pays_ID = s.Pays_ID;
```
4. Automatisation en Python
a) Traitement des données
```
preprocess_data.py :
import pandas as pd
```
# Chargement des données
```
data = pd.read_csv('data/raw/eau_potable.csv')
```
# Nettoyage des données
```
data_clean = data.dropna(subset=['Taux_AccesEau', 'Population_Totale'])
```
# Export
```
data_clean.to_csv('data/processed/data_clean.csv', index=False)
print("Données nettoyées et exportées.")
```
import pandas as pd

# Chargement des données
```
data = pd.read_csv('data/raw/eau_potable.csv')
```

# Nettoyage des données
```
data_clean = data.dropna(subset=['Taux_AccesEau', 'Population_Totale'])
```
# Export
```
data_clean.to_csv('data/processed/data_clean.csv', index=False)
print("Données nettoyées et exportées.")
```
visualisation_data.py :
```
import pandas as pd
import matplotlib.pyplot as plt
```

# Chargement des données nettoyées
data = pd.read_csv('data/processed/data_clean.csv')

# Création du graphique
```
plt.plot(data['Annee'], data['Taux_AccesEau'])
plt.title("Évolution de l'accès à l'eau potable")
plt.xlabel("Année")
plt.ylabel("Taux d'accès à l'eau (%)")
plt.show()
```

## Scripts utilisés dans le projet

### 1. **Scripts SQL**
Les scripts SQL permettent d'extraire et de préparer les données depuis la base de données source.

- [extraction_data.sql](scripts/sql/extraction_data.sql) : Extraction des ventes sur une période donnée.
```

- [nettoyage_data.sql](scripts/sql/nettoyage_data.sql) : Nettoyage des données et suppression des doublons.

### 2. **Scripts DAX**
Les scripts DAX contiennent les calculs nécessaires pour les visualisations dans Power BI.

- [ventes_totales.dax](scripts/dax/ventes_totales.dax) : Calcule les ventes totales.
- [marge_brute.dax](scripts/dax/marge_brute.dax) : Calcule la marge brute.

### 3. **Scripts Power Query (M)**
Scripts pour transformer et préparer les données dans Power BI avec Power Query.

- [transformation_etape1.m](scripts/powerquery/transformation_etape1.m) : Transformation initiale des données.
- [fusion_tables.m](scripts/powerquery/fusion_tables.m) : Fusion de plusieurs tables.
