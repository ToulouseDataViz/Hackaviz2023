Hackaviz 2023 : Le prix de l’énergie pour les véhicules particuliers
================

![](images/image-408964965.png)

Nous vous proposons cette année un jeu de données double, issue d’une
part du [Fichier consolidé des Bornes de Recharge pour Véhicules
Électriques](https://www.data.gouv.fr/fr/datasets/fichier-consolide-des-bornes-de-recharge-pour-vehicules-electriques/),
et du site gouvernemental [Le Prix des
Carburants](https://www.prix-carburants.gouv.fr/) d’autre part.

Le jeu de données est réparti sur deux fichiers. Il est possible de
faire de belles visualisations à partir d’un seul de ces fichiers. Vous
pouvez aussi les combiner, mais il n’est pas certain que la plus belle
histoire ait besoin de toutes ces données.

Retrouvez les règles et les modes d’évaluation sur la page des [règles
de l’Hackaviz](https://toulouse-dataviz.fr/hackaviz/reglement/) de
l’association [Toulouse DataViz (TDV)](http://toulouse-dataviz.fr).

N’hésitez pas à nous contacter sur le
[discord](https://discord.com/invite/RbTR4jKRp9) du Toulouse DataViz
pour discuter entre participants, si vous avez besoin d’aide à propos
des données ou pour rapporter des erreurs dans le jeu de données.

Bonne chance !

# Description générale des données

## Bornes de recharge pour véhicules électriques

Il s’agit du prix de la recharge aux bornes des véhicules électriques :

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
| prise_type_2           | type de prise de charge disponible                                       | FALSE                                      |
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

## Prix des Carburants

Il s’agit du prix des carburants à la pompe et de leur évolution

| Nom de colonne | Description                              | Exemple             |
|----------------|------------------------------------------|---------------------|
| carburant      | type de carburant                        | Gazole              |
| id             | identifiant unique de la station service | 100012              |
| latitude       | latitude de la station                   | 43.7                |
| longitude      | longitude de la station                  | 7.41                |
| cp             | code postal de la station                | 06320               |
| ville          | nom de la ville de la station            | Cap-D’ail           |
| maj            | date et heure de mise à jour du prix     | 2023-02-17 00:01:00 |
| prix           | prix du carburant (€)                    | 1.93                |

Descriptif des colonnes des données de `carburants`
