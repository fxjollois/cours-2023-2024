# Exercices autour des lois et du calcul de probabilités

<!-- reprise de l'exercice avec le dé et le gain (+1, -2, +5...) et comparer avec un autre jeu -->

## Loi uniforme continue

### Exercice 1

**_X_** est une v.a. de loi uniforme sur l'intervalle *I*. Déterminer pour chaque intervalle ci-dessous la fonction de densité et calculer *P(4 &le; X &le; 5)*.

1. *I = [4; 6]*
2. *I = [0; 5]*

### Exercice 2

**_X_** est une v.a. de loi uniforme sur *[-3;3]*.

1. Calculer *P(X &le; 1)*, et *P(X > 0.5)*
1. Donner l'espérance de **_X_**

### Exercice 3

Antoine doit venir voir Jean entre 14h45 et 16h30. Quelle est la probabilité qu'il arrive pendant la réunion de Jean qui a lieu entre 15h30 et 16h00 ?


## Lois discrètes

### Outil de calcul des probabilités d'une loi binomiale

<script>
function binom(n, p){
	if (p < 0 || p > n){
		return 0;
	}
	if (p > n / 2){
		return binom(n, n - p);
	}
	else {
		var c = 1;
		for (var k = 1; k <= p; k++){
			c = c * (n + 1 - k) / k;
		}
		return c;
	}
}

function f(N, p, K){
	return(binom(N, K) * Math.pow(p, K) * Math.pow(1-p, N-K));
}

function F(N, p, K){
	var somme = 0;
	for (var i = 0; i <= K; i++){
		somme += f(N, p, i);
	}
	return(somme);
}

function arrondi(x, d){
	var e, res;
  if (x < 0.0001) {
    res = "inférieur à 0.0001"
  } else {
    e = Math.pow(10, d);
    res = Math.round(e * x) / e;
  }
	return(res);
}


function maj(){
	N = parseInt(document.getElementById('entN').value);
	N = Math.max(N,1);
	N = Math.min(N,1000);
	document.getElementById('entN').value = N;
	document.getElementById('nbN').innerHTML = N;
	p = parseFloat(document.getElementById('entp').value);
	p = Math.max(p,0);
	p = Math.min(p,1);
	document.getElementById('entp').value = p;
	K = parseInt(document.getElementById('entK').value);
	K = Math.max(K,0);
	K = Math.min(K,N);
	document.getElementById('entK').value = K;
	document.getElementById("Pegal").innerHTML = arrondi(f(N,p,K), 4);
	document.getElementById("Pinf").innerHTML = arrondi(F(N,p,K), 4);
}
</script>

<table>
  <tr><th>Paramètre</th><th>Valeur</th><th>Limites</th></tr>
  <tr><td>N</td><td><input id="entN" value=25  onChange="maj();"></td><td>entre 1 et 1000</td></tr>
  <tr><td>p</td><td><input id="entp" value=1 onChange="maj();"></td><td>entre 0 et 1</td></tr>
  <tr><td>K</td><td><input id="entK" value=0   onChange="maj();"></td><td>entre 0 et <span id="nbN">25</span></td></tr>
</table>

<table>
  <tr><th>Proba</th><th></th><th>Valeur</th></tr>
  <tr><td>P(X = K)</td><td>=</td><td id="Pegal">--</td></tr>
  <tr><td>P(X &le; K)</td><td>=</td><td id="Pinf">--</td></tr>
</table>

### Outil de calcul des probabilités d'une loi de Poisson

<script>
function fact(num)
{
    var rval=1;
    for (var i = 2; i <= num; i++)
        rval = rval * i;
    return rval;
}

function fpois(L, K) {
    res = Math.pow(L, K) / fact(K) * Math.pow(Math.exp(1), -L);
    return(res);
}

function Fpois(L, K) {
    var somme = 0;
	for (var i = 0; i <= K; i++){
		somme += fpois(L, i);
	}
	return(somme);
}

function maj2(){
	L = parseInt(document.getElementById('entL').value);
	L = Math.max(L,0);
	L = Math.min(L,1000);
	document.getElementById('entL').value = L;
	K = parseInt(document.getElementById('entK2').value);
	K = Math.max(K,0);
	document.getElementById('entK2').value = K;
	document.getElementById("Pegal2").innerHTML = arrondi(fpois(L,K), 4);
	document.getElementById("Pinf2").innerHTML = arrondi(Fpois(L,K), 4);
}
</script>

<table>
  <tr><th>Paramètre</th><th>Valeur</th><th>Limites</th></tr>
  <tr><td>&lambda;</td><td><input id="entL" value=25  onChange="maj2();"></td><td>entre 0 et 1000</td></tr>
  <tr><td>K</td><td><input id="entK2" value=0   onChange="maj2();"></td><td>&ge; 0</td></tr>
</table>

<table>
  <tr><th>Proba</th><th></th><th>Valeur</th></tr>
  <tr><td>P(X = K)</td><td>=</td><td id="Pegal2">--</td></tr>
  <tr><td>P(X &le; K)</td><td>=</td><td id="Pinf2">--</td></tr>
</table>

### Pile ou face à répétition

On joue à pile ou face, 4 fois de suite. Et on note les résultats (dans l'ordre).

1. Déterminer la loi de probabilité 
2. Calculer les probabilités des 2 évènements suivants :
  - *A* : il y a strictement plus de piles que de faces
  - *B* : le premier lancer est pile

### De l'utilité des probabilités dans les choix stratégiques d'un étudiant

Un test comporte 10 questions, avec chacune 4 choix possibles et une seule réponse juste.

1. Combien y a t'il de grilles de réponses possibles ?
2. Quelle est la probabilité de répondre au hasard 6 fois correctement ? et d'avoir au moins 6 réponses correctes ?

### Prospection chanceuse ou efficiente

Supposons que nous avons un ensemble de 500 prospects, et on suppose qu'on a en général un taux de conversion de 20%. Nous avons 3 produits différents à vendre à ces prospects, le taux de conversion est supposé le même entre les 3. 

1. Que puis-je dire de la variable aléatoire modélisant le nombre de clients, après une campagne auprès de ces prospects ?
1. Suite à cette campagne, nous avons réussi à avoir 130 clients sur le produit 1, 110 clients sur le produit 2 et 80 clients sur le produit 3. Que peut-on dire de la performance de notre campagne pour chaque produit ?
1. Quelle est la probabilité qu'une personne achète les 3 produits ? Seulement 2 ? Seulement 1 ? Aucun ? 
1. Au final, combien de clients (quelque soit le produit) puis-je espérer avoir ?



### Gestion d'un magasin

Dans un magasin, entre 10h et 11h, on observe que la probabilité qu'une personne se présente entre la minute *m* et la minute *m+1* est égale à 10%. On veut calculer la probabilité pour que *n* personnes viennent dans ce magasin entre 10h et 11h.

1. Définir une variable aléatoire adaptée. Combien de personnes peut on espérer dans l'heure considérée ?
1. Donner les probabilités qu'aucune personne ne vienne ? qu'une seule personne ? que 6 personnes viennent ?
1. Sachant qu'à partir de 10 personnes dans le magasin, je dois prévoir 1 personne en plus. Quelle est la probabilité pour qu'au moins 10 personnes se présentent au magasin entre 10h et 11h ?


### Centenaire

Si dans une population une personne sur cent est centenaire, quelle est la probabilité de trouver au moins une personne centenaire parmi 100 personnes choisies au hasard ? Et parmi 200 personnes ? Combien de personnes doit-on choisir au hasard pour être quasiment sûr de trouver un centenaire (avec probabilité de se tromper inférieur à 1%) ?
