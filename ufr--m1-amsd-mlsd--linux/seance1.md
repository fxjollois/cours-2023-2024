---
layout: slides
---

class: middle, center, inverse, title
# Système pour la Data Science

## Master AMSD/MLSD

### Langage système de base

---
class: section, middle, center
## Linux

---

## Présention

- Issu de *Unix*, conçu dans les années 1960

- Débuté comme un projet étudiant par *Linus Torvald* (1991)

- Maintenant, système d'exploitation le plus répandu sur les serveurs
    - multi-utilisateurs
    - multi-tâches
    - gratuit

- Système d'exploitation regroupant 
    - Gestion mémoire et entrées-sorties
    - Interpréteur de langage de commandes (dont `bash` vu ici)
    - Système de messagerie
    - Nombreux utilitaires (compilateurs, éditeurs, ...)

---

## Caractéristiques

- Fiable et pas (ou très peu) de *plantage*
    - Moins de *bugs* que les concurrents comme *Windows*
    - Virus très rares car moins facile à déployer (pas d'exécutable type *Windows*)

- Fonctionne sur tout type de machine

- Gratuit et surtout *open source*

- Pas de support technique autre que la communauté (forums, sites web dédiés, ...)

- Possibilité de fonctionner sans interface graphique (utile pour les serveurs)


---

## Pourquoi un cours orienté Système est intéressant ?

Data Science principalement sur des outils fonctionnant sous Linux

- R et Python en particulier
- Tout ce qui est autour du Big Data
- Tout ce qui est autour du Deep Learning

## Comment mettre en pratique ?

Utilisation d'une machine virtuelle *Ubuntu Server*

- A créer (cf suite de la séance)

---

## Ce qu'on verra ? (dans le désordre)

- Commandes de base

- Ecritures de scripts `shell`
    - Automatisation et ests

- Déploiement autour de R
    - sur notre serveur propre
    - d'applications Shiny

- Déploiement autour de Python
    - sur notre serveur propre
    - d'applications Streamlit

- Installation d'outils (RStudio Server, Shiny Server, JupyterHub...)

---

## Comment lire ce document ?

- Présentation sommaire de différentes commandes et des paramètres usuels de celles-si

- Liens disponibles vers l'[aide Ubuntu](https://manpages.ubuntu.com/)

> **A FAIRE** : tester les commandes sur votre serveur (une fois celui-ci créé, dans la seconde partie de la séance)

> *Idéalement* : tester des variantes des commandes pour comprendre son fonctionnement

- Quelques liens intéressants en plus de l'aide Ubuntu :
    - [developpez.com](https://www.developpez.com/) : plusieurs sections très utiles
    - [stackoverflow](https://stackoverflow.com/) : forum de référence
    - [google](https://www.google.com/), [bing](https://www.bing.com/?cc=fr), [qwant](https://www.qwant.com/?l=fr) et consorts sont aussi vos amis
    
---
class: section, middle, center
## Commandes de base

---

## Interface de commande en ligne

- Commande à écrire, suivie des arguments si besoin
    - Après le *prompt* (**$** ou **>>** ou *%* ou ...)

- Exécution direct après appui sur *Entrée*
    - Langage dit interprété donc

- Interprétation si c'est possible
    - Sinon attente de la suite à la ligne suivante
    - Tant que le *prompt* n'apparaît pas, la commande n'est pas connsidérée comme interprétable

- Résultats affichés dans la console

- Navigation dans les anciennes commandes avec les flèches haut et bas

---

## Commande la plus utile (ou presque)

- [`man`](https://manpages.ubuntu.com/manpages/jammy/en/man1/man.1.html) : aide sur une commande en particulier
    - nom de la commande à mettre en paramètre
    - Navigation avec les flèches (ou les flèches *page précédente* et *page suivante*)
    - Quitter en tapant `q`
    
```bash
man man
```

---

## Commandes de base

- [`echo`](https://manpages.ubuntu.com/manpages/jammy/fr/man1/echo.1.html) : affichage d'une chaîne de caractères
    - Quotes (simples ou doubles) non utiles

```bash
$ echo "Bonjour à vous"
$ echo Bonjour à vous
```

- [`date`](https://manpages.ubuntu.com/manpages/jammy/en/man1/date.1.html) : date du jour (avec formatage possible)

```bash
$ date
```

- [`who`](https://manpages.ubuntu.com/manpages/jammy/en/man1/who.1.html) : qui est connecté sur le système ?
    - la deuxième permet de savoir qui on est et sur quel terminal ou fenêtre on est

```bash
$ who
$ who am i
```

---

## Navigation dans l'arborescence des fichiers

- [`pwd`](https://manpages.ubuntu.com/manpages/jammy/en/man1/pwd.1.html) : nom du répertoire de travail 

```bash
$ pwd
```

- [`cd`](https://manpages.ubuntu.com/manpages/kinetic/en/man1/cd.1posix.html) : changement du répertoire de travail
    - sans paramètre, répertoire *home* de l'utilisateur
    - adressage relatif ou absolu à utiliser
        - relatif : chemin par rapport à la position actuelle
        - absolu : chemin depuis la racine `/`
    - `..`, répertoire parent du répertoire actuel
    
```bash
$ cd Documents
$ cd 
```

.footnote[.small[L'auto-complétion fonctionne sur les commandes ET sur les chemins et fichiers.]]

---

## Contenu d'un répertoire

- [`ls`](https://manpages.ubuntu.com/manpages/jammy/en/man1/ls.1.html) : liste le contenu du répertoire courant
    - si nom de répertoire passé en paramètre, en liste le contenu
    - `*` permet de remplacer toute chaîne de caractères

```bash
$ ls
$ ls *.txt
```

- Options avec `-` puis une ou plusieurs lettres parmi
    - `l` : informations
        - type de fichier et droits d'accès
        - nombre de liens (1 si fichier, depend du contenu si répertoire)
        - propriétaire et groupe
        - taille,  date de dernire modification et nom
    - `h` : formatage de l'affichage de l'espace mémoire plus lisible
    - `a` : tous les fichiers (même cachés - *i.e* commençant par `.`)

```bash
$ ls -lh
$ ls -a
```

---

## Création d'un fichier

- Opérateur `>` envoie le résultat d'une commande dans un fichier texte

```bash
$ echo Ceci est un test > test.txt
$ date > test_date.txt
```

- [`touch`](https://manpages.ubuntu.com/manpages/jammy/en/man1/touch.1.html) : créé un fichier vide

```bash
$ touch test_vide.txt
```

- [`nano`](https://manpages.ubuntu.com/manpages/jammy/en/man1/nano.1.html) : éditeur de texte simple
    - `Ctrl+X` pour quitter
    - `Ctrl+O` pour écrire
    - Commandes indiquées en bas de l'écran

```bash
$ nano test_vide.txt
```


---

## Suppression d'un fichier

- [`rm`](https://manpages.ubuntu.com/manpages/jammy/en/man1/rm.1.html) : suppression d'un fichier (ou de plusieurs si utilisation de `*`)
    - Deuxième ligne : suppression de tous les fichiers finissant par `.txt`
    - Troisième ligne : suppression de tous les fichiers
    - Ne fonctionne pas pour un répertoire

```bash
$ rm test_date.txt
$ rm *.txt
$ rm *
```

---

## Création/Suppression d'un répertoire

- [`mkdir`](https://manpages.ubuntu.com/manpages/jammy/en/man1/mkdir.1.html) : créé un répertoire avec le nom passé en paramètre
    - Si espace(s) voulu(s), soit mettre entre quotes, soit utiliser `"\ "`

```bash
$ mkdir dir_test
$ mkdir "dir test2"
$ mkdir dir\ test3
```

- [`rmdir`](https://manpages.ubuntu.com/manpages/jammy/en/man1/rmdir.1.html) : supprime le répertoire passé en paramètre
    - Ne fonctionne que si le répertoire est vide
    - Deuxième et troisième lignes : utilisation possible de `*`
    
```bash
$ rmdir "dir test2"
$ rmdir dir*
$ rmdir *
```

---

## Informations, contenu et recherche d'un fichier

- [`file`](https://manpages.ubuntu.com/manpages/jammy/en/man1/file.1.html) : type de fichier
- [`wc`](https://manpages.ubuntu.com/manpages/jammy/fr/man1/wc.1.html) : nombre de caractères, de lignes et d'octets

```bash
$ echo "Ceci est encore un test" > test.txt
$ file test.txt
$ wc test.txt
```

- [`cat`](https://manpages.ubuntu.com/manpages/jammy/en/man1/cat.1.html) : affiche le contenu du fichier, quelqu'il soit (texte ou binaire)

```bash
$ cat test.txt
```

- [`find`](https://manpages.ubuntu.com/manpages/jammy/en/man1/find.1.html) : recherche un (ou plusieurs) fichiers dans le répertoire courant

```bash
$ find t*
```

---

## Complément sur la lecture d'un fichier texte

- [`head`](https://manpages.ubuntu.com/manpages/jammy/en/man1/head.1.html) : ne lit que le début du fichier
- [`tail`](https://manpages.ubuntu.com/manpages/jammy/en/man1/tail.1.html) : ne lit que les dernières lignes
    - Option `-n 5` : détermine le nombre de lignes à lire (10 par défaut)

```bash
$ head .profile # fichier caché
$ head .profile -n 1
$ tail .profile
$ tail .profile -n 5
```

- [`more`](https://manpages.ubuntu.com/manpages/jammy/en/man1/more.1.html) : affichage par pages
- [`less`](https://manpages.ubuntu.com/manpages/jammy/en/man1/less.1.html) : affichage par lignes
    - Interactifs tous les 2 : possibilité de choisir comment faire défiler les lignes

```bash
$ more .profile # peu utile ici car fichier assez court
$ less .profile
```

---

## Manipulation d'un fichier


- [`cp`](https://manpages.ubuntu.com/manpages/jammy/en/man1/cp.1.html) : permet de copier le fichier (premier paramètre) en fonction du 2ème
    - Si nom de fichier : copie avec le nouveau nom
    - Si répertoire : copie dans ce répertoire avec le même nom
    - Si répertoire + nom de fichier : idem mais avec nouveau nom

```bash
$ cp test.txt test2.txt
$ mkdir dir_test
$ cp test.txt dir_test
$ cp test.txt dir_test/test3.txt
```

- [`mv`](https://manpages.ubuntu.com/manpages/jammy/en/man1/mv.1.html) : déplace un fichier dans un répertoire 

```bash
$ mv test2.txt dir_test 
```

---

## Gestion des processus

- [`ps`](https://manpages.ubuntu.com/manpages/jammy/en/man1/ps.1.html) : liste les processus en cours
    - Informations de base dont
        - `PID`: numéro d'identification du processus
        - `TIME` : temps CPU utilisé depuis le début
    - `u` : informations complémentaires
    - `a` : ajout des processus des autres utilisateurs
    - `x` : chemin complet du programme lancé

```bash
$ ps
$ ps aux
```

- [`top`](https://manpages.ubuntu.com/manpages/jammy/en/man1/top.1.html) : affichage amélioré des processus
    - Choix possible du tri

```bash
$ top
```


---

## Redirection des sorties de commandes

- Comme on l'a déjà vu, opérateur `>` pour rediriger la sortie d'une commande dans un fichier

```bash
$ echo Encore un test > test4.txt
$ cat test4.txt
```

- `>>` : redirige la sortie d'une commande à la suite du fichier texte
    - Pas d'écrasement du contenu existant
    
```bash
$ echo Une deuxième ligne >> test4.txt
$ cat text4.txt
```

---

## Recherche dans un fichier

- [`grep`](https://manpages.ubuntu.com/manpages/jammy/en/man1/grep.1.html) : renvoie les lignes correspondant à une recherche textuelle

```bash
$ grep "un" test4.txt
```

- Utilisation des [expressions régulières](https://fr.wikipedia.org/wiki/Expression_r%C3%A9guli%C3%A8re)
    - `.` : un caractère quelqu'il soit
    - `exp+` : expression présente au moins une fois
    - `exp*` : expression présente zéro, une ou plusieurs fois
    - `[liste]` : un des caractères de la liste
    - `[^liste]` : un caractère qui n'est pas dans la liste
    -  `^` : caractère suivant `^` se trouvant en début de ligne
    -  `$` : caractère précédent `$` se trouvant en fin de ligne
    - ...

```bash
$ grep "un" test4.txt
$ grep "[eE]" test4.txt
```

---

## Processus multiples

- [`sleep`](https://manpages.ubuntu.com/manpages/jammy/en/man1/sleep.1.html) : pause du nombre de secondes passées en paramètres
    - `Ctrl+C` : tue le processus (valable pour tous les processus)

```bash
$ sleep 1
```

- Possibilité de lancer en une ligne plusieurs commandes, séparées par `;`
    - Exécution séquentielle (attente de la fin d'une pour faire l'autre)

```bash
$ date; sleep 1; who
```

- `&` : opérateur permettant de lancer un processus en arrière plan
    - Dans la liste des processus, vous devriez voir `sleep`

```bash
$ sleep 100&
$ ps
```


---

## Pipes

- `|` : opérateur *pipe* envoyant les résultats de la première commande (à gauche) dans la commande de droite

```bash
$ sleep 100&
$ ps | grep "sleep"
```

## Interruption d'un processus en cours

- [`kill`](https://manpages.ubuntu.com/manpages/jammy/en/man1/kill.1.html) : tue le processus dont le `PID` est passé en paramètre

```bash
$ sleep 100&
$ ps | grep "sleep"
$ kill <PID_sleep>
```

.footnote[.small[`pgrep` cherche un processus avec le nom passé en paramètre et ne renvoie que le `PID`.]]

---

## Usage de la mémoire

- [`free`](https://manpages.ubuntu.com/manpages/jammy/en/man1/free.1.html) : espace mémoire vive utilisé et disponible
    - On parle ici de la RAM
    - `-h` : option permettant un affichage plus concis des valeurs

```bash
$ free -h
```

- [`df`](https://manpages.ubuntu.com/manpages/jammy/en/man1/df.1.html) : espace mémoire morte utilisé et disponible
    - On parle ici des disques durs
    - idem pour `-h`

```bash
$ df -h
```

---

## Téléchargement d'un fichier via une URL

- [`wget`](https://manpages.ubuntu.com/manpages/jammy/en/man1/wget.1.html) : permet de télécharger un fichier dont l'URL est spécifiée

```bash
$ wget https://fxjollois.github.io/donnees/adult.data
```


---

## Compression : `.gz` ou `.zip`

Souvent nécessaire car fichiers trop volumineux

- `gz` : de base dans l'environnement Linux
- `zip` : archives (souvent) de l'environnement Windows

## Archivage : `.tar`

Opération permettant de regrouper ensemble des fichiers
## Les deux

Souvent les deux vont de paires, et produisent des fichiers avec l'extension `.tar.gz`

---

## Compression via `gzip`

- [`gzip`](https://manpages.ubuntu.com/manpages/jammy/en/man1/gzip.1.html) : compresse le fichier passé en paramètre (extension `.gz`)
    - Supprime par défaut le fichier compressé
    - `-k` : pour garder le fichier original

- [`gunzip`](https://manpages.ubuntu.com/manpages/jammy/en/man1/gunzip.1.html) : décompresse le fichier passé en paramètre
    - Supprime par défaut l'archive une fois celle-ci décompressé
    - `-k` : pour garder l'archive

```bash
$ gzip adult.data
$ gunzip adult.data
$ gzip -k adult.data
$ rm adult.data
$ gunzip -k adult.data
```

.footnote[.small[Exécutez `ls` entre chaque commande pour voir leur effet, voir avec `-h` pour voir l'effet de la compression.]]

---

## Compression via `zip`

- Installation du package 
    - Mot de passe requis (celui de la création de votre VM)

```bash
$ sudo apt install zip
```

- [`zip`](https://manpages.ubuntu.com/manpages/jammy/en/man1/zip.1.html) : compression du (ou des) fichier(s) dans l'archive (nom à fournir)

```bash
$ zip adult.zip adult.data
```

- [`unzip`](https://manpages.ubuntu.com/manpages/jammy/en/man1/unzip.1.html) : décompression du fichier

```bash
$ unzip adult.zip
```

.footnote[.small[Exécutez `ls` entre chaque commande pour voir leur effet, voir avec `-h` pour voir l'effet de la compression.]]

---

## Archivage dans un fichier via `tar`

- A faire pour tester

```bash
$ wget https://fxjollois.github.io/donnees/sakila/sakila_csv.zip
$ unzip sakila_csv.zip
```

- [`tar`](https://manpages.ubuntu.com/manpages/jammy/en/man1/tar.1.html) : archive les fichiers passés en paramètre dans un seul fichier
    - `c` : création d'une archive
    - `x` : extraction des fichiers de l'archive
    - `v` : détaille le fonctionnement
    - `f`: nomme le fichier à créer
    - `z` : effectue une compression en plus (ajout extension `.gz`)

```bash
$ tar -zcvf sakila.tar csv/
$ tar -zxvf sakila.tar
```

.footnote[.small[supprimer le répertoire `csv` entre les 2 commandes pour voir le fonctionnement.]]

---

## Recherche avancée dans un fichier texte

- [`sed`](https://manpages.ubuntu.com/manpages/jammy/en/man1/sed.1.html) : extraction de lignes d'un fichier texte
    - Format de type `sed option commande`
        - Options principales
            - `-n` : n'affiche pas toutes les lignes
            - `-e` : indique la commande à exécuter (on peut en enchaîner plusieurs)
        - Commandes principales
            - `p` : affichage des lignes sélectionnées
            - `$a` : ajoute une ligne à la fin
            - `s` : remplace une chaîne par une autre
        - Utilisation des expressions régulières

```bash
$ wget https://fxjollois.github.io/donnees/heart.txt
$ sed -n '5,10p' heart.txt # Affiche les lignes 5 à 10
$ sed -n -e '/femi/p' heart.txt # Affiche les lignes contenant la chaîne "femi"
$ sed -n -e '/femi.*absence/p' heart.txt # Affiche les lignes contenant "femi" puis plus loin "absence"
$ sed 's/feminin/Femme/g' heart.txt # Remplace "feminin" par "Femme"
$ sed 's/feminin/Femme/g' heart.txt | sed 's/masculin/Homme/g' # A deviner
```


---
class: section, middle, center

### Scripts `shell`

<!-- librement inspiré de cette page : https://linux.goffinet.org/administration/scripts-shell/ -->

---

## Scripts

> Pourquoi faire des scripts ?

- Possibilité de faire des opérations simples rapidement (voire moins simples parfois)
- Utile pour du traitement de fichiers de données
- Intéressant dans un cadre de pré-traitement de données ou d'intégration de données

### Liens intéressants :

- [Introduction aux scripts shell](https://doc.ubuntu-fr.org/tutoriel/script_shell) : doc Ubuntu
- [Guide avancé d'écriture des scripts](https://abs.traduc.org/abs-fr/index.html) : date un peu mais toujours d'actualité
- [Présentation de ksh](https://marcg.developpez.com/ksh/) : compatible avec bash

---

## shebang : `#!/bin/bash`

- Suite de caractères (`#!`) déterminant que c'est un fichier de script et avec quel interpréteur le lancer (`bash` ici)

- [`echo`](https://manpages.ubuntu.com/manpages/jammy/fr/man1/echo.1.html) : affichage d'un texte dans la console 

- Déclaration d'une variable sans mot-clé (sans espace autour de `=` et appel à sa valeur utilisant l'opérateur `$`)

- [`exit`](https://manpages.ubuntu.com/manpages/jammy/en/man1/exit.1posix.html) : sortie du script

```bash
#!/bin/bash
VAR="vous"
echo Bonjour $VAR
echo "Bonjour $VAR"
exit
```


---

## Droit sur un fichier

Avec `ls -l script.sh`, on a pour `script.sh` les informations suivantes

```bash
-rw-r--r--  1 fxjollois  staff  61 14 oct 19:08 script.sh
```

- Premier caractère : `-` fichier ou `d` répertoire
- 3 triplets de trois caractères donc :
    - Chaque triplet correspond dans l'ordre à 
        1. Propriétaire
        2. Groupe
        3. Public
    - Chaque caractère d'un triplet correspond à
        - `r` : droit en lecture (`-`sinon - assez rare)
        - `w` : droit en écriture (`-` sinon)
        - `x` : droit d'exécution (`-`sinon)

Traduction : `-rw-r--r--` = fichier non exécutable que tout le monde peut lire, mais que seul le propriétaire peut modifier. 

---

## Modification des droits

- [`chmod`](https://manpages.ubuntu.com/manpages/jammy/en/man1/chmod.1.html) : permet de modifier les droits

De manière spécifique : 

- dans l'ordre
    1. à qui on ajoute (`u` pour utilisateur, `g` groupe, `a` tout le monde)
    2. si on ajoute `+?` ou on enlève `-`
    3. le droit 
- si personne pour `r` ou `x` : pour tout le monde

```bash
$ chmod u+x fichier
$ chmod g-w fichier
```

---

## Modification des droits

- [`chmod`](https://manpages.ubuntu.com/manpages/jammy/en/man1/chmod.1.html) : permet de modifier les droits

De manière globale : 

- Un droit = une valeur (en puissance de 2)
    - `r` = 4, `w` = 2, `x` = 1
- Une configuration = la somme des valeurs
    - `r--` = 4, `r-x` = 5, `rwx` = 7, ...
- Un triplet de valeur (entre 0 et 7) = une liste de droit
    - `600` = lecture/écriture pour le propriétaire, rien pour les autres
    - `755` = lecture/exécution pour tous, avec écriture pour propriétaire
    - ...

```bash
$ chmod 600 fichier
$ chmod 755 fichier
```

---

## Exécution

- Pour exécuter un script, il faut qu'il soit donc **exécutable**

- Première chose à faire, une fois le script créé : ajoutez le droit d'exécution

```bash
$ touch script.sh # fichier vide
$ chmod +x script.sh # par exemple
```

- Faites `nano script.sh` pour écrire dedans les instructions de la slide 3

- Une fois qu'il est exécutable et que le contenu l'est aussi, on exécute ainsi

```bash
$ ./script.sh
```

---

## Interaction avec l'utilisateur

- [`read`](https://manpages.ubuntu.com/manpages/jammy/en/man1/read.1plan9.html) : lit les valeurs entrées au clavier et les stocke dans une variable

```bash
#!/bin/bash
echo "Votre nom :"
read var
echo Bonjour $var
```

- Paramètre `-p` permettant d'afficher le texte

```bash
#!/bin/bash
read -p "Votre nom :" var
echo Bonjour $var
```

---

## Un peu plus loin sur les variables

- Caractères spéciaux : `$`, `*`, `?`, `#`, `|`, `[]` et `{}`
    - `\` : Annulation de leur effet
    - Double quotes `""` : Annulation de l'effet de la plupart des caractères (sauf `$`, `\` et `|`)
    - Simple quotes `''` : Annulation de l'effet de toutes, sauf `\`

```bash
#!/bin/bash
# Ceci est un commentaire
VAR="vous"
echo Bonjour $VAR   # -> Bonjour vous
echo Bonjour \$VAR  # -> Bonjour $VAR
```

- Limitation de la variable avec `{}`

```bash
#!/bin/bash
USER="fxj"
echo "Dossier personnel : /home/${USER}/Documents/"
```

---

## Affectation de valeurs à une variable

- Toute variable est une chaîne de caractères

```bash
a=12
b=$a+2
echo a=$a, b=$b # Affiche a=12, b=12+2
```

- Evaluation d'une expression **entière** avec `((...))` 
    - `++` et `--` possible (incrémentation positive ou négative)

```bash
a=12
(( b=$a+2 ))
echo a=$a, b=$b # Affiche a=12, b=14
```

- `let` permet d'affecter aussi des valeurs (en évaluant si calcul)

```bash
let a=12
let b=$a+2
echo a=$a, b=$b # Affiche a=12, b=14
```

---

## Variables du script

- `$0` : Nom du script
- `$1`, `$2`, ... : premier, deuxième, ... paramètre de la ligne de commande 
- `$*` : Tous les paramètres dans une seule chaîne
- `$@` : Tous les paramètres dans une liste
- `$#` : Nombre de paramètres sur la ligne de commande
- `$-` : Options du shell
- `$?` : Code de retour de la dernière commande
- `$$` : PID du shell
- `$!` : PID du dernier processus lancé en arrière-plan
- `$_` : Dernier argument de la commande précédente

---

## Variables d'environnement

- [Variables](https://doc.ubuntu-fr.org/variables_d_environnement) connues dans `bash` (créées au lancement de la machine ou au lancement d'une application)
    - `$PATH` : liste des chemins où chercher les exécutables
    - `$USER` : nom de l'utilisateur
    - `$HOME` : répertoire de base de l'utilisateur
    - `$LANG` : langue du terminal
    - ...

- [`printenv`](https://manpages.ubuntu.com/manpages/jammy/en/man1/printenv.1.html) : Liste de toutes les variables 

```bash
$ printenv
```

---

## Structures conditionnelles - `if`

- Utilisation des opérateurs `if`, `then`, `else` et `fi` pour terminer
    - Existence de l'opérateur `elif` pour enchaîner plusieurs conditions et expressions à réaliser
    - Conditions à mettre entre `[]`, voire `[[]]`

```bash
if [ condition ]; then
    # lignes de commandes
elif [ condition ]; then
    # lignes de commandes
else
    # lignes de commandes
fi
```

- Plusieurs opérateurs de [`test`](https://manpages.ubuntu.com/manpages/jammy/fr/man1/test.1.html) existant
    - Comparaisons de valeurs : `=`, `!=`, `-eq`, `-ne`, `-ge`, `-gt`, `-le`, `-lt`
    - Opérateurs logique : `-a` (et), `-o` (ou), `!` (non)
    - Existence : `-e` fichier existe, `-d` répertoire existe...
    - Taille : `-n` (ou `-z`) chaîne de taille nulle
    - ...

---

## Structures conditionnelles - `case`

- Utilisation des opérateurs `case`, `in` et `esac` pour finir
    - Finir les commandes avec `;;`
    - Choix possible suivi de `)` puis des lignes à exécuter
        - opérateur `|` pour combiner plusieurs choix possibles sur une ligne
    - Choix par défaut `*)`

```bash
case $var in
    valeur1)
        # lignes de commandes
    valeur2)
        # lignes de commandes
    valeur3)
        # lignes de commandes
    ...
    *)
        # lignes de commandes si rien ne correspond
esac
```

---

## Structures itératives - `for`

- Utilisation des opérateurs `for`, `in`, `do` et `done`

- Possibilité de définir une liste de `a` à `b` avec `{a..b}`
    - ex : `{0..5}` pour aller de 0 à 5

```bash
for variable in liste ; do
    # lignes de commandes
done
```

- Possibilité d'utiliser l'écriture de `ls` pour naviguer dans les fichiers et répertoires
    - Recherche dans le répertoire de lancement du script par défaut

```bash
for f in pattern ; do
    # lignes de commande
    # $f représente chaque fichier
done
```

---

## Structures itératives - `while` et `until`

- Utilisation des opérateurs `while`/`until`, `do` et `done`
    - `while` : continue si la condition est vraie
    - `until` : continue si la condition est fausse

- Opérateurs `break` pour stopper la boucle et `continue` pour la reprendre


```bash
while [ conditon ] ; do
    # lignes de commande
    # modification à faire pour que la condition évolue, sinon boucle infinie
done
```

```bash
until [ conditon ] ; do
    # lignes de commande
    # modification à faire pour que la condition évolue, sinon boucle infinie
done
```

---

## Fonctions

- Bloc d'instructions déclaré avec `function` (ou non)
    - à écrire avant leur appel
    - définissable partout (même dans un sous-bloc de type `for` ou `if`)

```bash
function f(){
    # lignes de commande
}
f() {
    # lignes de commande
}
```

- Déclarable sur une seule ligne, avec `;` après chaque instruction

---

## Paramètres de fonction

- Pas de définition des paramètres dans les `()`
    - Et appel sans `()`

- Utilisation, comme pour le script, des variables `$1`, `$2`, ...
    - `$n` dans une fonction référence le n<sup>ième</sup> paramètre de cette fonction, pas du script
    - sauf `$0` : dans une fonction, reste le nom du script lancé

```bash
f() {
    echo $1
}
f 12            # Affichera 12 donc
```

---

## Manipulation de chaînes (dans une variable)

- Longueur de la chaîne : `${#var}`

```bash
a=Bonjour
echo ${#a}      # Affiche 7
```

- Extraction de caractères d'une chaîne : `${var:deb:lon}`
    - Premier caractère à la position 0
    - `${var:deb}` pour avoir de `deb` jusqu'à la fin
    - `${var::lon}` pour avoir du début sur `lon` caractères

```bash
a=Bonjour
echo ${a:1:3}   # Affiche onj
echo ${a:4}     # Affiche our
echo ${a::4}    # Affiche Bonj
```

---

## Manipulation de chaînes (dans une variable)

- Extraction à partir d'un pattern : `${var#pattern}`
    - Premier élément correspondant pris en compte
        - `##` : pour chercher le dernier élément correspondant
    - `*` : de 0 à n caractères (comme dans `ls`)
    - `?` : un seul caractère (idem)
    - `[]` : plage
    - `{e1,e2,...}` : liste d'éléments

```bash
a=Bonjour
echo ${a#Bon}       # Affiche jour
echo ${a#*n}        # Affiche jour (à partir du premier n)
echo ${a#?o}        # Affiche njour (car seconde lettre = o)
echo ${a#*o}        # Affiche njour (à partir du premier o)
echo ${a##*o}       # Affiche ur (à partir du second o)
```

---

## Manipulation de chaînes (dans une variable)

- Remplacement d'une sous-chaîne par une autre dans une chaîne : `${var/pattern/remp}`
    - `//` à la place du premier `/` pour remplacer toutes les occurences (uniquement la première sinon)
    - `pattern` peut donc avoir les caractères spéciaux `*`, `?`, ...
    - Si pas de remplacement, suppression de la sous-chaîne
    - `#` à mettre en début de pattern pour regarder le début de la chaîne uniquement
    - `%` à mettre en début de pattern pour regarder la fin de la chaîne uniquement

```bash
a=Bonjour
echo ${a/jour/soir}     # Affiche Bonsoir
echo ${a/o/O}           # Affiche BOnjour
echo ${a//o/O}          # Affiche BOnjOur
echo ${a/o}             # Affiche Bnjour
echo ${a//o}            # Affiche Bnjur
```

---

## Boucles sur une chaîne de caractères

- Si espace présent dans la chaîne, boucle sur chaque mot

```bash
a="Bonjour Bonsoir"
for m in $a ; do
    echo m=$m           # Affiche Bonjour puis Bonsoir
done
```

- Si autre séparateur (par exemple `,`), on peut remplacer par un espace

```bash
a=Bonjour,Bonsoir
for m in ${a//,/ } ; do
    echo m=$m           # Affiche Bonjour puis Bonsoir
done
```


---

## Commande `shift`

- Décale les paramètres vers la gauche, en supprimant le premier

```bash
while [ -n "$1" ] ; do
    echo Paramètre : $1
    shift
done
```

- Test possible sur le nombre de paramètres (restant donc) avec `$#`

```bash
while [ $# -ne 0 ] ; do
    echo Paramètre : $1
    shift
done
```

---

## Tableaux

- Déclaration d'un tableau avec `()` (éléments séparés par un espace)

- Indexation avec `[]`
    - `@` : tous les éléments
    - Affectation possible avec indexation (sans consécutivité obligatoire)

```bash
a=( un deux trois 4 )
echo ${a}           # Affiche un
echo ${a[@]}        # Affiche un deux trois 4
echo ${#a[@]}       # Affiche 4 (taille du tableau)
echo ${a[2]}        # Affiche trois (3ème élément)
a[10]=dix
echo ${a[@]}        # Affiche un deux trois 4 dix
echo ${a[10]}       # Affiche dix
echo ${a[5]}        # Affiche ligne vide
```
---

## Codes d'erreur en sortie

- Ajout d'un code de sortie à la fonction `exit`
    - Uniquement entre 0 et 255
    - Codes à définir et indiquer dans la partie commentaires du script

- Très utile lorsqu'on fait un code compliqué

- Par convention : `0` indique une sortie sans erreur

- Codes réservés : `1`, `2`, `126`, `127`, `128`, `130`, `255`


```bash
# lignes de commande
if [ condition_erreur ] ; do
    exit 1  # Dire à quoi cela correspond (mettre un message d'erreur est un plus mais pas toujours bon à faire)
fi
# ...
exit 0
```

---

## Structuration classique d'un script

1. `shebang`
1. Commentaires introductifs au programme
    - Détail du fonctionnement
    - Présentation des paramètres du script
1. Gestion de l'appel
    - Test que tout est ok (sortie avec erreur sinon)
    - Paramètres présents ? bien écrits ? ...
1. Fonction(s) utile(s)
    - Définition des fonctions servant dans le script
1. Corps principal
    - Coeur du script
1. Fin
    - Ecriture de fichiers et/ou affichage dans la console
    - Sortie du programme avec `exit`


