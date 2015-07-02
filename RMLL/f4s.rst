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

FW4SPL, a framework for applications based on medical imaging. 
==================================================================

|

**Flavien Bridault**

*RMLL 2015, Beauvais, Wednesday, 8th 2015*

----


:data-y: r1500
:data-rotate-z: 90

Presentation purpose : 
==================================================================

- Why IRCAD R&D team has developed FW4SPL ?
- Explain the design
- Show the main features
- Help to start developing

----

:class: square-background
:data-y: r1500

Outline
==================================================================

- *Introduction*
- Object/Service approach
- Communication
- Component based approach
- Community

.. note::

    - Introduction - 5min
    - Object/Service approach - 10 min
    - Communication -5min 
    - Component based approach - 5min
    - Community - 10min
    - Conclusion - 5min

----

:id: ircad-context
:data-y: r2000

IRCAD context
=================

.. image:: images/patient.png 
           :width: 30%

----

:data-x: r-300
:data-y: r-300
:data-scale: 0.4


.. raw:: html

       <div class="legend">Viewer</div>
       <video width="800" height="600">
          <source src="../git/RMLL/videos/VRMedNegato2D3D.mp4" >
          Your browser does not support the video tag.
       </video>

----

:data-x: r-270
      

.. raw:: html

       <div class="legend">Segmentation/3D models</div>
       <video width="800" height="600">
          <source src="../git/RMLL/videos/TeaserVisiblePatient2012.mp4" >
          Your browser does not support the video tag.
       </video>

----

:data-x: r-270
:data-y: r300


.. raw:: html

       <div class="legend">Planning</div>
       <video width="800" height="600">
          <source src="../git/RMLL/videos/TeaserVisiblePatient2012.mp4" >
          Your browser does not support the video tag.
       </video>

----

:data-x: r270
:data-y: r300

.. raw:: html

       <div class="legend">Simulation</div>
       <video width="800" height="600">
          <source src="../git/RMLL/videos/digitalTrainersSimu1.mov" >
          Your browser does not support the video tag.
       </video>
       
       
----

:data-x: r270


.. raw:: html

       <div class="legend">Augmented reality</div>
       <video width="800" height="600">
          <source src="../git/RMLL/videos/rdARinteractive1.mov" >
          Your browser does not support the video tag.
       </video>
       
----

:data-x: r-200
:data-y: r-300
:data-scale: 1.2

----

:data-y: r1500

IRCAD R&D team
=================


.. image:: images/team.jpg
           :width: 80%

- Researchers (3)
- Engineers (7)
- Phd. students (3)
- Trainees (6)
- Internships (4) 
   
----

IRCAD R&D needs
=================

- Quick development/prototyping on different plaforms
- Maximal source code re-using
- Intensive use of open source libraries (boost, Qt, VTK, ITK,...) 
- Trainees/phd (students) works integrated but fragmented
- Facilitate collaborations (source code available or not)

.. note::

    - software/prototype - Windows, OSX, Linux, Android, IOs
    - sample with image filter, something...
    
----

FW4SPL characteristics
===========================

- Object/services design
- Component based
- Developed in C++
- Applications built in XML
- Multi platforms (Windows, Linux, OSX, Android)
- Depends on many open source libraries: boost, Qt, VTK, ITK, gdcm, dcmtk, libxml2,...
- Licensed under LGPL

----

FW4SPL history
=================

- 2004-2007 : fw4spl project
- 2007-2009 : **VRRender** 0.7 (free)
- 09/2009 : fw4spl became open-source (LGPL)
- 2010 : PoC **Sofa** (Altran-Est), VRRender WLE 0.8.1 (free)
- 2011 : PoC **Kinect** (Altran-Est), VRRender 0.9 (open)
- 2012 : Introduction of multithreading
- 2013 : Creation of a board (*IRCAD*, *IHU*, *Visible Patient*) to manage the evolution of fw4spl

----

:data-x: r-700

- 2013 : Creation of fw4spl external repository (for branch 0.9.1 and after)
- 2014 : Switch to **CMake** for building
- 2014 : Creation of **GitHub** and **Bitbucket** repositories
- 2014 : Partial **Android** support
- 2015 : Documentation generated on **ReadTheDocs.org**
- 2015 : Creation of a blog for developers

