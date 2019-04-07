Introduction
========

**C'est quoi MineWeb ?**

MineWeb est un CMS. Un CMS est un système de gestion de contenu. Plus précisément il vous permet de vous créer rapidement et facilement un site complètement personnalisable. MineWeb est la version 2 de l'ancien CMS LapisCraft de Eywek. Celui-ci n'étant plus stable et mal développé (cf. raisons ici).

MineWeb est développé sous un framework PHP nommé CakePHP permettant un développement plus rapide, sécurisé et optimisé. Le projet a été lancé en 2015 en compagnie de Mac’ permettant de convenir entièrement à vos besoins.

Pré-requis
--------

Pour installer le CMS MineWeb votre hébergeur **doit** avoir :

- Version PHP supérieure ou égale à 5.6 et inférieure à 7.3
- PDO activé
- cURL activé
- Réécriture d'URL
- .htaccess activés
- La librairie GD2
- La possibilité d'ouvrir un zip
- La possibilité d'ouvrir un site à distance
- OpenSSL

Installation
========

**Informations**

Vous devez placer tout le contenu de l'archive téléchargée, sur votre hébergeur (les fichiers .DS_Store & \__MACOSX sont inutiles). Il faut ensuite appliquer les permissions 777 sur tous les fichiers en recursif (pour permettre les mises à jour). Puis rendez-vous sur http://{votre site}.fr

Étape 1 - Configuration de la base de données
-------
Vous devez avoir une page demandant vos identifiants de base de données, vous devez entrez ceux-ci et tester la connexion, puis il vous faudra cliquer sur un bouton qui installera la base de données automatiquement.

Étape 2 - Création de l'administrateur
-------

Voici la deuxième et dernière étape de l'installation du CMS, vous allez créer votre compte administrateur qui vous permettra d'accéder au panel admin du CMS. Vous avez juste à remplir les champs qui vous sont présentés et à soumettre vos informations en cliquant sur le bouton “Suivant”.

Installation terminée
-------

Une fois l'installation du CMS complétée vous pouvez passer à l'utilisation du CMS en lui-même. Pour configurer votre CMS il vous faut vous connecter en cliquant sur le bouton en haut à gauche de la barre de navigation. Vous cliquez sur connexion puis entrez vos informations pour vous connecter. Vous cliquez ensuite sur Panel administrateur, vous serez redirigé et vous pourrez ensuite cliquer sur Général puis Préférences générales.

Autres
-------
Si vous avez besoin d'aide, si vous rencontrez un problème non répertorié ici, vous pouvez nous contacter sur notre Discord.

Lier serveur-site
========

Compatibilité
-------
**Les plugins sont compatibles à partir de la version 1.8**

**Type de connexion:**
- Par Défaut : connexion à un serveur lié avec le plugin Bukkit/Spigot, permet l’utilisation de toutes les fonctionnalités du CMS (**boutique, classement factions, vote**…) 
- Par Rcon : connexion à un serveur lié avec le Rcon. Pour la liaison d'un serveur Bungee, utilisez le Plugin Bungeecord RCON, permet l’utilisation de toutes les fonctionnalités du CMS mais pas du classement factions 
- Ping : connexion à un serveur sans plugin, permet uniquement d’avoir le nombre de joueurs en ligne et le nombre de joueurs maximums (la **boutique** et le **classement factions** ne **pourront pas** être utilisés avec ce type de connexion)

Configuration préalable
-------
Rendez-vous sur la page de liaison site-serveur sur le panel admin de votre CMS. Vous devez dans un premier temps configurer le temps d’exécution maximum (appelé aussi timeout), il est conseillé de mettre 1 (seconde).

![Drag Racing](https://docs.mineweb.org/images/server_timeout.png)
