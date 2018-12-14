
**EN** | [RU][ru]

# 1. Introduction

This document is part of [OGStudio education program][education]. 
The document is designed to be used as an assignment for you to complete.
See [OGStudio education program][education] for details.

This is an introductory course to game development with `ogstudio`.

# Lessons

**Note**: the course is in development, so the list of lessons is not yet final.

| Lesson | Description | Estimated completion time |
|-|-|-|
| [1.1. Distribute][1.1.Distribute] | Distribute web version of the simplest `ogstudio` game with `GitHub Pages` | 5 minutes |
| [1.2. Screen color][1.2.ScreenColor] | Set screen color with `Lua` script | 15 minutes |
| [1.3. Local development][1.3.LocalDev] | Change screen color locally, without `GitHub Pages` | 10 minutes |
| [1.4. Mouse][1.4.Mouse] | Toggle screen color on mouse clicks (finger taps) | 10 minutes |

# API

Lessons use the following API:

* `main` namespace hosts `application` instance
* `main.application` instance hosts subsystems like `camera`
* `main.application.camera` instance is a viewport into application's scene
* `main.application.camera.clearColor` property is a clearing color (effectively background color) of the camera
    * **accepts** array of color components in RGB format
        ```lua
        main.application.camera.clearColor = {1, 0, 0}
        ```
    * **returns** array of color components in RGB format
        ```lua
        local color = main.application.camera.clearColor
        print("background color:", color[1], color[2], color[3])
        ```

[ru]: README-ru.md

[education]: http://opengamestudio.org/pages/education.html
[1.1.Distribute]: lessons/1.1.Distribute/README.md
[1.2.ScreenColor]: lessons/1.2.ScreenColor/README.md
[1.3.LocalDev]: lessons/1.3.LocalDev/README.md
[1.4.Mouse]: lessons/1.4.Mouse/README.md

