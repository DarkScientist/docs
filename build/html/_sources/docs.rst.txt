Introduction
------------

C'est quoi MineWeb ?
~~~~~~~~~~~~~~~~~~~~
MineWeb est un **CMS**. Un CMS est un système de gestion de contenu. Plus précisément il vous permet de vous créer rapidement et facilement un site complètement personnalisable. MineWeb est la version 2 de l'ancien CMS **LapisCraft** de Eywek. Celui-ci n'étant plus stable et mal développé (cf. raisons `ici <https://eywek.fr/lc-explications.pdf>`__).

MineWeb est développé sous un framework PHP nommé **CakePHP** permettant un développement plus **rapide**, **sécurisé** et **optimisé**. Le projet a été lancé en 2015 en compagnie de **Mac’** permettant de convenir entièrement à **vos besoins**.

Pré-requis
~~~~~~~~~~~~~~~~~~~~
Pour installer le CMS MineWeb votre hébergeur **doit** avoir :

- Version PHP supérieure ou égale à 5.6 et inférieure ou égale à 7.3
- PDO activé
- cURL activé
- Réécriture d'URL
- .htaccess activés
- La librairie GD2
- La possibilité d'ouvrir un zip
- La possibilité d'ouvrir un site à distance
- OpenSSL

Pour plus de simplicité vous pouvez télécharger le **fichier de compatibilité** `ici <https://docs.mineweb.org/files/compatibilite.zip>`_. Vous avez juste à extraire cette archive sur votre FTP pour voir si votre hébergeur est compatible.

Installation
------------
.. note:: Vous devez placer tout le contenu de l'archive téléchargée, sur votre hébergeur (les fichiers .DS_Store & \__MACOSX sont inutiles). Il faut ensuite appliquer les permissions **777** sur tous les fichiers en **recursif** (pour permettre les mises à jour). Puis rendez-vous sur http://votresite.fr

Étape 1 - Configuration de la base de données
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Vous devez avoir une page demandant vos identifiants de base de données, vous devez entrez ceux-ci et tester la connexion, puis il vous faudra cliquer sur un bouton qui installera la base de données automatiquement.

Étape 2 - Création de l'administrateur
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Voici la deuxième et dernière étape de l'installation du CMS, vous allez créer votre compte administrateur qui vous permettra d'accéder au panel admin du CMS. Vous avez juste à remplir les champs qui vous sont présentés et à soumettre vos informations en cliquant sur le bouton **“Suivant”**.

Installation terminée
~~~~~~~~~~~~~~~~~~~~~
Une fois l'installation du CMS complétée vous pouvez passer à l'utilisation du CMS en lui-même. Pour configurer votre CMS il vous faut vous connecter en cliquant sur le bouton en haut à gauche de la barre de navigation. Vous cliquez sur connexion puis entrez vos informations pour vous connecter. Vous cliquez ensuite sur **Panel administrateur**, vous serez redirigé et vous pourrez ensuite cliquer sur **Général** puis **Préférences générales**.

Lier serveur-site
-----------------
.. warning:: **Le plugins est compatibles à partir de la version 1.8**

.. note:: 
   **Type de connexion**:
   
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

.. note:: **Port customisé :** Vous pouvez également configurer un port personnalisé si vous ne souhaitez pas utiliser le port minecraft de votre serveur. Pour cela, assurez-vous d'avoir un port disponible et ouvert et effectuez la commande **/mineweb port <port>**.
.. note:: **ProtocolLib :** Si vous avez ProtocolLib et que le plugin produit une erreur à cause du plugin de MineWeb vous pouvez utiliser `cette version <https://github.com/MineWeb/ServerBridge/raw/no-injector/mineweb_bridge-2.0.0.jar>`_. Vous devez obligatoirement configurer un port disponible et ouvert à l'aide la commande **/mineweb port <port>**.

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

Créer un plugin
---------------
**Introduction**

Un plugin (aussi appelé *extension*), est un ensemble de **fichiers** qui sont ajoutés à votre CMS pour y ajouter plusieurs **fonctionnalités** ou modifier certains **comportements** par défaut. Différents plugins “officiels” sont *déjà disponibles* `ici <https://github.com/MineWeb?utf8=%E2%9C%93&q=Plugin-&type=&language=php>`__. D’autres peuvent être *développés par la communauté* et c’est le but de ce tutoriel.

Création
~~~~~~~~
**Création des fichiers/dossiers**

Dans un premier temps, il va falloir créer le dossier de votre plugin, ce dossier doit être créé dans le dossier `app/Plugin/`. Le nom du dossier doit être le nom de votre plugin.

