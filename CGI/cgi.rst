:title: Rétrospective CGI 2015
:data-transition-duration: 1250
:author: Flavien Bridault
:description: Rétrospective CGI 2015
:keywords: presentation
:css: css/presentation.css
:skip-help: true

----

:id: circle-no-background

|
|
|
|
|

Rétrospective CGI 2015 
==================================================================

|

**Flavien Bridault**

----

Keynote
================

Computer Graphics traditionnel
*******************************

- mesh + physics + simulation -> image
- Les images synthétiques sont sans vie, il nous manque les données pour recréer les petits détails

.. note::
	- coucou !

----

Keynote
================

- Rendu basé image -> mieux mais pour un lieu particulier
- Les photos que nous avons en général sont "génériques", par sur un endroit particulier

----

Keynote
================

- certains phénomènes ont des paramètres connus (fluides) d'autres sont beaucoup trop complexes (arbres,...)
- Paramétrisation trop complexe -> solution Big Data
- "Unreasonable Effectiveness of Data" [Haelvy 2009]

----

Keynote
================

- Google AI for the post-modern world
- Intelligence is in the data, in the requests of other users
- really stupid algorithms + lots of data = "unreasonable effectiveness"
- visual synthesis = visual matching + appearance transfer
- visual data is hard to match

----

Keynote
================

- distance metrics
- ex photo jardin luxembourg prise à divers instants ou avec effets -> ok pour condition normales, sinon 0 match
- Expérience : téléchargement de 2 millions de photos sur Flickr (premier essai avec 20000 -> échec total)
- recherche de matches pour remplacer château sur photo -> environ 200
- Les algorithmes ne sont pas si importants, ce sont les data qui importent !

----

Keynote
================

- Matching images avec translation, rotation, zoom
- Insertion objects dans photo -> ne pas prendre un objet en particulier mais en évaluer un grand nombre pour trouver celui qui matche le mieux
- capture illumination pour déterminer position soleil, conditions météos - extraction ombres

----

Keynote
================

Biais
******

- Point de vue (humain, oiseau)
- Prise de vue (psycho)
- Source (flickr, google)
- Sampling (ex zones du monde non couvertes)
- Social bias
- Réduction du biais -> prise de vue automatiques

----

Optimal Exposure Compression for HDR Content
===============================================

- HDR images 16 ou 32  bits -> très gros à transmettre !
- Stockage puis processing pour vision sur LDR monitors -> tone mapping (HDR monitors commencent à exister)
- Tone map, compute residuals
- Ward & Simmons original method, stores tone mapped images in JPG and downsampled residuals in 64Kb JPEG subband data

----

Optimal Exposure Compression for HDR Content
===============================================

Motivation
************

- Most HDR video compression is based on tone mapping but can go wrong !
- People prefer single exposure images
- No consensus on the best tone mapper
- Hard to find good parameters automatically

----

Optimal Exposure Compression for HDR Content
===============================================

Method
*******

- Aims to avoid tone mapping
- Backward compatible
- Find the optimal exposure

----

Sparse pixel sampling for appearance edit propagation
======================================================

Pas tout compris à la base mais intéressant, à relire !

----

Depth reconstruction
=======================

- depth images suffers from artifacts : black spots, flickering even if static existing solutions:
	- median and bilateral filters
	- gpu-adaptive kalman filters
	- joint bilateral filters
- good results but expensive and only works on static scenes

----

Depth reconstruction
=======================

Method:
********

- 1D Least Median of Squares regression
- Depth fluctuates over temporal domain (1D)
- Sliding window of frames
- Application aux tags ???

----

Learning best views of 3D shapes from sketch contour
======================================================

Essayer de matcher des objets à partir du contour

On ne prend pas tout le contour mais des segments entre des points clé (plus rapide)

----

A fast approach for perceptually-based fitting strokers into elliptical arcs
=============================================================================

Un trait est difficile à interpréter : arc, droite ? cela dépend du contexte
Reconnaisance de features à partir de 3D est un problème traité mais toujours WIP
En 2D c'est bcp plus compliqué
On essaie de fitter des arcs elliptiques

- conversion sketch en graphe de lignes

----