.. note::

    - VRRender: mesh/image viewer - mettre une image !

----

:data-y: r1500

FW4SPL board
=================

- IRCAD `<http://www.ircad.fr>`_
- IHU  `<http://www.ihu-strasbourg.eu>`_
- Visible Patient `<http://www.visiblepatient.com>`_

----

:data-y: r1500

FW4SPL statistics
=============================

UPDATE THAT

- Applications: 35 (PoC and Tutorials)
- Bundles: 52 (57 on private repository)
- Service number: 230 (380)
- Code line numbers: 220 000

----

:class: square-background
:data-x: r1500
:data-rotate-z: r90

Outline
==================================================================

- Introduction
- *Object/Service approach*
- Component based approach
- Communication
- Community

.. note::

    - Introduction - 5min
    - Object/Service approach - 10 min
    - Component based approach - 5min
    - Communication - 10min 
    - Community - 5min
    - Conclusion - 5min

----

:data-x: r1500

What is the Object/Service approach ?
==================================================================

----

:data-x: r1500

Classic approach
====================

- an object (i.e. an image) is represented by a class.
- this class contains all functionalities working on the object (reading, writing, visualization,image analysis, ...)

----

:class: centered
:data-y: r500
:data-scale: 0.45


.. image:: images/Image.png
           :width: 80%


----

:class: centered
:data-y: r300


.. image:: images/Image01.png
           :width: 80%
       
----

:data-y: r200
:data-scale: 1

|
|
|

.. code:: c++


    void readImageFromPacsWithDcmtk( ... )
    {
        // Load an image using dcmtk
        Dcmtk::Image img;
        
        // ...

        // Convert dcmtk image data in our format
        m_buffer = dcmtkHelper::getBuffer(img);
        m_size = dcmtkHelper::getSize(img);
    }
    
----

:class: centered
:data-scale: 0.45
:data-x: r1100
:data-y: r-200

.. image:: images/Image02.png
           :width: 80%

----

:data-y: r220
:data-scale: 1

|
|
|

.. code:: c++

    void cropImageWithItk( ... )
    {
        // Convert our data to an itk image
        Itk::Image imgIn = itkHelper::getImage(m_buffer, m_size);

        // Crop an img using library itk 
        // ...

        // Convert itk image data in our format
        m_buffer = itkHelper::getBuffer(imgOut);
        m_size = itkHelper::getSize(imgOut );
    }

----

:class: centered
:data-scale: 0.45
:data-x: r1300
:data-y: r-200

.. image:: images/Image03.png
           :width: 80%

----

:data-y: r220
:data-scale: 1

|
|
|

.. code:: c++

    void windowingImageWithOpenCV( ... )
    {
        // Convert our data to a OpenCV image
        OpenCV::Image imgIn = openCVHelper::getImage(m_buffer, m_size);

        // Apply windowing using OpenCV
        // ...

        // Convert openCV image data in our format
        m_buffer = openCVHelper::getBuffer(imgOut);
        m_size = openCVHelper::getSize(imgOut);
    }

----

:class: centered
:data-scale: 0.45
:data-x: r1400
:data-y: r-200

.. image:: images/Image04.png
           :width: 80%

----

:data-scale: 1
:data-y: r200

|
|
|

.. code:: c++

    void visuWithVtkAndQt( ... )
    {
        // Convert our data to a vtk image
        Vtk::Image img = vtkHelper::getVtkImage(m_buffer, m_size);

        // Open a Qt frame and show a negato using vtk and Qt
    }

----

:data-scale: 0.7
:data-y: r-350

.. code:: c++

    Image* img = new Image();
    img->readFromPacsWithDcmtk( patientInfo, pacsInfo );
    img->cropWithItk( cropParam );
    img->windowingImageWithOpenCV( windowParam );
    img->visuWithVtkAndQt( visuParam );

|
|
|


----

:data-x: r1500

Limits of this approach
============================================================

- Too many methods in the class, hard to maintain 
- Many dependencies required even if you only need a single method.
- Collaborative work harder

Solution
***********
- Split data and functions
- Put them in different files and libraries

.. note::

    - Too many functions, if team continue to add functions or if you split your main functions to have a better visibility
    - Many dependencies required (itk,vtk,qt,dcmtk,...) even if you need just cropping an image
    - Everyone work on the same file

