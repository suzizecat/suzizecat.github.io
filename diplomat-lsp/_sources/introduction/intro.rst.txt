Introduction
============

VS Code extension
------------------


The Diplomat VS Code extension (*Diplomat Client*, sometimes refered as *Diplomat Host*)
is the provided client for interfacing with Diplomat Server.

It features:
 * Workspace analysis using the `slang <https://github.com/MikePopoloski/slang>`_ open source SystemVerilog compiler.
 * Error checking and elaboration-level linting
 * Jump to definition/reference across files
 * Syntax coloration
 * Rename symbol
 * Assisted instanciation of any module found in the workspace


Language server
------------------

The Diplomat language server is a full C++ implementation of the *Language Server Protocol* (LSP) targetting SystemVerilog.
It relies on `slang <https://github.com/MikePopoloski/slang>`_ to perform code analysis and elaboration.
