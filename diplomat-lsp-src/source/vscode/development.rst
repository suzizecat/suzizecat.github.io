Development features
====================

Code analysis
-------------------
Diplomat client relies on the `slang <https://github.com/MikePopoloski/slang>`_ open source SystemVerilog compiler to analyze code, through Diplomat Server.
It allows a management in C++ and offer great performances.

Slang also provides a great support of SystemVerilog syntax, and not only Verilog.
The supported language features are listed `in the slang documentation <https://sv-lang.com/language-support.html>`_. 

The errors and warnings reported by slang will be returned to the editor and shown with squiggle lines in the editor and in the *Problems* view of VS Code.

.. figure:: /img/error_reporting_dark.png
    :align: center
    :figclass: only-dark

    Editor with reported errors

.. figure:: /img/error_reporting_light.png
    :align: center
    :figclass: only-light

    Editor with reported errors

The list of available warnings is provided `in the slang warning reference <https://sv-lang.com/warning-ref.html>`_.
Only the following warnings are ignored:

**Mismatched time scales** 
    Reports mismatched ```timescale`` statements, often not relevant as overriden at top level for the simulation.
    This is fairly annoying when dealing with source code comming from different sources.

**Missing time scale**
    Reports every file without the ```timescale`` statement. Generally omitted in design files, therefore ignored.

**Unused definition**
    Report every module found in the workspace that is not used in the design.
    Particularly annoying when working with a library of components and not really relevant in this context.

.. note:: When a top level module is specified, the design is elaborated before reporting the errors and warning. 
    Thus effectively ommiting diagnostics from file that are not used in the design.

Code navigation
--------------------

Using VS Code UI and Diplomat Language Server, the extension provides the *Go to definition*, *Go to reference* and *Find all references* features in the editor.
These functions will allow to:

* Go from a variable (net, parameter...) to its declaration statement (*Go to definition*)
* Go from a variable declaration to its reference if only one reference is found (*Go to reference*).
* Show all references of a given variable (*Find all references*)

Those actions are performed either through right-click menu in the editor, or by ``Ctrl+Click`` on any variable name in the editor.

.. figure:: /img/goto_dark.png
    :figclass: only-dark
    :align: center

    Go-to action triggered on the definition of a net.

.. figure:: /img/goto_light.png
    :figclass: only-light
    :align: center

    Go-to action triggered on the definition of a net.

.. tip:: 
    * ``Ctrl+Click`` on a reference will jump to its declaration.
    * ``Ctrl+Click`` on a definition will jump to its reference (if only one exists) or lookup all the references.
    * This feature works across files and on module ports.

Symbol renaming
----------------
Using VS Code UI, the extension is able to performs symbol renaming.
In editor, select a net and hit ``F2`` to trigger this feature.
All reference and the definition of the symbol will be renamed.

.. figure:: /img/rename_dark.png
    :align: center
    :figclass: only-dark

    Rename operation


.. figure:: /img/rename_light.png
    :align: center
    :figclass: only-light

    Rename operation

This is **not** a "Search and replace" function, as the lookup is done on symbols extracted from the elaborated design, while being aware of the context.
Therefore, renaming a net in a module will not affect nets from another module.
However, renaming a port will also affect the port name in all module instanctiations.

Module instanciaton
--------------------
Diplomat client povide an "Instanciate module" function, directly from the command palette.
This is invoked by using ``Ctrl+P > Instanciate Module``.
VS Code will then present a list of modules detected across the workspace, that may be instanciated.

.. note:: On large workspaces, there  might be few seconds between the command invocation and the selector popping up.

Selecting a module in the list will generate the instanciation statement where the editing cursor is located.