Layer the sphere for Accurate Voxelation by Integer Operation
==============================================================

----

Real-time adaptive content retargeting for live multi-view capture and light field display
===========================================================================================

Holografika

----

GPGPU-Perf: Efficient, Interval-based DVFS Algorithm for Mobile GPGPU Applications
=====================================================================================

Ajustement du voltage en fonction de la charge GPU
Les algos ne sont pas optimaux

----

Efficient grid construction on streaming architecture
=======================================================

Construction de grille

----

Past forward: when computer graphics and Archaeolgy meet
=========================================================

On retrouve de la recoloration par griboullis (interactive segmentation ?)
Hole completion by curves

----

Computer Graphics in Automotive Market
=======================================

Visteon
Member of Khronos Group
discussions sur Vulkan (OpenGL+OpenCL)

Constraints:
- safety rules (fiable, pas distraire le conducteur !)
- be attractive (différent pour chaque marque, sexy)

3 ans pour la mise sur marché d'une nouvelle techno

API pour sécurité : pixel checker ! (ex: brake display) -> certification ? super intéressant !!!
pour l'instant c'est juste du hardware sur demande auprès des constructeurs
possible en soft mais pas envisageable dans leur contexte (low-end gpus)
iso 26262

virtualization pour isoler/équilibrer charge GPU (compteur 60fps/GPS 15fps par ex)
problème car 1 seul GPU à partager entre 2/4 coeurs avec des OS différents
Instrumentation complète en WebGL
mais bcp plus lent et plus gourmand en mémoire qu'une appli native

futur -> réalité augmentée, cloud based rendering, 3D apprs, autostereoscopic 3D, virtualization, multi-layer rendering

----

Simplification of meshes using digitized radiance
==================================================

context : cultural heritage, digitization
dense mesh (ex dragon 1M vertices)
prendre en compte le spéculaire lors de l'acquisition plutôt que le diffus seul
coeff pour chaque point (coefs d'harmoniques sphériques par ex)
simplification du mesh : ok pour les attributs standards (distance erreur, etc) mais pour radiance on a une fonction !

----

Perceptual Effects of Volumetric Shading in SDEs
==================================================

Constat
*********
- Les rendus volumiques "avancées" permettent de mieux distinguer les objets
	- Survey of volume illumination dans les réfs [2014] ombres, GI, AO, etc.. <- à lire !!!!!!
	- Lindemann and... for monoscopic

----

Perceptual Effects of Volumetric Shading in SDEs
==================================================

Problématiques
***************

1. En rendu stéréoscopique, on distingue naturellement mieux la profondeur et donc les contours... Est-ce qu'on bénéficie toujours donc autant des techniques "avancées" ?
2. Est-ce que l'éclairage environnant affecte la perception ?

----

Perceptual Effects of Volumetric Shading in SDEs
==================================================

Après des mois de tests "perceptuels" avec des vrais gens, etc...

----


Perceptual Effects of Volumetric Shading in SDEs
==================================================

Résultat
*********

- Ben oui c'est mieux quand même...
- Et oui l'éclairage environnant altère un peu la perception mais pas trop

----

Using Half-Precision Floating Point numbers for storing BVH
=============================================================

si on change la borne sup' en half, on a des faux positifs
Odroid XU3 ???

----

Mocap
==========

Pb: occlusion
low rank matrix for missing data completion
marche bien avec 30% de miss, à 50% on voit des artefacts
Intéressants pour nous si on perd des marqueurs ?

Trajectory based representation



Mocap sequence compression
SVD

Détection de chute (trop rapide, pb difficile)
prendre seulements qq joints

----

Global Optimal Searching for Textureless 3D Object Tracking
============================================================
Tracking 3D

Feature based

Edge based -> no texture objects

----

Extended surface distance for local evaluation of 3D Medical Image Segmentations
=================================================================================

Intéressant pour Alex ?

----

Virtual cutting...
====================

Découpage de meshes
- soit on déplace les points sur la coupure
- soit on ajoute des points

----

Challenges ?
================

Big data
Mobile
Very large scenes
Multi sclaes
Graphics turing test characters

Internet everywhere, not 3D even if it existed prior
Killer app that will put 3D everywhere ?

AR

