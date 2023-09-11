# Introduction au Machine Learning en Python

## Mastère ESD - INSA Rouen

<!--
https://www.insa-rouen.fr/formation/mastere-specialiser/expert-en-sciences-des-donnees
-> Ingénierie des données
Contenu
1) Introduction à l’ingénierie des données : notion de chaine de traitements
2) Analyse exploratoire de données
    - Analyse en Composantes Principales (ACP)
    - Analyse factorielle des correspondances (AFC)
    - Méthode non-linéaire de projection des données
3) Méthodes de regroupement des données (Clustering)
    - Classification hiérarchique ascendante
    - K moyennes
    - Modèles de mélange
Ces méthodes couvriront les problématiques de description statistique des données, de projection et visualisation des données et de regroupement des données en catégories homogènes.

    - Jour 1 : Intro (ML, Apprentissage non-supervisé, étude de cas...) - ACP
    - Jour 2 : Classif (k-means, CAH) - Autres méthodes de classif (SOM ?, DBSCAN, BIRCH ? autre ?) + **Evaluation des résultats**
    - Jour 3 : Autres méthodes (MDS, NMF, ?) - TP noté ?
-->

- Séance 1 : 
    - [Introduction à l'ingénierie de données](intro-ingenierie) 
        - [Base sur Python](base-python.slides.html) 
        - [Demande](base-demande.html)
    - [Analyse en Composantes Principales](acp-cours.html) 
        - [Utilisation sous Python](acp-python.slides.html) 
        - [Demande](acp-demande.html)

- Séance 2 : 
    - [Clustering avec CAH et *k*-means](classif-cours.html) 
        - [CAH sous Python](cah-python.slides.html) 
        - [*k*-means sous Python](kmeans-python.slides.html) 
        - [Demande](classif-demande.html)
    - Tout ensemble

- Séance 3 :
    - Autres méthodes
        - [MDS]() ?
        - [DBSCAN](dbscan-python.slides.html) (voire BIRCH ou autres)
        - [SOM]() ?

    - [Sujet TP noté]()
        - [Aide pour l'importation](tp-note-import.html)

### Liens intéressants 

- Librairie [`pandas`](https://pandas.pydata.org/)
- Librairie [`seaborn`](https://seaborn.pydata.org/)
- Librairie [`scikit-learn`](https://scikit-learn.org/) 
- Librairie [`prince`](https://github.com/MaxHalford/prince)

<!--
old
        - **AFC** : [Cours](afc-cours.html) - [Utilisation sous Python](afc-python.slides.html) - [Demande](afc-demande.html)
        - **ACM** : [Cours](acm-cours.html) - [Utilisation sous Python](acm-python.slides.html)
- [Etude de cas](etude-de-cas-pendigits.slides.html)
-->

<!--
Pour création slide jupyter : cf https://medium.com/@mjspeck/presenting-code-using-jupyter-notebook-slides-a8a3c3b59d67
jupyter nbconvert fichier.ipynb --to slides --post serve
-->