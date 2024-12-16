**1. Contexte**

- **Client :** Organisation Nationale de Lutte contre le Faux-Monnayage (ONCFM).
- **Objectif :** Développer un algorithme pour détecter automatiquement les faux billets en euros à partir de dimensions et caractéristiques spécifiques.

---

**2. Approche**

- **Données :** Dimensions et caractéristiques des billets (vrai/faux inclus).
- **Méthodologie :**
    - Analyse exploratoire pour comprendre les patterns.
    - Nettoyage et traitement des données (imputation des valeurs manquantes avec régression linéaire).
    - Représenter les relations entre les variables avec la création du cercle de corrélation.
    - Choisir les méthodes de Prédiction.(régression logistique, Méthode K-means).
    - Comparer la performance de deux méthodes de prédiction: matrice de confusion et calcul des métriques (précision, rappel, F1-score)

---

**3. Résultats**

- **Modèle retenu :** Régression logistique (Précision : 95%, AUC : 0.98).
- **Impact :** Détection rapide et fiable des faux billets, réduction des erreurs humaines.

---

**4. Livrables**

- **Code Python :** Prétraitement des données, entraînement et déploiement du modèle.
- **Algorithme de test :** Permet de vérifier en temps réel l'authenticité de nouveaux billets.

---

**5. Outils Utilisés**

- Python (Pandas, Scikit-learn), Microsoft power bi pour les visualisations(Matplotlib/Seaborn).
- Outils de visualisation : Graphiques pour explorer les relations entre variables.(cercle de corrélation, matrice de confusion, méthode du coude).
