Supported standard LSP commands
===============================

The commands provided here are standard commands from the `Language Server Protocol specification <https://microsoft.github.io/language-server-protocol/>`_
The server will reply accordingly to the standard to the requests listed bellow.
Other request will be ignored.

As of today, the language server implements the standard version 3.17

``initialize`` request
----------------------
See `the LSP specification for initialize <https://microsoft.github.io/language-server-protocol/specifications/lsp/3.17/specification/#initialize>`_

``initialized`` notification
------------------------------
See `the LSP specification for initialized <https://microsoft.github.io/language-server-protocol/specifications/lsp/3.17/specification/#initialized>`_

Upon receiving this notification, the language server will request some configurations if the ``workspace/configuration`` request is 
supported by the client. 

``exit`` notification
----------------------
See `the LSP specification for exit <https://microsoft.github.io/language-server-protocol/specifications/lsp/3.17/specification/#exit>`_

``shutdown`` request
----------------------
See `the LSP specification for shutdown <https://microsoft.github.io/language-server-protocol/specifications/lsp/3.17/specification/#shutdown>`_

``textDocument/didOpen`` notification
-----------------------------------------------------


``textDocument/didSave`` notification
-----------------------------------------------------
See `the LSP specification for textDocument/didSave <https://microsoft.github.io/language-server-protocol/specifications/lsp/3.17/specification/#textDocument_didSave>`_

Upon receiving this notification, the language server will re-run a workspace analysis and refresh all diagnostics.


``textDocument/definition`` request
-----------------------------------------------------


``textDocument/references`` request
-----------------------------------------------------


``textDocument/rename`` request
-----------------------------------------------------


``textDocument/formatting`` request
-----------------------------------------------------
Invoke the internal formatter.

.. warning:: This is under development and the result may not be of great quality.

.. warning:: The range formating is not available and the file shall be saved before running this command.

``workspace/didChangeWorkspaceFolders`` notification
-----------------------------------------------------

``textDocument/publishDiagnostics`` notification
-----------------------------------------------------
See `the LSP specification for textDocument/publishDiagnostics <https://microsoft.github.io/language-server-protocol/specifications/lsp/3.17/specification/#textDocument_publishDiagnostics>`_

The ``textDocument/publishDiagnostics`` notification is actually sent by the server in order to provide the diagnostic results after a successful workspace analysis

``workspace/executeCommand`` notification
-----------------------------------------------------