----

:class: centered
:data-scale: 1
:data-x: r1000
:data-y: r-200

*Object contains data only*

*Helpers are static methods*

.. image:: images/helper01.png
           :width: 120%

----

:data-y: r200
:data-scale: 1

|
|
|

.. code:: c++

    Image* img = new Image();
    DcmtkHelper::readFromPacs(img, patientInfo, pacsInfo);
    ItkHelper::crop(img, cropParam);
    OpenCVHelper::window(img , windowParam);
    VtkQtHelper::visu(img, visuParam);

----

:class: centered
:data-scale: 1
:data-x: r1500
:data-y: r-200

*Helpers can be instantiated*

.. image:: images/helper02.png
           :width: 120%

----

:data-y: r300
:data-scale: 1

|
|
|

.. code:: c++

    Image* img = new Image();
    VtkQtHelper* visuHelper = new VtkQtHelper();
    visuHelper->initVisu(img, visuParam);
    
    DcmtkHelper::readFromPacs(img, patientInfo, pacsInfo);
    visuHelper->refresh();
    
    ItkHelper::crop(img, cropParam);
    visuHelper->refresh();
    
    OpenCVHelper::window(img, windowParam);
    visuHelper->refresh();
    
    
    
----

:class: centered
:data-scale: 0.8
:data-x: r1500
:data-y: r-200

*Group helpers by type*

.. image:: images/helper03.png
           :width: 130%

----

:data-y: r530
:data-scale: 1

|
|
|

.. code:: c++

    Image* img = new Image();
    
    IVisu * visu = new VtkQtVisu();
    visu->setVisuParam(img, visuParam );
    visu->init();
    
    IReader* reader = new DcmtkReader();
    reader->setReaderParam(img, patientInfo, pacsInfo );
    reader->read();
    
    IOperator* op1 = new ItkCropOperator();
    op1->setOperatorParam(img, cropParam);
    op1->compute();
    visu->refresh();
    
    IOperator* op2 = new OpenCVWindowOperator();
    op2->setOperatorParam(img, windowParam);
    op2->compute();
    visu->refresh();
    
----

:class: centered
:data-scale: 0.8
:data-x: r1500
:data-y: r-200

*Common interface for all services*

.. image:: images/IService01.png
           :width: 60%

----

:class: li1
:data-y: r380
:data-scale: 1

- setObject(obj) : set the object associated
- setConfiguration(cfg) : set the service parameters
- configure() : verify parameters and configure service
- start() : init/launch the service
- update() : compute data, refresh, etc
- stop() : close the service

----

:class: centered
:data-scale: 1
:data-x: r1500
:data-y: r-200

*Group helpers by type*

.. image:: images/IService02.png
           :width: 120%
       
----

:data-scale: 0.15
:data-x: r-50
:data-y: r360

DcmtkReaderSrv
================
    
- setConfiguration(cfg) : set a string that represents the url on network
- configure() : verify if url is ok
- start() : do nothing
- update() : read the data ( equivalent to **readImageFromPacsWithDcmtk()** )
- stop() : do nothing

----

:data-x: r165

ItkCropOperatorSrv
===================
    
- setConfiguration(cfg) : set a cropping region
- configure() : verify if the cropping region is valid
- start() : do nothing
- update() : compute the cropping on image and set the new data (equivalent to **cropImageWithItk** )
- stop() : do nothing

----

:data-x: r360

VtkQtVisuSrv
===================
    
- setConfiguration(cfg) : set title and window size
- configure() : verify if the screen support this size
- start() : initialize Qt frame and vtk pipeline and show the frame (image is not shown if image buffer is null )
- update() : check if the buffer has be changed, if true, refresh the vtk pipeline to show negato
- stop() : destroy vtk pipeline and uninitialize Qt frame.

----

:data-x: r-260
:data-y: r160

Program
===================

.. code:: c++

    Object* img = new Image();
    IService* visu = new VtkQtVisuSrv();
    visu->setObject( img );
    visu->setConfiguration( visuParam );
    visu->start();
    
    IService* reader = new DcmtkReaderSrv ();
    reader->setObject( img );
    reader->setConfiguration( readerParam );
    reader->start();
    reader->update();
    visu->update();
    
    IService* op1 = new ItkCropOperatorSrv ();
    op1->setObject( img );
    op1->setConfiguration ( cropParam );
    op1->start();
    op1->update();
    visu->update();
    
    IService* op2 = new OpenCVWindowOperatorSrv();
    ...

