<div id="table-of-contents">
<h2>Table of Contents</h2>
<div id="text-table-of-contents">
<ul>
<li><a href="#sec-1">1. Description</a></li>
<li><a href="#sec-2">2. Installation</a>
<ul>
<li><a href="#sec-2-1">2.1. Saga And haskell-platform</a>
<ul>
<li><a href="#sec-2-1-1">2.1.1. Linux</a></li>
<li><a href="#sec-2-1-2">2.1.2. Windows with Cygwin</a></li>
</ul>
</li>
<li><a href="#sec-2-2">2.2. saga-cmd-wrapper library</a></li>
</ul>
</li>
<li><a href="#sec-3">3. Usage</a>
<ul>
<li><a href="#sec-3-1">3.1. <code>sagaChain</code></a></li>
</ul>
</li>
<li><a href="#sec-4">4. Development</a></li>
</ul>
</div>
</div>

# Description

Haskell Library to wrap `saga_cmd`. This is *Work In Progress*

Currently there is one executable, `sagaChain` , which lets you
chain `saga_cmd`-commands.

These combinations are currently supported, where columns are
sources and rows destinations:

<table border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">


<colgroup>
<col  class="left" />

<col  class="left" />

<col  class="left" />

<col  class="left" />

<col  class="left" />
</colgroup>
<thead>
<tr>
<th scope="col" class="left">to\form</th>
<th scope="col" class="left">las</th>
<th scope="col" class="left">xyz-grid</th>
<th scope="col" class="left">grid</th>
<th scope="col" class="left">grid-filled</th>
</tr>
</thead>

<tbody>
<tr>
<td class="left">grid</td>
<td class="left">X</td>
<td class="left">X</td>
<td class="left">&#xa0;</td>
<td class="left">&#xa0;</td>
</tr>


<tr>
<td class="left">grid-filled</td>
<td class="left">X</td>
<td class="left">X</td>
<td class="left">X</td>
<td class="left">&#xa0;</td>
</tr>


<tr>
<td class="left">hillshade</td>
<td class="left">X</td>
<td class="left">X</td>
<td class="left">x</td>
<td class="left">X</td>
</tr>


<tr>
<td class="left">contour</td>
<td class="left">X</td>
<td class="left">X</td>
<td class="left">X</td>
<td class="left">X</td>
</tr>
</tbody>
</table>

where

-   **grid       :** A Grid which could contain gaps

-   **grid-filled:** A Grid with interpolated values

-   **hillshade  :** Analytical hillshade

-   **contour    :** Iso-value-lines

# Installation

## Saga And haskell-platform

### Linux

    sudo aptitude install haskell-platform
    sudo aptitude install saga

### Windows with Cygwin

-   Get the [haskell-platform](http://www.haskell.org/platform/)

-   Install Saga with [OSGeo4W](http://trac.osgeo.org/osgeo4w/)

-   Put `saga_cmd` in the search path: add `PATH`"$PATH:/cygdrive/c/Program
    Files (x86)/SAGA-GIS"= to your `$HOME/.bashrc`

## saga-cmd-wrapper library

    git clone https://www.github.com/michelk/saga-cmd-wrapper.hs.git
    cd saga-cmd-wrapper.hs
    cabal update && cabal install

The exectuables are usually installed into `$HOME/.cabal/bin`; to
use them you have to put them into your search path. Put this into
your `$HOME/.bashrc`:

    export PATH="$PATH:$HOME/.cabal/bin"

# Usage

## `sagaChain`

`sagaChain` lets you chain `saga_cmd` commands. The program needs the
follwing specification:

-   source-format

-   destination-format

-   parameters to use for conversion

-   input-file

    sagaChain --from xyz-grid --to hillshade --parameters xyzSep=tabulator:xyzCellSize=0.5

# Development

In order to extend functionality

-   find library and module

-   write wrapper-function

-   add default parameters and conversion-function in demConv.hs