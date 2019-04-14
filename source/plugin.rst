
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