.. note::
    - And now ? What's the next step
    
----

:class: text-small
:data-y: r600
:data-scale: 1

Use the factory pattern...
================================

.. code:: c++

    IService* Factory::createServiceInstance(const char* implName)
    {
        if ( implName == "DcmtkReaderSrv" )
        {
            return new DcmtkReaderSrv();
        }
        else if ( implName == "ItkReaderSrv" )
        {
            return new ItkReaderSrv();
        }
        else if
        {
            // ...
        }
    }
    
----

:class: text-small
:data-y: r500

.. code:: c++

    void main(int argc, char *argv[])
    {
        string srvReaderImpl ( argv[1] );
        string imgPath ( argv[2] );
        
        Object* img = new Image();

        // Call to the Factory
        IService* reader = Factory::createServiceInstance( srvReaderImpl );
        
        reader->setObject( img );
        reader->setConfiguration( imgPath );
        reader->configure(); // check if the path is correct
        reader->start(); // a service must be start before updating it
        reader->update(); // read image

        // ...
        reader->stop();
    }
    
----

:class: text-small
:data-x: r1200

Factory for the object creation
================================

.. code:: c++

    void main(int argc, char *argv[])
    {
        string objImpl ( argv[1] );
        string srvImpl ( argv[2] );
        string config  ( argv[3] );
        
        Object * obj = Factory::createObjectInstance( objImpl );
        IService * srv = Factory::createServiceInstance( srvImpl );
        srv->setObject( obj );
        srv->setConfiguration( config );
        srv->configure();
        srv->start();
        srv->update();
        srv->stop();

        // ...
    }
    
----

:class: text-small
:data-x: r1200

Example with reader and visualization
======================================

.. code:: c++

    void main(int argc, char *argv[])
    {
        string objImpl ( argv[1] );

        string srvImpl1 ( argv[2] ); // Reader
        string srvCfg1  ( argv[3] );

        string srvImpl2 ( argv[4] ); // Visu
        string srvCfg2  ( argv[5] );
        
        Object * obj = Factory::createObjectInstance( objImpl );
        
        IService * srv1 = Factory::createServiceInstance( srvImpl1 );
        srv1->setConfiguration( srvCfg1 );
        srv1->configure();
        srv1->start();  // Start reader ( do nothing )

        IService * srv2 = Factory::createServiceInstance( srvImpl2 );
        srv2->setConfiguration( srvCfg2 );
        srv2->configure();
        srv2->start(); // Start Visu

        srv1->update(); // Read image on filesystem
        srv2->update(); // Refresh vusalisation with the new image buffer
        // ...
        srv1->stop();
        srv2->stop();
    }
    
    
----

Last step
======================================

*Declaring objects and services from the command line is not really convenient...*

- Grab all objects and services from a file
- XML syntax


----

XML based launcher
======================================

.. code:: c++

    void main(int argc, char *argv[])
    {
        string xmlAppConfigPath = argv[1];

        XmlConfigManager xcm ( xmlAppConfigPath );
        
        xcm->createObjectsAndServices();
        xcm->startServices();
        xcm->updateServices();
    }
    
----

:class: text-small

XML configuration file
======================================

.. code:: xml

    <object type="::fwData::Image">

        <service uid="myFrame" impl="DefaultFrame" type="IFrame" >
            <gui>
                <frame>
                    <minSize width="800" height="600" />
                </frame>
            </gui>
            <registry>
                <view uid="myVisu" />
            </registry>
        </service>

        <service uid="myVisu" impl="vtkSimpleNegatoRenderer" type="IRender" />
        
        <service uid="myReader" impl="VtkImageReader" type="IReader" >
            <filename path="./TutoData/patient1.vtk"/>
        </service>

        <start uid="myFrame" />
        <start uid="myVisu"/>
        <start uid="myReader"/>

        <update uid="myReader"/>    <!-- Read the image on filesystem -->
        <update uid="myVisu"/>      <!-- Refresh the visu -->

    </object>
    
----

Problem
==============

Now the reader must be called by UI
****************************************************

- We can no longer call **update()** from the xml
- *How to automate the call ?*

