Setup Diplomat
======================

Getting a working copy of Diplomat
------------------------------------

In order to work with Diplomat, it is necessary to have both:

* The VS Code extension
* The language server

Both of those can be either build from sources or found compiled on github.

.. note:: The server is developped and built on modern Linux (Ubuntu 22.04). 
    Therefore the more old linux may not support running the pre-built server out of the box.

    The server has been seen working, after a fairly tedious setup, on RedHat (RHEL) 7. 

The VS Code extension should work regardless of the system VS Code is running on. 

Pre-built binaries
.....................................

Pre-built binaries are produced each time a relevant version is pushed to github. They can be found in:
* https://github.com/suzizecat/diplomat-vscode/releases For the VS Code extension.
* https://github.com/suzizecat/slang-lsp-tools/releases For the language server

At this point in time, the dev release may be used as safely as the "real" releases.

Be aware that the backward compatibility is **not** enforced across versions yet.
While attention is placed on not removing support and trying to keep this backward compatibility, there is no 
actual API freeze yet. 

Build from source
.....................................

VS Code extension
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Download the sources from https://github.com/suzizecat/diplomat-vscode/

The VS Code extension requires a node.js distribution. The rest of the build should be self contained.
You only requires a VS Code that handle Language Server Protocol 3.17 

.. code-block:: text

    git clone git@github.com:suzizecat/diplomat-vscode.git
    cd diplomat-vscode
    npm install
    npm run publish
    code --install-extension diplomat-host*.vsix


The extension will start once you open a SystemVerilog file in VS Code. 

Language server
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

In order to build the language server you will require:

* Git
* CMake 3.15 or newer
* A compiler able to handle C++20 (In my case, GCC 11 or 12)
* A compiler system such as Gnu Make

You may optionally use the ``mold`` linker. 

External dependencies should be packaged using the provided CMakeList, so no external library should be required.

.. code-block:: text
    
    git clone git@github.com:suzizecat/slang-lsp-tools.git
    cd slang-lsp-tools
    cmake -DCMAKE_BUILD_TYPE=Release -B./build
    cmake --build ./build --target slang-lsp -j `nproc`


The result file should be ``./build/slang-lsp``.

You may check that everything works fine by running the server:

.. code-block:: console

    user:~/$ ./build/slang-lsp --tcp
    [2024-08-04 15:15:09.862] [info] Await client on port 8080...

To exit the server, simply issue ``Ctrl-C``.

If you wish to use ``mold`` as a linker, please use ``-DDIPLOMAT_USE_MOLD=ON`` on the configuration step.
Also, you may specify the version shown when running ``slang-lsp --version`` by using (at configuration stage) ``DDIPLOMAT_VERSION=<the version>``.
To get the default behavior, use  ``DDIPLOMAT_VERSION=auto`` when reconfiguring, or omit the option on a clean configuration.

.. note:: The configuration step will pull all dependencies from github, which may take some time.

    It is recomended to re-run ``cmake -DCMAKE_BUILD_TYPE=Release -B./build``  each time a new version is pulled, 
    to ensure that any change in CMakeList or ``third-party.cmake`` will be taken into account. 

