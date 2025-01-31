
# Explication du notebook BreastCancerWisconsin-Classification01

## Importation ds données 

Utiliser les dictionnaire pour transformer les valeur qualitative en valeur quantitative 


## Standard Scaler 




## Séparation des données 


- Il faut séparer le jeu de données en plusieurs partie (apprentissage, test , validation)

*Parfois quand le jeu de données est trop petit, on ne peut pas avoir 3 échantillons. Dans le cas des données pour le cancer du sein on découpera les données en 2 train & test*


x (train) => l'enssemble des information qui pourront donner la réponse y 

y (test) => l'échantillions sur lequel on va test notre apprentissage 


- Il est important lors du découpage de données de conservé les ratio entre les valeurs importante. Ici il faut garder le même pourcentage entre personne malade et non malade dans le set de train & de test. **random _state=0** / **stratify = y** *(vérifie les proportion)*

- Création de colonne échantillon pour ceux qui on le même qu'apprentissage pour x_train et inversement 

``` python

donnees.loc[X_train.index,'échantillon'] = 'apprentissage'
donnees.loc[X_test.index ,'échantillon'] = 'test'
donnees.reset_index(inplace=True)
donnees.set_index(['échantillon','id','diagnosis'],inplace=True)

X = donnees.copy()
y = donnees.reset_index()[cible].apply(lambda x: dictDiagnosis[x])
y.index = X.index

X_train, X_test, y_train, y_test = X.loc[('apprentissage'),:],\
                                   X.loc[('test'),:],\
                                   y.loc[('apprentissage')],\
                                   y.loc[('test')] 

```


## Déclaration des classificateurs


copy / paste 


## analyse des résultat : comparaison des différents algo 

aucROC => aire de la courbe *(on veut que la ne soit pas une diagonal == random)* plus l'air est grande plus c'est préscis 

accuracy => sinon accuracy c'est bien aussi x) 

## Choix simple des variable worst 

Filtrage pour enlever les colones worst 

Il va falloir faire la classification pour ce filtrage nous même 

## Choix du meilleurs algorithme pour notre jeu de données 





# Algorithme supervisé : démarche 

Data set => cancer du sein 

Se positionner avant : Affichage des évolutions des métriques dans les essais 

On fait a d'abord fait un entrainement sans traitement sur les données x_train, à présent on va comparer nos résultat après avoir appliquer des modifications type standardScaler à nos données x_train. 

Ici on va faire 5 essaie différents avec des traitement différents 



## TP 

1.    Effectuer un essai nouveau avec les données centrées et réduites (StandardScaler). Le model de l’algorithmes de StandardScaler doit être entrainé sur le jeu de données d’apprentissage uniquement.

2.    Effectuer un essai nouveau avec uniquement le colonnes WORST centrées et réduites (StandardScaler). Le model de l’algorithmes de StandardScaler doit être entrainé sur le jeu de données d’apprentissage uniquement.*

3.    Effectuer un essai nouveau avec uniquement le colonnes MEAN centrées et réduites (StandardScaler). Le model de l’algorithmes de StandardScaler doit être entrainé sur le jeu de données d’apprentissage uniquement.

4.    Effectuer un essai nouveau avec uniquement le colonnes SE centrées et réduites (StandardScaler). Le model de l’algorithmes de StandardScaler doit être entrainé sur le jeu de données d’apprentissage uniquement.

5.    Effectuer un essai nouveau avec uniquement le colonnes WORST centrées et réduites (StandardScaler) et appliquer une réduction de dimensions avec l’algorithme d’analyse en composante principale ACP(PCA en anglais). Les modelés de l’algorithmes de StandardScaler et ACP doivent être entrainé sur le jeu de données d’apprentissage uniquement.






## la même avec d'autre données 


1. lire le fichier => ok

2. gérer les valeurs nul => ok

3. faire l'execution d'initial (avant le TP) => ok 


4. One hot (valeur présente 0/1) encoder

Mettre 0 / 1 si la valeur est présente 

``` python
df_dummies = pd.get_dummies(donnees, columns=variableQualitatives, drop_first=True)
```

**=> Permet de donner le même poids à chaque valeurs (colonne) car chaque colonnes a le même nombre d'entré**



# Classification binaire 


- traitement initial 

 >double train test split (découper en trois partie)

 1 train test split => 1024

 partie gauche (train) train test split (0.20%)

 tt les colonne sont qualitatives => transformé en modalité (features) => get dummies sur x 


- traitement transformer en modalité 



# Champignons 

1.    Lisez le jeu de données des champignons.

>ok


2.    Découpez le jeu de données en trois parties :
        1. Validation 1024 individus 
        2. Test 1024 individus
        3. Apprentissage les autres individus du jeu.


>ok


3.    Exécutez l’ensemble des classificateurs du dictionnaire à l’aide de la fonction :
                    initDictionnaireClassificateurs(arbres=128) avec les données initiales.

>ok


4.    Transformez les modalités de colonnes qualitatives en colonnes. (Toutes les colonnes sont des variables qualitatives)

>ok


5.    Comparez les deux exécutions.


comparer l'execution de tout les modèle xtrain & xtest // avec un cas avec les dummies & l'autre sans les demies 



# Titre du cours 


## Echantillonage 

### Le sur apprentissage 

>Quand on choix nos algo, on le fait par rapport au meilleurs résultat obtenu en comparaison avec notre jeu de test. le problème c'est qu'on optimise nos algo pour notre jeu de test et cela peut crée un biais. On peut très bien optimiser / paramettre notre jeu de données pour nos données de test et se retrouver avec un modèle qui est très bon pour notre jeu de test bien que nul en général.  

### Stratification 


Il peut arriver qu'après le découpage des données une colonnes soit manquant dans un des quatre data sets. 


### Validation 


Notre jeu de test est peut être particulier, on ne peut pas le savoir à l'avance. C'est pourquoi on conserve un jeu de validation.

1 - on divise l'échantillon traitement en 5 (précédement divisé en validation & test)

2 - c'est la validation croisée, on fait des test sur ce nouveau jeu de données par batch (petit groupe de 1/5 du totale)

3 - Il faut calculer le taux de d'erreur de chaque l'ago puis vérifier s'il reste identique quand on va le tester sur les jeu de validation croisée  

4 - cela permet de s'assurer que la réussite de notre algo n'est pas basé sur la taille de notre jeu de test


### Matrice de confusion 


### La courge ROC (courbe)

Après avoir calculé la matrice de confusion, on peut calculer la courbe roc. 

La matrice de confusion est renséigner en 0/1 les algorythme donnes des prédictions en % d'acceptabilité. En faisant varier le seuil de pourcentage acceptabilité, on peut remplir une multitude de matrice de confusion. 

l'enssemble de ses matrice nous donne une suite de point qui nous permet de remplir notre courge roc. 