----

:class: square-background
:data-y: r1500
:data-rotate-z: 90

Outline
==============================

- Introduction
- Object/Service approach
- *Communication*
- Component based approach
- Getting started

.. note::

    - Introduction - 5min
    - Object/Service approach - 10 min
    - Communication -5min 
    - Component based approach - 5min
    - Community - 10min
    - Conclusion - 5min
    
    
----

:data-y: r1500

Communication
===================

- *Signals/Slots*
    - Data -> Service
    - Service <-> Service
- Introduced in 0.9.2
- Replace the old messaging system
- Will be the only mechanism after 0.10.2

----

Features
===================

- Signal emission is either:
    - synchronous
    - asynchronous
- A slot can be executed on a specific worker thread

----

:class: centered

.. image:: images/sigslot.png
           :width: 100%
           :align: center
           
|
|
|
|
|
|

----

:class: text-small
:data-x: r-10
:data-y: r-150
:data-scale: 0.6

.. code:: c++

    void DcmtkReaderSrv::update()
    {
        // Load an image using dcmtk
        Dcmtk::Image img;
        ... 
        
        Image* img = this->getObject<Image>();
        
        // Convert dcmtk image data in our format
        img->createImage(img, size);
        
        // Emit the signal "modified"
        Signal* sig = img->signal("modified");
        sig->asyncEmit();
    }
      
----

:class: text-small
:data-x: r-40
:data-y: r350

.. code:: xml

    <object uid="imageUID" type="::fwData::Image">
        
        ...

        <service uid="myVisu" impl="vtkSimpleNegatoRenderer" type="IRender" />
        
        <service uid="myReader" impl="VtkImageReader" type="IReader" >
            <filename path="./TutoData/patient1.vtk"/>
        </service>
        
        <start uid="myFrame" />
        <start uid="myVisu"/>
        <start uid="myReader"/>

        <connect>
            <slot>imageUID/modified</slot>
            <signal>myVisu/update</signal>
        </connect>
            
    </object>
    
----

:class: square-background
:data-y: r1500
:data-rotate-z: 180

Outline
================================

- Introduction
- Object/Service approach
- Communication
- *Component based approach*
- Community
- Conclusion

.. note::

    - Introduction - 5min
    - Object/Service approach - 10 min
    - Communication -5min 
    - Component based approach - 5min
    - Community - 10min
    - Conclusion - 5min
    
----

:data-x: r-1500

Component based approach
========================

Benefits
***********

- Reuse code in another application, without recompiling your program
- Easier support (ex: correction of bug) of your program
- Easier collaborative work
- To split code and to improve external dependencies management (vtk, itk, qt, wx, ...)

----

Examples
========================

- Eclipse
- Applications with plugins (Firefox)
- More !

----

Component in FW4SPL
========================

- Group services, by thema and/or by dependency
- Also called *Bundle*
- Examples: 
    - **ioITK**: reading/writing image or mesh data with ITK formats
    - **uiImageQt**: user interface controls using Qt to manipulate images

----

Content of a Bundle
========================

- Xml description file ( plugin.xml ) to describe the content of the dynamic library
- Dynamic libraries ( .so, .dll, .dylib)
- Other shared resources ( icons, sounds, ... )

----

:class: text-small

Extract of plugin.xml (ioITK)
==============================

.. code:: xml

    <plugin id="ioITK" class="ioITK::Plugin">
        <library name="ioITK" />

        <requirement id="io" />
        <requirement id="gui" />

        <extension implements="::fwServices::registry::ServiceFactory">
            <type>::io::IReader</type>
            <service>::ioITK::InrImageReaderService</service>
            <object>::fwData::Image</object>
            <desc>Inrimage Reader (ITK/Ircad)</desc>
        </extension>

        <extension implements="::fwServices::registry::ServiceFactory">
            <type>::io::IWriter</type>
            <service>::ioITK::InrImageWriterService</service>
            <object>::fwData::Image</object>
            <desc>Inrimage Writer (ITK/Ircad)</desc>
        </extension>

        <extension implements="::fwServices::registry::ServiceFactory">
            <type>::io::IWriter</type>
            <service>::ioITK::JpgImageWriterService</service>
            <object>::fwData::Image</object>
            <desc>Jpeg Writer (ITK)</desc>
        </extension>
        ...
    </plugin>