Par **exemple** si je veux créer un plugin de **boutique**, je vais l’appeler : **Shop**.

Une fois ce dossier créé, il faut créer différents autres dossiers et fichiers :

- ``Config/``
- ``Controller/``
- ``Model/``
- ``View/``
- ``lang/``
- ``SQL/``

C’est tout pour les dossiers, il nous reste maintenant encore des fichiers à créer tels que :

- ``Config/bootstrap.php``
- ``Config/routes.php``
- ``config.json``

**Explications et configuration**

Maintenant que vous avez créé tous ces fichiers, nous allons passer à la configuration de votre plugin. Pour cela, ouvrez le fichier **config.json**, c'est dans ce fichier que toute la configuration sera située.

.. code-block:: none

   Configuration par défaut (à remplir)

.. code-block:: json

  {
  "name":"NAME",
  "author":"AUTHOR",
  "version":"1.0.0",
  "useEvents":false,
  "permissions" : {
    "available" : [],
    "default" : {
      "0" : [],
      "2" : []
    }
  },
  "requirements" : {
    "CMS" : "^1.7.0"
    }
  }
   
Maintenant, vous allez pouvoir configurer. Remplacez **NAME** par le *nom de votre plugin* et puis **AUTHOR** par votre pseudo.
Ensuite voici une explication des autres lignes :

- ``version`` : la version de votre plugin (**double**),
- ``useEvents`` : si votre plugin utilise les événements disponible sur le CMS (**boolean**),
- ``permissions`` : les permissions de votre plugin (voir plus tard) (**array**)
- ``requirements`` : les pré-requis de votre plugin : vous devez spécifier comme clé un autre ID de plugin (au format **auteur.slug**) ou CMS et comme valeur une version correcte (cf. le semantic versionning donc préfixée ou non par ^ / ~ / >= / <=). Si un des pré-requis n'est pas rempli, le plugin ne sera pas installé sur le CMS.

**Les liens de la barre de navigation**

Si votre plugin dispose d'une route publique (pouvant être accessible pour n'importe quel utilisateur) il peut être important de configurer lesquelles de ces routes peuvent être ajoutées sur la barre de navigation depuis le panel admin. Pour cela, il vous suffit d'ajouter la clé ``navbar_routes`` dans le fichier ``config.json``.
Cette clé doit contenir un objet avec comme clé le nom de la route et comme valeur la route.

.. code-block:: json

   {
	"name":"Boutique",
	"admin_menus": {},
	"navbar_routes": {
		"Boutique": "/shop"
	},
	"author":"Eywek",
	"version":"1.0.0",
	"useEvents":true,
	"permissions" : {
		"available" : [],
		"default" : {
			"0" : [],
			"2" : []
		}
	},
	"requirements" : {
		"CMS" : "^1.2.0"
	  }
	}

**Les menus panel admin**

Vous pouvez, si vous le souhaitez, avoir un menu au niveau du panel admin avec des sous-liens (comme pour la boutique). Pour ceci, il vous suffit d'ajouter la clé ``admin_menus`` dans la configuration du plugin.
La clé sera le nom du menu, vous pouvez utilisez des noms déjà utilisés pour placer votre menu en tant que sous-menu d'un déjà présent (comme sur l'exemple). Vous pouvez alors ajouter un index pour être après tel ou tel sous-menu
Les clés du panel admin sont les suivantes

.. list-table::
   :widths: 15 70
   :header-rows: 1

   * - Valeur
     - Explication
   * - ``Dashboard``
     - Correspondant au menu ‘Dashboard' du panel admin
   * - ``GLOBAL__ADMIN_GENERAL``
     - Correspondant au menu 'Général' du panel admin
   * - ``GLOBAL__CUSTOMIZE``
     - Correspondant au menu 'Personnalisation' du panel admin
   * - ``SERVER__TITLE``
     - Correspondant au menu 'Serveur' du panel admin
   * - ``GLOBAL__ADMIN_OTHER_TITLE``
     - Correspondant au menu 'Autres' du panel admin
   * - ``STATS__TITLE``
     - Correspondant au menu 'Statistiques' du panel admin
   * - ``MAINTENANCE__TITLE``
     - Correspondant au menu 'Maintenance' du panel admin
   * - ``GLOBAL__UPDATE``
     - Correspondant au menu 'Mise à jour' du panel admin
   * - ``HELP__TITLE``
     - Correspondant au menu 'Aide' du panel admin
	 
La valeur doit ensuite être un objet contenu l’``icon``, la ``route`` ou le ``menu`` (et optionnelement ``permission`` et ``index``)

