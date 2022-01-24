+++
title = "Introduction à A-FRAME"
date = "2022-01-24T16:25:23+01:00"
author = ""
authorTwitter = "" #do not include @
cover = ""
tags = ["", ""]
keywords = ["", ""]
description = ""
showFullContent = false
readingTime = false
+++

Comment créer une expérience de réalité virtuelle à destination des navigateurs et comment fonctionnent-elles? C'est à ces question que je vais tenter dans le présent article de trouver des pistes de réponses à travers une expérimentation avec le framework A-FRAME.

A-FRAME permet, à travers son langage à balise, de créer des scènes 3D. Cela représente un certain avantage pour ceux étant familiers avec le développement web car les mêmes concepts sont mobilisés. Cela a également pour avantage de permettre de développer des prototypes rapidement et sans avoir à écrire des lignes interminables de scripts JS.

Pour commencer, j'ai simplement crée un fichier html comprenant un squelette de code basique dans lequel je fais appel à la librairie d'A-FRAME.

```html
<!DOCTYPE html>
<html>
	<head>
		<title>Experimentation A-FRAME</title>
		<script src="aframe.min.js"></script>
	</head>
	<body>
	</body>
</html>

```



Le premier concept important à appréhender est celui de scène. La scène est le conteneur dans lequel se trouveront nos différents éléments. Créer une scène se fait à l'aide d'une balise:

```html
<body>
    <a-scene>
	</a-scene>
</body>
```

 

Il est ensuite possible d'ajouter toute sorte d'objets 3D dans celle-ci, commençons par un cube, soit un élément <a-box>. Les éléments d'A-FRAME, tous comme les différents éléments HTML peuvent prendre un certain nombre d'attributs. Ici une couleur, une position et une rotation.

```html
<a-scene>
	<a-box color="#0095DD" position="0 1 0" rotation="20 40 0"> </a-box>
</a-scene>

```

![](https://fly04.github.io/LabVeilTech/images/1.png)



Notre cube semble alors flotter dans un vide blanc. Rajoutons une skybox, c'est-à-dire le fond qu'aura notre scène 3D. L'élément <a-sky> va prendre un attribut color, ici un bleu clair.

```html
<a-scene>
	<a-sky color="#DBF3FF"></a-sky>
	<a-box color="#0095DD" position="0 1 0" rotation="20 40 0"> </a-box>
</a-scene>
```

 ![](https://fly04.github.io/LabVeilTech/images/2.png)



À ce stade nous avons une scène qui contient un cube et une skybox. En réalité, A-FRAME intègre également un caméra et des lumières par défaut sans lesquels il nous serait impossible de visualiser la scène. Voyons comment définir une caméra et une lumière customisées.

Pour la caméra, il suffit simplement d'ajouter à notre scène un élément <a-camera>. Celle-ci prendra comme attribut une position depuis laquelle on pourra observer la scène.

```html
<a-scene>
	<a-camera position="0 1 4"> </a-camera>
	<a-sky color="#dbf3ff"></a-sky>
	<a-box color="#0095DD" position="0 1 0" rotation="20 40 0"> </a-box>
</a-scene>
```



Il existe plusieurs types de lumières, par exemple d'ambiance ou directionnelle. Ici, on utilisera une lumière directionnelle, placée sur la gauche de notre cube. En plus des attributs que nous avons déjà vu, <a-light> aura besoin d'une couleur, d'une intensité et donc comme indiqué précédemment d'un type de lumière.

```html
<a-scene>
	<a-light
		type="directional"
		color="#FFF"
		intensity="0.5"
		position="-1 1 2"
	>
	</a-light>
	<a-camera position="0 1 4"> </a-camera>
	<a-sky color="#dbf3ff"></a-sky>
	<a-box color="#0095DD" position="0 1 0" rotation="20 40 0"> </a-box>
</a-scene>
```

![](https://fly04.github.io/LabVeilTech/images/3.png)



S'il est possible de créer des cubes, sphères, cylindres et autres formes géométriques définies, A-FRAME permet également de créer des formes plus complexes à l'aide de la balise <a-entity>.

```html
<a-scene>
	<a-light
		type="directional"
		color="#FFF"
		intensity="0.5"
		position="-1 1 2"
	>
	</a-light>
	<a-camera position="0 1 4"> </a-camera>
	<a-sky color="#dbf3ff"></a-sky>
	<a-entity
		geometry="
        primitive: torus;
        radius: 1;
        radiusTubular: 0.1;
        segmentsTubular: 12;"
		rotation="10 0 0"
		position="-3 1 0"
	>
	</a-entity>
	<a-box color="#0095DD" position="0 1 0" rotation="20 40 0"> </a-box>
</a-scene>
```



![](https://fly04.github.io/LabVeilTech/images/4.png)



Il est possible d'appliquer à nos éléments des matériaux. En plus de spécifier une couleur, les matériaux permettent de pouvoir définir comment celle-ci reflète la lumière et à quel point le matériau est métallique.

```html
<a-scene>
	<a-light
		type="directional"
		color="#FFF"
		intensity="0.5"
		position="-1 1 2"
	>
	</a-light>
	<a-camera position="0 1 4"> </a-camera>
	<a-sky color="#dbf3ff"></a-sky>
	<a-entity
		geometry="
        primitive: torus;
        radius: 1;
        radiusTubular: 0.1;
        segmentsTubular: 12;"
		rotation="10 0 0"
		position="-3 1 0"
		material="
        color: #EAEFF2;
        roughness: 0.1;
        metalness: 0.5;"
	>
	</a-entity>
	<a-box color="#0095DD" position="0 1 0" rotation="20 40 0"> </a-box>
</a-scene>
```

![](https://fly04.github.io/LabVeilTech/images/5.png)



Dans cet exemple, les deux formes géométriques que nous avons ont été créées directement via des balises HTML. A-FRAME permet également de faire cela à travers du JavaScript.

```javascript
let scene = document.querySelector('a-scene');
let cylinder = document.createElement('a-cylinder');
cylinder.setAttribute('color', '#FF9500');
cylinder.setAttribute('height', '2');
cylinder.setAttribute('radius', '0.75');
cylinder.setAttribute('position', '3 1 0');
scene.appendChild(cylinder);
```

![](https://fly04.github.io/LabVeilTech/images/6.png)


Finalement, il est possible d'animer nos objets avec une balise dédiée. En effet, la balise <a-animation> peut se placer en tant qu'enfant d'un élément existant et propose des attributs permettant de spécifier les variables d'animation classiques tels que la durée, le départ et l'arrivée, l'attribut animé, la courbe accélération, etc...).



```html
<a-box color="#0095DD" rotation="20 40 0" position="0 1 0">
	<a-animation
		attribute="rotation"
		from="20 0 0"
		to="20 360 0"
		direction="alternate"
		dur="4000"
		repeat="indefinite"
		easing="ease"
	>
	</a-animation>
</a-box>
```



Pour conclure cet article, je trouve qu'il est impressionnant de voir ce qu'il est possible de faire avec si peu de lignes et une complexité abordable. A-FRAME intègre la librairie d'animation tween.js et je suis très curieux d'expérimenter à l'avenir les possibilités qu'elle offre afin de créer des expériences interactives et animées.