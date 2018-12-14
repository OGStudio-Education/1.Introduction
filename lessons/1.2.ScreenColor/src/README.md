
**EN** | [RU][ru]

| < Back | Course | Next > |
|-|-|-|
| [1.1. Distribute][1.1.Distribute] | [1. Introduction][course] | [1.3. Local development][1.3.LocalDev] |

# 1.2. Screen color

In this tutorial we are going to change boring blue screen color to delightful
green one.

Estimated completion time: 15 minutes.

# Table of contents

* [Scripts](#scripts)
    * [API script](#api)
    * [Index script](#index)
* [Set screen color](#color)
* [Change screen color](#change)
* [Hard refresh](#refresh)
* [Summary](#summary)

<a name="scripts"/>

# Scripts

If you watched debug console closely, you should have noticed these lines:

```
main::Example(...) Loading embedded API script
main::Example(...) Successfully loaded embedded API script
main::Example(...) Loading a script from 'https://ogstudio-education.github.io/.../debug.html/../index.lua'
main::Example(...) ERROR Could not load the script. 'Failed. Status code: '404''
```

`ogstudio` is a `C++` application, so you have to build `ogstudio` before you can
use it. Web version is one of `ogstudio` builds we provide here in tutorials.

Since `ogstudio` purpose is to allow you to create games in the shortest time
possible, `ogstudio` has to support scripting, so that you can implement
your ideas without the need to configure and maintain development environment.

`ogstudio` uses `Lua` language for scripting because `Lua` is easy to integrate
and learn. However, we are not going to cover `Lua` language here, you are
expected to know it already. If you have experience with other programming
languages, `Lua` syntax should be easy for you to pick up.

<a name="api"/>

## API script

The purpose of so-called `API script` is to provide `Lua` API for you.
`API script` is embedded into `ogstudio`, `API script` maps `Lua` calls to
`C++` ones.

Here are the traces of `API script` in debug console:

```
main::Example(...) Loading embedded API script
main::Example(...) Successfully loaded embedded API script
```

<a name="index"/>

## Index script

Debug console also reports the problem of loading so-called `index script`,
`index.lua` file:

```
main::Example(...) Loading a script from 'https://ogstudio-education.github.io/.../debug.html/../index.lua'
main::Example(...) ERROR Could not load the script. 'Failed. Status code: '404''
```

This file does not yet exist, that's why it couldn't be loaded.

`Index script` contains **your** ideas expressed in `Lua`. This is where you
are going set screen color to delightful green.

<a name="color"/>

# Set screen color

Let's create `index.lua` file with the following contents:

```
main.application.camera.clearColor = {0, 1, 0}
```

| № | Action | Screenshot |
|-|-|-|
| 1. | Hit `Create new file` | ![screen-create-file] |
| 2. | Name file as `index.lua` | ![screen-name-file] |
| 3. | Add contents mentioned before | ![screen-file-contents] |
| 4. | Save file by hitting `Commit new file` | ![screen-file-save] |

Now you should see delightful green color:

![screen-green]

If you look at debug console, you should see the following lines:

```
main::Example(...) Loading a script from 'https://ogstudio-education.github.io/.../debug.html/../index.lua'
main::Example(...) Successfully loaded the script
main::Example(...) Successfully executed script
```

This means the script has been loaded, parsed, and executed successfully.

<a name="change"/>

# Change screen color

Let's see into API you used in `index.lua`:

// FEATURE main/API
// FEATURE main.application/API
// FEATURE main.application.camera/API
// FEATURE main.application.camera.clearColor/API

Now let's try to set red color instead of the green one:

| № | Action | Screenshot |
|-|-|-|
| 1. | Select `index.lua` | ![screen-select-index] |
| 2. | Start editing the file | ![screen-edit-index] |
| 3. | Change color to red | ![screen-change-color] |
| 4. | Save file by hitting `Commit changes` | ![screen-edit-save] |

Check the result. You might see green color again. If so, this is because
your web browser cached previous `index.lua` contents. To get rid of that
cache, you need to perform so-called `hard refresh`.

<a name="refresh"/>

# Hard refresh

Each web browser performs `hard refresh` in response to different key combinations.

Try the following combinations:

* hold `shift`, `alt`, `ctrl`, `command` alone or together and click the `Reload` button
* hold `shift`, `alt`, `ctrl`, `command` alone or together and press `F5`
* hold `shift`, `alt`, `ctrl`, `command` alone or together and press `R`

If none of these combinations work, try searching for a key combination of
your specific web browser in the Internet.

Once you do `hard refresh`, you should see red color:

![screen-red]

**Notes**:

* `GitHub Pages` take a few seconds to publish your files, too, so
if nothing changes in a couple of minutes, you did not perform `hard refresh`.
* to work around caching you may also try private browsing mode (incognito), however, `ogstudio` web version does not work in some web browsers when such mode is enabled

<a name="summary"/>

# Summary

You have successfully:

* set screen color with `main.application.camera.clearColor`
* found out about web browser cache that may drive you crazy if you forget about it

Here's API you used:

// FEATURE main/API
// FEATURE main.application/API
// FEATURE main.application.camera/API
// FEATURE main.application.camera.clearColor/API

| < Back | Course | Next > |
|-|-|-|
| [1.1. Distribute][1.1.Distribute] | [1. Introduction][course] | [1.3. Local development][1.3.LocalDev] |

[ru]: README-ru.md

[course]: ../../README.md
[1.1.Distribute]: ../1.1.Distribute/README.md
[1.3.LocalDev]: ../1.3.LocalDev/README.md

[screen-create-file]: readme/create-file.png
[screen-name-file]: readme/name-file.png
[screen-file-contents]: readme/file-contents.png
[screen-file-save]: readme/file-save.png
[screen-green]: readme/screen-green.png
[screen-red]: readme/screen-red.png
[screen-select-index]: readme/select-index.png
[screen-edit-index]: readme/edit-index.png
[screen-change-color]: readme/change-color.png
[screen-edit-save]: readme/edit-save.png
