Préparation de la configuration Docker
-------
1. Créer le répertoire contenant les conteneurs
```
mkdir -p ~/devoxx/search/docker
```
2. Copier/coller l'archive devoxx_search_docker_images.tar dans le répertoir docker
```
cp devoxx_search_docker_images.tar ~/devoxx/search/docker
```
3. Restaurer les images docker
```
docker load --input devoxx_search_docker_images.tar
```

Préparation de la donnée
-------

1. Créer le répertoire contenant la donnée __Paris__
```
mkdir -p ~/devoxx/search/data
```
2. Faire pointer la variable d'environnement dans le fichier __.env__
```
DATA_DIR=~/devoxx/search/data
```
3. Allumer le conteneur __Elasticsearch__
```
docker-compose up -d elasticsearch
```
4. Création du schéma __Elasticsearch__
```
docker-compose run --rm schema npm run create_index
```
5. Allumer le conteneur __API__
```
docker-compose up -d api
```
6. Tester la présence de Pelias
```
curl http://localhost:4000/v1/search?text=paris
```
7. Copier/coller la fichier __paris.osm.pbf__ OSM Paris dans le répertoire d'Elasticsearch
```
cp DEVOXX_SUPPORT/paris.osm.pbf ~/devoxx/search/data/openstreetmap/
```
8. Importer la donnée de OSM Paris dans Elasticsearch
```
docker-compose run --rm openstreetmap npm start
```
9. Tester la présence de données OSM Paris
```
curl http://localhost:4000/v1/search?text=rue%20de%20la%20pompe
```