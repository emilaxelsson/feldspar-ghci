# Introduction

This package provides a scripts for loading Feldspar-related packages in GHCi. One motivation is that using GHCi (or `ghccheck`; see below) is usually much faster than using Cabal, especially when making changes across several packages simultaneously. Another motivation is to give a common definition of all "innocent" extensions used in Feldspar-related packages avoiding the need for long list of pragmas at the beginning of each Haskell file. Less innocent extensions, such as the following, are not included in the script and have to be turned using pragmas where needed:

    CPP
    OverlappingInstances
    QuasiQuotes
    TemplateHaskell
    UndecidableInstances

The script can be used with [ghccheck](https://github.com/emilaxelsson/ghccheck) which is a tool for compiling Haskell code for the purpose of just syntax and type checking. `ghccheck` solves the problem that loading in GHCi can require a lot of memory and that every new GHCi session has to recompile from scratch.

# Usage

We assume a setting in which all packages are located as sub-directories in a common directory. (This assumption is coded also in the relative paths in the [feldspar-all.ghci](feldspar-all.ghci).)

Check out this repository in the project directory:

    git clone git@github.com:emilaxelsson/feldspar-ghci.git

In any package where you want to use the GHCi scripts, just add a `.ghci` file with the following content:

    -- :script ../feldspar-ghci/feldspar.ghci
    -- :script ../feldspar-ghci/feldspar-all.ghci

Uncomment the first line when you only want to load the current package and use installed versions of the other packages. Uncomment the second line when you want to make changes across several packages and be able to dynamically reload them in GHCi/`ghccheck`.
