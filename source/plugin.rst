
Créer un plugin
---------------
**Introduction**

Un plugin (aussi appelé *extension*), est un ensemble de **fichiers** qui sont ajoutés à votre CMS pour y ajouter plusieurs **fonctionnalités** ou modifier certains **comportements** par défaut. Différents plugins “officiels” sont *déjà disponibles* `ici <https://github.com/MineWeb?utf8=%E2%9C%93&q=Plugin-&type=&language=php>`__. D’autres peuvent être *développés par la communauté* et c’est le but de ce tutoriel.

Un PDF est disponible `ici <https://docs-mineweb.tk/files/Pl-Helper.pdf>`__ pour vous aider à comprendre et à créer votre plugin.

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

.. admonition:: Information

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

.. admonition:: Information
   
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

Utiliser les events
~~~~~~~~~~~~~~~~~~~
Dans la config.json du plugin, passez **useEvents** à **true**.

Pour créer un **écouteur** *(Listener)*, il vous faut créer un fichier dans le dossier */Event/* de votre plugin. Le fichier doit être appelé de la manière suivante *{PLUGIN_NAME}{NOM}EventListener.php* (préfixé par le slug de votre plugin).

.. admonition:: Exemple 

   ShopBuyEventListener et son contenu doit être comme ceci :
   
.. code-block:: php

   <?php
  App::uses('CakeEventListener', 'Event');

  class {PLUGIN_NAME}{NOM}EventListener implements CakeEventListener {

    private $controller;

    public function __construct($request, $response, $controller) {
      $this->controller = $controller;
    }

    public function implementedEvents() {
        return array();
    }
   }
   
.. admonition:: Information

   Pour écouter un event il vous faut l'ajouter dans l'array retourné par la fonction **implementedEvents()** avec votre fonction comme valeur. Et il vous faut ensuite créer votre fonction. Exemple :
   
.. code-block:: php

   <?php
  App::uses('CakeEventListener', 'Event');

  class NAMEEventListener implements CakeEventListener {

    public function implementedEvents() {
        return array(
          'requestPage' => 'mafonction'
        );
    }

    public function mafonction($event) {

    }
   }
   
**Liste des events disponibles**

**Global**

- **requestPage** : appelé lors de chaque requête sans données particulières.
- **onPostRequest** : appelé lors d’une requête POST sans données particulières.
- **beforePageDisplay** : appelé lors de chaque chargement de page dans le afterFilter sans données particulières.
- **onLoadPage** : appelé lors de chaque chargement de page dans le beforeRender sans données particulières.
- **onLoadAdminPanel** : appelé lors de chaque chargement de page admin (prefix) dans le beforeRender sans données particulières.

**Fonction particulière**

- **beforeEncodePassword** : appelé avant chaque encodage de mot de passe avec le pseudo et le mot de passe en données.
- **beforeSendMail** : appelé avant chaque envoi d’email avec le message et la configuration en données.
- **beforeUploadImage** : appelé avant chaque upload d’image avec la requête et le nom de l’image voulu en données.

**News**

- **beforeAddComment** : appelé avant que le commentaire ne soit enregistré avec le contenu, l’ID de la news et les infos de l’utilisateur en données.
- **beforeLike** : appelé avant que le like ne soit enregistré avec l’ID de la news et les infos de l’utilisateur en données.
- **beforeDislike** : appelé avant que le like ne soit supprimé avec l’ID de la news et les infos de l’utilisateur en données.
- **beforeDeleteComment** : appelé avant que le commentaire ne soit supprimé avec l’ID du commentaire, l’ID de la news et les infos de l’utilisateur en données.
- **beforeDeleteNews** : appelé avant que la news ne soit supprimé avec l’ID de la news et les infos de l’utilisateur en données.
- **beforeAddNews** : appelé avant que la news ne soit enregistré avec le contenu de la requête et les infos de l’utilisateur en données.
- **beforeEditNews** : appelé avant que la news ne soit enregistré avec le contenu de la requête, l’ID de la news et les infos de l’utilisateur en données.

**User**

- **onLogin** : appelé à chaque login avec l’utilisateur et register (boolean) comme données.
- **beforeRegister** : appelé avant l’enregistrement d’un utilisateur (après la validation) avec les données de la requête comme données.
- **beforeConfirmAccount** : appelé avant la confirmation en base de donnée de l’utilisateur avec l’ID de l’utilisateur et manual si confirmé par un administrateur comme données.
- **beforeSendResetPassMail** : appelé avant l’envoi de l’email permettant la réinitialisation du mot de passe avec l’ID de l’utilisateur et clé de reset comme données
- **beforeResetPassword** : appelé avant l’enregistrement du nouveau mot de passe avec l’ID de l’utilisateur et le nouveau mot de passe comme données.
- **onLogout** : appelé pendant la déconnexion avec la session “user” comme données.
- **beforeUpdatePassword** : appelé avant l’enregistrement du nouveau mot de passe avec l’utilisateur et le nouveau mot de passe encodé comme données.
- **beforeUpdateEmail** : appelé avant l’enregistrement du nouvel email avec l’utilisateur et le nouveau email comme données.
- **beforeSendPoints** : appelé avant l’enregistrement de la transaction avec l’utilisateur, le nouveau solde de l’utilisateur, à qui sont transféré les points et combien comme données.
- **beforeEditUser** : appelé avant que les données ne soit enregistrées avec l’ID de l’utilisateur, les données et ``password_updated`` comme données.
- **beforeDeleteUser** : appelé avant que l’utilisateur ne soit supprimé avec ses informations comme données.

Utiliser les modules
~~~~~~~~~~~~~~~~~~~~
**C'est quoi ?**

Les modules permettent aux développeurs de plugins d'ajouter du **code HTML**, **code PHP**, etc... facilement depuis des **pages du CMS**.

**Liste des modules**

Les modules disponibles sont :

- ``user_profile`` *profil d'utilisateur*
- ``user_profile_messages`` *profil d'utilisateur (haut de page)*
- ``admin_user_edit`` *modification admin d'un utilisateur (bas de page)*
- ``admin_user_edit_form`` *modification admin d'un utilisateur (dans le formulaire)*
- ``home`` *accueil*
- ``news`` *page affichant une news*

**Comment les utiliser ?**

Pour utiliser un module dans votre **plugin**, il vous suffit de créer un dossier */Modules/* dans le dossier de votre plugin. Il vous faut ensuite **créer** un fichier nommé par le **nom du module** que vous voulez utiliser et avec l'extension **.ctp**.

Par exemple pour utiliser le module **user_profile** il vous faut créer le fichier */Modules/user_profile.ctp*.

