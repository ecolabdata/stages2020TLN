FAQ Dataiku

# 1) Comment mettre un titre ou nommer une recipe?

On ne peut pas avoir un titre quis oit visible directement dans le flow. Par contre, on peut ajouter une « description courte » qui sera afficher au survol de la recipe et celle-ci aura un petit « i » indiquant qu’une description est présente.

Pour le faire : 
1) cliquer sur le recipe concerné
2) Aller dans l’onglet « Summary »
3) cliquer en dessous du titre sur « Create a short description » puis enter le texte voulu


________

# 2) Comment regrouper des recipe/dataset ensemble (pour notamment améliorer la visibilité du flow)?

Cette feature n’est pas encore disponible, mais il sera bientôt possible de mettre certaines recipe dans des « zones » permettant de faire des groupes. Actuellement, il est possible de mettre des « tags » sur les recipes et de mettre en évidence les récipes ayant certains tags.

Pour le faire :
1) cliquer sur la recipe
2) cliquer sur « Tag » dans le volet droit de l’écran
3) cliquer sur les tags souhaités et/ou créer les tags souhaités


________________


# 3) Comment partager un projet pour le rendre visible par d’autre utilisateurs ou groupes ?

Il suffit d’aller sur le projet en question puis dans l’onglet « Security ».
Ensuite dans « Permissions », il est possible d’autoriser des groupes et de choisir leur droit (ecriture, lecture, etc)


_____________


# 4) J’ai une erreur indiquant qu’un package n’est pas disponible alors qu’il est bien installé dans l’interface notebook / J’ai une erreur dans l’interface notebook qui semble être du à une version de python ou d’un package alors que je suis censé avoir la bonne version 

L’interface notebook (malgré l’affichage du l’environnement utilisé en haut à droite) utilise une environnement par défaut (python 2.7 ?). Il est possible de changer cet environnement en cliquant sur « kernel » puis sur « change kernel » et en sélectionnant l’environnement souhaité.


___________


# 5) Je n’ai pas l’affichage de toutes mes données lorsque je visualise mon dataset, pourquoi ?

L’affichage de données par DSS permet de restreindre l’affichage pour limiter la mémoire utilisée.
Il y a plusieurs options de limitations :

1) la première qui permet de limiter le nombre d’entrées et de configurer le « sample » (nombre fixe, pourcentage du dataset, tirage aléatoire, etc)

2) la deuxieme option permet de limiter la mémoire occupé par le sample en indiquant une quantité de mémoire maximale.

Pour modifier les options par défaut : 
- Cliquer sur le dataset
- Aller dnas l’onglet « Explore »
- Cliquer sur « Configure Sample »
- Modifier « Nb. records » et/ou « Max memory usage (MB) »

___________

# 6) Comment utiliser des exécutables externes ou upload des dossiers/fichiers pour les réutiliser sur DSS ?

Il ne semble pas possible d’ajouter directement des dossier dans DSS.

Pour les fichiers, il y a plusieurs possibilités :

1) upload des fichiers dans un dataset en se souvenant de l’option choisie dans « store on »(un dataset pouvant accueillir plusieurs fichiers)


Les fichiers sont accessibles au chemin suivant :
../../../../[type_de_folder]/[titre_du_projet]/datasets/[nom_dataset]/fichier_voulu


2) Créer un « folder » Dataiku et y mettre les fichiers en se souvenant de l’option choisie dans « store on ».


Les fichiers sont accessibles au chemin suivant :
../../../../[type_de_folder]/[titre_du_projet]/[identifiant_folder]/fichier_voulu


où 

[type_de_folder] est soit :
-‘uploads’ si on a choisi le « store on » par « defaut »
-‘managed_datasets’ si on a choisi le « store on » par « filesystem_managed »
- ‘managed_folders’ si on a choisi le « store on » par « filesystem_folders »


[titre_du_projet] est le nom du projet en majuscule comme entré à l’origine (donc en cas de changement de nom, il faut quand même mettre l’ancien titre).

[nom_dataset] est le nom indiqué lors de la création du dataset (en haut à droite).

[identifiant_folder] est une chaine de caratère identifiant un folder. Il peut être trouvé de 2 façons :
- en créant un code recipe python prenant en entrée le folder. L’identifiant sera indiqué dans le code généré comme argument de la fonction chargeant le dossier.
- en naviguant « à la main » dans l’arborescence de dataiku (au travers d’un notebook et de la fonction os.listdir(path) par exemple)


Exemple :

(contexte: nous sommes dans un projet intitulé « Exemple_upload_file » )

- Je crée un dataset en cliquant sur « + DATASET » puis sur « upload your file »
- J’indique le nom du dataset, ici « exemple1 »
- J’ajoute les fichiers que je souhaite utiliser, ici un fichier « test1.txt »
- Je choisis l’option de stockage, ici celle par défaut « Defaut (in DSS data dir.) » et je clique sur « CREATE »
- Je retourne dans mon flow, et je crée une recipe python sans mettant en entré n’importe qu’elle dataset (celui créer ou un autre peu importe) et en mettant n’importe qu’elle dataset en sortie.
- Je supprime tout le code et j’entre :
import os
os.listdir(‘../../../../uploads/EXEMPLE_UPLOAD_FILE/datasets/exemple1’)

Ainsi je peux observer la sortie qui contient la liste des fichiers de mon datatsets, ici seulement « test1.txt »

Pour utiliser ce fichier (par exemple pour ‘louvrir et el lire en python), il suffira d’utiliser son ptah qui est « ../../../../uploads/EXEMPLE_UPLOAD_FILE/datasets/exemple1/test1.txt »


________________


# 7) Comment utiliser les stopwords ntlk / J’ai une erreur lorsque je tente d’utiliser les stopwords nltk

- il faut faire attention au paramètre (qui est un nom de fichier) donné à la fonction nltk.corpus.stopwords.words(). En effet, il y a parfois des majuscules sur des codes disponibles en ligne (ou dans des exemples) et cela ne fonctionne pas. 
Par exemple, pour les stopwords français, il faut faire « nltk.corpus.stopwords.words(‘french’) » (et non ‘French’).

La liste des langues dispos (pour les stopwords) est disponible dans ce dossier :
/home/dataiku/nltk_data/corpora/stopwords/french
(ou en python : os.listdir('/home/dataiku/nltk_data/corpora/stopwords') )

