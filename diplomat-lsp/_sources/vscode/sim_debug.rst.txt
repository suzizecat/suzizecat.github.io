Simulation debug features
===========================

Open waveform in viewer
---------------------------

For all supported waveform type, Diplomat provides a shortcut to directly open the waveform in the appropriate external viewer.

.. figure:: /img/open_wave_dark.png
    :figclass: only-dark
    :align: center
    :scale: 75%

    Open waveform menu

.. figure:: /img/open_wave_light.png
    :figclass: only-light
    :align: center
    :scale: 75%

    Open waveform menu

.. note:: As of today, only GTKWave 3 is supported

Hierarchy explorer
---------------------
Once the workspace has been properly analyzed, the hierarchy explorer will show the hierarchy tree of the workspace.
If no top-level file is selected, all potential top-level modules will be shown in the tree.

.. figure:: /img/hier_explorer_dark.png
    :figclass: only-dark
    :align: center

    Hierarchy explorer view

.. figure:: /img/hier_explorer_light.png
    :figclass: only-light
    :align: center

    Hierarchy explorer view

Selecting an element in the hierarchy explorer will open the appropriate source file and select the instance for the :ref:`inline-value-display`, if enabled.

.. _inline-value-display:

Inline value display
----------------------

Diplomat Client is able, under some conditions, to display the value from a simulation within the source code.
This is done when:

1. A simulation which top-level module matches the workspace top-level is opened through Diplomat Client action.
2. A hierarchy level is selected in the Hierarchy Explorer

Once those conditions are met, the editor will display the simulation values for the selected time directly in the editor.
Changing the position of the marker will update the values in the editor.
The traces does not need to be displayed in the viewer for the values to be retrieved.

.. figure:: /img/inline_values_dark.png
    :figclass: only-dark
    :align: center

    Editor with inline value display enabled

.. figure:: /img/inline_values_light.png
    :figclass: only-light
    :align: center

    Editor with inline value display enabled

.. note:: As the value lookup is only meaninful in the context of the hierarchy, 
    please navigate your design using the Hierarchy explorer while usin gthe inline value display.