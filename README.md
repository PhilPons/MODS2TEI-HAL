# MODS to TEI-HAL

Ce répertoire git comprend deux documents:

* MODS2TEI-HAL.xqm: ce script en XQuery permet de transformer des données bibliographiques d'un auteur exportées de Zotero au format MODS en données au format XML-TEI qui respecte le schéma AOfr de l'API SWORD-HAL.
* auteurs.xml: ce document XML est un document exemple pour présenter les informations type concernant un auteur.
Une base de données XML "auteurs" de ce type est indispensable au fonctionnement du script MODS2TEI-HAL.xqm.


## Prérequis

* Disposer du logiciel de bases de données XML [Basex](http://basex.org/)
* Créer, dans BaseX, une base de données XML "auteurs" avec, au minimum, pour chaque auteur: 
    * le nom, 
    * le prénom, 
    * l'adresse mail, 
    * l'identifiant HAL (halauthorid), 
    * l'identifiant de l'affiliation de l'auteur (son institution de rattachement)
    * et au moins un domaine HAL concerné (par exemple "Sciences de l'Homme et Société")
   
(en suivant l'exemple donné dans auteurs.xml pour renseigner ces informations)

## Procédure

1. Compléter la base "auteurs" 
2. Créer une base de données dans BaseX avec une bibliographie [Zotero](https://www.zotero.org/) d'un auteur au format MODS. 
Pour cela, dans ZOTERO:

    * sélectionner la bibliographie de l'auteur, 
    * clic droit sur les références
    * choisir "Exporter les documents"
    * sélectionner le format MODS
    * et enregistrer l'export
3. Ouvrir le script MODS2TEI-HAL.xqm dans BaseX
4. Au début de ce script, remplir les informations demandées:
    * le prénom de l'auteur
    * le nom de l'auteur
    * le nom de la base de données que vous avez créé à l'étape 2 ci-dessus.
    * le prénom du déposant dans HAL
    * et le nom du déposant dans HAL (même si l'auteur et le déposant sont une seule et même personne)
5. Lancer dans BaseX le script MODS2TEI-HAL.xqm

Si tout s'est déroulé correctement, vous disposer alors d'un document TEI dans le dossier dans BaseX: *webapp>static*.

Le nom de ce document est la concaténation du nom de l'auteur et de ".xml", par exemple: *Dupont.xml*.

/!\ **Attention**: pour être sûr que le script fonctionne, assurez-vous que le prénom et le nom de l'auteur sont présentés exactement pareils:

* dans la base "auteurs"
* dans le script MODS2TEI-HAL.xqm
* et dans les références Zotero exportées en MODS.

## Remarques complémentaires

### La langue

La langue de rédaction d'un document est un élément difficile à repérer.

Il est donc vivement conseillé de renseigner dans Zotero le champs *Langue* pour chaque notice avec un code langue adéquat (par exemple, **fr** pour **français**, **en** pour **anglais**, etc.)

### Les dates

Les formats de date tolérés par Zotero sont beaucoup plus souples que ceux réclamés par HAL.

Il faut donc s'assurer que les dates dans Zotero sont renseignées sous le format: YYYY-MM-DD, ou YYYY-MM, ou YYYY.

Si ce n'est pas le cas, le script fonctionnera, mais un import par lot risque de ne pas fonctionner pour les références dont le format n'est pas adéquat.


