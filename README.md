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

## Prix aux bornes de recharge pour véhicules électriques

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
| last_modified          | horodatage de la derniere modification de prix   (format  ISO 8601 avec le T)  | 2023-02-26T08:53:12Z                        |
| consolidated_longitude | longitude de la station                                                  | 1.608554                                   |
| consolidated_latitude  | latitude de la station                                                   | 50.41349                                   |
| prix_kWh               | prix de la charge au kWh en €                                            | 0.22                                       |
| prix_session           | prix éventuel de démarrage de la session de charge. NA pour pas de prix. | NA                                         |

Descriptif des colonnes des données de `borne_de_recharge`

Attention : les prix ne sont pas inscrits  à des intervalles réguliers , seules les dates aux changements de prix sont enregistrées.

| Date | Prix |
|---- | ---- |
|2022-12-16 12:19:04|1.760
|2022-12-17 15:36:49|1.755
|2022-12-22 11:55:18|1.761
|2022-12-22 20:28:04|1.768

Dans l'exemple ci-dessus, pour le 16 et 17 décembre, nous n'avons qu'une seule mesure alors que le 22 décembre a connu deux changements de prix dans la même journée. 
Vous pouvez en déduire qu'au 16 décembre à 13:00:00, 14:00:00 jusqu'au lendemain, le prix est resté à 1.76€/l. 

## Prix des carburants pour les véhicules à combustion

Il s’agit du prix des carburants à la pompe et de leur évolution au
cours du temps.

Dans les archives vous trouverez deux fichiers: le premier contenant le détail des stations et le second, l'évolution des prix.

### Détail des stations
| Nom de colonne | Description                              | Exemple             |
|----------------|------------------------------------------|---------------------|
 | id             | identifiant unique de la station service | 100012              |
| latitude       | latitude de la station                   | 43.7323                |
| longitude      | longitude de la station                  | 7.4112               |
| cp             | code postal de la station                | 06320               |
| ville          | nom de la ville de la station            | Cap-D’ail           |

Descriptif des colonnes des données `essence` - partie détail

### Détail des prix

| Nom de colonne | Description                              | Exemple             |
|----------------|------------------------------------------|---------------------|
| carburant      | type de carburant                        | Gazole              |
| maj            | horodatage de la derniere modification de prix  (format  ISO 8601 sans le T) | 2023-02-17 00:01:00 |
| prix           | prix du carburant (€)                    | 1.93                |

Descriptif des colonnes des données `essence` - partie prix

Les plus gros des fichiers prix contiennent des prix à la demi-journée pour les années 2022 et 2023.
Même remarque pour les prix :seule la date de modification est enregistrée, à des intervalles pouvant être irréguliers.

Ces fichiers  étant volumineux (5 millions de lignes), une version aggrégée des prix est  aussi proposée par semaine ( plus d'un million de lignes) et par mois (500 000 lignes). Notez que dans ces deux versions aggrégées, les mesures sont répétées à des intervalles réguliers (par semaine ou par mois).


# Description des formats de fichiers

Pour chaque jeu de données, nous avons tenté de vous faciliter la tâche
en vous fournissant les fichiers sous plusieurs formats :

| Extension du fichier | Format                          | Outils de prédilection                                                       |
|----------------------|---------------------------------|------------------------------------------------------------------------------|
| csv.zip              | CSV, zippé, avec séparateur `,` | tous les outils dont les languages de programmation R, python, javascript, … |
| xlsx                 | Office Open XML pour tableurs   | Libre Office, Open Office, Microsoft Excel, …                                |


# Télécharger les données

## Prix aux bornes de recharge pour véhicules électriques 
    
-  [borne_de_recharge.xlsx](https://github.com/ToulouseDataViz/Hackaviz-2023/blob/main/data/borne_de_recharge.xlsx)      
-  [borne_de_recharge.csv.zip](https://github.com/ToulouseDataViz/Hackaviz-2023/blob/main/data/borne_de_recharge.csv.zip) 

## Le prix des carburants pour les véhicules à combustion

- [essence_2022.zip - prix à la demi-journée  et détail des stations pour l'année 2022 ](https://github.com/ToulouseDataViz/Hackaviz-2023/blob/main/data/essence_2022.zip) 
- [essence_2023-3-8.zip  - prix à la demi-journée  et détail des stations  pour l'année 2023 (jusqu'au 8 mars) ](https://github.com/ToulouseDataViz/Hackaviz-2023/blob/main/data/essence_2023-3-8.zip) 
- [essence_hebdomadaire.xlsx - prix agrégés à la semaine pour les années 2022 et 2023](https://github.com/ToulouseDataViz/Hackaviz-2023/blob/main/data/essence_hebdomadaire.xlsx) 
- [essence_mensuel.xlsx - prix agrégés au mois pour les années 2022 et 2023](https://github.com/ToulouseDataViz/Hackaviz-2023/blob/main/data/essence_mensuel.xlsx) 
