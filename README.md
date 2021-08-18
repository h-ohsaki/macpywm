# NAME

macpywm - A simple but extensible window manager for macOS.

![video](https://github.com/h-ohsaki/macpywm/blob/master/screenshot/video.gif)

# SYNOPSIS

macpywm command [args...]

# DESCRIPTION

This manual page documents **macpywm**, a simple but extensible macOS
window manager written in Python.  **macpywm** is a Python version of
**xpywm** (https://github.com/h-ohsaki/xpywm), an X11 window manager
written in Python.

**macpywm** is built on top of the Yabai
(https://github.com/koekeishiya/yabai), tiling window management for
the Mac.  Specifially, all window management on macOSes are handled
with Yabai.  **macpywm** only provides **xpywm**-compatible functions
such as the programmed window layout, the tiled window layout, and
several **xpywm**-compatible functions.

**macpywm** supports two types of window placement algorithms:
programmed mode and tiled mode.

In the programmed mode, you can specify rules for inferring
appropriate window geometries.  By default, Emacs is placed at the
top-left corner of the screen with 50% window width and 100% window
height.  Web browsers (e.g., Safari) and office applications are
placed next to the Emacs with 50% window width and 100% window height.
The terminal window is placed at the bottom-right corner with 50%
window width and 70% window height.  If there exist more than two
terminal windows, the size of each terminal window is shrunk to 1/4 of
the screen, and placed in a non-overlapping way.

In the titled mode, all windows are placed in a titled fashion so that
any window will have the same window width and height, and that any
window will not overlap with others, as like tile-based window
managers.  Moreover, **macpywm** tries to allocate larger area for
Emacs; i.e., if there are three windows, say, Emacs and two terminals,
Emacs will occupy the half of the screen, and each terminal will have
the quarter of the screen.

# OPTIONS

None

# SCREENSHOTS

![screenshot](https://github.com/h-ohsaki/macpywm/blob/master/screenshot/screenshot-1.png)

![screenshot](https://github.com/h-ohsaki/macpywm/blob/master/screenshot/screenshot-2.png)

# INSTALLATION

1. Save two configuration files (`.yabairc` and `.skhdrc`) in your
   home directory.

  - `.yabairc`
    https://github.com/h-ohsaki/macpywm/blob/master/.yabairc
  - `.skhdrc`
    https://github.com/h-ohsaki/macpywm/blob/master/.skhdrc

2. Install yabai (https://github.com/koekeishiya/yabai) and skhd
   (https://github.com/koekeishiya/skhd).

```sh
$ brew install koekeishiya/formulae/yabai
$ brew services start yabai
$ brew install koekeishiya/formulae/skhd
$ brew services start skhd
```

See yabai wiki (https://github.com/koekeishiya/yabai/wiki) for the
installation details.

Note that yabai and skhd configuration files (`.yabairc` and
`.skhdrc`) must not be overwritten.

3. Install macpywm from PyPI (https://pypi.org/project/macpywm/)

```sh
$ pip3 install macpywm
```

# CUSTOMIZATION

Since Python is one of interpreters, you can easily customize the
behavior of **macpywm** by directly modifying its variables,
functions, and methods.  For instance, if you want to customize the
rules for the programmed window placement, simply edit the definition
of the variable LAYOUT_RULES.

# BINDINGS

- Ctrl + Mod1 + i

  Focus the next window.  Available windows are circulated in the order of
  top-left, bottom-left, top-right, and bottom-right.

- Ctrl + Mod1 + '

  Toggle the maximization of the current active window.

- Ctrl + Mod1 + ;

  Toggle the vertical maximization of the current active window.

- Ctrl + Mod1 + ,

  Layout all available windows in the programmed mode.

- Ctrl + Mod1 + .

  Layout all available windows in the tiled mode.

- Ctrl + Mod1 + z

  Destroy the current active window.

- Ctrl + Mod1 + y

  Hide the current active window.

- Ctrl + Mod1 + 1

  Run a command "open -n -a /System/Applications/Utilities/Terminal.app/Contents/MacOS/Terminal".

- Ctrl + Mod1 + 2

  Run a command "open -a emacs --args -rv"

- Ctrl + Mod1 + 3

  Run a command "open -a /Applications/Safari.app/Contents/MacOS/Safari"

# AVAILABILITY

The latest version of **macpywm** is available at PyPI
(https://pypi.org/project/macpywm/) .

# AUTHOR

Hiroyuki Ohsaki <ohsaki[atmark]lsnl.jp>
