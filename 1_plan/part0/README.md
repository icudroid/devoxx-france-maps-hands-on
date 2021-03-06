## Récupération de la donnée et préparation des images Docker
La création des fichiers MBTiles (tuiles composant une carte) est gourmande en puissance de calcul et nécessite une machine puissante.
Nous allons donc partir des images mises à disposition par OpenMapTiles.org.

### Récupération de la data
Placez-vous dans le répertoire de données et choisissez de prendre le fichier __mbtiles__ de DEVOXX_SUPPORT ou du site OpenMapTiles.
```shell
$ cd ~/maps-hands-on/1_plan/data
```
Copier/coller le fichier mbtiles de DEVOXX_SUPPORT (solution 1)
```shell
cp ~/DEVOXX_SUPPORT/plan/data/2017-07-03_france_ile-de-france.mbtiles .
```
Télécharger le fichier __mbtiles__ depuis le site __openmaptiles__ (solution 2)
```shell
- se rendre sur https://openmaptiles.com/downloads/tileset/osm/europe/france/ile-de-france/
- cliquer sur "open-source or open-data project website"
- cliquer sur _Free download_ et se créer un compte
- copiez et exécutez la commande `wget` sous le bouton Free download

La sortie devrait être comme suit...
...
2017-07-03_france_ile-de-france.mbtile 100%[============================================================================>] 167.45M  16.2MB/s    in 11s     
2018-04-06 19:13:47 (15.8 MB/s) - ‘2017-07-03_france_ile-de-france.mbtiles’ saved [175587328/175587328]
```

### Lancement du serveur
Lancer l'image Docker
```shell
$ cd ~/maps-hands-on/1_plan/part0

$ docker-compose up
...
tiles_1  | No MBTiles specified, using 2017-07-03_france_ile-de-france.mbtiles
tiles_1  | Automatically creating config file for 2017-07-03_france_ile-de-france.mbtiles
...
```

### Tester le site
Ouvrez votre navigateur sur http://127.0.0.1:8080/ (attention, ne _pas_ utiliser localhost).

Vous devriez pouvoir vous déplacer sur la carte, zoomer, etc...