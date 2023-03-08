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

## Pompes à essences

Les données de pompes à essences se situent dans les fichiers essence_2022.zip (contenant toutes les données liées à l'année 2022) et essence_2023-3-3.zip (contenant les données extraites le 3 mars 2023).
Ces deux archives contiennent les fichiers suivants :
- `essence/details_stations.csv` concernant les détails de chaque pompe.
- `essence/fermetures_stations.csv` sur les détails de chaque fermeture.
- `essence/prix_stations.csv` sur l'évolution des prix pratiqués pour chaque station.
- `essence/ruptures_stations.csv`sur les ruptures pour chaque pompe.

Le lien entre ces différents fichiers peut se faire grâce à l'identifiant de la pompe se trouvant dans la colonne `id_pompe` de chaque fichier.

Voici une description détaillée du contenu de chacun de ces fichiers.

## Contenu de `details_stations`
Ce fichier contient les informations suivantes liées aux stations :


|        Nom de colonne |                                                        Description |             Exemple |
|-----------------------|--------------------------------------------------------------------|---------------------|
|              id_pompe |                                           Identifiant de la pompe. |             1000001 |
| latitude et longitude |                                        Coordonnés GPS de la pompe. |                     |
|                    cp |                    Code postal de l'endroit où se trouve la pompe. |               31000 |
|             autoroute |        Booléen égal à True lorsque la pompe est sur une autoroute. |               False |
|               adresse |                                Numéro et voie / chemin / avenue... | 16 Avenue de Marboz |
|                 ville |                                                    Nom de la ville |            Toulouse |
|        automate-24-24 | Booléen égal à True lorsque la station possède un automate 24h/24. |                True |

## Contenu de `fermetures_stations`
Fichier contenant les fermetures pratiquées

| Nom de colonne |                                                   Description |             Exemple |
|----------------|---------------------------------------------------------------|---------------------|
|       id_pompe |                                      Identifiant de la pompe. |             1000001 |
|           type | Type de fermeture. 'T' pour temporaire et 'D' pour définitive |                   T |
|          debut |                                    Date de début de fermeture | 2022-10-15T00:00:00 |
|            fin |            Date de fin de fermeture si le type est temporaire | 2022-10-15T00:20:00 |

## Contenu de `prix_stations`
Ce fichier contient l'évolution des prix pratiqués pour chaque station, les colonnes sont sous le format suivant :

| Nom de colonne |                      Description |             Exemple |
|----------------|----------------------------------|---------------------|
|       id_pompe |         Identifiant de la pompe. |             1000001 |
|  nom_carburant |       Nom du carburant concerné. |              Gazole |
|       date_maj | Date de la dernière mise à jour. | 2022-01-03 08:44:18 |
|           prix |                   Prix en euros. |               1.572 |

## Contenu de `ruptures_stations`
Ce fichier contient les ruptures de carburant reportées pour chaque station.

| Nom de colonne |                               Description |             Exemple |
|----------------|-------------------------------------------|---------------------|
|       id_pompe |                  Identifiant de la pompe. |             1000001 |
|  nom_carburant | Nom du carburant concerné par la rupture. |                SP98 |
|          debut |               Date de début de la rupture | 2022-10-21T07:51:17 |
|            fin |                 Date de fin de la rupture | 2022-10-21T07:52:49 |
