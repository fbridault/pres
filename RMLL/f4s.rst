:title: Basic example
:data-transition-duration: 1250
:author: Flavien Bridault
:description: Basic hovercraft example
:keywords: presentation
:css: css/presentation.css
:skip-help: true

.. role:: main-color
.. role:: big-bold
.. role:: bold-color
.. role:: big-bold-color
.. role:: funny-font

.. role:: mail

----

:id: circle-no-background

|
|
|
|

FW4SPL, a framework for applications based on medical imaging. 
==================================================================

|
|

**Flavien Bridault**

*RMLL 2015, Beauvais, Wednesday, 8th 2015*

----

:data-rotate-z: 90


Outline
==================================================================

- *Introduction*
- Object/Service approach
- Component based approach
- Framework features
- Community

.. note::

    - Introduction - 5min
    - Object/Service approach - 10 min
    - Component based approach - 5min
    - Framework features -5min 
    - Community - 10min
    - Conclusion - 5min

----

:data-y: r2000


Introduction
==================================================================

Presentation purpose : 
***************************
- Understand why we have developed FW4SPL
- Show the main features available
- Help to start developing

----

IRCAD context
=================

.. image:: images/context.jpg 
           :width: 70%

----

:data-y: r2000

IRCAD R&D team
=================

- Researchers (3)
- Engineers (7)
- Phd. students (3)
- Trainees (6)
- Internships (4)

----

:data-y: r2000

IRCAD R&D needs
=================

- Quick development/prototyping on different plaforms
- Maximal source code re-using
- Trainees/phd (students) works integrated but fragmented
- Facilitate collaborations (source code available or not)

.. note::

    - software/prototype - Windows, OSX, Linux, Android, IOs
    - sample with image filter, something...
    
----

:data-y: r2000

FW4SPL characteristics
===========================

- Object/services design
- Component
- Developed in C++
- Multi platforms
- Depends on many open source libraries: boost, Qt, VTK, ITK, gdcm, libxml2,...

----

:data-y: r2000

FW4SPL history
=================

- 2004-2007 : fw4spl project
- 2007-2009 : VRRender 0.7 (free)
- 09/2009 : fw4spl became Open Source
- 2010 : PoC Sofa (Altran-Est), VRRender WLE 0.8.1 (free)
- 2011 : PoC Kinect (Altran-Est), VRRender 0.9 (open)
- 2012 : Introduction of multithreading
- 2013 : Creation of a board (IRCAD, IHU, Visible Patient) to manage the evolution of fw4spl
- 2013 : Creation of fw4spl external repository (for branch 0.9.1 and after)
- 2014 : Switch to CMake for compiling
- 2014 : Creation of GitHub and Bitbucket repositories
- 2014 : Partial Android support

.. note::

    - VRRender: mesh/image viewer - mettre une image !

----

:data-y: r2000

FW4SPL in terms of code
=============================

- Applications: 35 (PoC and Tutorials)
- Bundles: 52 (57 on private repository)
- Service number: 230 (380)
- Code line numbers: 220 000

----

:data-rotate-z: r90

Outline
==================================================================

- Introduction
- *Object/Service approach*
- Component based approach
- Framework features
- Community

.. note::

    - Introduction - 5min
    - Object/Service approach - 10 min
    - Component based approach - 5min
    - Framework features - 10min 
    - Community - 5min
    - Conclusion - 5min

----

:data-x: r2000

:funny-font:`Contacts :`
==================================================================

this following lines insert a image among the text

.. image:: images/Image01.png
           :width: 10%



----

:data-y: r1000

.. image:: images/Image.png
           :width: 50%
           
Object/Service approach
=============================

           
           
Example with an image processing
**********************************

|
|
|
|
|

  
  
----

:data-y: r100
:data-x: r100
:data-scale: 0.75


----

:data-y: r2000

Method to read from a file
=============================

.. raw:: html

    <span class="mail"></span><br>
       
----

:data-x: r350
:data-y: r150
:data-scale: 0.75

.. code:: c++

    void readImageFromPacsWithDcmtk( ... )
    {
        // Code using dcmtk to load an image
        Dcmtk::Image img;
        
        // ...

        // Code to convert dcmtk image data in our own format
        m_buffer = itkHelper::getBuffer( img );
        m_size = itkHelper::getSize( img );
    }
    
----

:data-y: r2000
:data-rotate-z: r90


Outline
==================================================================

- *Introduction*
- Object/Service approach
- Component based approach
- Framework features
- Community

.. note::

    - Introduction - 5min
    - Object/Service approach - 10 min
    - Component based approach - 5min
    - Framework features -5min 
    - Community - 10min
    - Conclusion - 5min
    
----

:data-rotate-x: 45
:data-scale: 2
:data-y: r3000

Demonstration
===============================

.. raw:: html

       <video width="800" height="600" controls>
          <source src="ogre.mp4" type="video/mp4">
          Your browser does not support the video tag.
       </video> 


----

:data-x: -1000
:data-scale: 1/2

That's all folks!
=================


