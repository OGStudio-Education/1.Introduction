
**EN** | [RU][ru]

| < Back | Course | Next > |
|-|-|-|
| [1.3. Local development][1.3.LocalDev] | [1. Introduction][course] | [1.5. Scene node][1.5.SceneNode] |

# 1.4. Mouse

In this tutorial we are going to toggle screen color on mouse clicks
(finger taps).

Estimated completion time: 10 minutes.

# Table of contents

* [Detect mouse presses and releases](#press)
* [Detect mouse clicks](#click)
* [Introduce color toggler](#toggler)
* [Toggle screen color](#screen)
* [Summary](#summary)

<a name="press"/>

# Detect mouse presses and releases

To track mouse, we are going to use `main.application.mouse`:

* `main.application.mouse` instance lets you get current mouse (finger) properties like position, pressed mouse buttons and subscribe to changes of the properties
* `main.application.mouse.pressedButtonsChanged` is a notification instance (`core.Reporter`) that reports notifications when any mouse button (finger) is pressed or released
    * **to subscribe** to all notifications, use `core.Reporter`'s `addCallback()` method:
        ```lua
        main.application.mouse.pressedButtonsChanged:addCallback(
            function()
                print("A mouse button or finger has been pressed or released")
            end
        )
        ```


Let's subscribe to mouse press / release notifications. Update `index.lua`
to have the following contents:

```lua
main.application.mouse.pressedButtonsChanged:addCallback(
    function()
        print("Detected a mouse press / release")
    end
)
```

**Notes**:

* `pressedButtonsChanged` is a notification instance we subscribe to
* `addCallback()` is a method of `pressedButtonsChanged` notification instance
* `pressedButtonsChanged` and `addCallback` are separated by `:` because it's a method call
* `function() ... end` block represents a callback function (closure) to be executed each time notification is reported

You should see the following output in the debug console:

```
Detected a mouse press / release
Detected a mouse press / release
```

<a name="click"/>

# Detect mouse clicks

As you see, each mouse click or finger tap results in two lines
printed in the debug console. That's because both presses and releases
are reported.

To track a click, we need to:

1. tell presses from releases
1. make sure a press is followed by a release

**1)** To tell a press from a release, we should consult
`main.application.mouse.pressedButtons`:

* `main.application.mouse.pressedButtons` is a list of currently pressed mouse buttons (fingers)
    ```lua
    for _, button in pairs(main.application.mouse.pressedButtons)
    do
        print("Button", button, "is currently pressed")
    end
    ```


**2)** To simplify implementation, we can treat a release as a click.

Update the callback function to look like this:

```lua
function()
    -- Detect a click.
    if (#main.application.mouse.pressedButtons == 0)
    then
        print("Detected a mouse click")
    end
end
```

**Notes**:

* `#` returns the number of items of an array
* for simplicity we only check if all buttons are released, i.e., there are no `pressedButtons`

Now each click should result in a single line printed in the debug console.

<a name="toggler"/>

# Introduce color toggler

Introduce `colorToggler` instance to toggle between two colors.
Add the following code to the beginning of `index.lua`:

```lua
-- Define color toggling functionality.
local colorToggler = {
    -- List of colors to toggle between.
    colors = {
        {0, 1, 0}, -- Green.
        {1, 0, 0}, -- Red.
    },
    -- Keep track of which color is selected.
    isFirstColorSelected = true,
    -- Return toggled color.
    toggledColor = function(self)
        self.isFirstColorSelected = not self.isFirstColorSelected
        if (self.isFirstColorSelected)
        then
            return self.colors[1]
        else
            return self.colors[2]
        end
    end,
}
```

**Notes**:

* `colorToggler` instance is a `Lua` table with two variables to keep state and one function to toggle that state
* `colorToggler` can be seen as an instance of a class in other programming languages
* `local` means variable is local to current scope, otherwise variables are global
* `Lua` starts array indexing from `1`, not `0` (like `C`)
* comments start with `--` in `Lua`

<a name="screen"/>

# Toggle screen color

The only thing left now is to call `colorToggler` upon mouse clicks
(finger taps). Update the callback function to look like this:

```lua
function()
    -- Detect a click.
    if (#main.application.mouse.pressedButtons == 0)
    then
        -- Toggle screen color.
        local color = colorToggler:toggledColor()
        print("Set screen color to", color[1], color[2], color[3])
        main.application.camera.clearColor = color
    end
end
```

Now click the screen. It should toggle its color between red and green:

![video-result]

<a name="summary"/>

# Summary

You have successfully:

* reacted to mouse clicks by subscribing to `main.application.mouse.pressedButtonsChanged`
* implemented `colorToggler` to toggle between red and green
* used `colorToggler` together with `main.application.mouse.pressedButtonsChanged` and `main.application.camera.clearColor` to toggle the screen color

Here's new `ogstudio` API you used:

* `main.application.mouse` instance lets you get current mouse (finger) properties like position, pressed mouse buttons and subscribe to changes of the properties
* `main.application.mouse.pressedButtons` is a list of currently pressed mouse buttons (fingers)
    ```lua
    for _, button in pairs(main.application.mouse.pressedButtons)
    do
        print("Button", button, "is currently pressed")
    end
    ```

* `main.application.mouse.pressedButtonsChanged` is a notification instance (`core.Reporter`) that reports notifications when any mouse button (finger) is pressed or released
    * **to subscribe** to all notifications, use `core.Reporter`'s `addCallback()` method:
        ```lua
        main.application.mouse.pressedButtonsChanged:addCallback(
            function()
                print("A mouse button or finger has been pressed or released")
            end
        )
        ```


Here's final [index.lua][index.lua] you should have now.

| < Back | Course | Next > |
|-|-|-|
| [1.3. Local development][1.3.LocalDev] | [1. Introduction][course] | [1.5. Scene node][1.5.SceneNode] |

[ru]: README-ru.md

[course]: ../../README.md
[1.3.LocalDev]: ../1.3.LocalDev/README.md
[1.5.SceneNode]: ../1.5.SceneNode/README.md
[index.lua]: index.lua

[video-result]: readme/result.gif
