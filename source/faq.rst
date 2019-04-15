Questions et Problèmes Fréquents
================================

Installer un Plugin/Thème
-------------------------

Via le panel admin
^^^^^^^^^^^^^^^^^^^^^
**Installer un Thème**

Vous devez préalablement allez sur la page des Thème et être connecté à votre site pour accéder à la page **"/admin/theme"** et faire les manipulations suivantes :

*   Repérez le Thème voulu
*   Cliquez sur le bouton **"Installer"**
*   Actualisez la page, et cliquer sur le bouton **"Activer"**
*   Pour personnaliser votre Thème il suffit de cliquer le cliquer sur le bouton **"Personnaliser"**

**Installer un plugin**

Vous devez préalablement allez sur la page des Thème et être connecté à votre site pour accéder à la page **"/admin/plugin"** et faire les manipulations suivantes :

*   Repérez le Plugin voulu
*   Cliquez sur le bouton **"Installer"**
*   Actualisez la page, allez sur la page pour personnaliser la barre de navigation **"/admin/navbar"**
*   Cliquez sur **"Ajouter un lien"**
    *   Et ensuite cliquer sur **"Type"** et choisir **"classique"**
    *   Puis cliquer sur **"Plugin"** et chosir votre plugin

Via Github
^^^^^^^^^^
Certains Plugins ou Thèmes ne sont pas présents sur la panel-admin, vous pouvez donc allez sur le `Github <https://github.com/MineWeb>`__ de Mineweb.

**Installer un Thème**

Vous devez préalablement allez sur la page Github de votre thème mineweb et faire les manipulations suivantes :

*   Cliquez sur **"Clone or download"** présent sur la page de votre Thème
*   Téléchargez et enregistrez le ZIP, puis extrayez le
*   Renommez le dossier **"Theme-"Nom du Thème"-master"** par **"Nom du Thème"**, respectez tout de même les majuscules
*   Déplacez le dossier dans votre FTP à l'adresse **"/app/view/themed"** et de mettre les permissions **"777"** à tout le dossier dossier en récursif

**Installer un plugin**

Vous devez préalablement allez sur la page Github de votre plugin mineweb et faire les manipulations suivantes :

*   Cliquez sur **"Clone or download"** présent sur la page de votre Plugin
*   Téléchargez et enregistrez le ZIP, puis extrayez le
*   Renommez le dossier **"Plugin-"Nom du Plugin"-master"** par **"Nom du Plugin"**, respectez tout de même les majuscules
*   Déplacez le dossier dans votre FTP à l'adresse **"/app/Plugin"** et de mettre les permissions **"777"** à tout le dossier en récursif
*   Supprimez tous les fichiers dans le dossier **"/app/tmp/cache"** présent dans votre FTP

Si vous n'y arrivez pas vous pouvez rejoindre le `Discord <https://discordapp.com/invite/3QYdt8r>`__


Erreur 500 ou Erreur Interne
----------------------------
Pour corriger l'erreur 500 sur votre cms faites **toutes** les étapes :

*   Supprimez le contenu du fichier **"/app/tmp/"**

Si ca ne marche toujours pas :
 
*   Réeffectuez la manipulation qui a provoqué l'erreur
*   Mettez en ligne sur Pastebin le fichier **"/app/tmp/logs/error.log"** afin de donner le lien au support dans le chat du `Discord <https://discordapp.com/invite/3QYdt8r>`__


Pour éviter les confusions ou éviter toute erreur de votre part, merci de bien vouloir lire toute la documentation avant de demander de l'aide au support et pour être plus efficace.


Est ce qu'il faut garder le copyright
-------------------------------------
**Copyright sur le CMS**

Une question très légitime après le passage de MineWeb en open-source est ce qu'il faut garder le copyright de MineWeb ainsi que celui du Thème en bas du site. Il y a donc 2 manières dont les personnes voient le copyright :

*   Le copyright fait tache sur mon site
*   Le copyright est là pour le respect des développeurs qui ont conçu mon site

MineWeb est un CMS dit **Open Source**, cela vous autorise à utiliser le CMS à des fins commerciales, à modifier le code, le design, tout en restant gratuit pour vous. 
Toutefois vous avez **l’obligation de garder les noms des auteurs et du CMS** selon les règles établies par le fondateur du CMS et auteurs tiers (pour les thèmes & plugins). C’est grâce à cela que le CMS permet d’exister en restant gratuit. Cela agrandit la communauté du CMS, ce qui permet à de tiers développeurs d’agrandir par exemple le market.

MineWeb comporte actuellement une trentaine de thèmes et une trentaine de plugins développés par des développeurs de la communauté qui comme vous aussi ont voulu ajouter des fonctionnalités.
Si vous ne désirez pas laisser le copyright, nous ne pouvons pas vous forcer. Personne ne vous empêche de voler à la boutique du coin mais pourtant vous ne le faites pas puisque le vol est interdit.

**Si vous le faites tout de même**

*   C’est que vous ne respectez pas le travail d’autrui
*   Et personne ne sera près à vous aider sur ce Discord


Page introuvable
----------------
- Lorsque vous mettez un dossier a la racine du CMS vous avez une erreur de page introuvable suivez le PDF disponible `ici </files/Webroot-Helper.pdf>`__

Mineweb sous NGINX
------------------
Pour l'installation de mineweb avec nginx utilisez la vhost en suivant `ce lien <https://gist.github.com/Suertzz/52cbef8471d42bcb026fc0dd3a2ea2a8>`__.

Si vous avez le js ne load pas lors de l'installation 

.. image:: https://pics.suertzz.fr/11855O3e5r.png

.. admonition:: exécutez ceci

	sed -i -e "s/app\/webroot//g" /var/www/html/app/View/Install/first.ctp

Si vous avez une 502 bad gateway pokez @suertz sur discord 

(nginx ne parvient pas à communiquer avec php-cgi, ligne 13 dans la vhost voir `ce lien <https://www.digitalocean.com/community/questions/nginx-error-111-connection-refused>`__.

