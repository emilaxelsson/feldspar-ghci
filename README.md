# Introduction

This package provides a script for loading Feldspar-related packages in GHCi. The motivation is that using GHCi is usually much faster than going through Cabal when making changes across several packages simultaneously.

The script can be used with [ghccheck](https://github.com/emilaxelsson/ghccheck) which is a tool for compiling Haskell code for the purpose of just syntax and type checking. Ghccheck solves the problem that loading in GHCi can require a lot of memory, and that every new GHCi session has to recompile from scratch.

The script also gives a common list of all "innocent" extensions used in Feldspar-related packages avoiding the need for long list of pragmas at the beginning of each Haskell file. Less innocent extensions, such as the following, are not included in the script and have to be turned using pragmas where needed:

    CPP
    OverlappingInstances
    QuasiQuotes
    TemplateHaskell
    UndecidableInstances

# Usage

We assume a setting in which all packages are located in a common directory, e.g. `$HOME/Project`. (This assumption is coded also in the relative paths in the [script](feldspar-ghci).)

Check out this repository in the project directory:

    git clone git@github.com:emilaxelsson/feldspar-ghci.git

Next, in any package where you want to use [`feldspar.ghci`](feldspar.ghci), add a `.ghci` file with the following content:

    :script ../feldspar-ghci/feldspar.ghci

If you want to use an installed version of some package, just comment out the corresponding include path in the script; e.g.

    -- :set -i../syntactic/src

