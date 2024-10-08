.. _ref-rm_board_beaglebone-yocto:

Beaglebone Black
================

This tutorial covers both Beaglebone Black and Beaglebone Black Wireless.

.. include:: generic-prepare.rst

Flashing
--------

Now, flash the ``lmp-factory-image-beaglebone-yocto.wic.gz`` retrieved from the
previous section to an SD Card. This contains the :term:`system image` that the
device will boot.

By default Beaglebone Black boots from internal eMMC. There are several ways to
avoid this:

   * Press S2 button before powering on

     This causes boot sequence to start from SPI0 followed by SD card. If the
     board is not connected to any SPI boot source SD card should be used

   * Erase eMMC or disable 'bootable' flag on eMMC boot partition

.. include:: generic-flashing.rst
