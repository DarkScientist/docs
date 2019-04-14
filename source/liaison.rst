
Lier serveur-site
-----------------
.. warning:: **Le plugins est compatibles à partir de la version 1.8**

.. admonition:: **Type de connexion**
   
   - **Par Défaut** : connexion à un serveur lié avec le plugin `Bukkit/Spigot <https://github.com/MineWeb/ServerBridge/raw/master/mineweb_bridge-2.0.0.jar>`_, permet l’utilisation de toutes les fonctionnalités du CMS (**boutique, classement factions, vote**…) 

   - **Par Rcon** : connexion à un serveur lié avec le Rcon. Pour la liaison d'un serveur Bungee, utilisez le Plugin Bungeecord RCON, permet l’utilisation de toutes les fonctionnalités du CMS mais pas du classement factions 
   
   - **Par Ping** : connexion à un serveur sans plugin, permet uniquement d’avoir le nombre de joueurs en ligne et le nombre de joueurs maximums (la **boutique** et le **classement factions** ne **pourront pas** être utilisés avec ce type de connexion)

Configuration préalable
~~~~~~~~~~~~~~~~~~~~~~~
Rendez-vous sur la page de liaison site-serveur sur le panel admin de votre CMS. Vous devez dans un premier temps configurer le temps d’exécution maximum (appelé aussi timeout), il est conseillé de mettre 1 (seconde).

.. image:: https://docs.mineweb.org/images/server_timeout.png

.. note:: Vous avez à côté deux boutons pour désactiver la fonctionnalité (qui mettra automatiquement le statut du serveur à : éteint) si vous ne souhaitez pas utiliser la liaison site-serveur. Et un autre bouton pour activer/désactiver le cache sur la “bannière” (permet que le message affiché sur le site (joueurs connectés, MOTD…) soit stocké pendant quelques minutes permettant d’éviter la surcharge de commande au serveur).

Liaison à un serveur (par défaut)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Maintenant nous allons lier votre serveur Minecraft au **CMS**. Pour cela vous devez avoir installé sur votre serveur le plugin MineWeb disponible à `cette adresse <https://github.com/MineWeb/ServerBridge/raw/master/mineweb_bridge-2.0.0.jar>`_

Une fois le plugin téléchargé, placez-le dans votre dossier ``plugins`` de votre serveur et **redémarrez celui-ci**.
Vous n’avez pas à toucher à la configuration du plugin.

Maintenant que vous avez configuré le serveur vous pouvez ajouter un serveur et remplir les informations nécessaires :

- ``Type de la connexion`` mettez **Par défaut**
- ``Nom`` par le nom affiché.
- ``IP`` par l’ip (ou domaine) sans le port.
- ``Port`` par le port de votre serveur (25565 par défaut si vous n’avez pas de port).

Cliquez ensuite sur **Connexion** pour tester la connexion, si celle-ci échoue, rendez-vous sur `cette section <https://docs-mineweb.tk/docs.html#la-connexion-echoue>`_

.. admonition:: **Port customisé** 
   
   Vous pouvez également configurer un port personnalisé si vous ne souhaitez pas utiliser le port minecraft de votre serveur. Pour cela, assurez-vous d'avoir un port disponible et ouvert et effectuez la commande **/mineweb port <port>**.

.. admonition:: **ProtocolLib** 
   
   Si vous avez ProtocolLib et que le plugin produit une erreur à cause du plugin de MineWeb vous pouvez utiliser `cette version <https://github.com/MineWeb/ServerBridge/raw/no-injector/mineweb_bridge-2.0.0.jar>`_. Vous devez obligatoirement configurer un port disponible et ouvert à l'aide la commande **/mineweb port <port>**.

Liaison par RCON
~~~~~~~~~~~~~~~~
Vous n’avez pas besoin de plugin pour cette liaison. Le protocol RCON est disponible sur tous les serveurs minecraft et permet de communiquer avec le site. Pour utiliser ce protocol il vous faut le configurer dans votre server.properties :

- Passer enable-rcon à true
- Changer rcon.password par un mot de passe
- Changer rcon.port par un port disponible

Il vous suffit ensuite de configurer un serveur comme ceci depuis la page de liaison :

- ``Type de la connexion`` mettez **RCON**.
- ``Nom`` par le nom affiché.
- ``IP`` par l’ip (ou domaine) **sans le port**.
- ``Port`` par le port de votre serveur (25565 par défaut si vous n’avez pas de port).
- ``Port RCON`` par le port de RCON configureé (doit être **ouvert** et **disponible** bien sûr).
- ``Mot de passe RCON`` par le mot de passe RCON.

Cliquez ensuite sur **Connexion** pour tester la connexion.

Liaison par PING
~~~~~~~~~~~~~~~~
Vous n’avez pas besoin de plugin pour cette liaison, il vous suffit juste de configurer un serveur comme ceci depuis la page de liaison :

- ``Type de la connexion`` mettez **Ping**.
- ``Nom`` par le nom affiché.
- ``IP`` par l’ip (ou domaine) **sans le port**.
- ``Port`` par le port de votre serveur (25565 par défaut si vous n’avez pas de port).

Cliquez ensuite sur **Connexion** pour tester la connexion.

La connexion échoue
~~~~~~~~~~~~~~~~~~~
Dans un premier temps, vérifiez que vous n'avez pas d'erreur dans la console de votre serveur en rapport avec le plugin MineWeb.

Ensuite, essayez de **redémarrer votre serveur**.

Si la connexion échoue toujours, venez-nous voir sur `Discord <https://discordapp.com/invite/3QYdt8r>`_ avec un **maximum d'explications et d'informations**, et répondez à ces questions :

- Quelle IP avez-vous mis ?
- Quel port ?
- Aucune erreur dans la console ?
- Quelle version de Spigot avez-vous ?
- Avez-vous essayé de rédemarrer le serveur ?
- Fournissez-nous des **logs** de démarrage du serveur sur pastebin.com
- Fournissez-nous le fichier **mineweb.log** du plugin sur pastebin.com
