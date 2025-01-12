VM Big data : razvan Bizoi -> mdp : CoursSPARK#

### Download VMware 

https://softwareupdate.vmware.com/cds/vmw-desktop/ws/

### Initialiser le cluster de la VM 

*- est une réduction pour --login*

``` bat
sudo su -
ls
. start-stop-cluster/01-start-cluster.sh
```

<a href="https://zookeeper.apache.org/" >Zookeeper </a> && <a href="https://kafka.apache.org/"> Kafka </a>


**Hive**  => est un intermédier bach > match reduce. 

**Hadoop** => stockage HDFS & gestionnaires de ressource 

**Kafka** => gestionnaire de flux de données 

**Pandas || Koalas** => Panda ne supporte pas les DF de plus de 2Go alors que Koalas s'appuie sur la techno de spark pour offrir les même fonctionnalités que Pandas. 

#### Télécharger les données 

o)=> Recupérer la commande sur <a href="https://github.com/rbizoi/PythonFormation/tree/main/SparkMachine"> Github </a>

``` bat
sudo su - spark
ll
wget https://github.com/rbizoi/PythonFormation/blob/main/Spark-DataFrames/charge_meteo_2024.sh
```


#### Init spark Server


``` bat
export PYSPARK_DRIVER_PYTHON=jupyter
export PYSPARK_DRIVER_PYTHON_OPTS='notebook'
pyspark --master spark://jupiter.olimp.fr:7077 --executor-cores 4 --executor-memory 8g
```

### Start spark server 


```bat 
pyspark --master spark://jupiter.olimp.fr:7077 --executor-cores 4 --executor-memory 8g
```

### accéder au répertoire donnes depuis : *user spark*

```bat 
ll /home/spark | grep 'donnees'
```

#### Récuperer & Executer des nodeBook

```bat 
cd /home/spark/cours/notebook 

sudo wget https://github.com/rbizoi/PythonFormation/blob/main/SparkMachine/01-API.DataFrames-colonnes-projections.ipynb
```


### Lancer les noteBooks 

1/ Se connecter au lien <a href="jupiter.olimp.fr:8888"> jupiter.olimp.fr:8888 </a> 

2/ Executer toutes les cellules



