# Evaluation 1 - Sujet B

## Données

Dans cette évaluation, nous allons travailler sur des données concernant des films. Vous trouverez ci-dessous le contenu du premier document (réduit aux éléments importants pour cette évaluation - les textes longs ont été remplacé par `"..."`).

```json
{
	"_id" : ObjectId("573a1390f29313caabcd5c0f"),
	"plot" : "...",
	"genres" : [ "Drama", "History" ],
	"rated" : "NOT RATED",
	"cast" : [
		"Lillian Gish",
		"Spottiswoode Aitken",
		"Mary Alden",
		"Frank Bennett"
	],
	"num_mflix_comments" : 1,
	"title" : "Intolerance: Love's Struggle Throughout the Ages",
	"fullplot" : "...",
	"countries" : [ "USA" ],
	"released" : ISODate("1916-09-05T00:00:00Z"),
	"directors" : [ "D.W. Griffith" ],
	"writers" : [ "D.W. Griffith (scenario)", "Anita Loos (titles)" ],
	"awards" : {
		"wins" : 1,
		"nominations" : 0,
		"text" : "1 win."
	},
	"lastupdated" : "2015-09-05 00:01:19.580000000",
	"year" : 1916,
	"imdb" : {
		"rating" : 8,
		"votes" : 9880,
		"id" : 6864
	},
	"type" : "movie",
	"tomatoes" : {
		"viewer" : {
			"rating" : 3.8,
			"numReviews" : 4718,
			"meter" : 78
		},
		"dvd" : ISODate("2002-12-10T00:00:00Z"),
		"critic" : {
			"rating" : 8.1,
			"numReviews" : 32,
			"meter" : 97
		},
		"lastUpdated" : ISODate("2015-09-15T17:02:34Z"),
		"consensus" : "...",
		"rotten" : 1,
		"production" : "Cohen Media Group",
		"fresh" : 31
	}
}
```

Quelques points à noter :

- Un même film peut donc avoir plusieurs genres (cf champs `genres`), contenus dans un tableau
- Il en est de même pour les acteurs principaux (champs `cast`), les pays du film (champs `countries`), les directeurs (champs `directors`), et les scénaristes (champs `writers`)
- Le champs `imdb` reprend les éléments importants du site [IMDB](https://www.imdb.com/), sur lequel il est possible d'évaluer le film (sous-champs [`rating`](https://help.imdb.com/article/imdb/track-movies-tv/ratings-faq/G67Y87TFYYP6TWAV?ref_=helpsect_cons_2_4#ratings) - de 1 à 10)
- Le champs `tomatoes` fait lui référence au site [Rotten Tomatoes](https://www.rottentomatoes.com/), proposant aussi une évaluation du film (sous-champs `critic`, en particulier [`meter`](https://www.rottentomatoes.com/about#whatisthetomatometer) en pourcentage - donc sur 100)

## Questions

Les données sont accessibles sur le serveur distant, dans la collection **`movies`** de la base de données **`sample_mflix`**.

**ATTENTION A BIEN METTRE LE CODE ET PAS LE RESULTAT !!!**

<iframe src="https://docs.google.com/forms/d/e/1FAIpQLSdN74CskSAAAftcRNoPkmeEgQe-zHacSHOJnYmndA3G18QkmQ/viewform?embedded=true" width="800" height="2405" frameborder="0" marginheight="0" marginwidth="0">Chargement…</iframe>
