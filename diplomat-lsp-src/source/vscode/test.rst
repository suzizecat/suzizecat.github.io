Testing features
===================

Cocotb tests discovery
-----------------------

Diplomat automatically discover tests from Cocotb testbenches.
This is done by looking up Makefiles in the workspace tree and then checking if they match a cocotb makefile.

The tests are then individually discovered and can be run using the built-in "Testing" pane of VS Code.


.. figure:: /img/testing_dark.png
    :figclass: only-dark
    :align: center

    Testing pane view

.. figure:: /img/testing_light.png
    :figclass: only-light
    :align: center

    Testing pane view

.. note:: Only files named ``Makefile`` containing the line ``include $(shell cocotb-config --makefiles)/Makefile.sim`` will be analyzed.

.. tip:: It is possible to select multiple tests to run and they will be lauched together.