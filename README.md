# MODS to TEI-HAL

Ce répertoire git comprend deux documents:

* MODS2TEI-HAL.xqm: ce script en XQuery permet de transformer des données bibliographiques d'un auteur exportées de Zotero au format MODS en données au format XML-TEI qui respecte le schéma AOfr de l'API SWORD-HAL.
* auteurs.xml: ce document XML est un document exemple pour présenter les informations type concernant un auteur.
Une base de données XML "auteurs" de ce type est indispensable au fonctionnement du script MODS2TEI-HAL.xqm.


## Prérequis

* Disposer du logiciel de bases de données XML [Basex](http://basex.org/)
* Créer, dans BaseX, une base de données XML "auteurs" avec au minimum, pour chaque auteur: 
    * le nom, 
    * le prénom, 
    * l'adresse mail, 
    * l'identifiant HAL (halauthorid), 
    * l'identifiant de l'affiliation de l'auteur (son institution de rattachement)
    * et au moins un domaine HAL concerné (par exemple "Sciences de l'Homme et Société")
   
(en suivant l'exemple donné dans auteurs.xml pour renseigner ces informations)

## Procédure

* Compléter la base "auteurs" 
* Créer une base de données dans BaseX avec une bibliographie [Zotero](https://www.zotero.org/) d'un auteur au format MODS.
* Ouvrir le script MODS2TEI-HAL.xqm dans BaseX
* 