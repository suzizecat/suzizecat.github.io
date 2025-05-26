VS Code provided contribution points 
====================================

Diplomats uses several functions, context keys and such.
Those are documented here.

Context keys
------------


``diplomat-host:enabled``
.....................................

Is set at the end of the activation of Diplomat Host.
Is should be used to act on the extension being up and running.

This is set to ``true`` at the end of a proper initialization and set to ``false`` upon deactivation.

.. _Contrib.followWave:

``diplomat-host:followWaveSelection``
.....................................

This context key provide information about the "Wave Following" feature.
If set, selecting a signal in the waveform viewer (if any) should make the editor follow to the signal declaration (or any relevant location).


``diplomat-host:supportedDesignFiles``
......................................

This context key provides the list of the extensions that are expected to be supported by the LSP and the underlying functions.

In particular, this is used to setup the menu actions such as "set as top". 

``diplomat-host:supportedWavesFiles``
......................................

This context key provides the list of waveform files extension that are supported by the currently loaded(s) waveform viewer(s).

This is used to setup the menu action of "Open in waveform viewer"

``diplomat-host:viewerEnabled``
......................................

This context key indicate that a viewer is setup and currently running, thus enabling all features linked to waveform viewer.

This key should be set to ``true`` by the underlying waveform viewer and **shall** be reset upon closing the waveform viewer.


``diplomat-host:viewerCanFollowSignal``
.........................................

This context key indicate that the waveform viewer is able to notify the host that a signal has been selected, and to provide
the signal complete hierarchy, so that the extension can lookup the signal definition.

It complements :ref:`contrib.followwave`.