Dans ce fichier, vous pouvez ajouter le code que vous souhaitez, **HTML**, **PHP** ou encore **JS** ou **CSS**.

Exemple d'un plugin
~~~~~~~~~~~~~~~~~~~
Je vais avec vous, développer un plugin vous présentant le développement sous Mineweb avec le framework Cakephp 2.x .

Arborescence du plugin :

- ``app/Plugin/``
     - ``Tutorial/``
        - ``Config/``
           - ``bootstrap.php``
           - ``routes.php``
        - ``Controller/``
           - ``TutorialAppController.php``
           - ``TutorialController``
        - ``Model/``
           - ``Info.php``
           - ``TutorialAppModel.php``
        - ``SQL/``
           - ``schema.php``
        - ``View/``
           - ``Tutorial/``
               - ``admin_index.ctp``
               - ``index.ctp``
        - ``lang/``
           - ``en_US.json``
           - ``fr_FR.json``
        - ``config.json``

Dans un premier temps, nous allons créer les routes du plugin. Celles-ci permettent que nous puissions relier les divers arguments de l'url aux controleurs.

Pour des raisons de conventions, vous aurez remarqué que nous ne fermons pas nos balises PHP avec ?>. Cela évite de multiples problèmes et vous familiarise avec les frameworks PHP.  

Si vous voulez plus d'information, je vous conseille ces liens : `StackOverflow <http://stackoverflow.com/questions/4410704/why-would-one-omit-the-close-tag/4499749#4499749>`__ ainsi que les recommandations `PHP-Fig <http://www.php-fig.org/psr/psr-2/>`__.