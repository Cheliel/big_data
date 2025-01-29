

## Kmeans 

### Introduction
Le Kmeans est un algorithme de clustering qui permet de partitionner un ensemble de données en K groupes de clusters. L'objectif est de minimiser la variance intra-cluster et de maximiser la variance inter-cluster. 

### Fonctionnement
1. Initialisation: Choisir K points aléatoires comme centroïdes
2. Assigner chaque point au centroïde le plus proche
3. Mettre à jour chaque centroïde en calculant la moyenne des points qui lui sont assignés
4. Répéter les étapes 2 et 3 jusqu'à ce qu'il n'y ait pas de changement dans les centroïdes

### Implémentation
```python
from sklearn.cluster import KMeans
kmeans = KMeans(n_clusters=3)
kmeans.fit(X)
y_kmeans = kmeans.predict(X)
```

### Avantages
- Simple et rapide
- Efficace en grande dimension
- Donne des clusters de forme convexe

### Inconvénients
- Dépend du nombre de clusters K
- Sensible aux outliers
- Peut converger vers