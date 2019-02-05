
**EN** | [RU][ru]

| < Back | Course | Next > |
|-|-|-|
| [1.2. Screen color][1.2.ScreenColor] | [1. Introduction][course] | [1.4. Mouse][1.4.Mouse] |

# 1.3. Local development

Even though you can develop `ogstudio` games right at `GitHub`, there are a
few things that slow the process down:

* you have to wait for `GitHub Pages` to publish your updates
* you have to perform `hard reset`

To speed the process up, in this tutorial we're going to show you how to
develop `ogstudio` games locally, without `GitHub Pages`.

Estimated completion time: 10 minutes.

# Table of contents

* [Install Git and Python](#intall)
* [Clone repository](#clone)
* [Launch locally](#launch)
* [Change screen color](#change)
* [Summary](#summary)


<a name="install"/>

# Install Git and Python

To start developing locally, you need to have `git` and `python` installed.

We need `git` because `GitHub` manages `git` repositories. Have a look
here for possible [installation options of Git][git].

We need `python` because simple HTTP server (located at
`tools/simple-cors-http-sever.py`) is written in Python (just a few lines of
code). Have a look here for possible [installation options of Python][python].

## Linux

If you have Linux, you should install `git` and `python` by Linux distribution
package manager.

E.g., here's how to do it with `Debian`-based distributions:

```
apt install git python
```

## macOS

If you have macOS, you already have `python` installed. To get `git`, you can
install `Xcode` and its `command-line tools`.

## Verify Git and Python installation

To check if `git` works, run `git --version` command in console:

```
$ git --version
git version 2.15.1 (Apple Git-101)
```

To check if `python` works, run `python --version` command in console:

```
$ python --version
Python 2.7.10
```

<a name="clone"/>

# Clone repository

To work locally, you first need to clone repository from `GitHub` to your
hard drive:

| № | Action | Notes | Screenshot |
|-|-|-|-|
| 1 | Hit `Clone or download` | | ![screen-clone] |
| 2 | Copy repository URL into clipboard | | ![screen-clone-url] |
| 3 | Clone repository to your hard drive | `git clone <repository URL>`| `git clone https://github.com/OGStudio-Education/1-introduction-kornerr`<br><br>`Cloning into '1-introduction-kornerr'...`<br>`remote: Enumerating objects: 68, done.`<br>`remote: Counting objects: 100% (68/68), done.`<br>`remote: Compressing objects: 100% (46/46), done.`<br>`remote: Total 68 (delta 22), reused 60 (delta 20), pack-reused 0`<br>`Unpacking objects: 100% (68/68), done.` |

<a name="launch"/>

# Launch locally

Run simple HTTP server from the directory where `index.lua` is located:

```
$ cd /path/to/1.Introduction
$ ./tools/simple-cors-http-server.py 15000
```

You should see output similar to this:

```
Serving HTTP on 0.0.0.0 port 15000 ...
```

This means HTTP server is serving the directory you run it from at port
`15000`.

Now go to [http://localhost:15000](http://localhost:15000). You should see red
screen:

![screen-red]

<a name="change"/>

# Change screen color

Let's change the screen color to yellow. Update `index.lua` so that it
contains the following:

```
main.application.camera.clearColor = {1, 1, 0}
```

Go to [http://localhost:15000](http://localhost:15000). You should see yellow
screen now:

![screen-yellow]

**Note**: your web browser did not cache `index.lua` because simple HTTP
server does not provide HTTP headers to control cache life time.
`GitHub Pages`, however, provide HTTP headers to control cache life time,
that's why we needed `hard reset` in the previous tutorial.

<a name="summary"/>

# Summary

You have successfully changed screen color locally and instantly saw result
without web browser cache wizardry.

| < Back | Course | Next > |
|-|-|-|
| [1.2. Screen color][1.2.ScreenColor] | [1. Introduction][course] | [1.4. Mouse][1.4.Mouse] |

[ru]: README-ru.md

[course]: ../../README.md
[1.2.ScreenColor]: ../1.2.ScreenColor/README.md
[1.4.Mouse]: ../1.4.Mouse/README.md

[git]: https://git-scm.com/downloads
[python]: https://www.python.org/downloads

[screen-clone]: readme/clone.png
[screen-clone-url]: readme/clone-url.png
[screen-clone-repo]: readme/clone-repo.png
[screen-red]: readme/screen-red.png
[screen-yellow]: readme/screen-yellow.png
