# sway-borders

<<<<<<< HEAD
sway-borders is a fork of [Sway](https://swaywm.org), an [i3](https://i3wm.org/)-compatible [Wayland](http://wayland.freedesktop.org/) compositor. It introduces some new features like more customizable borders, but is otherwise kept up to date with [sway](https://github.com/swaywm/sway).

Please refer to the [Sway GitHub](https://github.com/swaywm/sway/) for docs and related material which isn't related to the new features below.

## Installation
The following package distributions exist. If you package sway-borders for another distribution, feel free to PR its entry here.
|Distribution|Name|Maintainer|
|---|---|---|
|AUR|`sway-borders-git`|TheAvidDev|

Releases will follow Sway's.

To compile from source, follow the same procedure as Sway [here](https://github.com/swaywm/sway#compiling-from-source).

# Features
 - [X] Border images (allow for drop shadows, outer curved borders, etc.)
 - [ ] Curved borders (inner)
 - [ ] Blur
 - And more, see [sway#3380](https://github.com/swaywm/sway/issues/3380)
 
Descriptions and usage of the features can be found below. If you would like some more features that won't be added by Sway, feel free to request them for this project instead.

## Border Images
This feature allows the use of eight images that get snapped on to the corners and edges of windows. This allows for any combination of outer curved borders, drop shadows, and multi-layer borders. These border images are drawn wherever gaps normally appear.

### Configuration
Directly from the manpage:
```
*border_images.<class>* <path>
	Configures the images used for borders. The _path_ is expected to be an
	absolute path to an image with an odd width and height which will be scaled to
	container sizes. The edges are expected to be 1 pixel in width for top and
	bottom edges, and 1 pixel in height for left edges as they will be stretched
	across container edges.

	For the classes below, "container" refers to a container which has gaps
	around it. The available classes are:
	
	*border_images.focused*
		The container which is focused or has a window that has focus.

	*border_images.focused_inactive*
		The container which has the most recently focused view within a container
		which is not focused.

	*border_images.unfocused*
		A container with all of its views unfocused.

	*border_images.urgent*
		A container which has view with an urgency hint. *Note*: Native Wayland windows do not
		support urgency. Urgency only works for Xwayland windows.
```

In less technical terms, you can draw your borders around a 1x1 pixel in the center of your image. This image doesn't have to be a square, but for offsets across a single axis, you have to use completely transparent pixels since the center of the image will always be used.

Unlike pixel borders, the border images will overflow into gaps, so you may have to alter your gaps to accomidate.

To use this in your config, you would probably use the following:
```
border_images.focused /some/folder/
border_images.focused_inactive /some/folder/
border_images.unfocused /some/folder/
border_images.urgent /some/folder/
```

The [`/contrib/borders/` folder](https://github.com/TheAvidDev/sway-borders/tree/master/contrib/borders/) contains some example and community contributed border images, alongside screenshots. Feel free to add your own and make a PR!

## Rounded Borders
While the border images allow for rounded borders to be added on the _outside_ of containers, always increasing the total size of the container. An option to round the inner borders, cropping the container content itself is planned.

## Blur
It would be nice to add bluring of semi-transparent windows since it's hard to use them with more complex backgrounds. This has quite a few nuances and may even require a custom wlroots build, we'll see.

See: [sway#4356](https://github.com/swaywm/sway/issues/4356)
=======
**[English][en]** - [日本語][ja] - [Français][fr] - [Українська][uk] - [Español][es] - [Polski][pl] - [中文-简体][zh-CN] - [Deutsch][de] - [Nederlands][nl] - [Русский][ru] - [中文-繁體][zh-TW] - [Português][pt] - [Danish][dk] - [한국어][ko] - [Română][ro]

sway is an [i3]-compatible [Wayland] compositor. Read the [FAQ]. Join the
[IRC channel] \(#sway on irc.freenode.net).

## Release Signatures

Releases are signed with [E88F5E48] and published [on GitHub][GitHub releases].

## Installation

### From Packages

Sway is available in many distributions. Try installing the "sway" package for
yours.

If you're interested in packaging sway for your distribution, stop by the IRC
channel or shoot an email to sir@cmpwn.com for advice.

### Compiling from Source

Check out [this wiki page][Development setup] if you want to build the HEAD of
sway and wlroots for testing or development.

Install dependencies:

* meson \*
* [wlroots]
* wayland
* wayland-protocols \*
* pcre
* json-c
* pango
* cairo
* gdk-pixbuf2 (optional: system tray)
* [scdoc] (optional: man pages) \*
* git (optional: version info) \*

_\*Compile-time dep_

Run these commands:

    meson build
    ninja -C build
    sudo ninja -C build install

On systems without logind, you need to suid the sway binary:

    sudo chmod a+s /usr/local/bin/sway

Sway will drop root permissions shortly after startup.

## Configuration

If you already use i3, then copy your i3 config to `~/.config/sway/config` and
it'll work out of the box. Otherwise, copy the sample configuration file to
`~/.config/sway/config`. It is usually located at `/etc/sway/config`.
Run `man 5 sway` for information on the configuration.

## Running

Run `sway` from a TTY. Some display managers may work but are not supported by
sway (gdm is known to work fairly well).

[en]: https://github.com/swaywm/sway#readme
[ja]: https://github.com/swaywm/sway/blob/master/README.ja.md
[fr]: https://github.com/swaywm/sway/blob/master/README.fr.md
[uk]: https://github.com/swaywm/sway/blob/master/README.uk.md
[es]: https://github.com/swaywm/sway/blob/master/README.es.md
[pl]: https://github.com/swaywm/sway/blob/master/README.pl.md
[zh-CN]: https://github.com/swaywm/sway/blob/master/README.zh-CN.md
[de]: https://github.com/swaywm/sway/blob/master/README.de.md
[nl]: https://github.com/swaywm/sway/blob/master/README.nl.md
[ru]: https://github.com/swaywm/sway/blob/master/README.ru.md
[zh-TW]: https://github.com/swaywm/sway/blob/master/README.zh-TW.md
[pt]: https://github.com/swaywm/sway/blob/master/README.pt.md
[dk]: https://github.com/swaywm/sway/blob/master/README.dk.md
[ko]: https://github.com/swaywm/sway/blob/master/README.ko.md
[ro]: https://github.com/swaywm/sway/blob/master/README.ro.md
[i3]: https://i3wm.org/
[Wayland]: http://wayland.freedesktop.org/
[FAQ]: https://github.com/swaywm/sway/wiki
[IRC channel]: http://webchat.freenode.net/?channels=sway&uio=d4
[E88F5E48]: https://keys.openpgp.org/search?q=34FF9526CFEF0E97A340E2E40FDE7BE0E88F5E48
[GitHub releases]: https://github.com/swaywm/sway/releases
[Development setup]: https://github.com/swaywm/sway/wiki/Development-Setup
[wlroots]: https://github.com/swaywm/wlroots
[scdoc]: https://git.sr.ht/~sircmpwn/scdoc
>>>>>>> upstream/master
