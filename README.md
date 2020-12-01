# Les données de trafic des stations de comptage de la DIRIF
La DIRIF a exploité jusqu'à 2600 stations de comptage dans le cadre du projet SIRIUS Elle exploite aussi environ 200 stations SIREDO. Depuis que la DIRIF utilise des données FCD pour connaitre l'état du trafic en temps réel, le nombre de stations a été réduit à environ 800. Les stations conservées sont dénommées "PARAD". Parmi ces stations, environ la moitié sont opérationnelles à un moment donné. La réparation des stations et des réseaux par lesquels les données transitent requièrent souvent la fermeture des voies à la circulation, pendant une ou plusieurs nuits. Cela explique les délais parfois long pour la remise en état d'une station.

Les premières données traitées sont les données de l'année 2019. On peut trouver les données d'environ 300 stations dans la table publique BigQuery

\`dir-idf.trafic.debit2019\`

Le lecteur est invité à rechercher dans la documentation de Google la méthode, pour l'extraction de données d'une base BigQuery.

Les données sont incomplètes mais pour plus de 200 stations, plus de 200 jours sont disponibles ce qui est suffisant pour faire fonctionner un algorithme de "reconstitution des données". Le schéma de la table est le suivant :

Stat STRING NULLABLE : Code la station tel qu'il apparait dans le SI de la DIRIF.

cd STRING NULLABLE : Code simplifié de la station la station

dt DATE NULLABLE : Date de la donnée

P6mn NUMERIC NULLABLE : numéro de période de 6mn, dans la journée (ex : 63 pour 6:12-6:18)

Db NUMERIC NULLABLE : valeur du débit 6mn à la station considérée

## Table des stations de mesures
Pour connaitre l'ensemble des points de mesures de la DIRIF, on pourra se référer à la table publique BigQuery :

<\`dir-idf.trafic.PointsMesure\`>

Le schéma de la table est le suivant :

Sta	STRING	NULLABLE	: Code la station tel qu'il apparait dans le SI de la DIRIF.

ID_SEGMENT	INTEGER	NULLABLE	: code de segment SIRIUS

Pour localiser les stations, à partir des PR, on pourra se référer aux informations publiées ici :

<https://www.data.gouv.fr/fr/datasets/gestionnaires-du-reseau-routier-national/>


ID_TYPE_CAPTEUR	INTEGER	NULLABLE	

TATOUAGE	STRING	NULLABLE	: code d'identification pour la maintenance DIRIF

PR_EQUIP	INTEGER	NULLABLE	: Point de repère

LONGUEUR	INTEGER	NULLABLE	: longueur de la section de référence (surtout utile pour les mesures FCD)

ax	STRING	NULLABLE	: axe routier

ln	INTEGER	NULLABLE	

cd	STRING	NULLABLE	: Code simplifié de la station la station