.. code-block:: none
   
   Associez-lui comme valeur un tableau avec vos sous-liens, comme ceci par exemple :
   
.. code-block:: json

   {
   "name":"NAME",
   "admin_menus": {
    "GLOBAL__CUSTOMIZE": {
      "Boutique": {
        "index": 1,
        "icon": "shopping-cart",
        "menu": {
          "Gérer les articles": {
            "icon": "shopping-basket",
            "permission": "SHOP__ADMIN_MANAGE_ITEMS",
            "route": "/admin/shop"
          },
          "Gérer les promotions": {
            "icon": "percent",
            "permission": "SHOP__ADMIN_MANAGE_VOUCHERS",
            "route": "/admin/shop/shop/vouchers"
          },
          "Gérer les paiements": {
            "icon": "credit-card",
            "permission": "SHOP__ADMIN_MANAGE_PAYMENT",
            "route": "/admin/shop/payment"
          }
        }
      }
    }
  },
	"navbar_routes": {
    "Boutique": "/shop"
  },
  "author":"AUTHOR",
  "version":"1.0.0",
  "useEvents":true,
  "permissions" : {
    "available" : [],
    "default" : {
      "0" : [],
      "2" : []
    }
  },
  "requirements" : {
    "CMS" : "^1.2.0"
    }
  }

.. code-block: json

   {
  "name":"NAME",
  "admin_menus": {
    "Boutique": {
      "index": 1,
      "icon": "shopping-cart",
      "menu": {
        "Gérer les articles": {
          "icon": "shopping-basket",
          "permission": "SHOP__ADMIN_MANAGE_ITEMS",
          "menu": {
            "Gérer les promotions": {
              "icon": "percent",
              "permission": "SHOP__ADMIN_MANAGE_VOUCHERS",
              "route": "/admin/shop/shop/vouchers"
            }
          }
        },
        "Gérer les paiements": {
          "icon": "credit-card",
          "permission": "SHOP__ADMIN_MANAGE_PAYMENT",
          "route": "/admin/shop/payment"
        }
      }
    }
  },
  "navbar_routes": {
    "Boutique": "/shop"
  },
  "author":"AUTHOR",
  "version":"1.0.0",
  "useEvents":true,
  "permissions" : {
    "available" : [],
    "default" : {
      "0" : [],
      "2" : []
    }
  },
  "requirements" : {
    "CMS" : "^1.2.0"
    }
  }

La clé ``permission`` dans chaque lien est optionnelle, elle permet d'afficher le lien seulement si la permission est accordée au groupe de l'utilisateur.

Les tables SQL
~~~~~~~~~~~~~~
Les tables dont vous avez besoin pour votre plugin vont être générées automatiquement par un shell.
Dans un premier temps, toutes les tables de votre plugin doivent être préfixées par le nom de votre plugin.
Par exemple, pour le plugin Shop les tables doivent être préfixés par **shop_**

Pour générer vos tables automatiquement dans un schema (qui sera **indispensable** pour avoir un plugin valide) il vous faut vous rendre sur le SSH de votre serveur dédié/VPS/ordinateur pour pouvoir utiliser la console de CakePHP. Il vous faut ensuite vous rendre dans le dossier contenant les fichiers du CMS puis, il vous faudra taper
``app/Console/cake schema generate plugin-shop``
Un fichier *schema.php* sera automatiquement créé dans le dossier SQL de votre plugin.

Si vous ne pouvez pas accéder à la console de CakePHP, vous pouvez toujours créer votre fichier *SQL/schema.php* **manuellement**.

Vous devez commençer le fichier comme ceci:

.. code-block:: php

   <?php
    class ShopAppSchema extends CakeSchema {

    public $file = 'schema.php';

    public function before($event = array()) {
        return true;
    }

    public function after($event = array()) {}
  }

Callbacks
~~~~~~~~~
Les **callbacks** sont des fonctions appelées automatiquement par le CMS lors de certaines actions.

Vous pouvez, si vous le souhaitez, créer un fichier **MainComponent.php** dans le dossier ``Controller/Component`` de votre plugin.

Dans ce fichier vous pouvez y ajouter :

.. code-block:: php

   <?php
   class MainComponent extends Object {

    public function onEnable() {
    }

    public function onDisable() {
    }

   }

Ces fonctions **onEnable** et **onDisable** seront **automatiquement** appelées par le CMS lors de l’**installation**, l’**activation** *(pour le onEnable)*, et pour la **désinstallation** et la **désactivation** *(pour le onDisable)* du plugin.

