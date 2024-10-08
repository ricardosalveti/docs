.. _ref-factory-sources:

Factory Source Code
===================

The FoundriesFactory provides you with a private git sandbox which allows you
to maintain and customize your platform.

Navigate to https://source.foundries.io/factories/<factory>/

.. figure:: /_static/factory-cgit.png
   :alt: Source code navigation
   :align: center
   :width: 5in

   CGit browser

You will find four git repositories, below is a brief description of each one.

.. Glossary::

   meta-subscriber-overrides.git
     This OE layer defines what is included into your factory image. You can add
     board specific customizations and override, add and remove packages provided
     in the default Linux microPlatform base.

   lmp-manifest.git
     The repo manifest for the platform build. It defines which layer versions
     are included in your platform image. The ``default.xml`` file is the latest
     released manifest of our Linux microPlatform, and the ``<factory>.xml``
     includes your factory changes which allows you to customize your image
     against our common base.

   containers.git
     This is where containers and docker-compose apps are defined. It allows you
     to define what containers to build, and how to orchestrate them on the
     platform.  By default it will build containers for amd64, aarch64, and
     armhf architectures.

   ci-scripts.git
     Defines your platform and container build job to our continuous integration system
     which uses the data from ``master`` branch.

     The **ci-scripts.git** repository prevents a commit changing the ``lmp:machines:`` 
     stanza as well as any changes altering the history (force push is disabled).  
     Factories are created to support specific machines.
     If you need to alter this behavior after starting a FoundriesFactory, 
     please open a support ticket at: http://support.foundries.io/

Triggering Builds
~~~~~~~~~~~~~~~~~

If you push changes to either ``lmp-manifest.git`` or ``meta-subscriber-overrides.git``,
a new platform build will be triggered, and if successful will deploy the
update to any registered devices.

Any changes pushed to ``containers.git`` will trigger a container build job, and
any containers defined will be pushed to your factory’s private Docker
registry at:

 https://hub.foundries.io/<factory>/<container>:latest


.. note::

   Commit messages that include ``[skip ci]`` or ``[ci skip]`` will not
   trigger CI builds.
