+++
title = "glTF, aka JPEG de la 3D"
date = "2022-01-24T16:20:07+01:00"
author = ""
authorTwitter = "" #do not include @
cover = ""
tags = ["", ""]
keywords = ["", ""]
description = ""
showFullContent = false
readingTime = false
+++

## Un format taillé pour les besoins actuels

À chaque type d'utilisation son format de fichier et la 3D ne déroge pas à cette règle. Encore méconnu du grand public, le glTF (GL Transmission Format) est un format de fichier open-source de scènes et modèles 3D basé sur le format JSON. Si ce format n'a pas été crée expressément pour la réalité virtuelle, son utilisation en parallèle de l'API WebXR semble paraître une évidence. Il a pour avantage d'être API-agonistique ce qui lui confère une grande flexibilité. Dans un contexte web, il peut donc être utilisé avec par exemple des framework tel que A-FRAME. 

Son utilisation est grandissante et de plus en plus d'acteurs importants de l'industrie tels que Google ou Facebook l'adoptent au fil des années. Son succès repose sur une taille réduite permettant des chargements très rapide, le fait d'être API-agnostique et sa capacité a représenter l'intégralité d'une scène 3D. Godot, un moteur de jeu au succès grandissant, souhaite voir le glTF devenir le format standard d'échange de ressources pour le développement de jeux, mettant en avant les avantages cités précédemment mais également le fait qu'il soit basé sur le JSON ce qui permet une grande lisibilité, l'absence de de données redondantes et sa modernité, le glTF lui-même supportant les dernières technologies utilisées dans la modélisation 3D.

## Une nécessité pour les technologies d'aujourd'hui

Avant sa création en 2015, les deux formats de fichiers 3D dominants et principalement utilisés dans des contextes de modélisation 3D et de moteurs de jeu 3D étaient FBX et OBJ mais ceux-ci présentaient des contraintes que le glTF a voulu dépasser. Par exemple, le format FBX est un format propriétaire et nécessite un lourd SDK C++ pour être chargé, le rendant quasiment impossible à afficher directement sur un navigateur web. De son côté, OBJ présente comme défaut d'être un format très lourd en terme de stockage et donc très lent à être chargé sur le web.


Qu'est-ce qu'il se cache derrière ce format? En réalité, un fichier .gltf est écrit en JSON et va simplement référencer d'autres fichiers comme par exemple des textures et des formes géométriques 3D.

![](https://www.khronos.org/assets/uploads/apis/2020-core-gltf-2-0-asset-structure.jpg)
*Construction d'un fichier .gltf*



Depuis 2017, le glTF en est à sa deuxième version et est depuis accompagné par le format GLB qui est sa forme binaire et qui a pour différence d'intégrer directement les textures au lieu de faire le lien vers des fichiers externes. Cinq ans après, le monde de la 3D a évolué et semble être en passe de continuer à sensiblement se complexifier dans les années à venir. Il sera intéressant de voir ce que proposeront les spécifications glTF 3.0 et les nouveaux formats de fichiers voués à émerger en fonction de nos besoins futurs.
