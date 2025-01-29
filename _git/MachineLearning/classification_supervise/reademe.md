
# Explication du notebook BreastCancerWisconsin-Classification01

## Importation ds données 

Utiliser les dictionnaire pour transorlmer les valeur qualitative en valeur quantitative 


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





















