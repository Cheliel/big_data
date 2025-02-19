

## Les types de variables 

- variable qualitatife 
- variable ordiannale 
- variable quantitatives (disctrète thé & café)
- variable quantitatives (continue taille, poids et age)

## Quand les données (quantitative) ne sont pas comparable 

- Centrage et réduction => favorise les algo qui utilise la déscente de gradiant. Pour pouvoir comparer les choux et les carrote et il faut centré et réduire les variable quantitative 

- Analyse en composant principale, ne peut être faîte que sur les variables quantitative. Pour faire des traitement il va devoir calculer des moyen, médianne, écrat type, mais cela n'a aucun sens mathématique sur les variable qualitative. 


## Quand les variables sont qualitatives 

(moyen de payement - état de santé)

- Donner à la place de chaque modalité une valeur numérique. Jour de la semaine (1 - 7). Les valeurs n'ont aucun impacte, ce sont des modalité, (1 - 7) === (15 - 22). 

- On peut transformer ces modalité en beans, chaque modalité devient une colonne Samedi (0 / 1)


## Clustering 

*comparer un individu avec un autre => clustering, call non supervisé*

>Non supervisé, j'ai un jeu de données et je n'ai aucune idée de comment comparer ces individu. C'est une première étape pour classifier un jeu de données préscis. 



## Classification 

déterminé qu'un indiv. appartient à une class => classification 

>Ici on a des données par le métier, on a une colonne qui devra être déterminer, es ce que l'individu appartient à la class A ou B, malade pas malade, toxic, comestible. 


## Régression 

déterminé les caractéristique d'un individu => régression 

> La colonne a déterminer est réel avec une infinité de valeur, elle n'est pas sur deux modalité. 


Classification => variable qualitative 

Régression => variable quantitative 


## Analyse en composant principale 

C'est une transformation linéaire, il n'y a pas de déformation des axes. l'ACP calcule la valeur par laquelle on va devoir multiplier chaque axe pour réaliser cette opération de transformation linéaire. 

Quand le jeu de données n'est pas linaire, ce n'est pas applicable. D'en le pourcentage d'inertie, s'il n'y a pas d'éboulie, cela signifiques que l'analyse en composant princiaple n'a pas d'impacte. Il faut observé des coudes dans l'éboulis des valeur propres. 


## Algorithme supervisés et non supervisé 

> e.g. donnez moi le nom d'un algorythme supervisés et dite moi comment es ce qu'il fonctionne. 

### Le clustering (non supervisé)

Hiérarchique ascendent & kmeans :

On se base sur la distance en les différents individu. 

#### Classification Hiérarchique ascendent 

##### Aglomératif

On recherche la distance la plus petite entre les individus plus les groupes. 

**La hauteur des branches représente la différence entre les différents cluster.**

> Cette arbre n'a qu'un role, permettre de définir un découpage en nombre de classes. Il est donc possible de couper cette arbre à n'importe quelle hauteur et de trouver un nombre de classe. Cela sert à déterminer le nombre de class qu'il est intéressant d'étudier. 

*E.g. découper toutes la France en deux (ville / météo) n'est pas pertinent.*

###### Divisif 

On fait l'inverse, on part d'un groupe d'individu avec une forte hétérogénéité et on essaye de trouver des feuilles et tous les différencier. Pour le culstering cette algorythme n'a jamais été mi en place mais pour la classification oui. 

Dans le cas du cancer du seins si une des colonne de mon tableau peut séparer les individus en malade / pas malade c'est gagner. 


##### Inconvégnient 

Il est impossible d'utilisé ce type d'algorythme sur des grands jeu de données. Il serait trop long à sortir un résultat. 



#### K-means (Lloyd)

- définir aléatoirement deux point
- calculer les distences des individus entre ces deux points 
- déplacer ces points dans les baricentre de ces classes. 


Il existe en deux version soit on commence en lui donnant 2 individu, soit 2 points aléatoire. 
L'algo s'arrête lorsqu'il n'y a plus de variation entre deux itérations, il est possible de que l'aglo n'arrivent pas à faire trois catégories et tourne en boucle. 

On détermine le nombre de class en : 

- on fait toutes les classifications possible 
- on utilise l'aglo silhouette pour déterminer le quel est le meilleurs 
    - pour chaque individu, on calcule la distance entre lui même contre tout les individu de sa class, puis de lui même contre le baricentre des tout les groupes.


> Es ce que la silhouette fonctionne dans tous les cas ? Non quand il y a des groupe qui entoure un autre (des cercles imbriquer les un dans les autres) la silhouette ne peut pas fonctionner, car un point à une extrémité du cercle sera forcément plus loins de l'autre extrémité du cercle que du cercle étant situé à l'intérieur de lui. 


K-means peut aussi être utilisé pour diminuer le nombre de valeur, diminuer la complexité des données. En faisant des clustering, je peut rajouter des individus qui vont être dans un cluster particulier. Je peux ainsi rajouter artificelement le nombre d'individu, je ne crée pas d'information mais on peut avoir plus de valeur ce qui permet au algo de classification de mieux se comporter par la suite. 

On en fait k-means que sur les colonnes centré réduite. 



### Les plus proche voisin (supervisé)

On continue de faire rechercher les proximités mais on donne un nombre de voisin à trouver pour aiguillé la classification. 

#### Apprentissage 

Il faut découper notre jeu de donné en apprentissage & test pour controller les prédictions de notre algo. 

 **La complexité** permet de découper les groupes par rapport à notre jeu de donnée de manière de plus en plus préscise (une ligne ou un dessin qui englobe l'intégralité des point). En augmentant la complexité de l'ago on peut avoir une taux de réussite de 100% sur notre jeu de données. 


 **généralisation** Cependant notre modèle une fois entrainé dois rester général. Il ne doit pas servir juste à prédire notre jeu de données initial. Si la complexité est trop élevé notre algo ne sera plus général et sera utilisable que pour sont jeu d'entrainement. 


 Surapprentissage => faible biais, variance élevé 

 Sous-apprentissage => biais élevé, variance faible 

 #### L'échantillonnage 





## La courbe Roc 

Tester la performance des algorythmes + données une probabilité. L'air qu'il y a sous la courbe détermine sa fiabilité. 

Deux informations : 

- la sensibilité en ordonné 
- la spécification en absyss 

La courbe Roc montre la pertinence d'un algo sur un jeu de données. 


## La régression linéaire 


## Kernel 

Lorsque les données ne sont pas purement linéaire, il permet de tordre l'espace dimensionnel pour améliorer les résultats. 





# Présentation 

2/3 min 
- Expliquer les grandes ligne de la recherche 
- Les étapes traversé 
- Dire si on a validé / invalidé notre hypothèse 


(avoir un plan de ce que l'on va présenter)

Ne pas montrer tout les graphiques, parler de l'analyse, les axes de recherche, nos conclusion. Montrer quelques graph intermédiaire. 


