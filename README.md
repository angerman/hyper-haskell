# Welcome to HyperHaskell, [![Hackage](https://img.shields.io/hackage/v/hyper-haskell-server.svg)](https://hackage.haskell.org/package/hyper-haskell-server) [![Build Status](https://travis-ci.org/HeinrichApfelmus/hyper-haskell.svg?branch=master)](http://travis-ci.org/HeinrichApfelmus/hyper-haskell)

… the strongly hyped Haskell interpreter.

*HyperHaskell* is a graphical interpreter for the programming language [Haskell][]. You use worksheets to enter expressions and evaluate them. Results are displayed using HTML.

*HyperHaskell* uses the [GHC][] API to interpret Haskell programs. The graphical front-end is built on the cross-platform [Electron][] framework.

*HyperHaskell* is currently *Level α*.

  [haskell]: https://haskell.org
  [ghc]: https://www.haskell.org/ghc/
  [electron]: http://electron.atom.io/
  [stack]: https://www.haskellstack.org

*HyperHaskell* looks like this:

  <img src="docs/screenshots/worksheet-diagrams.png" height="500">

# Installation

HyperHaskell is currently in a pre-release state, you have to run it from source.

## Overview

A HyperHaskell installation consists of two parts:

1. The graphical front-end.

    Currently written in HTML and JavaScript, packaged with the [Electron][] framework.

2. The interpreter back-end.

    Consists of an executable `hyper-haskell-server`,
    written in Haskell using the [GHC API][ghc],
    and a library (module) `Hyper` for visualizing and pretty printing Haskell values.
    
    Both parts depend on several different Haskell packages.
    Unfortunately, the versions of the packages used to compile the executable
    and to compile the library have to be exactly the same.
    
    This is why, at the moment,
    the front-end does *not* come with the back-end executable included.
    Instead, the user is asked to install the `hyper-haskell-server` back-end
    into his or her own database of Haskell packates,
    and then tell the front-end about it.
    This way, the user is free to use different package or compiler versions.

## Run from source

To run HyperHaskell from source, follow these steps:

1. [Download and install Electron](http://electron.atom.io/releases/)

    The whole thing is currently developed and tested with Electron v1.4.0.

2. Make sure that you have a working installation of
    * the [GHC][] Haskell compiler
    * the [`stack`][stack] utility

    (See the [Haskell homepage][haskell] for more on how to obtain these.)

3. You also need the `make` utility, which should be standard on any UN*X platform. Edit the file named [`Makefile`](Makefile) and tell it where to find the Electron executable

    On OS X: Typically,

        ELECTRON=/Applications/Electron.app/Contents/MacOS/Electron

    On Linux: ??
    
    On Windows: ??

4. Go into the root directory of this repository and type `make run`.

        $ cd hyper-haskell
        $ make run

    This will call the `stack` utility to build the server back-end,
    and finaly run the front-end.

5. Use the *File* menu to open one of the example worksheets from the [worksheets](worksheets/) folder. Voilà!

    You can also create a new worksheet, but note that you have to set the back-end path. In this case, you can use the path local to this repository, `./haskell/stack.yaml`, like this:
    
    ![Settings](docs/screenshots/settings-back-end.png)

    

# Contributors

The project was started by *Heinrich Apfelmus*.