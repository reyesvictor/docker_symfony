# docker_symfony

Résumé extrait du pdf du sujet du projet EPITECH. Introduction à Docker

## Compétences
Lors de ce projet vous devrez utiliser et maitriser les outils suivants:
• Docker
• Dockerfile
• Docker-compose

## CONTENEURS POUR LE PROJET SYMFONY
Vous devez créer ici au moins 3 conteneurs.

### MySQL
Le conteneur pour la base de données de votre (ou vos) projet(s) Symfony.
Créer une ‘base de donnée’ avec un utilisateur et un mot de passe.
Le port devra être exposé et un volume créé pour garder les données.

### PHP
Ce conteneur vous permettra de déployer votre projet Symfony.
Pour que tout fonctionne correctement, vous devrez créer un volume pour votre projet, exposer le bon port et si vous voulez bien faire les choses, créer un volume pour les logs.

### Nginx
Ce conteneur sera lié avec votre projet PHP, et exposera votre application Symfony.
Vous devrez exposer le port 80, créer un volume qui contiendra les informations comme le nom de domaine et un autre pour les logs nginx.

### ElasticSearch
Vous aurez besoin d’exposer des ports et de créer un volume qui vous permettra de garder les données
d’ElasticSearch.


### LogStash
Ce conteneur devra être lié à ElasticSearch, vous devrez exposer un port et créer un volume.
Attention, contrairement à ElasticSearch où vous n’aurez pas grand chose à faire si ce n’est le conteneur; là vous devrez en plus créer un fichier de configuration pour LogStash.
De plus, pour que vous puissiez récupérer les fichiers de logs et les envoyer à LogStash, vous devrez installer et configurer Filebeat (vous pouvez passer par un conteneur ou bien directement sur votre système).


### Kibana
Dernier élément de la stack ELK, ce conteneur vous permettra de visualiser vos logs !
Vous devrez lier le conteneur ElasticSearch et exposer le port nécessaire pour atteindre l’application web.
