:title: Enhancement of augmented-reality visualization in surgery
:data-transition-duration: 1250
:author: Flavien Bridault
:description: Enhancement of augmented-reality visualization in surgery
:keywords: presentation
:css: css/presentation.css
:skip-help: true

----

:id: circle-no-background

|
|
|

Enhancement of augmented-reality visualization in surgery. 
============================================================

**Flavien Bridault**

*Fellow meeting - Strasbourg, 18th September 2016*

----

:data-x: r0
:data-y: r2700
:data-rotate-z: 90
:class: text-small

Few words about me
====================

Background
*******************
- Phd. Thesis in Computer Graphics (2007)
- Senior programmer in the Video games industry (2008-2013)
    - Low-level programming
    - Graphics programming
    - XBox360, PS3, PC

Research engineer at IRCAD (2014)
***************************************
- Application development (3DSurg, Lasar, Dosimap)
- FW4SPL (in-house software framework) enhancements, focus on simplicity and productivity
- Graphics programming

----

Challenges in Augmented-Reality visualization
=================================================

Disclaimer
*************
- We won't speak about how to register or deform organs
- Only visualization !

----

Challenges in Augmented-Reality visualization
=================================================

Direct volume rendering 
**************************

- Organs segmentation via transfer functions
- Used to be slow
- Not well adapted for GPUs before 2001
- Usually employed with static 3D images

.. raw:: html
    
    <iframe width="560" height="315" src="https://www.youtube.com/embed/703Zzl8YYJk" frameborder="0" allowfullscreen></iframe>

----

Challenges in Augmented-Reality visualization
=================================================

Surfacic meshes rendering
***************************

- Need an automated or a manual segmentation step
- Well-suited for GPUs (only triangles !)
- Easier to apply deformations


----


:class: square-background

|
|

How to take advantage of latest graphics hardware in Augmented-Reality ?
===========================================================================


----

3DSurg
====================

Breathing
***************

- Context view
- Vessels

.. raw:: html

       <div class="legend">ARBreathing</div>
       <video width="800" height="600" controls>
          <source src="../git/fellowMeeting_20160915/videos/arbreathing-visu.mp4" >
          Your browser does not support the video tag.
       </video>
       
----

Volume Rendering
******************

- 
- Vessels annotation


----

Lasar
====================

- Tumor views in AR
    - Depth feeling ?
- Needle insertion
    - Feedback

----

:class: text-small
:data-rotate-z: 90
:data-x: r0
:data-y: r1500

Demonstration
===========================

.. raw:: html

       <video width="640" height="360" controls>
          <source src="../videos/tutos.mp4" >
          Your browser does not support the video tag.
       </video>
       
----

:class: centered
:data-y: r1500

Thank you !
=============

fw4spl at gmail.com

fbridault at ircad.fr

|
|

	Presentation made with Hovercraft_

.. _Hovercraft: https://github.com/regebro/hovercraft
