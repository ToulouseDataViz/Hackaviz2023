Hackaviz 2023 : Le prix de l’énergie pour les véhicules particuliers
================

![](images/image-408964965.png)

Nous vous proposons cette année un jeu de données double, issu d’une
part du [Fichier consolidé des Bornes de Recharge pour Véhicules
Électriques](https://www.data.gouv.fr/fr/datasets/fichier-consolide-des-bornes-de-recharge-pour-vehicules-electriques/),
et du site gouvernemental [Le Prix des
Carburants](https://www.prix-carburants.gouv.fr/) d’autre part.

Chaque jeu de donnée contient plusieurs fichiers pour couvrir différents
formats compatibles avec differents outils. Il est possible de faire de
belles visualisations à partir d’un seul de ces fichiers. Vous pouvez
aussi les combiner, mais il n’est pas certain que la plus belle histoire
ait besoin de toutes ces données.

Retrouvez les règles et les modes d’évaluation sur la page des [règles
de l’Hackaviz](https://toulouse-dataviz.fr/hackaviz/reglement/) de
l’association [Toulouse DataViz (TDV)](http://toulouse-dataviz.fr).

N’hésitez pas à nous contacter sur le
[discord](https://discord.gg/Dh8yw3Cc "Le Salon du Hackaviz 2023") du
Toulouse DataViz pour discuter entre participants, si vous avez besoin
d’aide à propos des données ou pour rapporter des erreurs dans le jeu de
données.

Bonne chance !

# Description générale des données

## Prix aux bornes de recharge pour véhicules électriques

Le jeu de données \`borne_de_recharge\` releve les prix de la recharge
aux bornes des véhicules électriques :

| Nom de colonne         | Description                                                                                                | Exemple                                    |
|------------------------|------------------------------------------------------------------------------------------------------------|--------------------------------------------|
| nom_operateur          | operateur de la station                                                                                    | Freshmile SAS                              |
| nom_enseigne           | Enseigne (nom commercial)                                                                                  | Freshmile                                  |
| nom_station            |                                                                                                            | Rang-Du-Fliers-Berck, Route de Berck -3659 |
| implantation_station   |                                                                                                            | Voirie                                     |
| adresse_station        |                                                                                                            | Route de Berck 62180 RANG DU FLIERS        |
| code_insee_commune     |                                                                                                            | 56252                                      |
| nbre_pdc               | nombre de points de comptages à cette station                                                              | 2                                          |
| puissance_nominale     | puissance instantanée disponible (kW)                                                                      | 22                                         |
| prise_type_2           | type de prise de charge disponible                                                                         | FALSE                                      |
| prise_type_combo_ccs   | idem                                                                                                       | TRUE                                       |
| prise_type_chademo     | idem                                                                                                       | TRUE                                       |
| prise_type_autre       | idem                                                                                                       | FALSE                                      |
| gratuit                | type de paiement                                                                                           | FALSE                                      |
| paiement_acte          | idem                                                                                                       | TRUE                                       |
| paiement_cb            | idem                                                                                                       | FALSE                                      |
| paiement_autre         | idem                                                                                                       | TRUE                                       |
| horaires               |                                                                                                            | 24/7                                       |
| accessibilite_pmr      | accessibilité aux personnes à mobilité réduite                                                             | Accessibilité inconnue                     |
| date_mise_en_service   | date au format ISO 8601 (année-mois-jour)                                                                  | 2022-06-27                                 |
| date_maj               | date de mise à jour                                                                                        | 2023-01-31                                 |
| last_modified          | horodatage de la dernière modification de prix (format [ISO 8601](https://fr.wikipedia.org/wiki/ISO_8601)) | 2023-02-26T08:53:12Z                       |
| consolidated_longitude | longitude de la station                                                                                    | 1.608554                                   |
| consolidated_latitude  | latitude de la station                                                                                     | 50.41349                                   |
| prix_kWh               | prix de la charge au kWh en €                                                                              | 0.22                                       |
| prix_session           | prix éventuel de démarrage de la session de charge. NA pour pas de prix.                                   | NA                                         |

Descriptif des colonnes des données de `borne_de_recharge`

## `essence`: Le prix des carburants pour les véhicules à combustion

Il s’agit du prix des carburants à la pompe et de leur évolution au
cours du temps.

Dans chaque archive, vous trouverez plusieurs fichiers:

- le détail des stations dans `details_stations`

- `prix_stations.csv` pour l’évolution des prix.

- les ruptures d’approvisionnement des stations services :
  `ruptures_stations.csv`

- les fermetures des stations

Ces tables peuvent être reliées à l’aide d’une jointure sur
l’identifiant unique de la station service (eg. 100012).

### Détail des stations

| Nom de colonne | Description                              | Exemple   |
|----------------|------------------------------------------|-----------|
| id             | identifiant unique de la station service | 100012    |
| latitude       | latitude de la station                   | 43.7323   |
| longitude      | longitude de la station                  | 7.4112    |
| cp             | code postal de la station                | 06320     |
| ville          | nom de la ville de la station            | Cap-D’ail |

Descriptif des colonnes des données `detail_stations.csv` dans
`essence.zip`

### Détail des prix

| Nom de colonne | Description                                                      | Exemple              |
|----------------|------------------------------------------------------------------|----------------------|
| id             | identifiant unique de la station service                         | 100012               |
| carburant      | type de carburant                                                | Gazole               |
| maj            | horodatage de la dernière modification de prix (format ISO 8601) | 2023-02-17T00:01:00Z |
| prix           | prix du carburant (€)                                            | 1.93                 |

Descriptif des colonnes des données `prix_stations.csv` dans
`essence.zip`

Attention : les prix ne sont pas inscrits à des intervalles réguliers,
seules les dates aux changements de prix sont enregistrées.

| Date                | Prix  |
|---------------------|-------|
| 2022-12-16 12:19:04 | 1.760 |
| 2022-12-17 15:36:49 | 1.755 |
| 2022-12-22 11:55:18 | 1.761 |
| 2022-12-22 20:28:04 | 1.768 |

Dans l’extrait ci-dessus par exemple, pour le 16 et 17 décembre, nous
n’avons qu’une seule mesure alors que le 22 décembre a connu deux
changements de prix dans la même journée. Vous pouvez en déduire qu’au
16 décembre à 13:00:00, 14:00:00 jusqu’au lendemain, le prix est resté à
1.76€/l.

Ces fichiers étant volumineux (5 millions de lignes), une version
agrégée des prix est aussi proposée par semaine ( plus d’un million de
lignes) et par mois (500 000 lignes).

Notez que dans ces deux versions agrégées, les mesures sont

- répétées à des intervalles réguliers (par semaine ou par mois),

- remplies avec les valeurs de l’intervalle precédent s’il n’y a eu
  aucun changement (valeur manquante)

### Détail des ruptures d’approvisionnement en car

| Nom de colonne | Description                              | Exemple              |
|----------------|------------------------------------------|----------------------|
| id_pompe       | identifiant unique de la station service | 100012               |
| nom_carburant  | type de carburant                        | SP95                 |
| debut          | début de la fermeture                    | 2023-02-17T00:01:00Z |
| fin            | fin de la fermeture                      | 2023-02-19T13:07:00Z |

Descriptif des colonnes des données `fermetures_stations.csv` dans
`essence.zip`

### Détail des fermetures de station-service

<table style="width:99%;">
<caption>Descriptif des colonnes des données
<code>fermetures_stations.csv</code> dans
<code>essence.zip</code></caption>
<colgroup>
<col style="width: 20%" />
<col style="width: 51%" />
<col style="width: 27%" />
</colgroup>
<thead>
<tr class="header">
<th>Nom de colonne</th>
<th>Description</th>
<th>Exemple</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>id_pompe</td>
<td>identifiant unique de la station service</td>
<td>100012</td>
</tr>
<tr class="even">
<td>type</td>
<td><p>type de la fermeture :</p>
<ul>
<li><p>T: Temporaires</p></li>
<li><p>D: Définitives</p></li>
</ul></td>
<td>T</td>
</tr>
<tr class="odd">
<td>debut</td>
<td>début de la fermeture</td>
<td>2023-02-17T00:01:00Z</td>
</tr>
<tr class="even">
<td>fin</td>
<td>fin de la fermeture</td>
<td>2023-02-19T13:07:00Z</td>
</tr>
</tbody>
</table>

Descriptif des colonnes des données `fermetures_stations.csv` dans
`essence.zip`

# Description des formats de fichiers

Pour chaque jeu de données, nous avons tenté de vous faciliter la tâche
en vous fournissant les fichiers sous plusieurs formats :

| Extension du fichier | Format                          | Outils de prédilection                                                       |
|----------------------|---------------------------------|------------------------------------------------------------------------------|
| csv.zip              | CSV, zippé, avec séparateur `,` | tous les outils dont les languages de programmation R, python, javascript, … |
| xlsx                 | Office Open XML pour tableurs   | Libre Office, Open Office, Microsoft Excel, …                                |

Les fichiers de données étant volumineux, deux versions agrégées du jeu
de donnée `essence` sont aussi proposée :

# Télécharger les données

## Ensemble des données

L’ensemble des fichiers est accessible ici : [Page de
téléchargement](https://github.com/ToulouseDataViz/Hackaviz2023/releases/tag/v3)

## Prix aux bornes de recharge pour véhicules électriques

- [borne_de_recharge.xlsx](https://github.com/ToulouseDataViz/Hackaviz2023/releases/download/v3/borne_de_recharge.xlsx)  
- [borne_de_recharge.csv.zip](https://github.com/ToulouseDataViz/Hackaviz2023/releases/download/v3/borne_de_recharge.csv)

## Le prix des carburants pour les véhicules à combustion

- [essence_2022.zip - prix à la demi-journée et détail des stations pour
  l’année
  2022](https://github.com/ToulouseDataViz/Hackaviz2023/releases/download/v3/essence_2022.zip)

- [essence_2023-3-8.zip - prix à la demi-journée et détail des stations
  pour l’année 2023 (jusqu’au 8
  mars)](https://github.com/ToulouseDataViz/Hackaviz2023/releases/download/v3/essence_2023-3-8.zip)

- [essence.xlsx - l’ensemble au format
  xlsx](https://github.com/ToulouseDataViz/Hackaviz2023/releases/download/v3/essence.xlsx)

- [essence_hebdomadaire.xlsx - prix agrégés à la semaine pour les années
  2022 et
  2023](https://github.com/ToulouseDataViz/Hackaviz2023/releases/download/v3/essence_hebdomadaire.xlsx)

- [essence_mensuel.xlsx - prix agrégés au mois pour les années 2022 et
  2023](https://github.com/ToulouseDataViz/Hackaviz2023/releases/download/v3/essence_mensuel.xlsx)

- [essence_hebdomadaire.csv.zip](https://github.com/ToulouseDataViz/Hackaviz2023/releases/download/v3/essence_hebdomadaire.csv.zip)
  et
  [essence_mensuel.csv.zip](https://github.com/ToulouseDataViz/Hackaviz2023/releases/download/v3/essence_mensuel.csv.zip)

## Les départements français

[departements_france.csv](https://github.com/ToulouseDataViz/Hackaviz2023/releases/download/v3/departements-france.csv)

# Une erreur dans les données ?

Malgré toute l’attention portée à la préparation des données, une erreur
est si vite arrivée…

Pour une faute d’orthographe, une explication peu claire sur les
données, ou une grave erreur de format ou de contenu dans données,
n’hésitez pas à nous faire part de vos doutes ou simples questions sur
le [forum de discussion discord
dédié](https://discord.gg/Dh8yw3Cc "Le salon discord hackaviz 2023"), ou
bien à directement lever [un problème dans le dépot de code
github](https://github.com/ToulouseDataViz/Hackaviz2023/issues "nouveau bug github").
