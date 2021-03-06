.. _common-kde-can-escs:

============
KDE CAN ESCs
============

.. image:: ../../../images/kde-can-esc.jpg

KDECAN ESCs are high-end ESCs that allow control and feedback using a custom CAN protocol

.. note::

    Support for these ESCs is included in Copter-3.7 (and higher), Plane-3.10 (and higher) and Rover-3.5 (and higher)

Where To Buy
------------

- `KDE-UAS125UVC <https://www.kdedirect.com/collections/uas-multi-rotor-electronics/products/kde-uas125uvc>`__ and `KDE-UAS85UVC <https://www.kdedirect.com/collections/uas-multi-rotor-electronics/products/kde-uas85uvc>`__ can be purchased from `KDEDirect.com <https://www.kdedirect.com/collections/uas-multi-rotor-electronics>`__ (other KDE ESCs may also support CAN, check the images of the ESC, those with "CAN" written on the side should work).
- `KDECAN Wire Kit <https://www.kdedirect.com/collections/kdecan-bus-cables/products/kdecan-ph-kit>`__ is also required

Connection and Configuration
----------------------------

`KDE's instructions for connecting and configuring with ArduPilot are here <https://cdn.shopify.com/s/files/1/0496/8205/files/KDECAN_Pixhawk_QuickStart.pdf>`__

.. image:: ../../../images/kde-can-esc-cube.jpg
    :target: ../_images/kde-can-esc-cube.jpg
    :width: 400px

- ESCs should be daisy chained together using the KDECAN Wire Kit.  One 4-pin CAN cable should be connected to the flight controller's CAN port.  The CAN terminator (the 4-pin connector with a black loop) should be connected to the last ESC in the chain

.. warning::

    If using a Cube autopilot, the CAN1 and CAN2 labels are reversed.  These instructions assume the ESCs are connected to the CAN1 port which is labelled "CAN2" on Cube autopilots

- Set :ref:`CAN_D1_PROTOCOL <CAN_D1_PROTOCOL>` = 2 (KDECAN)
- Set :ref:`CAN_P1_DRIVER <CAN_P1_DRIVER>` = 1 (First driver) to specify that the ESCs are connected to the CAN1 port
[site wiki="copter,rover"]
- Set :ref:`MOT_PWM_MIN <MOT_PWM_MIN>` = 1000 and :ref:`MOT_PWM_MAX <MOT_PWM_MAX>` = 2000 so ArduPilot uses an output range that matches the ESCs input range
[/site]
- Set ``SERVOx_MIN`` = 1000 and ``SERVOx_MAX`` = 2000 for each ESC connected (``x`` corresponds to the ESC number) so ArduPilot uses an output range that matches the ESCs input range
