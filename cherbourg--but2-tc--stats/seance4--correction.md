# Exercices autour des lois et du calcul de probabilités - *Correction*

## Loi uniforme continue

---

### Exercice 1

**X** est une v.a. de loi uniforme sur l'intervalle $I$. Déterminer pour chaque intervalle ci-dessous la fonction de densité et calculer $P(4 &le; X &le; 5)$.

1. *I = [4; 6]*
2. *I = [0; 5]*

#### Solution

Pour rappel, nous avons comme définition de la fonction de répartition :

> *F(x) = P(X &le; x) = (x - a) / (b - a)*

De plus, nous savons que 

> *P(c &le; X &le; d) = P(X &le; d) - P(X &le; c)*

##### Avec *I = [4; 6]*

On reprend la formule pour calculer *P(X &le; 5)$. Par contre, *P(X &le; 4)* est forcément égal à 0, car les valeurs sont entre 4 et 6 (donc il n'y aucune chance d'avoir une valeure inférieure à 4). Et, de plus, on sait que *P(X = x) = 0* dans le cas continu (donc *P(X = 4) = 0*).

> *P(4 &le; X &le; 5)  = P(X &le; 5) - P(X &le; 4) = (5 - 4) / (6 - 5) - 0 = .5*

##### Avec *I = [0; 5]*

> *P(4 &le; X &le; 5) = P(X &le; 5) - P(X &le; 4) = 1 - (4 - 0) / (5 - 0) = .2*

---

### Exercice 2

*__X__* est une v.a. de loi uniforme sur *[-3;3]*.

Calculer *P(X &le; 1)*, et *P(X > 0.5)*

#### Solution

##### Calcul de $P(X &le; 1)$

> *P(X &le; 1) = (1 - (-3)) / (3 - (-3)) = 4 / 6 = .6667*

##### Calcul de $P(X > 0.5)$

On sait que *{X &le; 5}* est le complémentaire de *{X > 5}*, donc on a l'égalité suivante :

> *P(X > 0.5) = 1 - P(X &le; 5)*

On a donc le calcul suivant :

> *P(X > 5) = 1 - P(X &le; 0.5) = 1 - (0.5 - (-3)) / (3 - (-3)) = 1 - 3.5 / 6 = 2.5 / 6 = 0.4167*


---

### Exercice 3

Antoine doit venir voir Jean entre 14h45 et 16h30. Quelle est la probabilité qu'il arrive pendant la réunion de Jean qui a lieu entre 15h30 et 16h00 ?

#### Solution

On considère donc **_X_** la v.a. de loi uniforme continue sur l'intervale *[14.75; 16.5]*. Et on calcule *P(15.5 &le; X &le; 16)*.

> *P(15.5 &le; X &le; 16) = P(X &le; 16) - P(X &le; 15.5)<br>
<span style="width:112px;display:inline-block"></span>= (16 - 14.75) / (16.5 - 14.75) - (15.30 - 14.75) / (16.5 - 14.75)<br>
<span style="width:112px;display:inline-block"></span>= 1.25 / 1.75 - .75 / 1.75<br>
<span style="width:112px;display:inline-block"></span>= .5 / 1.75<br>
<span style="width:112px;display:inline-block"></span>= 0.2857*


---

## Lois discrètes


