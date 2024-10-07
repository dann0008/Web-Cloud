# Projet Données Massives & Cloud
## Lucas Danneaux - URL du Projet : https://sound-catalyst-437209-c1.appspot.com/

## Commande manipulés lors de la mise en place de la Machine distante

#### Commande exécuté dans le cloud shell
- `mvn -v`
- `gcloud init`
- `git clone https://github.com/momo54/webandcloud.git`
`cd webandcloud`
`mvn install` -> "" Build Success ""

#### Modification de fichier dans l'éditeur cloud shell
- [pom.xml](webandcloud/pom.xml) : Remplacement de sobike44 par sound-catalyst-437209-c1
- [src/main/webapp/WEB-INF/appengine-web.xml](webandcloud/src/main/webapp/WEB-INF/appengine-web.xml) : Remplacement de sobike44 par sound-catalyst-437209-c1

#### Commande dans le cloud shell
- `gcloud app create`
- `6 - Europe west 6`
- `mvn package appengine:deploy`

La machine distante est désormais accessible à l'adresse suivante : [https://sound-catalyst-437209-c1.appspot.com/](https://sound-catalyst-437209-c1.appspot.com/)

## Commande pour la manipulation du Cloud 
- `mvn package` -> Compilation du Java
- `mvn appengine:run` -> Déploiement dans l'environnement de developpement  
- `mvn appengine:deploy` -> Deploiement sur l'adresse principale

## Mise en oeuvre du TP My Score

- Fichier [ScoreEndpoint.java](webandcloud/src/main/java/foo/ScoreEndpoint.java) : Ajout d'une méthode myscore permettant de faire un appel sur l'API et de récupérer les 10 meilleurs scores
de la personne qui joue.
- Fichier [index3.html](webandcloud/src/main/webapp/index3.html) : Ajout du code Mithril permettant de faire l'appel et 'affichage des scores récupérés avec l'appel de l'API configuré ci-dessus.
- Fichier [index3.html](webandcloud/src/main/webapp/index3.html) : Ajout dans la fonction play d'un nouvel appel à l'API si le nom du joueur est changer avant le début de partie.

#### Test du fonctionnement du code dans l'environnement de test
- `mvn package`
- `mvn appengine:run`

#### Mise en place de l'indexation de l'API Score pour la récupération des scores filtrés sur le nom à l'aide du fichier [index.yaml](webandcloud/src/main/webapp/WEB-INF/index.yaml)
- `cd src/main/webapp/WEB-INF`
- `gcloud datastore indexes cleanup index.yaml`
- `gcloud datastore indexes create index.yaml`
- `cd ~/webandcloud`
- `mvn appengine:deploy`

Le jeu est désormais accessible avec l'ajout des fonctionnalités de myscore à l'adresse suivante : [https://sound-catalyst-437209-c1.oa.r.appspot.com/index3.html](https://sound-catalyst-437209-c1.oa.r.appspot.com/index3.html)

## Source
- https://sound-catalyst-437209-c1.appspot.com/
- https://console.cloud.google.com/welcome?hl=fr&project=sound-catalyst-437209-c1
- https://shell.cloud.google.com/?show=ide%2Cterminal


## Ressources utilisés 
- https://cloud.google.com/appengine/docs/standard/java-gen2/using-maven?hl=fr
- https://github.com/momo54/webandcloud.git
- https://cloud.google.com/appengine/docs/legacy/standard/java/datastore/indexes?hl=fr#index-definition-structure
