# Application sur données réelles 

## Airbnb

Fichier de base à télécharger : [`seance7--airbnb.xlsx`](seance7--airbnb.xlsx)

Ce fichier comporte 2 feuilles :
- AirBnB-Paris
- AirBnB-Lyon

Pour les villes de Paris et de Lyon, nous avons un échantillon de logements AirBnB (500 pour chaque ville) proposés à la location, avec quelques informations sur ceux-ci. Nous nous posons en particulier ces questions auxquelles vous devez répondre :

### Comparaison entre Paris et Lyon
    
- Le prix des logements est-il le même entre les deux villes ?
    - A faire idéalement dans une nouvelle feuille
- La répartition de logements complets (“Entire home/appt”) est-elle identique ?
    - Vous pouvez créer une nouvelle colonne indiquant si c'est le logement complet ou non qui est disponible, pour simplifier le calcul

### Pour chaque ville séparemment

- Le prix d’un logement de type “Entire home/appt” est-il plus élevé que les autres logements ?
    - Vous pouvez ré-utiliser la colonne créée précédemment
    - La fonction `MOYENNE.SI()` permet de calculer une moyenne sur une colonne, pour les lignes qui respectent une condition particulière sur une autre colonne
- La proportion de logement ayant le Wifi est-elle la même entre les logements complets (“Entire home/appt”) et les autres logements ?
- Même question pour la télévision ?
