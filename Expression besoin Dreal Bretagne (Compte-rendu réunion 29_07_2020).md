Expression besoin Dreal Bretagne (Compte-rendu réunion 29/07/2020)

Nous avons repris dans l’ordre les éléments du document « Maquette de l’outil » qui donnait plusieurs pistes de réflexions.


# 1) Problématique sur la similitude entre des études d’un même bureau d’étude


Le calcul de similitude s’effectue surtout en prenant en compte le vocabulaire utilisé et non la structure. De plus, il est possible de ne prendre en compte que certains types de mots comme les noms et les verbes (afin de réduire l’impact de l’utilisation de certains adverbes ou expression récurrente à un même bureau qui pourrait faire augmenter la similarité).

Dans tous les cas, nous allons voir les résultats de l’outil et modifier/ajouter des caractéristiques si ce biais est présent.


# 2) Temps de recherche de l’algorithme 


- Premier test effectué sur une base de 129 études.
- temps d’analyse d’une nouvelle étude moins d’une minute
- il faut rajouter le temps d’envoyer le fichier pdf de l’étude (quelques secondes à quelques minutes)
- il faut rajouter le temps de conversion du fichier en texte (quelques minutes)

=> pas de résultat instantané, mais de l’ordre du quart d’heure donc exploitable d’après les retours Dreal.


# 3) Similitude sur certains critères


- titre : faire une première analyse de similarité en ne prenant que les titres (souvent composé du nom de l’entreprise, de la zone et du type de projet)

- verbes au conditionnel  & mots/expressions « warnings »: faire une analyse de similarité sur les verbes au conditionnel & la présence/absence de mots/expressions « warnings »

- localité : voir partie « filtres »


# 4) Informations dans l’avis


- rajouter dans la sortie de l’outil une colonne indiquant la présence ou non de certains termes dans l’avis => pas prioritaire car l’avis étant un document assez court et léger, on peut aller voir assez rapidement son contenu


# 5) Ajout d’informations pour les études


Discussion autour de la possibilité d’ajouter (par les utilisateurs) des informations aux différents dossiers pour pouvoir filtrer plus tard sur ces nouvelles informations:
- compliqué car projet un peu différent plutôt orienté « application de moteur de recherche » qui utiliserai d’autres technologies (elasticsearch)


# 6) Filtrages avant (ou après) calcul de similarité 


- localité :  permettre le filtrage selon le département (donnée accessible facilement). Possibilité d’amélioration (non prioritaire) en exploitant la ville et/ou les coordonnées gps (disponible pour environ la moitié des projets sur projets-environnements)

- non prise en compte des annexes : voir partie « fiches synthétique » 


# 7) Association entre mots clefs


Nous n’avons pas saisi ce qui était entendu par « informations associés à des mots » ou par « caractériser des associations ». A éclaircir avec Fabien Chapouillie


# 8) Fiche synthétique


- extraction du sommaire : le but est d’extraire les pages de l’études contenant le sommaire pour avoir une première lecture rapide sur le contenu de l’étude pour faire gagner du temps au départ (en ne chargeant pas la fichier entier). Une amélioration possible (non prioritaire) est d’extraire un sommaire « sémantique » basé sur le contenu de l’étude (peut aussi être utile si l’étude d’impact n’a pas du tout de sommaire)

- extraction du Résumé Non Technique (RNT) et/ou des annexes (compliqué car) :
    * certains documents pdf ne sont que l’étude d’impact elle-même et les autre documents (RNT et annexes) sont dispersés dans des dossiers (et donc la structure du dossier complique l’automatisation)
    * certains document pdf contiennent l’étude d’impact et le RNT/annexes. L’extraction de ces différentes parties est alors une problématique de Traitement du Langage compliqué

=> la plupart des documents utilisés seront seulement l’étude d’impact mais certains documents auront aussi le RNT/annexes compris. Nous vérifierons la qualité des résultats malgré cela.

- présence de mots/expressions warnings : ajouter une colonne au résultat pour indiquer la présence ou non des certains mots/expressions dans l’étude retournée.

- mots clefs associés à l’avis : cf partie 4) « Informations dans l’avis »


# 9) Direction pour la suite


Nous allons essayer le prototype sur des études d’impact en cours pour avoir une première impression sur les résultats