### Pile ou face à répétition
On joue à pile ou face, 4 fois de suite. Et on note les résultats (dans l'ordre).

1. Déterminer la loi de probabilité 
2. Calculer les probabilités des 2 évènements suivants :
  - $A$ : il y a strictement plus de piles que de faces
  - $B$ : le premier lancer est pile

#### Solution

##### Loi 

On a une loi discrète à 16 issues (l'ordre a du sens a priori) équi-probable (avec *P* : pile et *F* : face) :

*&Omega; = {PPPP, PPPF, PPFP, PPFF, PFPP, PFPF, PFFP, PFFF, FPPP, FPPF, FPFP, FPFF, FFPP, FFPF, FFFP, FFFF}*

Pour chaque évènement élémentaire &omega;, on a donc 

*P(&omega;) = 1 / 6

##### Calcul

On sait que la probabilité d'un évènement *A* est égale, dans le cas discret, à la somme des probabilités des évènements élémentaires qui le composent.

On a donc pour l'évènement *A*

> *P(A) = P(PPPP) + P(PPPF) + P(PPFP) + P(PFPP) + P(FPPP) = 5 / 16 = .3125*

Pour l'éveénement $B$, nous n'avons finalement pas besoin de regarder plus loin que juste le premier lancer. On a une chance sur deux d'avoir pile lors du premier jet.

> *P(B) = .5*

---

### De l'utilité des probabilités dans les choix stratégiques d'un étudiant

Un test comporte 10 questions, avec chacune 4 choix possibles et une seule réponse juste.

1. Combien y a t'il de grilles de réponses possibles ?
2. Quelle est la probabilité de répondre au hasard 6 fois correctement ? et d'avoir au moins 6 réponses correctes ?

#### Solution

1. On a *4<sup>10</sup> = 1048576* grilles possibles
1. On a dix tirages aléatoires d'une loi de Bernouilli avec *p=.25* donc *__X__ ~ Binomiale(10, .25)*
    - On utilise l'outil disponible sur la page de cours pour faire les calculs
    - *P(X = 6) = 0.016222*
    - *P(X &ge; 6) = 1 - P(X &le; 5) = 1 - 0.9803  = 0.0197*

---

### Prospection chanceuse ou efficiente

Supposons que nous avons un ensemble de 500 prospects, et on suppose qu'on a en général un taux de conversion de 20%. Nous avons 3 produits différents à vendre à ces prospects, le taux de conversion est supposé le même entre les 3. 

1. Que puis-je dire de la variable aléatoire modélisant le nombre de clients, après une campagne auprès de ces prospects ?
1. Suite à cette campagne, nous avons réussi à avoir 130 clients sur le produit 1, 110 clients sur le produit 2 et 80 clients sur le produit 3. Que peut-on dire de la performance de notre campagne pour chaque produit ?
1. Quelle est la probabilité qu'une personne achète les 3 produits ? Seulement 2 ? Seulement 1 ? Aucun ? 
1. Au final, combien de clients (quelque soit le produit) puis-je espérer avoir ?

#### Solution

On utilise ici aussi l'outil pour les calculs concernant la loi Binomiale.

1. Soit $X_1$, $X_2$ et $X_3$ les v.a. estimant le nombre de vente pour chaque produit. Elles suivent toutes les trois une loi Binomiale de paramètre $n=500$ et $p.2$. Dans ce cadre, l'espérance de vente de chaque produit est de 100 unités :
$$E(X_1) = E(X_2) = E(X_3) = np = 500 \times .2 = 100$$
1. La question est de savoir si la situation (*i.e* le nombre de ventes) est exceptionnelle. Pour les produits 1 et 2, nous allons chercher la probabilité d'avoir (au moins) cette situation, puisqu'ils dépassent l'espérence de vente. Donc, pour le produit 1, nous cherchons la probabilité d'avoir au moins 130 ventes. On cherche à calculer $P(X_1 \ge 130)$. De même pour le produit 2, on va chercher $P(X_2 \ge 110)$. Pour le produit 3, puisque le résultat est inférieur à ce qu'on espère, on va plutôt chercher $P(X_3 &le; 80)$.
    - Pour le produit 1, **le résultat est très bon, avec moins de 1% de chance de faire aussi bien.**
\begin{eqnarray*}
P(X_1 \ge 130) &=& 1 - P(X_1 < 130)    &\mbox{$\rightarrow$ complémentaire}\\
               &=& 1 - P(X_1 &le; 129)  &\mbox{$\rightarrow$ cas discret ici}\\
               &=& 1 - 0.9993          &\mbox{$\rightarrow$ utilisation de l'outil} \\
               &=& 0.007
\end{eqnarray*}
    - Pour le produit 2, **la situation, bien que favorable, est "normale".**
\begin{eqnarray*}
P(X_2 \ge 110) &=& 1 - P(X_2 < 110)\\
               &=& 1 - P(X_2 &le; 109)\\
               &=& 1 - 0.8556\\
               &=& 0.1444
\end{eqnarray*}
    - Pour le produit 3, **le résultat est très décevant, avec 1.3% de risque de faire aussi peu**
\begin{eqnarray*}
P(X_3 &le; 80) &=& 0.0130
\end{eqnarray*}
1. Maintenant, on va définir $Z$ la v.a. donnant le nombre de produits achetés par un client, parmi les 3 qu'on lui propose. Dans ce cadre, $Z$ suit une loi Binomiale de paramètre $n=3$ et $p=.2$. Grâce à l'outil, on détermine :
    - Voici les valeurs pour chaque cas possible
        - $P(Z = 3) = 0.008$
        - $P(Z = 2) = 0.096$
        - $P(Z = 1) = 0.384$
        - $P(Z = 0) = 0.512$
    - On peut compléter en indiquant qu'un client achète en moyenne $E(Z) = np = 3 \times .2 = .6$ produit
    - On voit aussi qu'un client a une probabilité 0.488 d'acheter au moins un produit (.384 + .096 + .008)
1. Pour répondre à cette question, nous définissons $Y$ la v.a. modélisant le nombre de personnes ayant acheté au moins un produit, parmi les 500. $Y$ suit une loi Binomial de paramètres $n=500$ et $p=.488$. On calcule donc l'espérance de $Y$ avec
$$E(Y) = np = 500 \times .488 = 244$$
    - On peut donc espérer avec 244 clients au final


---

### Guichet de poste

Dans une poste d’un petit village, on remarque qu’entre 10 heures et 11 heures, la probabilité pour que deux personnes entrent durant la même minute est considérée comme nulle et que l'arrivée des personnes est indépendante de la minute considérée. On a observé que la probabilité pour qu'une personne se présente entre la minute $m$ et la minute $m+1$ est : $p = 0.1$. On veut calculer la probabilité pour que $n$ personnes se
présentent au guichet entre 10h et 11h.

1. Définir une variable aléatoire adaptée. Combien de personnes peut on espérer dans l'heure considérée ?
1. Donner les probabilités qu'aucune personne ne vienne ? qu'une seule personne ? que 6 personnes viennent ?
2. Quelle est la probabilité pour qu'au moins 10 personnes se présentent au guichet entre 10h et 11h ?

#### Solution

1. Une variable aléatoire adaptée à ce problème est le nombre $X$ de personnes se présentant au guichet entre 10h et 11h. Compte tenu des hypothèses, on partage l'heure en 60 minutes. Alors $X$ suit une loi de Poisson de paramètre $\lambda = 60×0.1 = 6$.
1. On peut alors calculer les probabilités demandées : 
    - $P(X = 0) = 0.0025$
1.  Calculons maintenant la probabilité pour que au moins 10 personnes se présentent au guichet entre 10h et 11h :
    - $P(X \ge 10) = 1 - P(X &le; 9) = 1 - 0.9161 = 0.0839$
    
---

### Centenaire

Si dans une population une personne sur cent est centenaire, quelle est la probabilité de trouver au moins une personne centenaire parmi 100 personnes choisies au hasard ? Et parmi 200 personnes ?

#### Solution

On considère $X$ suivant une loi de Poisson d'espérance $\lambda = 100 \times \frac{1}{100} = 1$. On peut ainsi calculer les valeurs suivantes :
$$
  P(X \ge 1) = 1 - P(X = 0) = 1 - 0.3679 = 0.6321
$$

Si on a 200 personnes, $Y$ suit une loi de Poisson avec $\lambda = 200 \times \frac{1}{100} = 2$. On a ainsi 
$$
  P(Y \ge 1) = 1 - P(Y = 0) = 1 - 0.1353 = 0.8647
$$