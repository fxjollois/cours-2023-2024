1- Trouver une source temps réel (API)
2- Créer un script téléchargeant les données de l'API toutes les minutes (ou heures selon la source)
    - Script bash
    - Dans un fichier `JSON` (ou `XML`)
    - Stocké dans un répertoire dédié, avec un nom de fichier explicite sur la date et l'horaire de téléchargement (format au choix)
    - Définir la tâche `chron` à associé pour la programmation automatique de ce script
3- Créer un script résumant les données stockées dans les fichiers toutes les heures (ou tous les jours selon la source)
    - Script Python ou R
    - Stockage du résultat dans Mongo
    - Suppression des fichiers résumés
    - Définir la tâche `chron` à associé pour la programmation automatique de ce script
4- Créer un script d'analyse des données tous les jours (ou semaines voire mois selon la source)
    - Script Python ou R
    - Génération d'un fichier PDF ou d'une appli web (shiny ou streamlit)
    - Définir la tâche `chron` à associé pour la programmation automatique de ce script


