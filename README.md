# TidalCycles plugin for Atom
[![Build Status](https://travis-ci.org/tidalcycles/atom-tidalcycles.svg?branch=master)](https://travis-ci.org/tidalcycles/atom-tidalcycles)

[TidalCycles](https://tidalcycles.org) is a live-coding pattern language

For installation instructions, please visit:
  https://tidalcycles.org/index.php/Installation

Then, you can:
  * Open a `.tidal` file
  * `shift+enter` to evaluate the current line or selection
  * `(cmd/ctrl)+enter` to evaluate multiple-lines or selection

To send patterns to [SuperDirt](https://github.com/musikinformatik/SuperDirt), use `d1` .. `d9`, e.g.:
```
d1 $ sound "bd cp"
```

## Configuration

### Interpreter
You can choose between 3 Haskell interpreters:
* Default: ghci installed with Cabal is the default choice
* Stack: ghci installed with stack
* Nix: ghci installed with nix

### Haskell Path

By default the plugin will use the `ghci` and `ghc-pkg` binaries in $PATH configuration.

You can configure your Haskell binary folder to use a different version of it.
(Only works with *Default* interpreter)

### Boot Tidal Path

The plugin will load the `BootTidal.hs` file according to this sequence:
  * if configured, the file set in the  *Boot Tidal Path* configuration
  * if exists, the one in the current directory
  * if exists, the one in the current Tidal installation, given by the `ghc-pkg` binary configured with *Haskell Path*
  * the fallback choice is the one [included with the plugin](lib/BootTidal.hs)

### Autocomplete
You can turn on/off autocomplete with flag.

#### Documentation details with Hoogle
With [hoogle](https://github.com/ndmitchell/hoogle/blob/master/docs/Install.md) the autocomplete experience will improve and official tidal documentation will be shown.

Install hoogle and set the *Hoogle Path* configuration (by default it's already `hoogle`) if you install it with `stack`, add two dashes at the end of the property (e.g. `stack hoogle --`).

After installation you have to generate tidal documentation, in your terminal run:\
`hoogle generate tidal`\
or\
`stack hoogle -- generate tidal` (with stack)

### Other configurations
  * **Filter Prompt From Log Messages**: filter long prompt comming from ghci
  * **Only Log Last Message**: shows only last log message on console
  * **Only Show Log When Errors**: show only errors from ghci


## Contributing

If you'd like to contribute to this package, here are some guidelines:

### JavaScript Formatting

A `.jsbeautifyfc` file is used to define JavaScript formatting settings. Please use
a beautifier package (we recommend `atom-beautify`) to format your changes with
these settings.

### Specs

Always run specs before PR.  
On Atom, execute the `Window: Run Package Specs` command (`ctrl+shift+y`).  
`0 failures` should be the result
