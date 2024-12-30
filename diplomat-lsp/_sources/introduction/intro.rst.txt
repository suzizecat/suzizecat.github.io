Introduction
============

Diplomat is a bundle of tools used to ease the development and debugging of SystemVerilog designs.
While its aim is to be as complete and useful as possible in a seamless and straightforward way, 
it cannot be guaranteed to work without bugs or issues.

If you found bugs, usability problems or missing features, please drop a word by raising an issue against the element that seems to cause an issue:
 * The `VSCode extension <https://github.com/suzizecat/diplomat-vscode/issues>`_ is reponsible for the GUI and everything not related to code analysis proper.
 * The `Language server <https://github.com/suzizecat/slang-lsp-tools/issues>`_ is reponsible for providing informations about the design to the extension.


VS Code extension
------------------


The Diplomat VS Code extension (*Diplomat Client*, sometimes refered as *Diplomat Host*)
is the provided client for interfacing with Diplomat Server.

It features:
 * Workspace analysis using the `slang <https://github.com/MikePopoloski/slang>`_ open source SystemVerilog compiler.
 * Error checking and elaboration-level linting
 * Scope-aware autocompletion suggestions
 * Jump to definition/reference across files
 * Syntax coloration
 * Rename symbol
 * Assisted instanciation of any module found in the workspace


Language server
------------------

The Diplomat language server is a full C++ implementation of the *Language Server Protocol* (LSP) targetting SystemVerilog.
It relies on `slang <https://github.com/MikePopoloski/slang>`_ to perform code analysis and elaboration.
