Development features
====================

Code analysis
-------------------
Diplomat client relies on the `slang <https://github.com/MikePopoloski/slang>`_ open source SystemVerilog compiler to analyze code, through Diplomat Server.
It allows a management in C++ and offer great performances.

Slang also provides a great support of SystemVerilog syntax, and not only Verilog.
The supported language features are listed `in the slang documentation <https://sv-lang.com/language-support.html>`_. 

The errors and warnings reported by slang will be returned to the editor and shown with squiggle lines in the editor and in the *Problems* view of VSCode.

.. figure:: /img/error_reporting.png
    :align: center

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