.. note::
    - This shows how to register services in the factory
    - Don't talk about extension points
    
----

Example : I/O Bundles
==============================

.. raw:: html

       <video width="800" height="600" controls>
          <source src="../git/RMLL/videos/component.mp4" >
          Your browser does not support the video tag.
       </video>

----

:class: square-background
:data-y: r-20500
:data-rotate-z: 270

Outline
==================================================================

- Introduction
- Object/Service approach
- Communication
- Component based approach
- *Discussion*
- Getting started

.. note::

    - Introduction - 5min
    - Object/Service approach - 10 min
    - Communication -5min 
    - Component based approach - 5min
    - Community - 10min
    - Conclusion - 5min
    
----

:data-y: r-1500

Discussion
================================

*We have introduced services*

**Cons**

- Think design differently
- Need to write a new class for each new function

**Pros**

- Far less coupling !
- No need for a public and private API

----

*How to share common code ?*

- We still have regular shared libraries

----

:class: square-background
:data-rotate-z: 90
:data-x: r1500

Outline
==================================================================

- Introduction
- Object/Service approach
- Communication
- Component based approach
- Discussion
- *Getting started*

----

:data-y: r1500

Where can I find documentation ?
========================================

- Documentation `<http://fw4spl-doc.readthedocs.org/>`_
- Developper blog `<http://fw4spl-org.github.io/fw4spl-blog/>`_ 

----

Where can I download FW4SPL ?
==============================

- Github : `<https://github.com/fw4spl-org>`_
- BitBucket : `<https://bitbucket.org/fw4splorg>`_
- Do not use the obsolete googlecode page `<https://code.google.com/p/fw4spl/>`_ 

----

Which version to use ?
=========================

Current stable version
**************************
- 0.10.1

Current development version
******************************
- 0.10.2
- Strongly advised for new software (communication API is simpler)
- For now need patches repositories, only available on bitbucket

.. code:: bash

    hg qclone https://bitbucket.org/fw4splorg/fw4spl-patches

----

Repositories
================

Dependencies
*************

- Main : *fw4spl-deps*
- Extended : *fw4spl-deps-ext*
- Augmented reality : *fw4spl-deps-ar*

Sources
*************

- Main : *fw4spl*
- Extended : *fw4spl-ext*
- Augmented : *fw4spl-ar*

----

Main repository
================

- Basic data (Float, Integer, String, Image, Mesh,... )
- GUI (Qt)
- Data I/O (JSON, DICOM (gdcm), VTK, Inr)
- 2D rendering (Qt)
- 3D rendering (VTK)
- Around 15 tutorials

----

:data-x: r-320

.. raw:: html

       <video width="800" height="600" controls>
          <source src="../git/RMLL/videos/tutos.mp4" >
          Your browser does not support the video tag.
       </video>
       
- Medical images viewer : **VR-Render**

----

:data-x: r-350


.. raw:: html

       <video width="800" height="600" controls>
          <source src="../git/RMLL/videos/vrrender.mp4" >
          Your browser does not support the video tag.
       </video>

----

:data-y: r1500

Extended repository
=====================

- Timeline data
- DICOM (dcmtk)
- OpenIGTLink support

----

:data-x: r-300

.. raw:: html

       <video width="800" height="600" controls>
          <source src="../git/RMLL/videos/openigtlink.mp4" >
          Your browser does not support the video tag.
       </video>
       
----

:data-y: r1500

Augmented reality repository
=============================

- Video player (**QtMultimedia**): file, camera or network
- Tag-based video tracking (**Aruco**, **OpenCV**)
- *ARCalibration* : Camera calibration (mono, stereo)

----

:data-x: r-320

.. raw:: html

       <video width="800" height="600" controls>
          <source src="../git/RMLL/videos/tutos.mp4" >
          Your browser does not support the video tag.
       </video>
       
- *VideoTracking* : Video tracking

----

:data-x: r-350


.. raw:: html

       <video width="800" height="600" controls>
          <source src="../git/RMLL/videos/vrrender.mp4" >
          Your browser does not support the video tag.
       </video>


.. note::
    - VideoTracking requires a calibration

----

:data-y: r1500

Repositories
================

In September 2015
**************************

- Ogre3D integration : *fw4spl-Ogre3d*



