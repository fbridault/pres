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
- Application development (**3DSurg**, **Lasar**, **Dosimap**)
- FW4SPL (in-house software framework) enhancements, focus on simplicity and productivity
- Graphics programming

----

Context
==============

- IRCAD R&D team engaged in AR software (**3DSurg**, **Lasar**, **Dosimap**)
- Historically and still today, the focus is:
    - Segmentation
    - Registration
    - Tracking
    - Deformation
- So far, few work on visualization !

----

Visualization
==============

Previous work
****************
- Our rendering backend was outdated
- We have worked last two years to get a modern renderer

Now start the real interesting work !
*******************************************

- Improve the rendering algorithm of our software
- End-of-studies project of a student (Florent Nuttens) (**3DSurg**)
- Work package planned on **Lasar2**

----

Our plans so far...
=================================================

1. Improve virtual world incrustation
****************************************
2. Enhance volume rendering
******************************
3. Annotations
*********************
4. ...
***********

----

:class: square-background

|

.. image:: images/we_need_you.jpg
           :width: 30%

We need you !
**************

----

1/ Improve virtual world incrustation
========================================

- How to mix virtual data/information with real-world ?

.. raw:: html

    <center>
    <iframe width="560" height="315" src="https://www.youtube.com/embed/uVDxMr-47kU?t=5m26s" frameborder="0" allowfullscreen></iframe>
    </center>

----

1/ Improve virtual world incrustation
========================================

- Context (clear-view)
- Depth perception (truc)

----

1/ Improve virtual world incrustation
========================================

.. raw:: html

       <video width="800" height="600" controls>
          <source src="../git/fellowMeeting_20160915/videos/arbreathing-visu.mp4" >
          Your browser does not support the video tag.
       </video>

----

2/ Enhance volume rendering
=================================================

- Organs segmentation via transfer functions
- Used to be slow
- Not well adapted for GPUs before 2001
- Usually employed with static 3D images

.. raw:: html

    <center>
    <iframe width="560" height="315" src="https://www.youtube.com/embed/703Zzl8YYJk" frameborder="0" allowfullscreen></iframe>
    </center>

----

Challenges in Augmented-Reality visualization
=================================================

Surfacic meshes rendering
***************************

- Need an automated or a manual segmentation step
- Well-suited for GPUs (only triangles !)
- Easier to apply deformations

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

Conclusion
===========================

- Sometimes it is just a matter of taste

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
