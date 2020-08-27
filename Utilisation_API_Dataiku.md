Utilisation de l’API publique Dataiku

# Utilisation de l’API publique Dataiku

## 1) Introduction 

Il est possible de communiquer à l’API dataiku qui se trouve à l’adresse :
http://dataiku.din.developpement-durable.gouv.fr/

Il est possible d’effectuer toutes les opérations disponibles sur l’interface (créer des datasets, interagir avec, lancer des scénarios, etc).

La description de l’API et des possibilités est disponible à cette adresse (version 7 de dataiku) :
https://doc.dataiku.com/dss/7.0/publicapi/index.html (description)
https://doc.dataiku.com/dss/api/7.0/rest/  (doc API)

## 2) API key

Pour effectuer des requêtes, il faut créer une API key dans son espace profil sur dataiku DSS:
- aller dans « Security », onglet « API keys »  puis bouton « + NEW API KEY » 

Il faut ensuite aller régler les droits toujours dans l’onglet « API keys » pour limiter ou augmenter les possibilités (droit en écriture notamment désactivé par défaut).

## 3) Communiquer avec l’API

Voici les requêtes identifiées pour la mise en place de l’interface web.
Il faut remplacer les données entre accolades par les valeurs réelles.

### a) Lancer un scénario

Méthode : POST
URL : http://dataiku.din.developpement-durable.gouv.fr/public/api/projects/{projectKey}/scenarios/{scenarioId}/run

### b) Supprimer un fichier dans un folder

Méthode : POST
URL : http://dataiku.din.developpement-durable.gouv.fr/public/api/projects/{projectKey}/managedfolders/{folderId}/contents/{path}

### c) Upload un fichier dans un folder

Méthode : POST
URL : http://dataiku.din.developpement-durable.gouv.fr/public/api/projects/{projectKey}/managedfolders/{folderId}/contents/