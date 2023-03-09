Hackaviz 2023 : Le prix de l’énergie pour les véhicules particuliers
================

![](images/image-408964965.png)

Nous vous proposons cette année un jeu de données double, issu d’une
part du [fichier consolidé des bornes de recharge pour véhicules
électriques](https://www.data.gouv.fr/fr/datasets/fichier-consolide-des-bornes-de-recharge-pour-vehicules-electriques/),
et du site gouvernemental du [prix des
carburants](https://www.prix-carburants.gouv.fr/) d’autre part.

Chaque jeu de donnée contient plusieurs fichiers pour couvrir différents
formats compatibles avec differents outils. Il est possible de faire de
belles visualisations à partir d’un seul de ces fichiers. Vous pouvez
aussi les combiner, mais il n’est pas certain que la plus belle histoire
ait besoin de toutes ces données.

Retrouvez les règles et les modes d’évaluation sur la page des [règles
de l’Hackaviz](https://toulouse-dataviz.fr/hackaviz/reglement/) de
l’association [Toulouse DataViz (TDV)](http://toulouse-dataviz.fr).

N’hésitez pas à nous contacter sur le
[discord](https://discord.gg/xRUkJRx5Q4) de Toulouse DataViz
pour discuter entre participants, si vous avez besoin d’aide à propos
des données ou pour rapporter des erreurs dans le jeu de données.

Bonne chance !

# Description générale des données

## Bornes de recharge pour véhicules électriques

Le jeu de données \`borne_de_recharge\` relève les prix de la recharge
aux bornes des véhicules électriques :

| Nom de colonne         | Description                                                              | Exemple                                    |
|------------------------|--------------------------------------------------------------------------|--------------------------------------------|
| nom_operateur          | operateur de la station                                                  | Freshmile SAS                              |
| nom_enseigne           | Enseigne (nom commercial)                                                | Freshmile                                  |
| nom_station            |                                                                          | Rang-Du-Fliers-Berck, Route de Berck -3659 |
| implantation_station   |                                                                          | Voirie                                     |
| adresse_station        |                                                                          | Route de Berck 62180 RANG DU FLIERS        |
| code_insee_commune     |                                                                          | 56252                                      |
| nbre_pdc               | nombre de points de comptages à cette station                            | 2                                          |
| puissance_nominale     | puissance instantanée disponible (kW)                                    | 22                                         |
| prise_type_ef           | type de prise de charge disponible                                       | FALSE                                      |
| prise_type_2           | idem                                       | FALSE                                      |
| prise_type_combo_ccs   | idem                                                                     | TRUE                                       |
| prise_type_chademo     | idem                                                                     | TRUE                                       |
| prise_type_autre       | idem                                                                     | FALSE                                      |
| gratuit                | type de paiement                                                         | FALSE                                      |
| paiement_acte          | idem                                                                     | TRUE                                       |
| paiement_cb            | idem                                                                     | FALSE                                      |
| paiement_autre         | idem                                                                     | TRUE                                       |
| horaires               |                                                                          | 24/7                                       |
| accessibilite_pmr      | accessibilité aux personnes à mobilité réduite                           | Accessibilité inconnue                     |
| date_mise_en_service   | date au format ISO 8601 (année-mois-jour)                                | 2022-06-27                                 |
| date_maj               | date de mise à jour                                                      | 2023-01-31                                 |
| last_modified          | horodatage de la derniere modification de prix                           | 2023-02-26 08:53:12                        |
| consolidated_longitude | longitude de la station                                                  | 1.608554                                   |
| consolidated_latitude  | latitude de la station                                                   | 50.41349                                   |
| prix_kWh               | prix de la charge au kWh en €                                            | 0.22                                       |
| prix_session           | prix éventuel de démarrage de la session de charge. NA pour pas de prix. | NA                                         |

Descriptif des colonnes des données de `borne_de_recharge`

## `essence`: Le prix des carburants

Il s’agit du prix des carburants à la pompe et de leur évolution au
cours du temps.

| Nom de colonne | Description                              | Exemple             |
|----------------|------------------------------------------|---------------------|
| carburant      | type de carburant                        | Gazole              |
| id             | identifiant unique de la station service | 100012              |
| latitude       | latitude de la station                   | 43.7323                |
| longitude      | longitude de la station                  | 7.4112               |
| cp             | code postal de la station                | 06320               |
| ville          | nom de la ville de la station            | Cap-D’ail           |
| maj            | date et heure de mise à jour du prix     | 2023-02-17 00:01:00 |
| prix           | prix du carburant (€)                    | 1.93                |

Descriptif des colonnes des données `essence`

# Description des formats de fichiers

Pour chaque jeu de données, nous avons tenté de vous faciliter la tâche
en vous fournissant les fichiers sous plusieurs formats :

| Extension du fichier | Format                          | Outils de prédilection                                                       |
|----------------------|---------------------------------|------------------------------------------------------------------------------|
| csv.zip              | CSV, zippé, avec séparateur `,` | tous les outils dont les languages de programmation R, python, javascript, … |
| xlsx                 | Office Open XML pour tableurs   | Libre Office, Open Office, Microsoft Excel, …                                |

Les fichiers de données étant volumineux, une version aggrégée du jeu de
donnée `essence` est aussi proposée par semaine et par mois.

# Télécharger les données

| Ensemble.zip | [essence_2023.zip](https://github.com/ToulouseDataViz/Hackaviz-2023/blob/main/data/essence_2023.zip) | [borne_de_recharge.csv.zip](https://github.com/ToulouseDataViz/Hackaviz-2023/blob/main/data/borne_de_recharge.csv.zip) |
|--------------|------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------|
|              | [essence_2022.zip](https://github.com/ToulouseDataViz/Hackaviz-2023/blob/main/data/essence_2022.zip) |                                                                                                                       |
|              | essence.xlsx                                                                                         | [borne_de_recharge.xlsx](https://github.com/ToulouseDataViz/Hackaviz-2023/blob/main/data/borne_de_recharge.xlsx)       |
|              | essence_resumé_hebdomadaire.xlsx                                                                     |                                                                                                                       |
