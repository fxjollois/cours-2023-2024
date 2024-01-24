# SAE Collecte automatisée de données web

<!--
- 10h de TP
- 6 heures de suivi
- Pas de soutenances
Base SIRENE à compléter par
- Coordonnées géographiques
- Informations sur le web via Google Maps
-->

A partir des données de la [base SIRENE](https://www.data.gouv.fr/fr/datasets/base-sirene-des-entreprises-et-de-leurs-etablissements-siren-siret/) (et plus particulièrement le fichier `StockEtablissement`), vous devez compléter les informations par :

- les coordonnées géographiques via l'[API Adresse](https://adresse.data.gouv.fr/api-doc/adresse) ([guide](https://guides.etalab.gouv.fr/apis-geo/1-api-adresse.html#les-donnees-d-adresses))
- les informations obtenues via une recherche sur [Google Maps](https://www.google.com/maps/search/), via du web-scraping.

### A PRENDRE EN CONSIDERATION

- Fichier de départ très lourd (**6,84 Go**) donc à ne pas charger en une fois !
- Appel à l'API à modérer (limite de 50 requêtes par seconde et par IP pour le géocodage simple via l’API Adresse - tous les ordinateurs de l'IUT ont la même adresse IP en sortie)
    - Utilisation de `time.sleep(1)` (ne pas oublier `import time`) pour retarder d'une seconde ce qui suit
- Rendu au format `zip`, contenant un fichier de code (`.ipynb`) et un court rapport expliquant la démarche et les problèmes rencontrés, à déposer sur cette adresse : 

<https://cloud.parisdescartes.fr/index.php/s/BsdJWfD7rnGdtnr>

## Récupération de données de l'API Adresse

### D'une adresse vers des coordonnées géographiques

A partir d'une adresse (par exemple, le *143 Avenue de Versailles, Paris*), nous allons chercher les coordonnées géographiques de ce lieu. 

Pour cela, nous avons besoin du package `requests` (généralement déjà présent).

```python
import requests

adresse = "143+avenue+Versailles+paris"
url = "https://api-adresse.data.gouv.fr/search/"
recherche = url + "?q=" + adresse

reponse = requests.get(recherche)
reponse
```

Si le résultat est `<Response [200]>`, c'est que tout est OK. Sinon, se reporter à la [liste des erreurs](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status)

On peut ensuite récupérer les résultats au format `JSON` 

```python
reponse.json()
```

Dans notre cas, il y a plusieurs résultats. Généralement, le premier est celui avec le `score` le plus élevé.

## Web-scraping avec Python

- Inspiré par cette page : <https://outscraper.com/how-to-scrape-google-maps-with-python-and-selenium/>
- Installation à faire auparavant :
    - Packages [`selenium`](https://selenium-python.readthedocs.io/api.html#locate-elements-by) et [`bs4`](https://www.crummy.com/software/BeautifulSoup) (BeautifulSoup) pour Python
    - Exécutable [`chromedriver`](https://chromedriver.chromium.org/downloads) (selon votre OS)

### Première étape : configurer le navigateur 

Si vous faites cela bien, `chromedriver` est dans le même répertoire que votre notebook

```python
from selenium import webdriver

chromedrive_path = './chromedriver' # chemin vers votre exécutable 
driver = webdriver.Chrome(chromedrive_path)
```

#### Création de l'URL à récupérer

```python
base_url = "https://www.google.com/maps/search/"
place_info = "IUT+paris+rives+de+seine"
comp_url = "/@48.8489968,2.3125954,12z"

url = base_url + place_info + comp_url
url
```

### Deuxième étape : récupération du contenu HTML

- Lors de la première exécution de ce code, une fenêtre va s'ouvrir dans laquelle vous devrez cliquer (a priori sur "Tout accepter")
- **NE PAS FERMER CETTE FENETRE !**
- Relancer le code une deuxième fois pour effectivement récupérer le contenu désiré

```python
driver.get(url)
html = driver.page_source
```

### Troisième étape : recherche de ce qui nous intéresse (ici la partie Informations)

```python
from bs4 import BeautifulSoup

soup = BeautifulSoup(html)
results = soup.select("div[aria-label*='Informations']")
results
```

- Si on cherche s'il y a un site web 

```python
results = soup.select("a[aria-label*='Site Web']")
results
```

- Dernière étape : une fois qu'on a récupéré tout ce qu'on souhaite, on ferme correctement le navigateur

```python
driver.close()
```

